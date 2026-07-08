# Premium Auth Flow - Quick Reference Guide

## 🎯 Design System Overview

### Color Tokens
```
Primary:     #6366F1  (Indigo)
Secondary:   #8B5CF6  (Purple)
Accent:      #06B6D4  (Cyan)
BG Primary:  #0B1020  (Deep Navy)
BG Sec:      #111827  (Dark Blue)
Text:        #FFFFFF  (White)
Text-2:      #94A3B8  (Slate)
Text-3:      #64748B  (Gray)
```

### Spacing (8px Grid)
- xs: 4px | sm: 8px | md: 16px | lg: 24px | xl: 32px | 2xl: 48px

### Border Radius
- sm: 8px | md: 12px | lg: 20px

### Shadows
```css
shadow-sm:   0 4px 8px rgba(0,0,0,0.2)
shadow-md:   0 8px 32px rgba(0,0,0,0.3) + inset highlight
shadow-lg:   0 12px 24px rgba(99,102,241,0.4)
glow:        0 0 20px rgba(99,102,241,0.3)
```

---

## 🧩 Component Inventory

### BUTTONS (6 variants)
| Component | Width | Height | Padding | States |
|-----------|-------|--------|---------|--------|
| Primary | Auto | 48px | 12/24 | default, hover, active, disabled |
| Secondary | Auto | 48px | 12/24 | default, hover, disabled |
| Text | Auto | 24px | 0 | default, hover |
| Social | 280px | 48px | 12/24 | default, hover |
| Small | Auto | 40px | 10/16 | default, hover |
| Large | Auto | 56px | 14/32 | default, hover |

### INPUTS (6 states)
| Input Type | Height | Padding | States |
|-----------|--------|---------|--------|
| Text | 44px | 12/16 | default, focus, filled, error, success, disabled |
| Password | 44px | 12/16 | default, focus, filled, error, success, disabled |
| Tel/Number | 44px | 12/16 | default, focus, filled, error, success, disabled |

### CARDS (3 types)
| Card | Padding | Corner R | Effects |
|------|---------|----------|---------|
| Glassmorphism | 32px | 20px | blur(20px), shadow-md |
| Feature | 16px | 12px | blur(10px), shadow-sm |
| Social Button | 12/24px | 12px | blur(10px), shadow-sm |

### FORM ELEMENTS
| Element | Size | States |
|---------|------|--------|
| Checkbox | 18×18px | unchecked, checked, disabled |
| Label | 13px | default, required |
| Helper Text | 12px | default, error |
| Error Message | 12px | error state |

### TYPOGRAPHY (7 styles)
| Style | Size | Weight | Usage |
|-------|------|--------|-------|
| H1 | 42px | 700 | Page titles |
| H2 | 32px | 700 | Section heads |
| H3 | 20px | 700 | Card titles |
| Body | 16px | 400 | Descriptions |
| Body Small | 14px | 400 | Default text |
| Label | 13px | 600 | Form labels |
| Caption | 12px | 500 | Helper text |

---

## 📄 PAGE LAYOUTS

### Page 1: Welcome (Split Screen)
```
┌─────────────────────────────────────┐
│                                     │
│  [Illustration]    [Welcome Card]   │
│  + Floating Items  • Logo          │
│                   • Heading        │
│                   • Subtitle       │
│                   • 3 Features     │
│                   • 2 Buttons      │
│                   • Footer Links   │
│                                     │
└─────────────────────────────────────┘
```

### Page 2: Login (Center Card)
```
┌─────────────────────────────────────┐
│                                     │
│          [Login Card]               │
│        • Logo                       │
│        • Heading: "Welcome Back"    │
│        • Email Input                │
│        • Password Input (toggle)    │
│        • Remember Me + Forgot       │
│        • Sign In Button             │
│        • Divider                    │
│        • 2 Social Buttons           │
│        • Footer: "Create Account"   │
│                                     │
└─────────────────────────────────────┘
```

