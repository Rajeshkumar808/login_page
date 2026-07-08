# Premium Auth Flow - Figma Build Guide

## Complete Step-by-Step Instructions for Figma

---

## 🚀 Part 1: Initial Setup

### Step 1: Create New File
1. **File** → **New**
2. Name: `Premium Auth Flow - Design System`
3. **Default Artboard**: Delete
4. **Settings**: Enable "Grid" (8px)
   - View → **Show grid**
   - File → **Preferences** → **Grid** → 8px

### Step 2: Set Up Workspace
1. **Create Pages** in order:
   - 📄 Components
   - 📄 Design System
   - 📄 Page 1: Welcome
   - 📄 Page 2: Login
   - 📄 Page 3: Sign Up
   - 📄 Mobile Variants
   - 📄 Prototype Notes
   - 📄 Assets

2. **Enable** → **Settings** → **Collaborators** (Add team if needed)

### Step 3: Set Up Color Library

**Go to**: **Assets** panel (left sidebar) → **Colors** → **+**

Create these color styles:

#### Background Colors
- **Name**: `bg/primary` | **Color**: #0B1020
- **Name**: `bg/secondary` | **Color**: #111827

#### Action Colors
- **Name**: `color/primary` | **Color**: #6366F1
- **Name**: `color/secondary` | **Color**: #8B5CF6
- **Name**: `color/accent` | **Color**: #06B6D4

#### Text Colors
- **Name**: `text/primary` | **Color**: #FFFFFF
- **Name**: `text/secondary` | **Color**: #94A3B8
- **Name**: `text/tertiary` | **Color**: #64748B

#### Semantic Colors
- **Name**: `color/error` | **Color**: #EF4444
- **Name**: `color/success` | **Color**: #10B981
- **Name**: `color/warning` | **Color**: #F59E0B

#### Border & Overlay
- **Name**: `border/default` | **Color**: rgba(255, 255, 255, 0.1)
- **Name**: `border/light` | **Color**: rgba(255, 255, 255, 0.05)
- **Name**: `overlay/hover` | **Color**: rgba(255, 255, 255, 0.08)

---

## ✍️ Part 2: Typography System

**Go to**: **Assets** panel → **Typography**

### Create Text Styles

#### Heading 1
1. **Create new text style** → **+**
2. **Name**: `Heading/H1`
3. **Font**: Poppins
4. **Weight**: Bold (700)
5. **Size**: 42px
6. **Line Height**: 1.2 (50px)
7. **Letter Spacing**: -0.5px
8. **Text Color**: `text/primary`
9. **Save**

#### Heading 2
- **Name**: `Heading/H2`
- **Size**: 32px
- **Weight**: 700
- **Line Height**: 1.3

#### Heading 3
- **Name**: `Heading/H3`
- **Size**: 20px
- **Weight**: 700
- **Line Height**: 1.4

#### Body Regular
- **Name**: `Body/Regular`
- **Size**: 16px
- **Weight**: 400
- **Line Height**: 1.6
- **Color**: `text/secondary`

#### Body Small
- **Name**: `Body/Small`
- **Size**: 14px
- **Weight**: 400
- **Line Height**: 1.5

#### Label
- **Name**: `Label/Default`
- **Size**: 13px
- **Weight**: 600
- **Line Height**: 1.4
- **Letter Spacing**: 0.5px
- **Transform**: Uppercase
- **Color**: `text/secondary`

#### Caption
- **Name**: `Caption/Small`
- **Size**: 12px
- **Weight**: 500
- **Letter Spacing**: 0.3px
- **Color**: `text/tertiary`

---

## 🎭 Part 3: Effects & Shadows

**Assets** panel → **Shadows** (some Figma versions)
Or: Create shadow presets in components

### Create Shadow Styles

#### Shadow SM
1. **Name**: `Shadow/sm`
2. **Effect Type**: Drop Shadow
3. **Color**: #000000
4. **Opacity**: 20%
5. **X**: 0, **Y**: 4
6. **Blur**: 8
7. **Spread**: 0

#### Shadow MD
- **Name**: `Shadow/md`
- **Color**: #000000
- **Opacity**: 30%
- **Y**: 8, **Blur**: 32
- **Spread**: 0
- **Add second shadow**:
  - **Type**: Inner shadow
  - **Color**: #FFFFFF
  - **Opacity**: 10%
  - **Y**: 1, **Blur**: 0

