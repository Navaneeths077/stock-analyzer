# Stock Fundamental Analyzer 📊

A free, open-source web application for comprehensive stock fundamental analysis. Input any company's financial metrics and get instant analysis with detailed ratings.

**🌐 Live Demo:** [stockanalyzer.example.com](https://yourname.github.io/stock-analyzer/)

## Features

✅ **Complete Fundamental Analysis**
- Valuation metrics (P/E, P/B, Dividend Yield, EPS)
- Profitability metrics (ROE, ROCE, Margins)
- Growth metrics (Revenue Growth, CAGR, Profit Growth)
- Financial health (Debt-to-Equity, Current Ratio, Reserves)

✅ **Instant Scoring System**
- Overall rating (0-100 score)
- Category breakdown (Valuation, Profitability, Growth, Health)
- Color-coded recommendations (Strong Buy → Sell)
- Visual gauge indicators

✅ **User-Friendly Interface**
- Tab-based navigation (Input, Results, Guide)
- Responsive design (mobile & desktop)
- Dark mode support
- Real-time calculation

✅ **Educational**
- Built-in parameter guide
- Investment rating explanations
- Help text for each metric
- Sample data examples

## How to Use

### 1. **Input Metrics**
   - Enter company name and basic info
   - Fill in financial metrics (all optional)
   - Click "Analyze Stock"

### 2. **Get Results**
   - See overall score (0-100)
   - View category breakdowns
   - Read strengths & concerns
   - Check metric ratings

### 3. **Learn**
   - Review parameter explanations
   - Understand rating system
   - Explore investment categories

## Local Setup

### Option A: Direct Usage
```bash
# 1. Clone the repository
git clone https://github.com/yourusername/stock-analyzer.git
cd stock-analyzer

# 2. Open in browser
open index.html
# or drag index.html to your browser
```

### Option B: Live Server (Recommended)
```bash
# Install live-server globally
npm install -g live-server

# Run in project directory
live-server

# Open http://localhost:8080
```

### Option C: Python Server
```bash
# Python 3
python -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Open http://localhost:8000
```

## Deploy to GitHub Pages

### Step 1: Create Repository
```bash
# Create new repo on GitHub named: stock-analyzer
# Clone it
git clone https://github.com/yourusername/stock-analyzer.git
cd stock-analyzer
```

### Step 2: Add Files
```bash
# Copy index.html to repository
cp /path/to/index.html ./

# Add all files
git add .
git commit -m "Initial commit: Stock analyzer tool"
git push origin main
```

### Step 3: Enable GitHub Pages
1. Go to repository settings
2. Navigate to "Pages" section
3. Select "main" branch as source
4. Save

**Your site will be live at:** `https://yourusername.github.io/stock-analyzer/`

## File Structure
```
stock-analyzer/
├── index.html          # Complete application (all-in-one file)
├── README.md           # This file
└── LICENSE             # MIT License (optional)
```

## Features Explained

### 📊 Valuation Metrics
- **P/E Ratio:** Price per rupee of earnings. Lower = Cheaper
- **P/B Ratio:** Price vs. book value. < 1 = Trading below assets
- **Dividend Yield:** Annual cash return to shareholders
- **EPS:** Earnings per share - higher is better

### 💰 Profitability
- **ROE:** Return on equity. > 20% is excellent
- **ROCE:** Return on capital. > 15% shows efficiency
- **Margins:** Operating and Net profit margins

### 📈 Growth
- **Revenue Growth:** Annual sales increase
- **CAGR:** Compound annual growth rate (3 & 5 year)
- **Profit Growth:** Earnings expansion rate

### 🏦 Financial Health
- **Debt-to-Equity:** Leverage level. < 1.0 is safe
- **Current Ratio:** Liquidity position. > 1.5 is healthy
- **Reserves:** Cash available for operations
- **Promoter Holding:** Founder ownership %

### 🎯 Investment Ratings

| Score | Rating | Meaning |
|-------|--------|---------|
| 75+ | 🟢 STRONG BUY | Exceptional opportunity |
| 60-74 | 🟢 BUY | Good fundamentals |
| 45-59 | 🟡 HOLD | Mixed signals |
| 30-44 | 🔴 WEAK SELL | Concerns present |
| 0-29 | 🔴 SELL | Poor fundamentals |

## Example Analysis

**Input:**
```
Company: Unknown Stock
P/E Ratio: 2.83
ROE: 25.9%
ROCE: 20.5%
Revenue Growth: 21.4%
Debt-to-Equity: 0.12
```

**Output:**
```
Overall Score: 82/100
Recommendation: STRONG BUY

Valuation: 95/100  (Exceptional bargain)
Profitability: 88/100  (Outstanding)
Growth: 90/100  (Excellent)
Health: 96/100  (Fortress balance sheet)
```

## Technology Stack

- **HTML5** - Structure
- **CSS3** - Styling (with dark mode support)
- **Vanilla JavaScript** - Logic & calculations
- **No dependencies** - Runs in any browser

## Browser Support

✅ Chrome/Edge 90+  
✅ Firefox 88+  
✅ Safari 14+  
✅ Mobile browsers (iOS Safari, Chrome Mobile)

## Customization

### Change Colors
Edit the `:root` color variables in `<style>` section:
```css
:root {
    --color-bg-success: #28a745;
    --color-bg-info: #378add;
    /* ... more colors ... */
}
```

### Modify Scoring Logic
Edit the `calculateScores()` function in `<script>` section:
```javascript
// Adjust weights and thresholds
if (!isNaN(m.pe) && m.pe <= 20) val += 30;
```

### Add More Metrics
1. Add input field in HTML
2. Extract value in `analyzeStock()`
3. Add scoring logic in `calculateScores()`
4. Display in results

## Contributing

Contributions welcome! To contribute:

1. Fork the repository
2. Create feature branch (`git checkout -b feature/improvement`)
3. Make changes
4. Commit (`git commit -m 'Add feature'`)
5. Push (`git push origin feature/improvement`)
6. Open Pull Request

## Issues & Support

Found a bug? Have a suggestion?

1. Check [existing issues](https://github.com/yourusername/stock-analyzer/issues)
2. Create new issue with details
3. Include screenshots if helpful

## Educational Disclaimer

⚠️ **This tool is for educational purposes only**

- Not financial advice
- Do your own research
- Consult financial advisors
- Past performance ≠ future results
- Stock markets are risky

This calculator helps you understand fundamentals, not predict stock prices.

## License

MIT License - see LICENSE file for details

Free to use, modify, and distribute!

## Roadmap

Planned features:
- [ ] Compare multiple companies
- [ ] Export analysis as PDF
- [ ] Historical data tracking
- [ ] Industry benchmarks
- [ ] Watchlist functionality
- [ ] API integration (NSE, BSE data)

## Acknowledgments

Built with ❤️ for stock market enthusiasts & value investors

## Contact

- GitHub: [@yourusername](https://github.com/yourusername)
- Email: your.email@example.com

---

**Made with ❤️ for smart investors**

Star ⭐ this repo if you find it useful!

