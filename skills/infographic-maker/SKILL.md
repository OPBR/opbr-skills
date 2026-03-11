---
name: infographic-maker
description: >
  Transform raw data, statistics, reports, or plain text into beautiful, interactive HTML infographics and data visualizations. Use this skill whenever the user wants to visualize data, create charts, make an infographic, turn numbers into visuals, display statistics beautifully, build a dashboard, summarize data visually, or create any kind of visual data story. Trigger even when the user just says things like "make this look good", "visualize this", "turn this into a chart", "make an infographic", "create a visual summary", or pastes raw numbers and says "show this". Works with CSV data, copied table data, bullet points of stats, or even descriptive text containing numbers.
---

# Infographic Maker

This skill transforms data and information into polished, interactive HTML infographics — no coding or design tools required.

## When to Use

Trigger this skill when the user:
- Pastes data (CSV, table, bullet points with numbers)
- Says "make this visual", "create a chart", "make an infographic"
- Shares a report/research and wants a visual summary
- Wants to present statistics in a compelling way
- Mentions keywords: dashboard, visualization, chart, graph, infographic, data story

## Core Workflow

### Step 1: Analyze Input

Parse what the user gave you:
- **Structured data** (CSV, table) → identify columns, data types, relationships
- **Stats/bullet points** → extract key numbers, categories, trends
- **Text/report** → identify the most impactful 5-8 statistics worth highlighting
- **No data yet** → ask for the data or topic, then suggest what would make a great infographic

### Step 2: Choose Visualization Strategy

Select chart types intelligently based on data shape:

| Data Type | Best Visualization |
|-----------|-------------------|
| Comparison (A vs B vs C) | Bar chart, grouped bars |
| Trend over time | Line chart, area chart |
| Part of whole | Donut chart, waffle chart |
| Distribution | Histogram, box plot style |
| Correlation | Scatter plot |
| Geographic | Map with color coding |
| Single impressive stat | Big number "hero stat" card |
| Multi-metric overview | Dashboard with mixed charts |
| Process/flow | Timeline or step infographic |

For most requests, combine 2-4 chart types with hero stats for a compelling infographic.

### Step 3: Generate the HTML Infographic

**Always output a complete, self-contained HTML file** using the guidelines in `references/html-template-guide.md`.

Key requirements:
- Single HTML file, no external dependencies except CDN libraries
- Use Chart.js (from cdnjs) for charts
- Mobile responsive
- Beautiful default styling (see design principles below)
- Interactive (hover tooltips, animations on load)
- Include a title, subtitle, and source/notes section

### Step 4: Save and Present

Save the output to `/mnt/user-data/outputs/infographic.html` and use `present_files` to share with the user.

---

## Design Principles

### Color Palettes (pick one based on context)

**Professional/Corporate:**
```
Primary: #2D3748, Accent: #4299E1, Highlights: #48BB78, #ED8936, #9F7AEA
```

**Vibrant/Modern:**
```
#FF6B6B, #4ECDC4, #45B7D1, #96CEB4, #FFEAA7, #DDA0DD
```

**Minimal/Clean:**
```
#1A1A2E, #16213E, #0F3460, #E94560 (dark theme)
```

**Nature/Health:**
```
#2D6A4F, #40916C, #52B788, #74C69D, #95D5B2
```

### Layout Templates

**Single Hero Stat:**
Large centered number with context label and trend indicator.

**3-Column Stats Row:**
Three key metrics side by side with icons and descriptions.

**Full Dashboard:**
Top row: 3 hero stats. Middle: Large main chart. Bottom: 2 smaller supporting charts.

**Narrative Infographic:**
Vertical scroll layout telling a data story from top to bottom.

### Typography
- Titles: Bold, 2-3rem, high contrast
- Stats: Extra-bold, 3-5rem for hero numbers
- Labels: 0.85rem, muted color
- Body: 1rem, good line-height

---

## Code Templates

