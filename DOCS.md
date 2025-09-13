# Technical Documentation

This document provides detailed technical information for developers working on the LunarCal.

## 📋 Table of Contents

- [Architecture Overview](#architecture-overview)
- [Code Structure](#code-structure)
- [API Reference](#api-reference)
- [Styling System](#styling-system)
- [State Management](#state-management)
- [Performance Considerations](#performance-considerations)
- [Browser Compatibility](#browser-compatibility)

## 🏗️ Architecture Overview

The LunarCal follows a **single-file architecture** for simplicity and ease of deployment. The entire application is contained within `calendar.html`.

### Design Principles
- **Vanilla JavaScript**: No frameworks to minimize complexity and size
- **CSS Custom Properties**: Enable dynamic theming
- **Progressive Enhancement**: Core functionality works without JavaScript
- **Mobile-First**: Responsive design starting from mobile devices
- **Accessibility**: WCAG 2.1 AA compliance where possible

### Dependencies
- **[lunar-javascript](https://github.com/6tail/lunar-javascript)** v1.6.12: Chinese lunar calendar calculations
- **Modern Browser APIs**: LocalStorage, CSS Custom Properties, Backdrop Filter

## 📁 Code Structure

### HTML Structure
```html
<!DOCTYPE html>
<html>
<head>
  <!-- Meta tags, title, external dependencies -->
  <script src="lunar-javascript CDN"></script>
  <style>
    /* CSS Variables for theming */
    /* Component styles */
    /* Theme-specific overrides */
  </style>
</head>
<body>
  <!-- Main calendar container -->
  <div class="container">
    <!-- Navigation controls -->
    <div class="controls">...</div>

    <!-- Calendar grid -->
    <table class="calendar">...</table>
  </div>

  <!-- Settings modal -->
  <div id="settingsPanel">...</div>

  <script>
    /* JavaScript functionality */
  </script>
</body>
</html>
```

### CSS Architecture

#### CSS Custom Properties (Variables)
```css
:root {
  /* Dark theme (default) */
  --bg-gradient-start: #1e3a8a;
  --text-primary: rgba(255, 255, 255, 0.95);
  /* ... other variables */
}

[data-theme="light"] {
  /* Light theme overrides */
  --bg-gradient-start: #dbeafe;
  --text-primary: rgba(0, 0, 0, 0.9);
  /* ... other overrides */
}
```

#### Component Structure
- **Container**: Main application wrapper with glass morphism
- **Controls**: Navigation and theme controls
- **Calendar Grid**: Table-based calendar layout
- **Settings Panel**: Modal overlay for customization

### JavaScript Modules

#### Core Functions
```javascript
// Calendar Generation
function generateCalendar(month, year)
function updateCalendar()

// Navigation
function goToPreviousMonth()
function goToNextMonth()
function goToToday()

// Theme Management
function toggleTheme()
function initializeTheme()
function updateBackgroundColors(darkColor, lightColor)

// Settings
function openSettings()
function saveSettings()
function loadCurrentColors()

// Lunar Calendar
function solarToLunar(solarDate)
function formatLunarDate(lunarDate)
```

## 🔧 API Reference

### Core Calendar Functions

#### `generateCalendar(month, year)`
Generates the calendar grid for the specified month and year.

**Parameters:**
- `month` (number): Month index (0-11)
- `year` (number): Four-digit year

**Example:**
```javascript
generateCalendar(8, 2025); // September 2025
```

#### `solarToLunar(solarDate)`
Converts a Gregorian date to Chinese lunar calendar.

**Parameters:**
- `solarDate` (Date): JavaScript Date object

**Returns:**
```javascript
{
  year: number,     // Lunar year
  month: number,    // Lunar month (1-12)
  day: number,      // Lunar day (1-30)
  monthName: string, // Chinese month name
  dayName: string   // Chinese day name
}
```

### Theme Functions

#### `toggleTheme()`
Switches between light and dark themes, applying appropriate colors.

#### `updateBackgroundColors(darkColor, lightColor)`
Updates the background gradient colors for both themes.

**Parameters:**
- `darkColor` (string): Hex color for dark theme
- `lightColor` (string): Hex color for light theme

### Settings Functions

#### `saveSettings()`
Saves current color preferences to localStorage.

#### `resetColors()`
Resets colors to default values and clears localStorage.

## 🎨 Styling System

### CSS Custom Properties

The application uses a comprehensive CSS custom properties system for theming:

```css
/* Color System */
--text-primary: Primary text color
--text-secondary: Secondary/muted text
--text-muted: Very light text (disabled states)

/* Background System */
--bg-gradient-start: Background gradient start
--bg-gradient-end: Background gradient end
--container-bg: Main container background
--container-border: Container border color

/* Component Colors */
--cell-bg: Calendar cell background
--cell-border: Calendar cell border
--cell-hover-bg: Calendar cell hover state
--button-bg: Button background
--button-border: Button border
--button-hover-bg: Button hover state

/* Special States */
--today-bg: Today's date highlight
--sunday-color: Sunday date text color
```

### Glass Morphism Implementation

```css
.glass-element {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(20px) saturate(180%);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: 20px;
}
```

### Responsive Design

Mobile-first approach with breakpoints:
- **Mobile**: Default styles
- **Tablet**: 768px+
- **Desktop**: 1024px+

## 💾 State Management

### LocalStorage Schema

```javascript
// Theme preference
localStorage.setItem('theme', 'dark' | 'light');

// Custom colors
localStorage.setItem('darkBgColor', '#hexcolor');
localStorage.setItem('lightBgColor', '#hexcolor');
```

### State Synchronization

The application maintains state consistency through:
1. **Theme changes**: Update DOM data attributes and CSS variables
2. **Color changes**: Update CSS variables and localStorage
3. **Navigation**: Update dropdowns and regenerate calendar

## ⚡ Performance Considerations

### Optimization Strategies

#### Calendar Rendering
- **Minimal DOM manipulation**: Only update necessary cells
- **CSS transitions**: Hardware-accelerated animations
- **Event delegation**: Single event listener for calendar interactions

#### Memory Management
- **No memory leaks**: Proper event listener cleanup
- **Efficient date calculations**: Cache lunar calendar results
- **Minimal global scope**: Function-scoped variables

#### CSS Performance
```css
/* Efficient selectors */
.calendar-cell { /* ... */ }

/* Hardware acceleration */
.animated-element {
  transform: translateZ(0); /* Force GPU layer */
  will-change: transform; /* Hint to browser */
}

/* Avoid expensive properties in animations */
.transition-element {
  transition: transform 0.2s ease; /* Good */
  /* transition: box-shadow 0.2s ease; /* Avoid */
}
```

### Performance Monitoring

Key metrics to watch:
- **First Paint**: < 100ms
- **Calendar Generation**: < 50ms
- **Theme Switch**: < 100ms
- **Memory Usage**: < 10MB

## 🌐 Browser Compatibility

### Required Features
- **CSS Custom Properties**: Chrome 49+, Firefox 31+, Safari 9.1+
- **CSS Grid**: Chrome 57+, Firefox 52+, Safari 10.1+
- **Backdrop Filter**: Chrome 76+, Firefox 103+, Safari 18.0+
- **ES6+ JavaScript**: Chrome 51+, Firefox 54+, Safari 10+

### Fallback Strategies

#### Backdrop Filter
```css
.glass-element {
  background: rgba(255, 255, 255, 0.9); /* Fallback */
  backdrop-filter: blur(20px); /* Progressive enhancement */
}
```

#### CSS Grid
```css
.calendar {
  display: table; /* Fallback */
  display: grid; /* Progressive enhancement */
}
```

### Testing Matrix

| Browser | Version | Status |
|---------|---------|---------|
| Chrome | 88+ | ✅ Full support |
| Firefox | 94+ | ✅ Full support |
| Safari | 15.4+ | ✅ Full support |
| Edge | 88+ | ✅ Full support |
| Chrome Mobile | 88+ | ✅ Full support |
| Safari iOS | 15.4+ | ✅ Full support |

## 🔍 Debugging Guide

### Common Issues

#### Theme not switching properly
```javascript
// Check DOM data attribute
console.log(document.body.dataset.theme);

// Check CSS variable values
console.log(getComputedStyle(document.documentElement)
  .getPropertyValue('--bg-gradient-start'));
```

#### Lunar dates incorrect
```javascript
// Test lunar conversion
const testDate = new Date(2025, 8, 13); // Sept 13, 2025
const lunarResult = solarToLunar(testDate);
console.log('Lunar result:', lunarResult);
```

#### Settings not persisting
```javascript
// Check localStorage
console.log('Saved theme:', localStorage.getItem('theme'));
console.log('Saved colors:', {
  dark: localStorage.getItem('darkBgColor'),
  light: localStorage.getItem('lightBgColor')
});
```

### Development Tools

#### Browser DevTools
1. **Elements**: Inspect CSS variables and DOM structure
2. **Console**: Debug JavaScript and test functions
3. **Application**: Check localStorage values
4. **Performance**: Monitor rendering performance

#### Useful Console Commands
```javascript
// Test theme switching
toggleTheme();

// Generate specific month
generateCalendar(11, 2025); // December 2025

// Test color changes
updateBackgroundColors('#ff0000', '#00ff00');

// Check current settings
console.log({
  theme: document.body.dataset.theme,
  darkColor: localStorage.getItem('darkBgColor'),
  lightColor: localStorage.getItem('lightBgColor')
});
```

---

This documentation is maintained alongside the codebase. When making changes, please update the relevant sections to keep it accurate and helpful for future developers.