### Page 3: Sign Up (Center Card)
```
┌─────────────────────────────────────┐
│                                     │
│        [Sign Up Card]               │
│        • Logo                       │
│        • Heading: "Create Account"  │
│        • Full Name Input            │
│        • Email Input                │
│        • Phone Input                │
│        • Password Input (toggle)    │
│        • Confirm Password (toggle)  │
│        • Terms Checkbox             │
│        • Create Button              │
│        • Divider                    │
│        • 2 Social Buttons           │
│        • Footer: "Sign In"          │
│                                     │
└─────────────────────────────────────┘
```

---

## 🎬 Interaction Flows

### Welcome → Login
```
"Get Started" button → On Tap → Navigate → Login
"I already have..." → On Tap → Navigate → Login
Animation: Smart Animate, 300ms, ease-out
```

### Login ↔ Sign Up
```
Login "Create Account" → Navigate → Sign Up
Sign Up "Sign In" → Navigate → Login
Animation: Smart Animate, 300ms, ease-out
```

### Form Interactions
```
Input Focus:       Border primary, glow effect, 200ms
Password Toggle:   Icon swap, instant
Checkbox:          Gradient fill, 200ms
Button Hover:      Elevation +2px, glow, 300ms
Button Active:     Scale down slightly, 100ms
```

---

## 🎨 Design Specifications Quick Check

### 8px Grid
- ✅ All layouts use 8px grid
- ✅ Padding: 8, 16, 24, 32, 48px
- ✅ Gaps: 8, 16, 24px

### Auto Layout (Figma)
- ✅ All containers use Auto Layout
- ✅ Cards: Column, 24px gap, 32px padding
- ✅ Buttons: Row, 12/24 padding, centered

### Glassmorphism
- ✅ Background: rgba(255,255,255,0.05)
- ✅ Border: rgba(255,255,255,0.1)
- ✅ Backdrop: blur(20px)
- ✅ Shadow: Inset + drop shadow

### Responsive (Mobile 375px)
- ✅ Cards: 100% width - 24px padding
- ✅ Buttons: 44px height minimum
- ✅ Inputs: 44px height minimum
- ✅ Text: Scale down H1 to 32px
- ✅ Illustration: Hidden on mobile