### Basic Chart.js Setup
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Infographic Title</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
  <style>
    /* Reset + base */
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: 'Segoe UI', system-ui, sans-serif; background: #f8fafc; color: #1a202c; }
    
    /* Container */
    .infographic { max-width: 900px; margin: 0 auto; padding: 2rem; }
    
    /* Header */
    .header { text-align: center; margin-bottom: 2rem; }
    .header h1 { font-size: 2rem; font-weight: 800; color: #1a202c; }
    .header p { font-size: 1rem; color: #718096; margin-top: 0.5rem; }
    
    /* Hero stats */
    .stats-row { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 1.5rem; margin-bottom: 2rem; }
    .stat-card { background: white; border-radius: 12px; padding: 1.5rem; text-align: center; box-shadow: 0 2px 8px rgba(0,0,0,0.08); }
    .stat-number { font-size: 3rem; font-weight: 900; line-height: 1; }
    .stat-label { font-size: 0.85rem; color: #718096; margin-top: 0.5rem; text-transform: uppercase; letter-spacing: 0.05em; }
    
    /* Chart cards */
    .chart-card { background: white; border-radius: 12px; padding: 1.5rem; margin-bottom: 1.5rem; box-shadow: 0 2px 8px rgba(0,0,0,0.08); }
    .chart-title { font-size: 1rem; font-weight: 700; margin-bottom: 1rem; color: #2d3748; }
    
    /* Footer */
    .footer { text-align: center; font-size: 0.75rem; color: #a0aec0; margin-top: 2rem; }
  </style>
</head>
<body>
  <div class="infographic">
    <!-- Header -->
    <div class="header">
      <h1>Your Infographic Title</h1>
      <p>Subtitle or description of the data story</p>
    </div>
    
    <!-- Hero Stats Row -->
    <div class="stats-row">
      <div class="stat-card">
        <div class="stat-number" style="color: #4299E1;">42%</div>
        <div class="stat-label">Metric Name</div>
      </div>
      <!-- more stat cards... -->
    </div>
    
    <!-- Chart -->
    <div class="chart-card">
      <div class="chart-title">Chart Title</div>
      <canvas id="mainChart" height="300"></canvas>
    </div>
    
    <div class="footer">Source: Your data source · Created with Claude</div>
  </div>

  <script>
    // Animate hero numbers on load
    document.querySelectorAll('.stat-number').forEach(el => {
      el.style.opacity = '0';
      el.style.transform = 'translateY(20px)';
      el.style.transition = 'all 0.6s ease';
      setTimeout(() => {
        el.style.opacity = '1';
        el.style.transform = 'translateY(0)';
      }, 200);
    });

    // Bar chart example
    new Chart(document.getElementById('mainChart'), {
      type: 'bar',
      data: {
        labels: ['Label 1', 'Label 2', 'Label 3'],
        datasets: [{
          label: 'Dataset',
          data: [65, 89, 72],
          backgroundColor: ['#4299E1', '#48BB78', '#ED8936'],
          borderRadius: 8,
          borderSkipped: false,
        }]
      },
      options: {
        responsive: true,
        plugins: {
          legend: { display: false },
          tooltip: { 
            backgroundColor: '#1a202c',
            titleColor: '#e2e8f0',
            bodyColor: '#a0aec0',
            padding: 12,
            cornerRadius: 8,
          }
        },
        scales: {
          y: { grid: { color: '#f7fafc' }, ticks: { color: '#718096' } },
          x: { grid: { display: false }, ticks: { color: '#718096' } }
        }
      }
    });
  </script>
</body>
</html>
```

---

## Handling Different Input Types

### CSV / Table Data
Parse the data, identify the most interesting patterns (biggest values, trends, outliers), and build charts around them. Don't just chart everything — **select the most compelling 2-4 views**.

### Report / Article Text
Extract the top statistics mentioned. Prioritize:
1. Surprising or impressive numbers
2. Before/after comparisons
3. Growth metrics
4. Part-of-whole breakdowns

### Vague Request ("make something about climate change")
Ask: "Do you have specific data you'd like me to use, or should I create a sample infographic with representative statistics?" Then proceed with whatever they provide.

### "Make this prettier" (existing chart or visualization)
Recreate it in the infographic style — better colors, rounded corners, hero stats, clean typography.

---

## Quality Checklist

Before outputting, verify:
- [ ] All data is accurately represented (no hallucinated numbers)
- [ ] Charts have clear titles and axis labels
- [ ] Color contrast is accessible (WCAG AA minimum)
- [ ] File is completely self-contained (no broken external links)
- [ ] Animations don't break on first load
- [ ] Responsive on mobile widths
- [ ] Source attribution included if data was provided by user

---

## Common Pitfalls to Avoid

- **Don't use 3D charts** — they distort perception, always use 2D
- **Don't use pie charts with more than 5 slices** — use bar chart instead  
- **Don't start Y-axis at a non-zero value** without clear labeling
- **Don't use rainbow gradients** — stick to 2-4 color palette
- **Don't crowd the layout** — whitespace is your friend
- **Don't forget mobile** — use CSS grid with `auto-fit`

---

## Advanced Techniques

### Animated Number Counter
```javascript
function animateCounter(el, target, duration = 1500) {
  const start = 0;
  const increment = target / (duration / 16);
  let current = start;
  const timer = setInterval(() => {
    current += increment;
    if (current >= target) { current = target; clearInterval(timer); }
    el.textContent = Math.floor(current).toLocaleString();
  }, 16);
}
```

### Progress Bar Component
```html
<div class="progress-item">
  <div style="display:flex; justify-content:space-between; margin-bottom:6px;">
    <span class="label">Category Name</span>
    <span class="value">73%</span>
  </div>
  <div style="background:#e2e8f0; border-radius:999px; height:10px; overflow:hidden;">
    <div style="width:73%; background:#4299E1; height:100%; border-radius:999px; 
         transition: width 1s ease; animation: growBar 1s ease forwards;"></div>
  </div>
</div>
<style>
@keyframes growBar { from { width: 0; } to { width: 73%; } }
</style>
```

### Donut Chart with Center Label
```javascript
// Plugin to show text in center of donut
const centerTextPlugin = {
  id: 'centerText',
  afterDraw(chart) {
    const { ctx, chartArea: { width, height, left, top } } = chart;
    const centerX = left + width / 2;
    const centerY = top + height / 2;
    ctx.save();
    ctx.font = 'bold 2rem Segoe UI, sans-serif';
    ctx.fillStyle = '#1a202c';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillText('72%', centerX, centerY - 10);
    ctx.font = '0.75rem Segoe UI, sans-serif';
    ctx.fillStyle = '#718096';
    ctx.fillText('COMPLETION', centerX, centerY + 18);
    ctx.restore();
  }
};
Chart.register(centerTextPlugin);
```

---

See `references/chart-examples.md` for more complete chart implementations and layout examples.