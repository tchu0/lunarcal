# LunarCal

A beautiful, modern calendar web application featuring both Gregorian and Chinese lunar calendar dates with customizable themes and Apple-inspired liquid glass design.

![Calendar Preview](https://img.shields.io/badge/Status-Active-brightgreen)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## ✨ Features

### 🎨 **Beautiful UI/UX**
- **Apple-inspired liquid glass design** with backdrop blur effects
- **Smooth animations** and transitions throughout the interface
- **Responsive design** that works on all screen sizes
- **Full-width layout** that adapts to any viewport

### 🌙 **Dual Calendar System**
- **Gregorian Calendar**: Standard Western calendar dates
- **Chinese Lunar Calendar**: Traditional Chinese calendar with accurate lunar dates
- **Month names in Chinese**: 正月, 二月, 三月, etc.
- **Day names in Chinese**: 初一, 初二, 十五, 廿一, etc.

### 🌈 **Theme Customization**
- **Light and Dark modes** with instant switching
- **Customizable background colors** for each theme
- **Default themes**: Dark blue gradient (dark mode), Light blue gradient (light mode)
- **Persistent settings** saved in browser localStorage

### 🧭 **Navigation Features**
- **Month/Year selectors** with dropdown menus
- **Navigation arrows** for quick month/year changes (←/→)
- **"Go to Today" button** for instant navigation to current date
- **Year range**: Current year ±100 years for historical/future viewing

### 🎯 **Enhanced Readability**
- **Large, clear text** - doubled font sizes for better visibility
- **Color-coded Sundays** in red for easy weekend identification
- **Today highlighting** with blue background and enhanced styling
- **Proper contrast ratios** in both light and dark themes

### ⚙️ **Settings Panel**
- **Modal-style settings** with glass morphism design
- **Color pickers** for background customization
- **Live preview** of color changes
- **Reset to defaults** functionality
- **Save settings** with localStorage persistence

## 🚀 Quick Start

### Prerequisites
- Modern web browser (Chrome, Firefox, Safari, Edge)
- No server required - runs entirely client-side

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/tchu0/lunarcal.git
   cd lunarcal
   ```

2. **Open in browser**
   ```bash
   open calendar.html
   # or simply double-click calendar.html
   ```

That's it! The application runs entirely in the browser with no build process required.

## 🎯 Usage

### Basic Navigation
- Use the **month dropdown** to select any month
- Use the **year dropdown** to jump to any year
- Click **← / →** buttons for quick month/year navigation
- Click **"Go to Today"** to return to the current date

### Theme Switching
- Click the **🌙 / ☀️** button to toggle between dark/light modes
- Themes are automatically saved and restored on page reload

### Customizing Colors
1. Click the **⚙️** (settings) button
2. Use the **color pickers** to select your preferred background colors
3. See **live preview** as you adjust colors
4. Click **"Save Settings"** to apply and persist changes
5. Use **"Reset to Default"** to restore original colors

### Reading the Calendar
- **Large numbers**: Gregorian calendar dates
- **Chinese characters**: Lunar calendar dates below Gregorian dates
- **Red text**: Sunday dates
- **Blue highlight**: Today's date
- **Month names**: First day of lunar month shows month name (正月, 二月, etc.)

## 🏗️ Technical Architecture

### Dependencies
- **[lunar-javascript](https://github.com/6tail/lunar-javascript)**: Accurate Chinese lunar calendar calculations
- **Pure HTML/CSS/JavaScript**: No frameworks or build tools required

### Key Technologies
- **CSS Variables**: Dynamic theming system
- **CSS Grid & Flexbox**: Responsive layout
- **LocalStorage API**: Settings persistence
- **CSS Backdrop Filter**: Glass morphism effects
- **CSS Transitions**: Smooth animations

### Browser Support
- Chrome 88+
- Firefox 94+
- Safari 15.4+
- Edge 88+
- (Requires backdrop-filter support)

## 📁 Project Structure

```
lunarcal/
├── calendar.html          # Main application file
├── README.md             # Project documentation
├── CONTRIBUTING.md       # Contribution guidelines
├── LICENSE              # Project license
└── .gitignore          # Git ignore rules
```

### Single File Architecture
The entire application is contained in `calendar.html` for simplicity:
- **HTML Structure**: Semantic markup for calendar grid and controls
- **CSS Styles**: Modern styling with CSS variables for theming
- **JavaScript Logic**: All functionality including lunar calendar integration

## 🔧 Configuration

### Default Settings
```javascript
// Default theme colors (can be customized via settings)
const defaults = {
  darkMode: '#1e3a8a',    // Dark blue
  lightMode: '#dbeafe',   // Light blue
  theme: 'dark'           // Default theme
};

// Year range
const yearRange = {
  past: 100,              // Years before current
  future: 100             // Years after current
};
```

### Customization Options
- **Background colors**: Fully customizable via settings panel
- **Text colors**: Automatic based on theme (light/dark)
- **Hover effects**: CSS-based with smooth transitions
- **Animation timing**: Configurable via CSS variables

## 🤝 Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Development Workflow
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes to `calendar.html`
4. Test in multiple browsers
5. Commit your changes (`git commit -m 'Add amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

### Code Style
- Use **2-space indentation**
- Follow **semantic HTML** principles
- Use **CSS custom properties** for theming
- Write **clear, commented JavaScript**
- Maintain **mobile-first responsive design**

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **[lunar-javascript](https://github.com/6tail/lunar-javascript)** by 6tail for accurate lunar calendar calculations
- **Apple Design Guidelines** for inspiration on glass morphism and animations
- **Chinese Calendar System** for traditional lunar calendar knowledge

## 📞 Support

If you encounter any issues or have questions:
1. Check the [Issues](https://github.com/tchu0/lunarcal/issues) page
2. Create a new issue with detailed information
3. Include browser version and operating system

## 🔄 Version History

### v1.0.0 (Current)
- Initial release
- Dual calendar system (Gregorian + Chinese Lunar)
- Light/Dark theme support
- Customizable background colors
- Apple-inspired liquid glass design
- Full navigation controls
- Settings panel with persistence

---

**Built with ❤️ using vanilla HTML, CSS, and JavaScript**