#### Shadow LG
- **Name**: `Shadow/lg`
- **Color**: #6366F1
- **Opacity**: 40%
- **Y**: 12, **Blur**: 24
- **Spread**: 0

#### Glow Effect
- **Name**: `Shadow/glow`
- **Color**: #6366F1
- **Opacity**: 30%
- **Y**: 0, **Blur**: 20
- **Spread**: 0

---

## 🧩 Part 4: Create Main Components

### Component 1: Button - Primary

1. **Page**: Components
2. **Create new frame**: 200×48px
3. **Name**: `Button/Primary`
4. **Auto Layout**: 
   - Direction: Horizontal
   - Padding: 12px 24px
   - Gap: 8px
   - Align: Center

5. **Fill**: Gradient (Linear)
   - 135deg angle
   - #6366F1 → #8B5CF6
   
6. **Stroke**: None
7. **Corner Radius**: 12px
8. **Effects**:
   - Shadow: `Shadow/md`
   - Add shadow: `Shadow/glow`

9. **Text inside**:
   - **Name**: "Label"
   - **Content**: "Get Started"
   - **Style**: `Body/Small`
   - **Color**: White

10. **Right-click** → **Create component**

### Component 2: Button - Secondary

1. **Duplicate** Button/Primary
2. **Name**: `Button/Secondary`
3. **Fill**: rgba(255, 255, 255, 0.05)
4. **Stroke**: 1px, `border/default`
5. **Shadow**: Only `Shadow/sm`
6. **Hover variant**:
   - **Right-click** → **Add variant**
   - **Name**: `Button/Secondary:hover`
   - **Fill**: rgba(255, 255, 255, 0.08)
   - **Stroke**: 1px, rgba(255, 255, 255, 0.2)

### Component 3: Button - Text

1. **Create new frame**: 140×24px
2. **Name**: `Button/Text`
3. **Auto Layout**: Disabled
4. **Fill**: None
5. **Text**:
   - **Content**: "Forgot Password?"
   - **Color**: `color/accent`
   - **Weight**: 600
   - **Size**: 14px

6. **Right-click** → **Create component**

### Component 4: Button - Social

1. **Create frame**: 280×48px
2. **Name**: `Button/Social`
3. **Auto Layout**:
   - Direction: Horizontal
   - Padding: 12px 24px
   - Gap: 10px
   - Alignment: Center

4. **Fill**: rgba(255, 255, 255, 0.03)
5. **Stroke**: 1px, `border/default`
6. **Corner Radius**: 12px
7. **Add icon** (32×32px):
   - Name: "Icon"
   - Content: "🔵" or use Google/GitHub icon
   
8. **Add text** (after icon):
   - Name: "Label"
   - Content: "Continue with Google"
   - Style: `Body/Small`
   - Color: White

9. **Create component**

### Component 5: Input Field

1. **Create frame**: 280×44px
2. **Name**: `Input/Text/Default`
3. **Auto Layout**:
   - Direction: Horizontal
   - Padding: 12px 16px
   - Gap: 8px

4. **Fill**: rgba(255, 255, 255, 0.05)
5. **Stroke**: 1px, `border/default`
6. **Corner Radius**: 12px
7. **Add text layer**:
   - **Name**: "Placeholder"
   - **Content**: "you@example.com"
   - **Color**: `text/tertiary`
   - **Style**: `Body/Small`

8. **Create component**

