# Premium Authentication Flow - Figma Design Specification

## Overview
A production-ready 3-page authentication flow inspired by Linear, Stripe, Framer, Notion, Apple, and Vercel. Modern minimalism with glassmorphism, dark theme, and blue-purple gradient accents.

---

## 📐 Canvas & Document Setup

### Artboard Specs
- **Page 1 (Welcome)**: 1440 × 1024px
- **Page 2 (Login)**: 1440 × 1024px
- **Page 3 (Sign Up)**: 1440 × 1024px
- **Device Frame Option**: Create responsive variants at 375px (mobile)

### Document Structure
```
📁 Premium Auth
├── 📄 Components
├── 📄 Design System
├── 📄 Page 1: Welcome
├── 📄 Page 2: Login
├── 📄 Page 3: Sign Up
├── 📄 Assets & Icons
└── 📄 Prototype Notes
```

---

## 🎨 Color Palette & Design Tokens

### Primary Colors
| Token | Value | Usage |
|-------|-------|-------|
| `bg-primary` | #0B1020 | Main background |
| `bg-secondary` | #111827 | Card backgrounds |
| `primary` | #6366F1 | Primary actions, highlights |
| `secondary` | #8B5CF6 | Secondary accent |
| `accent` | #06B6D4 | Links, tertiary actions |
| `text-primary` | #FFFFFF | Main text |
| `text-secondary` | #94A3B8 | Secondary text |
| `text-tertiary` | #64748B | Disabled, subtle text |

### Gradient Definitions
```
primary-gradient: 135deg, #6366F1 0%, #8B5CF6 100%
secondary-gradient: 135deg, #0B1020 0%, #1a1f3a 50%, #0B1020 100%
```

### Opacity Scales
- `border`: rgba(255, 255, 255, 0.1)
- `border-light`: rgba(255, 255, 255, 0.05)
- `hover`: rgba(255, 255, 255, 0.08)
- `focus`: rgba(99, 102, 241, 0.1)

---

## 📏 Spacing System (8px Grid)

| Token | Value | Use Case |
|-------|-------|----------|
| `xs` | 4px | Micro spacing |
| `sm` | 8px | Small gaps |
| `md` | 16px | Standard spacing |
| `lg` | 24px | Large sections |
| `xl` | 32px | Component padding |
| `2xl` | 48px | Section margins |

**Auto Layout**: Enable 8px grid on all frames. Use 16px padding for cards, 8px for internal components.

---

## 🔲 Border Radius & Corners

| Token | Value | Usage |
|-------|-------|-------|
| `radius-sm` | 8px | Small elements, inputs |
| `radius-md` | 12px | Buttons, small cards |
| `radius-lg` | 20px | Main cards, large elements |

---

## ✍️ Typography System

### Font: Poppins (Variable or specific weights)

#### Heading 1 (H1)
- **Size**: 42px
- **Weight**: 700 Bold
- **Line Height**: 1.2 (50px)
- **Letter Spacing**: -0.5px
- **Usage**: Page titles

#### Heading 2 (H2)
- **Size**: 32px
- **Weight**: 700 Bold
- **Line Height**: 1.3
- **Usage**: Section headings

#### Heading 3 (H3)
- **Size**: 20px
- **Weight**: 700 Bold
- **Line Height**: 1.4
- **Usage**: Card titles

#### Body Text (Regular)
- **Size**: 16px
- **Weight**: 400
- **Line Height**: 1.6 (26px)
- **Color**: `text-secondary`
- **Usage**: Descriptions, subtitles

#### Body Small
- **Size**: 14px
- **Weight**: 400
- **Line Height**: 1.5
- **Usage**: Default body text

#### Label
- **Size**: 13px
- **Weight**: 600
- **Line Height**: 1.4
- **Letter Spacing**: 0.5px
- **Text Transform**: Uppercase
- **Usage**: Form labels, captions