### Accessibility
- ✅ Contrast: 12.5:1 (white on #0B1020)
- ✅ Touch targets: 44×44px minimum
- ✅ Focus states: 2px ring + glow
- ✅ Color not only indicator
- ✅ Icons + text together

---

## 💾 Export Checklist

### File Naming Convention
```
btn-{type}-{state}.svg
├─ btn-primary-default.svg
├─ btn-primary-hover.svg
├─ btn-secondary-default.svg
├─ input-text-default.svg
├─ input-text-focus.svg
├─ card-glass-default.svg
└─ icon-{name}.svg
```

### Export Settings
- **Format**: SVG (vectors)
- **Density**: 2x for high DPI
- **Size**: Exact pixel dimensions
- **Path**: `/assets/components/`

### Design Token Exports
```javascript
// colors.js
export const colors = {
  primary: '#6366F1',
  secondary: '#8B5CF6',
  accent: '#06B6D4',
  // ... etc
}

// spacing.js
export const spacing = {
  xs: '4px',
  sm: '8px',
  md: '16px',
  // ... etc
}

// shadows.js
export const shadows = {
  sm: '0 4px 8px rgba(0,0,0,0.2)',
  md: '0 8px 32px rgba(0,0,0,0.3)',
  // ... etc
}
```

---

## 🔍 Quality Checklist (Pre-Handoff)

### Design System
- [ ] All colors created as styles
- [ ] All typography as text styles
- [ ] All shadows as effects
- [ ] All components have variants
- [ ] Component documentation complete

### Pages
- [ ] Welcome page complete
- [ ] Login page complete
- [ ] Sign Up page complete
- [ ] Mobile variants created
- [ ] All text using text styles
- [ ] All colors using color styles

### Interactions
- [ ] All buttons have click states
- [ ] All inputs have focus states
- [ ] Navigation flows connected
- [ ] Animation timing consistent
- [ ] Prototype preview works

### Accessibility
- [ ] Contrast ratios checked
- [ ] Touch targets 44×44px+
- [ ] Focus states visible
- [ ] Color has icon support
- [ ] Form labels present

### Assets
- [ ] Components exported as SVG
- [ ] Icon library complete
- [ ] Naming convention applied
- [ ] 2x density provided
- [ ] Zipped for delivery

---

## 📊 Figma File Stats

**Estimated File Size**: 8-12MB
**Component Count**: 30+
**Color Styles**: 15+
**Text Styles**: 7+
**Artboards**: 6 (3 desktop + 3 mobile)
**Layers**: 200+
**Design Time**: 20-30 hours

---

## 🚀 Developer Implementation Checklist

### HTML/CSS
- [ ] Recreate components in CSS
- [ ] Use CSS variables for tokens
- [ ] Implement Auto Layout equivalent
- [ ] Add hover/focus states
- [ ] Test accessibility

### React
- [ ] Create Button component
- [ ] Create Input component
- [ ] Create Card component
- [ ] Manage form state
- [ ] Add form validation
- [ ] Implement navigation

### Testing
- [ ] Test all interactions
- [ ] Mobile responsive test
- [ ] Accessibility audit
- [ ] Performance check
- [ ] Cross-browser testing

---

## 🎓 Design Principles Applied

1. **Modern Minimalism** - Clean, spacious, purposeful
2. **Glassmorphism** - Translucent with blur effects
3. **Consistency** - Unified design language
4. **Hierarchy** - Clear visual priority
5. **Feedback** - Visible states & animations
6. **Accessibility** - WCAG AA compliant
7. **Performance** - Optimized assets
8. **Scalability** - Component-based system
9. **Premium Feel** - Subtle gradients & effects
10. **Developer Ready** - Clear specs & tokens

---

## 📚 Inspiration References

- **Linear**: Minimalist UI, clean typography
- **Stripe**: Premium design, gradient use
- **Framer**: Modern animations, micro-interactions
- **Notion**: Spacious, clear hierarchy
- **Apple**: Premium aesthetic, elegant design
- **Vercel**: Dark mode, modern gradients

---

## ⚡ Pro Tips

1. **Use component variants** instead of copying components
2. **Master Auto Layout** for responsive design
3. **Create design tokens** in Figma using plugins (Tokens Studio)
4. **Document everything** for developer handoff
5. **Test prototypes** on different screen sizes
6. **Use grid smartly** for alignment without over-constraining
7. **Layer naming** should follow component structure
8. **Create variants** for all interactive states
9. **Use guides** for consistent spacing
10. **Export batches** to save time

---

## 🆘 Common Issues & Solutions

### Issue: Components not resizing with content
**Solution**: Check Auto Layout settings. Ensure "Hug contents" or "Fill container" is set correctly.

### Issue: Glassmorphism blur not working
**Solution**: Use backdrop filter in CSS, not blur effect on shape. In Figma, apply to entire card frame.

### Issue: Mobile layout broken
**Solution**: Use constraints or resize components smartly. Test on actual mobile frame (375×812).

### Issue: Colors don't match on export
**Solution**: Export as SVG with color preservation. Use sRGB color space.

### Issue: Animations feel slow
**Solution**: Standard is 300ms for most interactions. Use ease-out for enter, ease-in for exit.

---

## 📞 Quick Links

- **Figma Design System**: [Your Figma Link]
- **Design Tokens**: See FIGMA-DESIGN-SPEC.md
- **Build Instructions**: See FIGMA-BUILD-GUIDE.md
- **Component Library**: Components page in Figma
- **Prototype**: Play button in Figma (top right)

---

**Version**: 1.0  
**Last Updated**: 2024  
**Status**: Production Ready ✓

💡 **Pro Tip**: Keep this guide open while building. Reference it frequently!
