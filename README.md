# LunarCal

A calendar web app that shows both Gregorian and Chinese lunar dates. It has a clean, warm design with light/dark themes and customizable colors.

## Features

### UI
- Clean layout with warm earth-tone palette
- Subtle animations and transitions
- Responsive layout that works on different screen sizes

### Dual Calendar System
- Standard Gregorian dates alongside Chinese lunar dates
- Lunar month names in Chinese (e.g. 正月, 二月)
- Lunar day names in Chinese (e.g. 初一, 初二)

### Themes
- Light and dark modes
- Customizable background colors for each theme
- Settings saved in localStorage

### Navigation
- Month and year dropdowns
- Arrow buttons for stepping through months and years
- "Go to Today" button
- Covers current year +/- 100 years

### Readability
- Large text for easy reading
- Sundays shown in red
- Today highlighted in blue
- Good contrast in both themes

### Settings Panel
- Color pickers for background customization
- Live preview of changes
- Reset to defaults option
- Saves to localStorage

## Quick Start

### Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge)
- No server needed -- runs entirely client-side

### Installation

1. Clone the repository
   ```bash
   git clone https://github.com/tchu0/lunarcal.git
   cd lunarcal
   ```

2. Open in browser
   ```bash
   open calendar.html
   # or just double-click calendar.html
   ```

No build step required.

## Usage

### Navigation
- Use the month dropdown to pick a month
- Use the year dropdown to jump to a year
- Use the arrow buttons to step forward or back
- Click "Go to Today" to return to the current date

### Switching Themes
- Click the theme toggle button to switch between dark and light modes
- Your choice is saved and restored on reload

### Customizing Colors
1. Open the settings panel
2. Pick your preferred background colors
3. Preview updates live as you adjust
4. Click "Save Settings" to keep your changes
5. Click "Reset to Default" to go back to the original colors

### Reading the Calendar
- Large numbers are Gregorian dates
- Chinese characters below are the lunar dates
- Red text marks Sundays
- Blue highlight marks today
- The first day of a lunar month shows the month name

## Technical Details

### Dependencies
- [lunar-javascript](https://github.com/6tail/lunar-javascript) for lunar calendar calculations
- Plain HTML, CSS, and JavaScript -- no frameworks or build tools

### Key Technologies
- CSS variables for theming
- CSS Grid and Flexbox for layout
- LocalStorage for saving settings
- CSS custom properties for theming
- CSS transitions for animations

### Browser Support
- Chrome 88+
- Firefox 94+
- Safari 15.4+
- Edge 88+

## Project Structure

```
lunarcal/
├── calendar.html          # Main application file
├── README.md             # This file
└─── LICENSE              # MIT license
```

The whole app lives in a single `calendar.html` file:
- HTML for the calendar grid and controls
- CSS for styling and theming
- JavaScript for logic and lunar calendar integration

## Configuration

### Defaults
```javascript
const defaults = {
  darkMode: '#1e3a8a',    // Dark blue
  lightMode: '#dbeafe',   // Light blue
  theme: 'dark'
};

const yearRange = {
  past: 100,
  future: 100
};
```

## License

MIT -- see the [LICENSE](LICENSE) file.

## Acknowledgments

- [lunar-javascript](https://github.com/6tail/lunar-javascript) by 6tail for the lunar calendar logic
- Chinese calendar tradition for the underlying system


## Version History

### v1.0.0
- Initial release
- Gregorian and Chinese lunar calendar side by side
- Light and dark themes
- Customizable background colors
- Clean, warm design
- Navigation controls
- Settings panel with persistence