#### Caption
- **Size**: 12px
- **Weight**: 500
- **Line Height**: 1.4
- **Letter Spacing**: 0.3px
- **Usage**: Footer text, helper text

---

## 🎭 Effects & Shadows

### Box Shadows

#### Shadow-sm (Subtle hover)
```
0 4px 8px rgba(0, 0, 0, 0.2)
```

#### Shadow-md (Button, card default)
```
0 8px 32px rgba(0, 0, 0, 0.3),
inset 0 1px 0 rgba(255, 255, 255, 0.1)
```

#### Shadow-lg (Interactive hover)
```
0 12px 24px rgba(99, 102, 241, 0.4),
inset 0 1px 0 rgba(255, 255, 255, 0.2)
```

#### Shadow-glow (Accent)
```
0 0 20px rgba(99, 102, 241, 0.3)
```

### Backdrop Filters
- **Blur Value**: 20px (cards)
- **Blur Value**: 10px (secondary elements)

---

## 🧩 Component Library

### 1. Button Component

#### Button - Primary
- **Padding**: 12px 24px
- **Background**: Primary gradient (#6366F1 → #8B5CF6)
- **Text**: White, 14px, 600 weight
- **Border Radius**: 12px
- **Shadow**: Box shadow-md + glow effect
- **Hover State**: 
  - Transform: translateY(-2px)
  - Shadow: Box shadow-lg
  - Opacity on overlay: 10%
- **Active State**: 
  - Transform: translateY(0)
  - Shadow: Reduced

#### Button - Secondary
- **Padding**: 12px 24px
- **Background**: rgba(255, 255, 255, 0.08)
- **Border**: 1px solid `border`
- **Text**: White, 14px, 600 weight
- **Border Radius**: 12px
- **Hover State**:
  - Background: rgba(255, 255, 255, 0.12)
  - Border: 1px solid rgba(255, 255, 255, 0.2)

#### Button - Text
- **Background**: None
- **Border**: None
- **Text**: Accent color (#06B6D4), 14px, 600 weight
- **Hover**: Color changes to #22d3ee

#### Button - Social
- **Padding**: 12px 24px
- **Background**: rgba(255, 255, 255, 0.03)
- **Border**: 1px solid `border`
- **Icon + Text**: Flex, gap 10px
- **Hover State**: 
  - Background: `hover` opacity
  - Transform: translateY(-2px)
  - Border: rgba(255, 255, 255, 0.2)

### 2. Input Component

#### Text Input
- **Padding**: 12px 16px
- **Background**: rgba(255, 255, 255, 0.05)
- **Border**: 1px solid `border`
- **Border Radius**: 12px
- **Font**: Poppins, 14px, 400
- **Text Color**: White
- **Placeholder Color**: `text-tertiary`
- **Focus State**:
  - Background: rgba(255, 255, 255, 0.08)
  - Border: 1px solid rgba(99, 102, 241, 0.5)
  - Box Shadow: 0 0 0 3px rgba(99, 102, 241, 0.1)
  - Outline: None
- **Disabled State**:
  - Opacity: 50%
  - Cursor: not-allowed

### 3. Checkbox Component

#### Checkbox
- **Size**: 18px × 18px
- **Border**: 1px solid rgba(255, 255, 255, 0.2)
- **Border Radius**: 4px
- **Background**: Transparent (default)
- **Checked State**:
  - Background: Primary gradient
  - Border: 1px solid rgba(99, 102, 241, 0.5)
  - Icon: ✓ (white, centered)
- **Hover State**:
  - Border: rgba(255, 255, 255, 0.3)

### 4. Card Component

#### Glassmorphism Card
- **Background**: rgba(255, 255, 255, 0.05)
- **Border**: 1px solid `border`
- **Border Radius**: 20px
- **Padding**: 32px
- **Backdrop Filter**: blur(20px)
- **Box Shadow**: Box shadow-md
- **Inset Border**: 0 1px 0 rgba(255, 255, 255, 0.1)
- **Auto Layout**: Column, Gap 24px
- **Constraints**: Horizontal center, Y center

#### Feature Card
- **Background**: rgba(255, 255, 255, 0.03)
- **Border**: 1px solid rgba(255, 255, 255, 0.08)
- **Border Radius**: 12px
- **Padding**: 16px
- **Layout**: Flex, Row, Gap 16px
- **Hover State**:
  - Background: rgba(255, 255, 255, 0.06)
  - Border: 1px solid rgba(255, 255, 255, 0.12)

### 5. Logo Component
- **Size**: 40px × 40px
- **Background**: Primary gradient
- **Border Radius**: 12px
- **Icon**: Center aligned, white, 20px font
- **Style**: Flex, center all content

### 6. Form Label
- **Font**: 13px, 600 weight
- **Color**: `text-secondary`
- **Transform**: Uppercase
- **Letter Spacing**: 0.5px
- **Margin Bottom**: 8px

### 7. Divider
- **Layout**: Flex, Row, Gap 16px
- **Line**: Gradient from transparent → white 10% → transparent
- **Height**: 1px
- **Text**: 12px, uppercase, `text-tertiary`

---

## 📄 Page 1: Welcome Screen

### Layout
- **Type**: Split screen grid (1fr 1fr)
- **Gap**: 48px
- **Alignment**: Center both columns

### Left Side: Illustration Area
- **Size**: Full height (500px recommended)
- **Main Illustration**:
  - Border Radius: 20px
  - Border: 1px solid `border`
  - Background: Radial gradients (primary & secondary with 20% opacity)
  - Perspective: 3D enabled
  - Content: Centered placeholder (👥✨🎨 or custom illustration)

### Floating Elements (Animated)
- **Element 1**: 200×120px, top: 50px, left: 40px
- **Element 2**: 150×150px, bottom: 80px, right: 60px
- **Element 3**: 180×100px, top: 200px, right: 40px
- **Animation**: Float 6s ease-in-out infinite
- **Style**: Glassmorphism card (semi-transparent)

### Right Side: Welcome Card
- **Type**: Glassmorphism card
- **Max Width**: 500px
- **Content Order**:
  1. Logo (40×40px)
  2. App Name (14px, uppercase)
  3. Heading (42px, bold)
  4. Subtitle (16px, `text-secondary`)
  5. Feature Cards (3 items)
  6. Button Group (Get Started + Text Button)
  7. Footer Links (Privacy, Terms)

### Feature Cards Layout
- **Type**: Flex column
- **Gap**: 8px
- **3 Cards with**:
  - Icon (24×24px, gradient background)
  - Title (14px, bold)
  - Description (13px, secondary)
  - Padding: 16px
  - Border Radius: 12px

---

## 📄 Page 2: Login Screen

### Layout
- **Type**: Center single card
- **Max Width**: 420px
- **Vertical Center**: Yes
- **Horizontal Center**: Yes

### Card Content (Auto Layout)
1. **Logo** (40×40px)
2. **App Name** (14px, uppercase)
3. **Heading**: "Welcome Back" (42px, bold)
4. **Subtitle** (16px, secondary)
5. **Form Fields**:
   - Email input
   - Password input (with show/hide toggle)
   - Remember me + Forgot password link
6. **Primary Button**: "Sign In" (full width)
7. **Divider**
8. **Social Buttons** (Google, GitHub)
9. **Footer Text**: "Don't have an account?"

### Form Elements
- **Form Group**: Flex column, Gap 8px, Margin bottom 24px
- **Input Fields**: Full width, auto layout
- **Password Toggle**: Absolute positioned on right (12px)
- **Remember Me**: Checkbox + label, 18px checkbox
- **Form Links**: Flex between, gap 24px

### Interactive States
- **Focus**: Input glows with primary color
- **Hover Buttons**: Slight elevation
- **Active Buttons**: Press animation

---

## 📄 Page 3: Sign Up Screen

### Layout
- **Same as Login** (centered, 420px max)

### Form Fields (Order)
1. **Logo & App Name**
2. **Heading**: "Create Account" (42px)
3. **Subtitle** (16px)
4. **Full Name** Input
5. **Email** Input
6. **Phone Number** Input
7. **Password** Input (with toggle)
8. **Confirm Password** Input (with toggle)
9. **Terms & Conditions** Checkbox (with link)
10. **Create Account** Button (full width)
11. **Divider**
12. **Social Buttons**
13. **Footer**: "Already have an account?"

### Additional Interactions
- **Form Validation**: Subtle error states (red border, error message)
- **Success**: Green border on valid inputs
- **Password Strength**: Optional indicator below password field

---

## 🎬 Animations & Interactions

### Page Transitions
- **Type**: Smart Animate
- **Duration**: 300ms
- **Easing**: ease-out
- **Effect**: Fade + slight Y translation

### Button Interactions
- **Hover**:
  - Primary: Glow effect, elevation, 0 -2px
  - Secondary: Background change, border highlight
  - Duration: 300ms
  - Easing: ease-out
- **Active/Press**:
  - Scale: 0.98
  - Duration: 100ms
  - Elevation: Reduce

### Input Focus
- **Duration**: 200ms
- **Effect**: 
  - Border color change
  - Background color change
  - Glow box shadow
  - Cursor visible

### Password Toggle
- **Type**: Instant toggle
- **Animation**: Icon fade (cross-dissolve)

### Card Entrance
- **Type**: Fade in + scale up
- **Duration**: 500ms
- **Easing**: ease-out
- **From**: Scale 0.95, opacity 0
- **To**: Scale 1, opacity 1

### Floating Background
- **Type**: Continuous loop
- **Duration**: 20s
- **Easing**: ease-in-out
- **Movement**: Subtle translate + rotate

### Checkbox Animation
- **Type**: Morphing
- **Duration**: 200ms
- **Effect**: Fill gradient, check icon appears

---

## 🔄 Component Prototyping

### Page 1 → Page 2
- **Button**: "Get Started" OR "I already have an account"
- **Interaction**: On Tap
- **Destination**: Page 2
- **Animation**: Smart Animate (300ms, ease-out)

### Page 2 → Page 3
- **Button**: "Create Account" (footer link)
- **Interaction**: On Tap
- **Destination**: Page 3
- **Animation**: Smart Animate (300ms, ease-out)

### Page 3 → Page 2
- **Button**: "Sign In" (footer link)
- **Interaction**: On Tap
- **Destination**: Page 2
- **Animation**: Smart Animate (300ms, ease-out)

### Form Submission
- **Button**: "Sign In" / "Create Account"
- **Animation**: Button pulse + form loading state
- **Duration**: 500ms
- **Effect**: Loading spinner appears, button text fades

---

## 📐 Responsive Variants

### Mobile (375×812px)
- **Hidden Elements**:
  - Illustration side on welcome page
  - Grid becomes single column
- **Card Width**: 100% with padding
- **Font Sizes**: Reduce to 32px headings
- **Padding**: 24px instead of 32px
- **Button Height**: 44px (touch target)
- **Input Height**: 44px (touch target)

### Tablet (768×1024px)
- **Canvas**: 768×1024px
- **Card Max Width**: 500px
- **Layout**: Flex column if needed
- **Spacing**: Adjusted proportionally

---

## 🎨 Design System Components (Figma Library)

Create these as **Main Components** for reuse:

### Buttons
- [ ] Button/Primary
- [ ] Button/Secondary
- [ ] Button/Text
- [ ] Button/Social
- [ ] Button/Small
- [ ] Button/Large

### Inputs
- [ ] Input/Text Default
- [ ] Input/Text Focus
- [ ] Input/Text Error
- [ ] Input/Text Success
- [ ] Input/Text Disabled
- [ ] Input/Password

### Forms
- [ ] Checkbox/Unchecked
- [ ] Checkbox/Checked
- [ ] Checkbox/Disabled
- [ ] Form Label
- [ ] Form Helper Text
- [ ] Form Error Message

### Cards
- [ ] Card/Glassmorphism
- [ ] Card/Feature
- [ ] Card/Social
- [ ] Card/Elevated

### Typography
- [ ] Text/H1
- [ ] Text/H2
- [ ] Text/H3
- [ ] Text/Body
- [ ] Text/Body Small
- [ ] Text/Label
- [ ] Text/Caption

### Other
- [ ] Logo
- [ ] Divider
- [ ] Icon/Google
- [ ] Icon/GitHub
- [ ] Icon/Eye (password toggle)

---

## ♿ Accessibility Guidelines

### Contrast Ratios
- **WCAG AA Compliance**:
  - Primary text on background: 12.5:1 ✓
  - Secondary text on background: 6.2:1 ✓
  - All interactive elements: Minimum 4.5:1

### Touch Targets
- **Minimum Size**: 44×44px (all buttons, inputs)
- **Spacing**: 8px minimum between interactive elements

### Focus States
- **Visible Focus Rings**: 2px solid primary color
- **Glow**: 3px blur, primary color
- **Accessible**: Keyboard navigation supported

### Color Independence
- Don't rely on color alone for status
- Use icons + text + color together
- Example: Error state = red border + ⚠️ icon + text

---

## 🛠️ Developer Handoff

### Export Specifications
- **Format**: SVG for icons, PNG for images
- **Size**: 2x resolution (@ 2x)
- **Naming Convention**: `component-state.svg`
- **Example**: `button-primary-hover.svg`

### CSS Variables (For Development)
```css
:root {
  --color-primary: #6366F1;
  --color-secondary: #8B5CF6;
  --color-accent: #06B6D4;
  --spacing-xs: 4px;
  --spacing-sm: 8px;
  --radius-lg: 20px;
  --shadow-md: 0 8px 32px rgba(0, 0, 0, 0.3);
}
```

### Figma to Code
- **Penpot**: Use "Export" for SVG
- **Zeroheight**: Link Figma for auto documentation
- **Tokens Studio**: Sync design tokens to code

---

## 📋 Implementation Checklist

- [ ] Set up Figma file with 3 pages
- [ ] Create color styles library
- [ ] Create typography text styles
- [ ] Build all button components
- [ ] Build all input components
- [ ] Create card components
- [ ] Design page 1 (Welcome)
- [ ] Design page 2 (Login)
- [ ] Design page 3 (Sign Up)
- [ ] Create prototype connections
- [ ] Add all animations
- [ ] Create responsive variants
- [ ] Add accessibility notes
- [ ] Export assets
- [ ] Create developer documentation
- [ ] User test flow
- [ ] Final polish & review

---

## 🎯 Design Principles Applied

1. **Modern Minimalism**: Clean, spacious, purposeful design
2. **Glassmorphism**: Translucent cards with blur effects
3. **Consistency**: Grid system, spacing, typography hierarchy
4. **Hierarchy**: Clear visual weight for important elements
5. **Feedback**: Hover, focus, and active states on all interactions
6. **Accessibility**: WCAG AA compliant, touch-friendly
7. **Performance**: Optimized assets, smooth animations
8. **Scalability**: Component-based, responsive design
9. **Premium Feel**: Subtle gradients, soft shadows, premium typography
10. **Developer Ready**: Clear specs, organized layers, design tokens

---

## 📚 Design Inspiration References

- **Linear**: Minimalist UI, focus on typography
- **Stripe**: Premium glassmorphism, gradient use
- **Framer**: Modern animations, subtle effects
- **Notion**: Spacious layouts, hierarchy
- **Apple**: Clean design, premium feel
- **Vercel**: Dark mode, blue gradients

---

**Version**: 1.0  
**Last Updated**: 2024  
**Status**: Production Ready ✓