9. **Create variants**:
   - `Input/Text:focus` (Stroke: primary, Background: lighter)
   - `Input/Text:error` (Stroke: #EF4444)
   - `Input/Text:success` (Stroke: #10B981)
   - `Input/Text:disabled` (Opacity: 50%)

### Component 6: Checkbox

1. **Create frame**: 18×18px (square)
2. **Name**: `Checkbox/Unchecked`
3. **Fill**: Transparent
4. **Stroke**: 1px, rgba(255, 255, 255, 0.2)
5. **Corner Radius**: 4px
6. **Create component**

7. **Duplicate** → **Checkbox/Checked**
8. **Fill**: Gradient (primary)
9. **Add text**: "✓" (white, centered)
10. **Create component**

### Component 7: Card - Glassmorphism

1. **Create frame**: 500×600px (typical)
2. **Name**: `Card/Glass`
3. **Auto Layout**:
   - Direction: Column
   - Padding: 32px
   - Gap: 24px
   - Fill: 100%

4. **Fill**: rgba(255, 255, 255, 0.05)
5. **Stroke**: 1px, `border/default`
6. **Corner Radius**: 20px
7. **Effects**:
   - Blur: 20px (Backdrop filter)
   - Add shadow: `Shadow/md`
   - Add inner stroke for inset effect

8. **Create component**

### Component 8: Feature Card

1. **Create frame**: 280×100px
2. **Name**: `Card/Feature`
3. **Auto Layout**:
   - Direction: Row
   - Padding: 16px
   - Gap: 16px

4. **Fill**: rgba(255, 255, 255, 0.03)
5. **Stroke**: 1px, rgba(255, 255, 255, 0.08)
6. **Corner Radius**: 12px
7. **Children**:
   - **Icon** (24×24px): Gradient background
   - **Text group**: Flex column, gap 2px
     - Title: 14px, 600 weight
     - Description: 13px, secondary color

8. **Create component**

### Component 9: Form Label

1. **Create text frame**
2. **Name**: `Label/Form`
3. **Style**: `Label/Default`
4. **Create component**

### Component 10: Divider

1. **Create frame**: 400×32px
2. **Name**: `Divider/Text`
3. **Auto Layout**:
   - Direction: Row
   - Gap: 16px
   - Alignment: Center

4. **Left line** (flex: 1):
   - Height: 1px
   - Fill: Gradient rgba(255,255,255,0) → rgba(255,255,255,0.1) → rgba(255,255,255,0)
   
5. **Center text**:
   - Content: "Or continue with"
   - Style: `Caption/Small`
   - Color: `text/tertiary`

6. **Right line**: Same as left

7. **Create component**

---

## 📄 Part 5: Design Page 1 - Welcome Screen

### Step 1: Create Artboard
1. **Page**: "Page 1: Welcome"
2. **Create new frame**: 1440×1024px
3. **Name**: "Welcome - Desktop"
4. **Fill**: Color `bg/primary`

### Step 2: Add Background
1. **Add rectangle** (full size)
2. **Name**: "Background Gradient"
3. **Fill**: Gradient
   - 135deg
   - #0B1020 → #1a1f3a → #0B1020
4. **Lock** this layer
5. **Add second rectangle** (for animated blobs):
   - **Name**: "Blob - Primary"
   - **Width/Height**: 500px
   - **Fill**: Radial gradient, primary color
   - **Opacity**: 15%
   - **Blur**: 100px
   - **Position**: 20%, 30%
   - **Constraints**: Fix size, absolute positioning

6. **Duplicate blob** with secondary color at 80%, 70%

### Step 3: Add Grid Pattern (Optional)
1. **Create rectangle** (full artboard)
2. **Name**: "Grid Pattern"
3. **Fill**: None
4. **Stroke pattern**: 
   - Create SVG pattern or use a subtle grid overlay
   - Opacity: 2%

### Step 4: Build Content Section
1. **Create frame**: 1400×800px
2. **Name**: "Content"
3. **Auto Layout**:
   - Direction: Row (left-right)
   - Gap: 48px
   - Padding: 48px
   - Alignment: Center, vertical center

### Step 5: Left Side - Illustration
1. **Create frame**: 600×500px
2. **Name**: "Illustration"
3. **Fill**: Linear gradient with primary/secondary colors
4. **Stroke**: 1px, `border/default`
5. **Corner Radius**: 20px
6. **Effect**: Blur 10px
7. **Add placeholder text**:
   - Font size: 64px
   - Content: "👥✨🎨"
   - Center aligned

8. **Add floating elements**:
   - **Floating card 1**: 200×120px
     - Style: Glassmorphism (lighter)
     - Position: Absolute, top: 50px, left: 40px
   - **Floating card 2**: 150×150px
     - Position: bottom: 80px, right: 60px
   - **Floating card 3**: 180×100px
     - Position: top: 200px, right: 40px

9. **Add animations to floating elements** (will do in prototype step)

### Step 6: Right Side - Welcome Card
1. **Insert component**: `Card/Glass`
2. **Name**: "Welcome Card"
3. **Width**: Auto (but max 500px)
4. **Add children in order**:

   **Logo**
   - Create frame: 40×40px
   - Fill: Gradient primary
   - Corner radius: 12px
   - Add text: "⚡"
   - Center aligned

   **App Name**
   - Apply style: `Label/Default`
   - Content: "Premium Auth"
   - Margin top: 16px

   **Heading**
   - Apply style: `Heading/H1`
   - Content: "Welcome"
   - Margin top: 8px

   **Subtitle**
   - Apply style: `Body/Regular`
   - Content: "Manage everything in one place with a fast, secure, and modern experience."

   **Features Container**
   - Create frame, Auto Layout, Column
   - Gap: 8px
   - Insert 3× `Card/Feature`
   - Customize text for each:
     1. Icon: 🔒 | Title: "Secure Authentication" | Desc: "Enterprise-grade security"
     2. Icon: ⚡ | Title: "Fast Performance" | Desc: "Lightning-quick load times"
     3. Icon: 📱 | Title: "Responsive Design" | Desc: "Works on all devices"

   **Button Group**
   - Create frame, Auto Layout, Column
   - Gap: 8px
   - Insert `Button/Primary`
     - Change text to "Get Started"
   - Insert `Button/Text`
     - Change text to "I already have an account"

   **Footer Links**
   - Create frame, Auto Layout, Row
   - Add divider on top
   - Add 2 links: "Privacy Policy" | "Terms of Service"
   - Style: `Caption/Small`

### Step 7: Responsive Variant
1. **Duplicate** entire welcome artboard
2. **Resize**: 375×812px (mobile)
3. **Name**: "Welcome - Mobile"
4. **Hide**: Illustration side
5. **Adjust**: 
   - Padding to 24px
   - Gap to 24px
   - Card width to 100%
   - Heading to 32px
   - Button height to 44px

---

## 📄 Part 6: Design Page 2 - Login Screen

### Step 1: Create Artboard
1. **Page**: "Page 2: Login"
2. **Create frame**: 1440×1024px
3. **Name**: "Login - Desktop"
4. **Fill**: `bg/primary`

### Step 2: Add Background (same as Welcome)
1. **Copy backgrounds** from Page 1
2. **Paste** into this artboard

### Step 3: Build Center Container
1. **Create frame**: 420×600px
2. **Name**: "Login Container"
3. **Center** on artboard (use auto layout on parent if needed)
4. **Alignment**: Center, both directions

### Step 4: Build Login Card
1. **Insert component**: `Card/Glass`
2. **Size**: 420×550px
3. **Add children**:

   **Logo**
   - Copy from Welcome card
   
   **App Name**
   - "Premium Auth"

   **Heading**
   - Style: `Heading/H1`
   - Content: "Welcome Back"

   **Subtitle**
   - Content: "Sign in to continue."

   **Form Group 1: Email**
   - Create frame, Auto Layout, Column
   - Gap: 8px
   - Add: `Label/Form` → "Email"
   - Add: `Input/Text/Default` → "you@example.com"

   **Form Group 2: Password**
   - Create frame, Auto Layout, Column
   - Gap: 8px
   - Add: `Label/Form` → "Password"
   - Add: `Input/Text/Default` → "••••••••"
   - **Add eye icon overlay**:
     - Position: Absolute right
     - Content: "👁️"
     - Cursor: pointer

   **Remember Me + Forgot**
   - Create frame, Auto Layout, Row, Space-between
   - Left: Checkbox + label
     - Add: `Checkbox/Unchecked`
     - Add text: "Remember me"
   - Right: Button/Text → "Forgot Password?"

   **Sign In Button**
   - Insert: `Button/Primary`
   - Full width (constraints)
   - Content: "Sign In"
   - Margin top: 24px

   **Divider**
   - Insert: `Divider/Text`
   - Text: "Or continue with"

   **Social Buttons**
   - Create frame, Auto Layout, Column
   - Gap: 8px
   - Insert 2× `Button/Social`:
     1. "🔵 Continue with Google"
     2. "⚫ Continue with GitHub"

   **Footer**
   - Create frame, Auto Layout, Row
   - Add divider on top (1px stroke)
   - Text: "Don't have an account?"
   - Add link: `Button/Text` → "Create Account"
   - Text align: Center

---

## 📄 Part 7: Design Page 3 - Sign Up Screen

### Follow same steps as Login, but:

1. **Artboard**: 1440×1024px
2. **Card size**: 420×720px (taller for more fields)
3. **Heading**: "Create Account"
4. **Subtitle**: "Join us today."

5. **Form fields (in order)**:
   - Full Name: `Input/Text/Default`
   - Email: `Input/Text/Default`
   - Phone Number: `Input/Text/Default`
   - Password: `Input/Text/Default` + eye icon
   - Confirm Password: `Input/Text/Default` + eye icon

6. **Terms checkbox**:
   - `Checkbox/Unchecked` + label
   - Text: "I agree to the Terms & Conditions"
   - Make "Terms & Conditions" a link

7. **Create Account button**: `Button/Primary`

8. **Divider**: "Or continue with"

9. **Social buttons**: Same as login

10. **Footer**: "Already have an account? Sign In"

---

## 🎬 Part 8: Create Prototype Connections

### Step 1: Enable Prototyping
1. **Page 1** artboard → Select
2. **Right panel** → "Prototype" tab
3. **Interaction settings** visible

### Step 2: Welcome → Login
1. **Select** "Get Started" button
2. **Blue dot** appears (interaction anchor)
3. **Drag** blue dot to "Login" artboard
4. **Interaction type**: "On Tap"
5. **Action**: "Navigate to Page 2: Login"
6. **Animation**: "Smart Animate"
7. **Duration**: 300ms
8. **Easing**: ease-out

### Step 3: Welcome → Also Login
1. **Select** "I already have an account" button
2. **Drag** blue dot to Login artboard
3. **Same settings** as above

### Step 4: Login → Sign Up
1. **Select** "Create Account" link in footer
2. **Drag** blue dot to Sign Up artboard
3. **Animation**: Smart Animate, 300ms

### Step 5: Sign Up → Login
1. **Select** "Sign In" link in footer
2. **Drag** blue dot back to Login artboard
3. **Same animation settings**

### Step 6: Add Hover States
1. **Select** any button
2. **Duplicate** the state artboard
3. **Name**: "Button - Hover"
4. **Modify**: Add glow, change opacity
5. **Create interaction**: "On Hover" → Navigate
6. **Duration**: 0ms (instant visual)

---

## ✨ Part 9: Add Animations

### In Figma (Interactive Components):

1. **Button Hover Animation**:
   - **Create variant** of Button/Primary
   - **Name**: `Button/Primary:hover`
   - **Effects**: 
     - Add glow shadow
     - Increase blur slightly
   - **In prototyping**: "While hovering" trigger

2. **Input Focus Animation**:
   - **Create variant** of Input/Text
   - **Name**: `Input/Text:focus`
   - **Changes**:
     - Stroke color to primary
     - Background lightened
     - Add glow effect
   - **Trigger**: "While focused"

3. **Floating Elements Animation**:
   - **Select** floating element
   - **Duplicate** 3 times
   - **Create animation loop**:
     1. Original position (0s)
     2. Moved up 20px (at 50% timeline)
     3. Original position (at 100% timeline)
   - **Duration**: 6000ms
   - **Loop**: Infinite

4. **Page Transition**:
   - **All navigation interactions**: 300ms, ease-out
   - **Type**: Smart Animate

### Prototype View Testing
1. **Top right**: Click "Play" (▶️)
2. **Test all interactions**
3. **Verify animation timing**
4. **Check mobile view** (if created)

---

## 📊 Part 10: Design System Documentation Page

### Create a page showing:

1. **Color Palette**
   - All colors with hex values
   - Usage guidelines

2. **Typography Scale**
   - All text styles with examples
   - Sizing hierarchy

3. **Component Gallery**
   - All components in different states
   - Examples of proper usage
   - Do's and don'ts

4. **Spacing Grid**
   - 8px grid visualization
   - Padding examples

5. **Effects & Shadows**
   - All shadow examples
   - Backdrop blur examples

6. **Icons & Assets**
   - Icon library
   - SVG exports

---

## 🔄 Part 11: Component Variants Setup

### Create component variants for different states:

**For Buttons:**
```
Button/Primary
├─ Default
├─ Hover
├─ Active
├─ Disabled
└─ Loading

Button/Secondary
├─ Default
├─ Hover
└─ Disabled
```

**For Inputs:**
```
Input/Text
├─ Default
├─ Focus
├─ Filled
├─ Error
├─ Success
├─ Disabled
└─ Loading
```

**For Cards:**
```
Card/Glass
├─ Default
└─ Elevated

Card/Feature
├─ Default
└─ Hover
```

### To create variants in Figma:
1. **Right-click component**
2. **Add component set**
3. **Add property**: "State" (value: Default, Hover, etc.)
4. **Create separate components** for each state
5. **In main selector**: Mix & match

---

## 🎨 Part 12: Mobile Responsive Variants

### Create mobile versions (375×812px):

**Mobile Welcome**
1. Hide illustration
2. Center card only
3. Full width with 24px padding
4. Heading: 32px instead of 42px

**Mobile Login**
1. Same structure as desktop
2. Card: 100% width
3. Buttons: 44px minimum height
4. Input: 44px minimum height
5. Touch padding: 8px between elements

**Mobile Sign Up**
1. Same responsive treatment
2. Consider form scroll
3. Sticky button at bottom (optional)

---

## 📦 Part 13: Asset Preparation

### Export components for development:

1. **Select component**
2. **Right-click** → **Copy as → Copy as SVG**
3. **Or: Export settings**:
   - **Format**: SVG
   - **Suffix**: @1x, @2x

4. **Create export batch**:
   - Select all buttons
   - **Export → SVG** (batch export)
   - Naming: `btn-primary.svg`, `btn-secondary.svg`, etc.

5. **Export locations**:
   - `/images/buttons/`
   - `/images/icons/`
   - `/images/cards/`

---

## ✅ Quality Checklist

- [ ] All colors using color styles
- [ ] All text using text styles
- [ ] All components use Auto Layout
- [ ] All buttons 44px+ touch target
- [ ] Contrast ratios WCAG AA
- [ ] 8px grid alignment throughout
- [ ] All interactions prototyped
- [ ] Mobile variants created
- [ ] Component documentation written
- [ ] Developer handoff notes added
- [ ] Assets exported with naming convention
- [ ] Animations timing consistent (300ms standard)
- [ ] All shadows using shadow styles
- [ ] Form validation states designed
- [ ] Loading states included
- [ ] Disabled states visible
- [ ] Focus states for accessibility
- [ ] Color swatches accessible
- [ ] Typography scale complete
- [ ] Spacing consistent across all pages

---

## 🚀 Part 14: Developer Handoff

### Create handoff documentation:

1. **In Figma**: 
   - **Plugins** → Install "Zeroheight" or "Reflect"
   - **Link Figma file** to design system doc

2. **Create README**:
   ```
   # Premium Auth Flow - Design System
   
   ## Quick Start
   - Components page: Design system overview
   - Design tokens: Colors, spacing, typography
   - Mobile variants: Responsive designs
   
   ## Exporting
   - SVG: Components → Right-click → Copy as SVG
   - Batch: Select folder → Export
   
   ## Development
   - Use color variables: --color-primary, etc.
   - All animations: 300ms ease-out
   - Button sizes: 44px minimum
   - Grid: 8px base spacing
   ```

3. **CSS Variables file**:
   - Create document listing all design tokens
   - Provide in CSS, SCSS, and JSON formats

4. **React component examples**:
   - Show prop variations
   - States management
   - Accessibility props

---

## 📱 Final Deliverables

Your Figma file should now contain:

✅ **Component Library**
- 30+ components with variants
- Fully documented
- Production-ready

✅ **Design System Page**
- Colors, typography, effects
- Usage guidelines
- Spacing grid

✅ **3 Complete Pages**
- Welcome, Login, Sign Up
- Desktop (1440px) + Mobile (375px)
- Fully functional prototype

✅ **Animations**
- Page transitions
- Hover states
- Focus states
- Loading indicators

✅ **Documentation**
- Design specifications
- Developer notes
- Accessibility guidelines
- Export naming conventions

✅ **Prototyping**
- All navigation flows
- Interactive states
- Interaction timing
- Mobile compatible

---

**Estimated Build Time**: 20-30 hours  
**Complexity**: Medium-High  
**Team**: 1-2 designers (1 for components, 1 for pages recommended)

---

Happy designing! 🎨✨
