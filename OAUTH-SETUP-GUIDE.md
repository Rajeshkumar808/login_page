# OAuth Setup Guide - Google & GitHub Integration

## Overview

The authentication flow now includes fully functional Google and GitHub OAuth integration. This guide walks you through setup for both providers.

---

## 🔵 Google OAuth Setup

### Step 1: Create Google Cloud Project

1. **Go to**: [Google Cloud Console](https://console.cloud.google.com/)
2. **Sign in** with your Google account
3. **Create new project**:
   - Click project dropdown (top-left)
   - Click **"New Project"**
   - Enter name: `Premium Auth Flow` (or your choice)
   - Click **"Create"**

### Step 2: Enable Google+ API

1. **Search** for "Google+ API"
2. **Click** the result
3. **Click "Enable"**
4. Wait for it to enable (30 seconds)

### Step 3: Create OAuth Credentials

1. **Go to**: **APIs & Services** → **Credentials** (left sidebar)
2. **Click**: **"Create Credentials"** (blue button, top)
3. **Select**: **"OAuth client ID"**
4. **If prompted** to create consent screen:
   - Click **"Configure Consent Screen"**
   - Choose **"External"** for User Type
   - Fill in:
     - **App name**: Premium Auth Flow
     - **User support email**: your-email@gmail.com
     - **Developer contact**: your-email@gmail.com
   - **Save and continue** through all screens
   - Return to credentials creation

5. **On OAuth 2.0 Client ID screen**:
   - **Application type**: Web application
   - **Name**: Premium Auth Flow Web Client
   - **Authorized JavaScript origins** (Add these):
     ```
     http://localhost:3000
     http://localhost:8000
     http://localhost
     https://yourdomain.com
     ```
   - **Authorized redirect URIs** (Add these):
     ```
     http://localhost:3000/
     http://localhost:3000/callback
     http://localhost:8000/
     http://localhost:8000/callback
     http://localhost/
     http://localhost/callback
     https://yourdomain.com/callback
     https://yourdomain.com/
     ```

6. **Click "Create"**
7. **Copy your credentials**:
   - **Client ID**: (looks like `xxxx.apps.googleusercontent.com`)
   - **Client Secret**: (keep this secret!)

### Step 4: Add to Code

In `auth-flow-complete.html`, find this section:

```javascript
const OAUTH_CONFIG = {
    google: {
        clientId: 'YOUR_GOOGLE_CLIENT_ID.apps.googleusercontent.com',
        // ... rest of config
    }
};
```

Replace `YOUR_GOOGLE_CLIENT_ID` with your actual Client ID:

```javascript
const OAUTH_CONFIG = {
    google: {
        clientId: '123456789.apps.googleusercontent.com', // Your actual ID
        redirectUri: window.location.origin,
        authEndpoint: 'https://accounts.google.com/o/oauth2/v2/auth',
        scopes: ['openid', 'profile', 'email']
    }
};
```

---

## ⚫ GitHub OAuth Setup

### Step 1: Register New OAuth Application

1. **Go to**: [GitHub Settings](https://github.com/settings/developers)
   - Or: GitHub → Settings (top-right) → Developer settings → OAuth Apps
2. **Click**: **"New OAuth App"**

### Step 2: Fill Application Details

| Field | Value |
|-------|-------|
| **Application name** | Premium Auth Flow |
| **Homepage URL** | `http://localhost:3000` or your domain |
| **Authorization callback URL** | `http://localhost:3000/callback` |
| **Application description** | Premium authentication design demo |

### Step 3: Get Credentials

1. **After creation**, you'll see:
   - **Client ID**: (32 character string)
   - **Client Secret**: (click "Generate" if needed)

2. **Copy both values** (keep secret safe)

### Step 4: Add to Code

In `auth-flow-complete.html`, find:

```javascript
const OAUTH_CONFIG = {
    github: {
        clientId: 'YOUR_GITHUB_CLIENT_ID',
        // ... rest of config
    }
};
```

Replace with your actual ID:

```javascript
const OAUTH_CONFIG = {
    github: {
        clientId: 'abc123def456ghi789', // Your actual ID
        redirectUri: window.location.origin,
        authEndpoint: 'https://github.com/login/oauth/authorize',
        scopes: ['user:email', 'read:user']
    }
};
```

---

## 🚀 Implementation Options

### Option 1: Demo Mode (Current - No Backend)

**Current setup**: Buttons show demo popups

```javascript
// Demonstrates the flow without actual OAuth
handleGoogleLogin() → Shows demo alert → User sees success message
```

**Pros**:
- ✅ Works instantly
- ✅ No backend needed
- ✅ Perfect for UI/design demo

**Cons**:
- ❌ No actual authentication
- ❌ For design preview only

**How to test**:
1. Open `auth-flow-complete.html` in browser
2. Click Google/GitHub buttons
3. See demo success message

---

### Option 2: Production Backend

**Requires**: Node.js + Express backend

#### Step 1: Create Backend Server

**Create `server.js`**:

```javascript
const express = require('express');
const axios = require('axios');
const cors = require('cors');
const session = require('express-session');
require('dotenv').config();

const app = express();

app.use(express.json());
app.use(cors());
app.use(session({
    secret: process.env.SESSION_SECRET,
    resave: false,
    saveUninitialized: true
}));

// Google OAuth Token Exchange
app.post('/api/auth/google', async (req, res) => {
    const { code } = req.body;

    try {
        const response = await axios.post('https://oauth2.googleapis.com/token', {
            code,
            client_id: process.env.GOOGLE_CLIENT_ID,
            client_secret: process.env.GOOGLE_CLIENT_SECRET,
            redirect_uri: process.env.REDIRECT_URI,
            grant_type: 'authorization_code'
        });

        const { access_token } = response.data;

        // Get user info
        const userResponse = await axios.get(
            'https://www.googleapis.com/oauth2/v2/userinfo',
            { headers: { Authorization: `Bearer ${access_token}` } }
        );

        // Create session/JWT
        req.session.user = {
            id: userResponse.data.id,
            email: userResponse.data.email,
            name: userResponse.data.name,
            provider: 'google'
        };

        res.json({ success: true, user: req.session.user });
    } catch (error) {
        res.status(400).json({ error: error.message });
    }
});

// GitHub OAuth Token Exchange
app.post('/api/auth/github', async (req, res) => {
    const { code } = req.body;

    try {
        const response = await axios.post('https://github.com/login/oauth/access_token', {
            client_id: process.env.GITHUB_CLIENT_ID,
            client_secret: process.env.GITHUB_CLIENT_SECRET,
            code,
            redirect_uri: process.env.REDIRECT_URI
        }, {
            headers: { Accept: 'application/json' }
        });

        const { access_token } = response.data;

        // Get user info
        const userResponse = await axios.get(
            'https://api.github.com/user',
            { headers: { Authorization: `token ${access_token}` } }
        );

        // Create session/JWT
        req.session.user = {
            id: userResponse.data.id,
            email: userResponse.data.email,
            name: userResponse.data.name,
            username: userResponse.data.login,
            provider: 'github'
        };

        res.json({ success: true, user: req.session.user });
    } catch (error) {
        res.status(400).json({ error: error.message });
    }
});

// Get current user
app.get('/api/auth/user', (req, res) => {
    if (!req.session.user) {
        return res.status(401).json({ error: 'Not authenticated' });
    }
    res.json(req.session.user);
});

// Logout
app.post('/api/auth/logout', (req, res) => {
    req.session.destroy();
    res.json({ success: true });
});

// Email/Password Login
app.post('/api/auth/login', (req, res) => {
    const { email, password } = req.body;

    // Validate against your database
    // This is a simplified example
    if (!email || !password) {
        return res.status(400).json({ error: 'Email and password required' });
    }

    // In production: Hash password, check against DB
    req.session.user = {
        email,
        provider: 'email'
    };

    res.json({ success: true, user: req.session.user });
});

// Email/Password Signup
app.post('/api/auth/signup', (req, res) => {
    const { fullName, email, password, phone } = req.body;

    // Validate
    if (!fullName || !email || !password) {
        return res.status(400).json({ error: 'Missing required fields' });
    }

    // In production:
    // 1. Hash password
    // 2. Check if email exists
    // 3. Save to database
    // 4. Send verification email

    req.session.user = {
        name: fullName,
        email,
        phone,
        provider: 'email'
    };

    res.json({ success: true, user: req.session.user });
});

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

**Create `.env` file**:

```env
GOOGLE_CLIENT_ID=your_google_client_id
GOOGLE_CLIENT_SECRET=your_google_secret
GITHUB_CLIENT_ID=your_github_client_id
GITHUB_CLIENT_SECRET=your_github_secret
REDIRECT_URI=http://localhost:3000/callback
SESSION_SECRET=your_secret_key_here
PORT=5000
```

#### Step 2: Update Frontend Code

**In your frontend JS** (replace demo handlers):

```javascript
// Google OAuth
async function handleGoogleLogin(event) {
    event.preventDefault();
    const btn = event.currentTarget;
    btn.disabled = true;
    btn.classList.add('loading');

    const params = new URLSearchParams({
        client_id: OAUTH_CONFIG.google.clientId,
        redirect_uri: OAUTH_CONFIG.google.redirectUri,
        response_type: 'code',
        scope: OAUTH_CONFIG.google.scopes.join(' '),
        access_type: 'offline'
    });

    window.location.href = `${OAUTH_CONFIG.google.authEndpoint}?${params.toString()}`;
}

// GitHub OAuth
async function handleGitHubLogin(event) {
    event.preventDefault();
    const btn = event.currentTarget;
    btn.disabled = true;
    btn.classList.add('loading');

    const params = new URLSearchParams({
        client_id: OAUTH_CONFIG.github.clientId,
        redirect_uri: OAUTH_CONFIG.github.redirectUri,
        scope: OAUTH_CONFIG.github.scopes.join(' ')
    });

    window.location.href = `${OAUTH_CONFIG.github.authEndpoint}?${params.toString()}`;
}

// Handle OAuth Callback
async function checkOAuthCallback() {
    const params = new URLSearchParams(window.location.search);
    const code = params.get('code');
    const state = params.get('state');
    const error = params.get('error');

    if (error) {
        showAlert(`OAuth Error: ${error}`, 'error', 'login');
        return;
    }

    if (code) {
        // Determine provider (Google or GitHub)
        const provider = determineProvider(); // Implement logic
        
        try {
            const response = await fetch(`/api/auth/${provider}`, {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify({ code })
            });

            const data = await response.json();
            
            if (data.success) {
                showAlert('✓ Sign in successful!', 'success', 'login');
                // Redirect to dashboard
                setTimeout(() => window.location.href = '/dashboard', 1500);
            }
        } catch (error) {
            showAlert('Authentication failed', 'error', 'login');
        }
    }
}
```

#### Step 3: Install Dependencies

```bash
npm install express axios cors express-session dotenv
```

#### Step 4: Start Server

```bash
node server.js
# Server running on port 5000
```

---

## 📋 Testing Checklist

### Local Testing (Demo Mode)

- [ ] Open `auth-flow-complete.html` in browser
- [ ] Click "Get Started" on Welcome page
- [ ] On Login page, click "Continue with Google"
- [ ] Verify demo alert appears
- [ ] Click "Continue with GitHub"
- [ ] Verify demo alert appears
- [ ] Go to Sign Up page (click "Create Account")
- [ ] Test social buttons there
- [ ] Test form validation (invalid email, mismatched passwords)
- [ ] Test password toggle
- [ ] Test "Remember me" checkbox
- [ ] Test responsive on mobile (375px viewport)

### Production Testing (With Backend)

- [ ] Ensure `.env` file is configured
- [ ] Backend server is running (`node server.js`)
- [ ] Click Google login
- [ ] Redirects to Google consent screen
- [ ] Approve permissions
- [ ] Redirected back to app with user data
- [ ] Session is created
- [ ] User info displays correctly
- [ ] Test logout functionality
- [ ] Test with different OAuth providers
- [ ] Test error handling (reject permissions)

---

## 🔒 Security Best Practices

### 1. Environment Variables
- ✅ Never commit `.env` to git
- ✅ Store secrets in environment variables
- ✅ Use `.env.example` as template

### 2. HTTPS in Production
- ✅ Always use HTTPS (not HTTP)
- ✅ Set secure cookie flags
- ✅ Use CSP headers

### 3. CSRF Protection
```javascript
// Add CSRF tokens to forms
<input type="hidden" name="csrf_token" value="<%= csrfToken %>">
```

### 4. Rate Limiting
```javascript
const rateLimit = require('express-rate-limit');

const limiter = rateLimit({
    windowMs: 15 * 60 * 1000,
    max: 100
});

app.post('/api/auth/*', limiter);
```

### 5. Password Security
```javascript
const bcrypt = require('bcrypt');

// Hash password
const salt = await bcrypt.genSalt(10);
const hashedPassword = await bcrypt.hash(password, salt);

// Verify password
const isValid = await bcrypt.compare(password, hashedPassword);
```

---

## 🐛 Troubleshooting

### Issue: "Redirect URI mismatch"

**Solution**:
- Check OAuth app settings match your URL
- For localhost: `http://localhost:3000`
- For production: `https://yourdomain.com`
- Add all URLs to allowed list

### Issue: "Invalid client ID"

**Solution**:
- Verify Client ID is copied correctly
- Check for extra spaces
- Confirm it matches OAuth app settings

### Issue: "CORS error"

**Solution**:
```javascript
// Add CORS headers
app.use(cors({
    origin: process.env.CLIENT_URL,
    credentials: true
}));
```

### Issue: "Authorization code expired"

**Solution**:
- Codes expire quickly (usually 10 minutes)
- Handle immediately after callback
- Implement error handling

### Issue: "Can't get user email from GitHub"

**Solution**:
- Ensure `user:email` scope is included
- Make separate request to `/user/emails` endpoint
- GitHub doesn't always return email in main user object

---

## 📦 Deployment Checklist

**Before going live**:

- [ ] Replace demo mode with production backend
- [ ] Set up environment variables on server
- [ ] Enable HTTPS with valid SSL certificate
- [ ] Add authorized redirect URIs to OAuth apps
- [ ] Implement CSRF protection
- [ ] Add rate limiting
- [ ] Enable secure session cookies
- [ ] Set up database for user storage
- [ ] Implement email verification
- [ ] Set up password reset flow
- [ ] Add user consent logging
- [ ] Test complete auth flow end-to-end
- [ ] Load testing under expected traffic
- [ ] Security audit
- [ ] Monitor failed authentication attempts

---

## 📚 Useful Resources

- [Google OAuth 2.0 Docs](https://developers.google.com/identity/protocols/oauth2)
- [GitHub OAuth Docs](https://docs.github.com/en/developers/apps/building-oauth-apps)
- [OAuth 2.0 Security Best Practices](https://www.ietf.org/rfc/rfc6749.html)
- [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)

---

## 🎯 Quick Start (Demo Mode)

1. **Open** `auth-flow-complete.html` in browser
2. **Click** any social button
3. **See** demo success message
4. No configuration needed! ✓

---

## 🚀 Quick Start (Production)

1. **Set up Google OAuth** (see above)
2. **Set up GitHub OAuth** (see above)
3. **Add Client IDs** to `OAUTH_CONFIG`
4. **Deploy backend** server
5. **Configure redirect URIs**
6. **Test** complete flow
7. **Monitor** authentication logs

---

**Version**: 1.0  
**Last Updated**: 2024  
**Status**: Ready for Implementation
