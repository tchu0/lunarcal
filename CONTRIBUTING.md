# Contributing to LunarCal

First off, thank you for considering contributing to the LunarCal! 🎉

The following is a set of guidelines for contributing to this project. These are mostly guidelines, not rules. Use your best judgment, and feel free to propose changes to this document in a pull request.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Development Setup](#development-setup)
- [Style Guide](#style-guide)
- [Pull Request Process](#pull-request-process)
- [Issue Reporting](#issue-reporting)

## 📜 Code of Conduct

This project and everyone participating in it is governed by our commitment to creating a welcoming, inclusive environment. By participating, you are expected to uphold this standard.

### Our Standards

**Positive behavior includes:**
- Being respectful and inclusive
- Gracefully accepting constructive feedback
- Focusing on what is best for the community
- Showing empathy towards other contributors

**Unacceptable behavior includes:**
- Harassment of any kind
- Discriminatory language or actions
- Personal attacks or trolling
- Publishing private information without permission

## 🤝 How Can I Contribute?

### 🐛 Reporting Bugs

Before creating bug reports, please check the [existing issues](https://github.com/tchu0/lunarcal/issues) to avoid duplicates.

When creating a bug report, please include:

- **Browser and version** (e.g., Chrome 119, Firefox 118)
- **Operating system** (e.g., macOS 14, Windows 11, Ubuntu 22.04)
- **Steps to reproduce** the issue
- **Expected behavior** vs **actual behavior**
- **Screenshots** if applicable
- **Console errors** if any

**Bug Report Template:**
```markdown
## Bug Description
A clear description of what the bug is.

## Steps to Reproduce
1. Go to '...'
2. Click on '...'
3. See error

## Expected Behavior
What you expected to happen.

## Actual Behavior
What actually happened.

## Environment
- Browser: [e.g., Chrome 119]
- OS: [e.g., macOS 14]

## Screenshots
If applicable, add screenshots to help explain your problem.
```

### ✨ Suggesting Enhancements

Enhancement suggestions are welcome! Please provide:

- **Clear description** of the proposed feature
- **Use cases** - why would this be useful?
- **Implementation ideas** if you have any
- **Mockups or wireframes** for UI changes

### 🔧 Contributing Code

We welcome code contributions! Here are some areas where you can help:

#### 🎨 **UI/UX Improvements**
- Enhance visual design
- Improve accessibility
- Add new animations or transitions
- Responsive design improvements

#### 🌍 **Internationalization**
- Add support for more languages
- Lunar calendar systems for other cultures
- Right-to-left language support
- Date format localization

#### ⚡ **Performance**
- Optimize calendar rendering
- Reduce bundle size
- Improve loading times
- Better caching strategies

#### 🆕 **New Features**
- Event system (add/edit/delete events)
- Export functionality (PDF, ICS)
- Print styles
- Keyboard navigation
- Holiday support

## 🛠️ Development Setup

### Prerequisites
- Modern web browser with developer tools
- Text editor or IDE
- Git for version control

### Getting Started

1. **Fork and clone the repository**
   ```bash
   git fork https://github.com/tchu0/lunarcal.git
   git clone https://github.com/tchu0/lunarcal.git
   cd lunarcal
   ```

2. **Open the application**
   ```bash
   # Simply open calendar.html in your browser
   open calendar.html  # macOS
   start calendar.html # Windows
   xdg-open calendar.html # Linux
   ```

3. **Start developing!**
   - Make changes to `calendar.html`
   - Refresh browser to see changes
   - Use browser dev tools for debugging

### Testing Your Changes

Since this is a single-file application, testing is straightforward:

1. **Manual Testing**
   - Test in multiple browsers (Chrome, Firefox, Safari, Edge)
   - Test responsive design on different screen sizes
   - Test both light and dark themes
   - Verify lunar calendar accuracy for various dates
   - Test all navigation controls

2. **Browser Compatibility**
   - Ensure backdrop-filter support fallbacks work
   - Test CSS Grid and Flexbox layouts
   - Verify JavaScript ES6+ features work

3. **Performance Testing**
   - Check calendar rendering performance
   - Test with different date ranges
   - Verify smooth animations

## 📝 Style Guide

### HTML
- Use **semantic HTML5** elements
- Maintain **proper nesting** and **indentation** (2 spaces)
- Add **accessible attributes** (aria-labels, roles) where needed
- Use **meaningful IDs** and **class names**

```html
<!-- Good -->
<button id="themeToggle" aria-label="Toggle dark/light theme">🌙</button>

<!-- Avoid -->
<div onclick="toggleTheme()">🌙</div>
```

### CSS
- Use **CSS custom properties** for theming
- Follow **mobile-first** responsive design
- Use **meaningful class names** (BEM methodology preferred)
- **Group related styles** together
- Add **comments** for complex calculations

```css
/* Good */
.calendar-cell {
  background: var(--cell-bg);
  border: 1px solid var(--cell-border);
  transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
}

.calendar-cell:hover {
  background: var(--cell-hover-bg);
  transform: translateY(-2px);
}

/* Avoid */
.cell {
  background: rgba(255,255,255,0.08);
}
```

### JavaScript
- Use **ES6+ features** appropriately
- Write **clear, documented** functions
- Use **meaningful variable names**
- Handle **errors gracefully**
- Follow **functional programming** principles where possible

```javascript
// Good
function updateBackgroundColors(darkColor, lightColor) {
  const root = document.documentElement;
  const currentTheme = document.body.dataset.theme;

  // Create gradients from selected colors
  const darkGradient = adjustBrightness(darkColor, 20);
  const lightGradient = adjustBrightness(lightColor, -10);

  // Apply colors based on current theme
  if (currentTheme === 'light') {
    root.style.setProperty('--bg-gradient-start', lightColor);
    root.style.setProperty('--bg-gradient-end', lightGradient);
  } else {
    root.style.setProperty('--bg-gradient-start', darkColor);
    root.style.setProperty('--bg-gradient-end', darkGradient);
  }
}

// Avoid
function update(d,l){
  var r=document.documentElement;
  if(document.body.dataset.theme=='light'){
    r.style.setProperty('--bg-gradient-start',l);
  }
  // ...
}
```

### Commit Messages
Use **clear, descriptive commit messages** following conventional commits:

```bash
# Good
git commit -m "feat: add keyboard navigation for calendar"
git commit -m "fix: correct lunar date calculation for leap months"
git commit -m "style: improve mobile responsive design"
git commit -m "docs: update README with new features"

# Types: feat, fix, docs, style, refactor, test, chore
```

## 🔄 Pull Request Process

1. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/issue-description
   ```

2. **Make your changes**
   - Follow the style guide
   - Test thoroughly
   - Update documentation if needed

3. **Commit your changes**
   ```bash
   git add .
   git commit -m "feat: add your amazing feature"
   ```

4. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```

5. **Create a Pull Request**
   - Use a clear, descriptive title
   - Fill out the PR template
   - Reference any related issues
   - Add screenshots for UI changes

### Pull Request Template

When creating a PR, please include:

```markdown
## Description
Brief description of what this PR does.

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Tested in Chrome
- [ ] Tested in Firefox
- [ ] Tested in Safari (if on macOS)
- [ ] Tested responsive design
- [ ] Tested both light/dark themes

## Screenshots
Include screenshots for UI changes.

## Additional Notes
Any additional information or context.
```

## 🐛 Issue Reporting

### Before Reporting
1. **Search existing issues** to avoid duplicates
2. **Update to latest version** if possible
3. **Try different browsers** to isolate the issue

### Issue Labels

We use labels to categorize issues:
- `bug` - Something isn't working
- `enhancement` - New feature or improvement
- `good first issue` - Good for newcomers
- `help wanted` - Extra attention needed
- `question` - Further information requested
- `documentation` - Improvements to docs

## 🎉 Recognition

Contributors will be recognized in:
- GitHub contributors page
- Future changelog entries
- Special thanks in documentation

## 📞 Questions?

If you have questions about contributing:
1. Check this document first
2. Look through [existing issues](https://github.com/tchu0/lunarcal/issues)
3. Create a new issue with the `question` label

---

**Happy Contributing!** 🚀

Thank you for helping make the LunarCal better for everyone!