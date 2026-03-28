# Customization Guide

## How to Customize Your Stock Analyzer

All customization happens in `index.html`. No external files needed!

---

## 1. Change App Title & Description

**Find this in the `<head>` section:**

```html
<title>Stock Fundamental Analyzer - Free Stock Analysis Tool</title>
```

**Change to:**
```html
<title>My Stock Analyzer - Professional Edition</title>
```

**Also change the header:**

Find:
```html
<h1>📊 Stock Fundamental Analyzer</h1>
<p class="subtitle">Free comprehensive stock analysis tool | Input metrics to get instant ratings</p>
```

Change to your description:
```html
<h1>📊 My Awesome Stock Analyzer</h1>
<p class="subtitle">Professional stock analysis for smart investors</p>
```

---

## 2. Change Colors

**Find the `:root` CSS variables (around line 20 in `<style>`):**

```css
:root {
    --color-bg-success: #28a745;      /* Green */
    --color-bg-info: #378add;         /* Blue */
    --color-bg-warning: #ffc107;      /* Yellow */
    --color-bg-danger: #dc3545;       /* Red */
}
```

### Color Reference:
| Element | Variable | Default | Use For |
|---------|----------|---------|---------|
| Success/Buy | `--color-bg-success` | #28a745 | Green elements |
| Info/Good | `--color-bg-info` | #378add | Blue elements |
| Warning/Hold | `--color-bg-warning` | #ffc107 | Yellow elements |
| Danger/Sell | `--color-bg-danger` | #dc3545 | Red elements |

### Example: Make theme Purple
```css
--color-bg-success: #6f42c1;    /* Purple instead of green */
--color-bg-info: #7952b3;       /* Dark purple for info */
--color-bg-warning: #d63384;    /* Pink for warning */
--color-bg-danger: #8f0a1a;     /* Dark red for danger */
```

---

## 3. Change Rating Thresholds

**Find the `getRating()` function (in `<script>` section):**

```javascript
function getRating(score) {
    if (score >= 75) return { text: 'STRONG BUY', class: 'score-excellent' };
    if (score >= 60) return { text: 'BUY', class: 'score-good' };
    if (score >= 45) return { text: 'HOLD', class: 'score-fair' };
    if (score >= 30) return { text: 'WEAK SELL', class: 'score-fair' };
    return { text: 'SELL', class: 'score-poor' };
}
```

### Change thresholds:
```javascript
// More conservative (fewer strong buys)
if (score >= 85) return { text: 'STRONG BUY', class: 'score-excellent' };
if (score >= 70) return { text: 'BUY', class: 'score-good' };

// More aggressive (easier to buy)
if (score >= 65) return { text: 'STRONG BUY', class: 'score-excellent' };
if (score >= 50) return { text: 'BUY', class: 'score-good' };
```

---

## 4. Change Scoring Weights

**Find the `calculateScores()` function and adjust weights:**

### Example: More weight on Growth
```javascript
// Default: growth += 30
// Change to: growth += 50
if (!isNaN(m.revGrowth) && m.revGrowth > 20) growth += 50;  // More weight
```

### Example: Less weight on Valuation
```javascript
// Default: val += 30
// Change to: val += 15
if (!isNaN(m.pe) && m.pe <= 20) val += 15;  // Less weight
```

### Current Scoring Structure:
```
Valuation: 30%
Profitability: 30%
Growth: 20%
Health: 20%
```

To change distribution, modify the individual metric weights.

---

## 5. Add Custom Metrics

### Add a new input field:

**1. Add to HTML form (around line 350):**
```html
<div class="form-group">
    <label>Free Cash Flow Growth %</label>
    <div class="input-wrapper">
        <input type="number" id="fcfGrowth" placeholder="5" step="0.1">
        <span class="unit-label">%</span>
    </div>
    <div class="help-text">Free cash flow growth rate</div>
</div>
```

**2. Extract value in `analyzeStock()` function:**
```javascript
fcfGrowth: parseFloat(document.getElementById('fcfGrowth').value),
```

**3. Add to scoring in `calculateScores()`:**
```javascript
if (!isNaN(m.fcfGrowth) && m.fcfGrowth > 10) growth += 20;
```

**4. Display in results:**
```javascript
${createMetricCard('FCF Growth', (m.fcfGrowth?.toFixed(1) || 'N/A') + '%', 'Free cash flow', scores.growth)}
```

---

## 6. Change Footer

**Find the footer (near end of `<body>`):**

```html
<footer>
    <p>Stock Fundamental Analyzer | Free tool for educational purposes</p>
    <p>Built with ❤️ | <a href="https://github.com" class="github-link">View on GitHub</a></p>
</footer>
```

**Change to:**
```html
<footer>
    <p>My Stock Analyzer | Powered by Your Name</p>
    <p>Built with ❤️ | <a href="https://github.com/yourname/stock-analyzer" class="github-link">View on GitHub</a></p>
</footer>
```

---

## 7. Change Default Sample Data

**Find this section in the HTML:**

```html
<div class="sample-data">
    <strong>Sample Data:</strong> Try the earlier example - P/E: 2.83, ROE: 25.9%, ROCE: 20.5%, Revenue Growth: 21.4%, D/E: 0.12
</div>
```

