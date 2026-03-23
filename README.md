# MCF Personal Finance Tracker

A fully self-contained, single-file personal finance tracker built for [My College Finance](https://www.mycollegefinance.com/) — designed to help college students track spending, set budgets, and build smarter money habits.

![My College Finance](https://static.wixstatic.com/media/c24a60_2b6231b666214539ae22ebd2dffe7a09~mv2.png)

## Features

### Core Tracking
- **Expense Entry** — Add expenses with amount, category (8 categories), date, and optional notes
- **Dynamic Charts** — Bar chart (spending by category) and donut chart (spending distribution) update instantly on every submission via Chart.js
- **Monthly Filtering** — View expenses by specific month
- **Recent Expenses List** — Scrollable list with color-coded category dots and inline delete

### Budget Management
- **Set Monthly Budget** — Prominent budget input that auto-saves as you type
- **Budget vs. Spending Comparison** — Three-stat panel showing Budget, Spent, and Remaining with percentage tracking
- **Visual Progress Bar** — Color-coded gauge (green → yellow → red) with contextual status messages
- **Budget vs. Actual Chart** — Grouped bar chart comparing budget allocation against actual spending per category
- **Over-Budget Alerts** — Visual indicators when spending exceeds budget

### AI Budget Assistant (Beta)
- **"Chat with Oliver"** — Floating chat button with AI sparkle icon
- **Context-Aware Advice** — Oliver can see your current expense data and give personalized budgeting tips
- **Starter Prompts** — Three suggested questions to get the conversation going
- **Powered by Google Gemini** — Free tier, no cost to you or your users (see [SETUP.md](SETUP.md))

### Data & Export
- **localStorage Persistence** — All data saved locally, no account required
- **Export CSV** — Download expense data as a spreadsheet-ready CSV file
- **Save & Download PDF** — Full branded PDF report with summary, expense table, and category breakdown via jsPDF
- **Download Template** — Blank printable PDF template for offline use
- **Reset** — Clear all data with confirmation

### Design
- **MCF Branded** — Official logo, colors (navy #012699, green #26e011, amber #fdc003), and tagline
- **Dark/Light Mode** — Toggle with localStorage preference persistence
- **Fully Responsive** — Mobile-first design, works on all screen sizes
- **Smooth Animations** — Transitions, hover states, and slide-in effects throughout

## Tech Stack

- **HTML5 / CSS3 / Vanilla JavaScript** — Zero framework dependencies
- **[Chart.js 4.4.7](https://www.chartjs.org/)** — Charts via CDN
- **[jsPDF 2.5.1](https://github.com/parallax/jsPDF)** — PDF generation via CDN
- **[Google Gemini API](https://ai.google.dev/)** — AI chat assistant (free tier)
- **localStorage** — Client-side data persistence

## Getting Started

### 1. Add Your Gemini API Key

The AI chat feature ("Chat with Oliver") requires a free Google Gemini API key. See **[SETUP.md](SETUP.md)** for step-by-step instructions — it takes about 2 minutes.

### 2. Open the App

Simply open `index.html` in any modern web browser. Everything works out of the box.

For a local server (recommended for development):

```bash
# Python
python -m http.server 8000

# Node.js
npx serve .

# VS Code
# Install "Live Server" extension → Right-click index.html → "Open with Live Server"
```

Then visit `http://localhost:8000`

### 3. Deploy (Optional)

This is a single static HTML file — deploy it anywhere:
- **GitHub Pages** — Push to repo, enable Pages in Settings
- **Netlify / Vercel** — Drag and drop the file
- **Any web host** — Upload `index.html`

> **Note:** For public deployments, consider using a backend proxy for the API key. See [SETUP.md](SETUP.md) for details.

## Project Structure

```
mcf-personal-finance-tracker/
├── index.html          # Complete self-contained application
├── assets/             # Reserved for future static assets
├── SETUP.md            # Gemini API key setup instructions
├── README.md           # This file
├── CHANGELOG.md        # Version history
├── LICENSE             # MIT License
└── .gitignore          # Git ignore rules
```

## Browser Support

- Chrome 90+
- Firefox 90+
- Safari 15+
- Edge 90+

## Brand Guidelines

This app follows the [My College Finance Brand Identity](https://www.mycollegefinance.com/):

| Element | Value |
|---------|-------|
| Brand Blue | `#012699` |
| Brand Green | `#26e011` |
| Brand Amber | `#fdc003` |
| Tagline | EDUCATE • MOTIVATE • ELEVATE |
| Logo | [Official PNG](https://static.wixstatic.com/media/c24a60_2b6231b666214539ae22ebd2dffe7a09~mv2.png) |

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

## Credits

- **My College Finance** — Brand, mission, and educational framework
- **Oliver** — AI Budget Assistant persona
- **Google Gemini** — AI model powering Oliver
- **Chart.js** — Open-source charting library
- **jsPDF** — Client-side PDF generation

---

**EDUCATE • MOTIVATE • ELEVATE**

© 2025 My College Finance. All rights reserved.
