# Technical Documentation

Notes for anyone working on LunarCal.

## Table of Contents

- [Architecture Overview](#architecture-overview)
- [Code Structure](#code-structure)
- [API Reference](#api-reference)
- [Styling System](#styling-system)
- [State Management](#state-management)
- [Performance](#performance)
- [Browser Compatibility](#browser-compatibility)

## Architecture Overview

Everything lives in a single `calendar.html` file. No build step, no frameworks.

### Principles
- Vanilla JavaScript -- keeps things simple and small
- CSS custom properties for theming
- Mobile-first responsive design
- Reasonable accessibility (WCAG 2.1 AA where practical)

### Dependencies
- [lunar-javascript](https://github.com/6tail/lunar-javascript) v1.6.12 for lunar calendar math
- Google Fonts: Newsreader (display) and DM Sans (body)

## Code Structure

### HTML Layout
```html
<!DOCTYPE html>
<html>
<head>
  <!-- Meta, title, fonts, lunar-javascript CDN -->
  <style>
    /* CSS variables, component styles, responsive rules */
  </style>
</head>
<body>
  <div class="container">
    <!-- Header with title and action buttons -->
    <!-- Navigation controls -->
    <!-- Calendar table -->
  </div>

  <!-- Settings modal -->
  <div id="settingsPanel">...</div>

  <script>
    /* All JavaScript */
  </script>
</body>
</html>
```

### CSS Architecture

#### Theme Variables
```css
:root {
  /* Dark theme (default) */
  --bg: #111110;
  --text: #e8e4dd;
  --accent: #c5453a;
  /* ... */
}

[data-theme="light"] {
  --bg: #f5f0e8;
  --text: #2c2a25;
  --accent: #b33d33;
  /* ... */
}
```

#### Main Components
- **Container**: Centered content wrapper
- **Header**: Title and action buttons (theme toggle, settings)
- **Controls**: Month/year navigation with dropdowns
- **Calendar Grid**: Table-based layout with day cells
- **Settings Panel**: Modal for color customization

### JavaScript Functions

#### Core
```javascript
function generateCalendar(month, year)
function updateCalendar()
```

#### Navigation
```javascript
function goToPreviousMonth()
function goToNextMonth()
function goToPreviousYear()
function goToNextYear()
function goToToday()
```

#### Theme
```javascript
function toggleTheme()
function initializeTheme()
function updateThemeIcon()
function updateBackgroundColors(darkColor, lightColor)
```

#### Settings
```javascript
function openSettings()
function saveSettings()
function resetColors()
function loadCurrentColors()
```

#### Lunar Calendar
```javascript
function solarToLunar(solarDate)
function formatLunarDate(lunarDate)
```

## API Reference

### `generateCalendar(month, year)`
Builds the calendar grid for a given month and year.

- `month` (number): 0-11
- `year` (number): four-digit year

```javascript
generateCalendar(8, 2025); // September 2025
```

### `solarToLunar(solarDate)`
Converts a Gregorian date to Chinese lunar calendar data.

- `solarDate` (Date): a JavaScript Date object

Returns:
```javascript
{
  year: number,
  month: number,    // 1-12
  day: number,      // 1-30
  monthName: string, // Chinese month name
  dayName: string   // Chinese day name
}
```

### `toggleTheme()`
Switches between light and dark themes and updates colors.

### `updateBackgroundColors(darkColor, lightColor)`
Sets the background gradient colors for both themes.

- `darkColor` (string): hex color for dark theme
- `lightColor` (string): hex color for light theme

### `saveSettings()`
Writes current color choices to localStorage.

### `resetColors()`
Restores default colors and clears saved preferences.

## Styling System

### CSS Custom Properties

The app uses CSS variables for all colors and spacing:

```css
/* Text */
--text: main text color
--text-secondary: secondary text
--text-muted: faint text

/* Backgrounds */
--bg: page background
--surface: card/cell background
--surface-hover: hover state

/* Borders */
--border: standard borders
--border-subtle: lighter borders

/* Accent */
--accent: cinnabar red, used for today and Sundays
--accent-soft: light accent for backgrounds
--today-bg: today cell background
--sunday: Sunday text color
```

### Responsive Breakpoints

- Default: mobile
- 640px+: small tablets
- 768px+: tablets
- 1024px+: desktop

## State Management

### localStorage Keys

```javascript
localStorage.getItem('theme');        // 'dark' or 'light'
localStorage.getItem('darkBgColor');  // hex color string
localStorage.getItem('lightBgColor'); // hex color string
```

### How State Stays in Sync

1. Theme changes update the `data-theme` attribute on `<body>` and CSS variables
2. Color changes update CSS variables and localStorage
3. Navigation updates the dropdowns and regenerates the calendar

## Performance

### What We Do
- Rebuild only the calendar body on navigation (no full page re-render)
- CSS transitions for animations (hardware-accelerated where possible)
- No backdrop-filter or heavy GPU effects
- Function-scoped variables to avoid polluting global scope

### Rough Targets
- First paint: under 100ms
- Calendar generation: under 50ms
- Theme switch: under 100ms

## Browser Compatibility

### Required Features
- CSS Custom Properties: Chrome 49+, Firefox 31+, Safari 9.1+
- CSS Grid: Chrome 57+, Firefox 52+, Safari 10.1+
- ES6 JavaScript: Chrome 51+, Firefox 54+, Safari 10+

### Tested Browsers

| Browser | Version | Works |
|---------|---------|-------|
| Chrome | 88+ | Yes |
| Firefox | 94+ | Yes |
| Safari | 15.4+ | Yes |
| Edge | 88+ | Yes |
| Chrome Mobile | 88+ | Yes |
| Safari iOS | 15.4+ | Yes |

## Debugging

### Theme not switching
```javascript
console.log(document.body.dataset.theme);
console.log(getComputedStyle(document.documentElement)
  .getPropertyValue('--bg'));
```

### Lunar dates look wrong
```javascript
const testDate = new Date(2025, 8, 13); // Sept 13, 2025
console.log(solarToLunar(testDate));
```

### Settings not saving
```javascript
console.log({
  theme: localStorage.getItem('theme'),
  dark: localStorage.getItem('darkBgColor'),
  light: localStorage.getItem('lightBgColor')
});
```

### Handy Console Commands
```javascript
toggleTheme();
generateCalendar(11, 2025); // December 2025
updateBackgroundColors('#ff0000', '#00ff00');
```

---

Keep this file up to date when making changes to the codebase.