**Change to your preferred example:**
```html
<div class="sample-data">
    <strong>Sample Data:</strong> TCS - P/E: 24.5, ROE: 28%, ROCE: 22%, Revenue Growth: 18%, D/E: 0.3
</div>
```

---

## 8. Add Google Analytics (Optional)

**Add before `</head>` closing tag:**

```html
<!-- Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```

Replace `GA_MEASUREMENT_ID` with your Google Analytics ID.

---

## 9. Change Font Family

**Find in CSS:**
```css
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', sans-serif;
```

**Change to popular alternatives:**

```css
/* For modern look */
font-family: 'Inter', 'Helvetica', sans-serif;

/* For professional look */
font-family: 'Georgia', 'Times New Roman', serif;

/* For developer look */
font-family: 'Courier New', 'Monaco', monospace;

/* Import from Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap');
font-family: 'Poppins', sans-serif;
```

---

## 10. Add Favicon

**Add to `<head>` section:**

```html
<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>📊</text></svg>">
```

Or use your own image:
```html
<link rel="icon" href="path/to/favicon.ico">
```

---

## 11. Change Button Text

**Find button in form:**
```html
<button class="primary" onclick="analyzeStock()">Analyze Stock ↗</button>
```

**Change to:**
```html
<button class="primary" onclick="analyzeStock()">Generate Report ↗</button>
```

---

## 12. Add Custom Help Text

**Find metric help text (example):**
```html
<div class="help-text">Lower = Better. Typical: 15-25</div>
```

**Change to:**
```html
<div class="help-text">📊 Lower is better. Industry average: 18</div>
```

---

## 13. Modify Scoring Benchmarks

**Current benchmarks in `calculateScores()`:**

```javascript
// P/E scoring
if (m.pe <= 20) val += 30;        // P/E under 20
else if (m.pe <= 25) val += 20;   // P/E under 25
else if (m.pe <= 35) val += 10;   // P/E under 35
```

**Change for different market:**
```javascript
// For high-growth tech stocks
if (m.pe <= 40) val += 30;        // P/E under 40
else if (m.pe <= 60) val += 20;   // P/E under 60
else if (m.pe <= 100) val += 10;  // P/E under 100
```

---

## 14. Change Tab Names

**Find tabs section:**
```html
<button class="tab-btn active" onclick="switchTab('input', event)">Input Metrics</button>
<button class="tab-btn" onclick="switchTab('results', event)">Results</button>
<button class="tab-btn" onclick="switchTab('guide', event)">Parameter Guide</button>
```

**Change to:**
```html
<button class="tab-btn active" onclick="switchTab('input', event)">📝 Enter Data</button>
<button class="tab-btn" onclick="switchTab('results', event)">📊 Analysis</button>
<button class="tab-btn" onclick="switchTab('guide', event)">❓ Help</button>
```

---

## 15. Theme Presets

### Conservative Value Investor Theme
```css
--color-bg-success: #1a472a;      /* Dark green */
--color-bg-info: #1c3a70;         /* Dark blue */
--color-bg-warning: #8b6914;      /* Gold */
--color-bg-danger: #5a1a1a;       /* Dark red */
```

### Modern Tech Theme
```css
--color-bg-success: #00d084;      /* Bright green */
--color-bg-info: #00b4ff;         /* Bright blue */
--color-bg-warning: #ff9500;      /* Bright orange */
--color-bg-danger: #ff3333;       /* Bright red */
```

### Minimalist Theme
```css
--color-bg-success: #333333;      /* Dark gray */
--color-bg-info: #666666;         /* Medium gray */
--color-bg-warning: #999999;      /* Light gray */
--color-bg-danger: #cccccc;       /* Very light gray */
```

---

## 16. Quick Find & Replace

**Find these for easy customization:**

- `Stock Fundamental Analyzer` → Your app name
- `Free comprehensive stock analysis` → Your tagline
- `https://github.com` → Your GitHub URL
- `🚀 Analyze Stock` → Your button text
- `input-metrics` → Your preferred tab structure

---

## Testing Your Changes

After making changes:

1. **Save the file**
2. **Open in browser** (or refresh if already open)
3. **Clear cache** (Ctrl+Shift+Del or Cmd+Shift+Del)
4. **Test functionality** - Try a sample analysis
5. **Check mobile** - Test on phone/tablet

---

## Common Mistakes to Avoid

❌ **Don't remove closing braces `}`**
```javascript
// Wrong
if (score >= 75) return { text: 'STRONG BUY'

// Right
if (score >= 75) return { text: 'STRONG BUY', class: 'score-excellent' };
```

❌ **Don't break HTML structure**
```html
<!-- Wrong -->
<input type="number"
<button>Click</button>

<!-- Right -->
<input type="number">
<button>Click</button>
```

❌ **Don't modify CSS variable names**
```css
/* Wrong */
--my-color: blue;  /* Changed name */

/* Right */
--color-bg-info: blue;  /* Use existing name */
```

---

## Getting Help

If you break something:

1. **Undo** your last change
2. **Use browser DevTools** (F12) to find errors
3. **Check console** for JavaScript errors
4. **Compare** with original `index.html`
5. **Copy-paste** working code from backup

---

**Pro Tip:** Keep a backup of the original `index.html` before making big changes!

