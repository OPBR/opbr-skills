# Chart Examples & Layout Reference

## Layout: Full Dashboard

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dashboard Infographic</title>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body { font-family: 'Segoe UI', system-ui, sans-serif; background: #f0f4f8; }
    .page { max-width: 960px; margin: 0 auto; padding: 2rem 1.5rem; }
    .header { text-align: center; padding: 1.5rem 0 2rem; }
    .header h1 { font-size: 2.2rem; font-weight: 900; color: #1a202c; letter-spacing: -0.02em; }
    .header .subtitle { color: #718096; margin-top: 0.5rem; font-size: 1.05rem; }
    .header .badge { display: inline-block; background: #ebf8ff; color: #2b6cb0; padding: 0.25rem 0.75rem; border-radius: 999px; font-size: 0.8rem; font-weight: 600; margin-top: 0.75rem; }
    
    /* Stats row */
    .kpi-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 1rem; margin-bottom: 1.5rem; }
    .kpi { background: white; border-radius: 16px; padding: 1.5rem 1.25rem; box-shadow: 0 1px 3px rgba(0,0,0,0.06), 0 4px 12px rgba(0,0,0,0.04); position: relative; overflow: hidden; }
    .kpi::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 4px; background: var(--color); }
    .kpi-icon { font-size: 1.5rem; margin-bottom: 0.5rem; }
    .kpi-number { font-size: 2.4rem; font-weight: 900; color: var(--color); line-height: 1; }
    .kpi-label { font-size: 0.8rem; text-transform: uppercase; letter-spacing: 0.08em; color: #a0aec0; margin-top: 0.4rem; }
    .kpi-change { font-size: 0.8rem; margin-top: 0.5rem; }
    .kpi-change.up { color: #38a169; }
    .kpi-change.down { color: #e53e3e; }
    
    /* Charts grid */
    .charts-grid { display: grid; grid-template-columns: 2fr 1fr; gap: 1.5rem; margin-bottom: 1.5rem; }
    .chart-card { background: white; border-radius: 16px; padding: 1.5rem; box-shadow: 0 1px 3px rgba(0,0,0,0.06), 0 4px 12px rgba(0,0,0,0.04); }
    .chart-card.full { grid-column: 1 / -1; }
    .chart-title { font-size: 0.95rem; font-weight: 700; color: #2d3748; margin-bottom: 0.25rem; }
    .chart-subtitle { font-size: 0.8rem; color: #a0aec0; margin-bottom: 1.25rem; }
    
    /* Bottom charts */
    .bottom-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem; }
    
    /* Footer */
    .footer { text-align: center; color: #cbd5e0; font-size: 0.75rem; margin-top: 2rem; padding-top: 1rem; border-top: 1px solid #e2e8f0; }
    
    @media (max-width: 640px) {
      .charts-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>
<div class="page">
  <div class="header">
    <h1>Your Dashboard Title</h1>
    <p class="subtitle">Description of the data being shown</p>
    <span class="badge">📅 2024 Annual Report</span>
  </div>
  
  <!-- KPI Row -->
  <div class="kpi-grid">
    <div class="kpi" style="--color: #4299e1">
      <div class="kpi-icon">📈</div>
      <div class="kpi-number">$2.4M</div>
      <div class="kpi-label">Total Revenue</div>
      <div class="kpi-change up">↑ 24% vs last year</div>
    </div>
    <div class="kpi" style="--color: #48bb78">
      <div class="kpi-icon">👥</div>
      <div class="kpi-number">12.8K</div>
      <div class="kpi-label">Active Users</div>
      <div class="kpi-change up">↑ 8% growth</div>
    </div>
    <div class="kpi" style="--color: #ed8936">
      <div class="kpi-icon">⭐</div>
      <div class="kpi-number">4.7</div>
      <div class="kpi-label">Avg Rating</div>
      <div class="kpi-change up">↑ 0.3 pts</div>
    </div>
    <div class="kpi" style="--color: #9f7aea">
      <div class="kpi-icon">🎯</div>
      <div class="kpi-number">89%</div>
      <div class="kpi-label">Goal Reached</div>
      <div class="kpi-change down">↓ 5% behind target</div>
    </div>
  </div>
  
  <!-- Main Charts -->
  <div class="charts-grid">
    <div class="chart-card">
      <div class="chart-title">Monthly Revenue Trend</div>
      <div class="chart-subtitle">Jan – Dec 2024</div>
      <canvas id="lineChart" height="200"></canvas>
    </div>
    <div class="chart-card">
      <div class="chart-title">Revenue by Category</div>
      <div class="chart-subtitle">Distribution</div>
      <canvas id="donutChart" height="200"></canvas>
    </div>
  </div>
  
  <!-- Bottom Charts -->
  <div class="bottom-grid">
    <div class="chart-card">
      <div class="chart-title">Top Performers</div>
      <div class="chart-subtitle">By sales volume</div>
      <canvas id="barChart" height="200"></canvas>
    </div>
    <div class="chart-card">
      <div class="chart-title">Weekly Activity</div>
      <div class="chart-subtitle">This month</div>
      <canvas id="areaChart" height="200"></canvas>
    </div>
  </div>
  
  <div class="footer">Data Source: Internal Systems · Generated with Claude Infographic Maker</div>
</div>

<script>
const colors = { blue: '#4299e1', green: '#48bb78', orange: '#ed8936', purple: '#9f7aea', red: '#fc8181', teal: '#4fd1c5' };
const chartDefaults = {
  plugins: {
    legend: { labels: { color: '#718096', font: { size: 12 } } },
    tooltip: { backgroundColor: '#1a202c', titleColor: '#e2e8f0', bodyColor: '#a0aec0', padding: 12, cornerRadius: 8 }
  }
};

// Line chart
new Chart(document.getElementById('lineChart'), {
  type: 'line',
  data: {
    labels: ['Jan','Feb','Mar','Apr','May','Jun','Jul','Aug','Sep','Oct','Nov','Dec'],
    datasets: [{
      label: 'Revenue',
      data: [180,220,190,280,310,290,340,380,360,420,450,390],
      borderColor: colors.blue,
      backgroundColor: colors.blue + '20',
      borderWidth: 3,
      fill: true,
      tension: 0.4,
      pointRadius: 4,
      pointHoverRadius: 6,
    }]
  },
  options: {
    ...chartDefaults,
    scales: {
      y: { grid: { color: '#f7fafc' }, ticks: { color: '#a0aec0', callback: v => '$' + v + 'k' } },
      x: { grid: { display: false }, ticks: { color: '#a0aec0' } }
    }
  }
});

// Donut chart
new Chart(document.getElementById('donutChart'), {
  type: 'doughnut',
  data: {
    labels: ['Product A', 'Product B', 'Product C', 'Others'],
    datasets: [{
      data: [42, 28, 18, 12],
      backgroundColor: [colors.blue, colors.green, colors.orange, colors.purple],
      borderWidth: 0,
      hoverOffset: 8,
    }]
  },
  options: {
    ...chartDefaults,
    cutout: '65%',
    plugins: { ...chartDefaults.plugins, legend: { position: 'bottom', labels: { padding: 16, color: '#718096' } } }
  }
});

// Bar chart
new Chart(document.getElementById('barChart'), {
  type: 'bar',
  data: {
    labels: ['Alice', 'Bob', 'Carol', 'Dave', 'Eve'],
    datasets: [{
      label: 'Sales',
      data: [89, 76, 72, 65, 58],
      backgroundColor: [colors.blue, colors.green, colors.orange, colors.purple, colors.teal],
      borderRadius: 8,
      borderSkipped: false,
    }]
  },
  options: {
    ...chartDefaults,
    indexAxis: 'y',
    plugins: { ...chartDefaults.plugins, legend: { display: false } },
    scales: {
      x: { grid: { color: '#f7fafc' }, ticks: { color: '#a0aec0' } },
      y: { grid: { display: false }, ticks: { color: '#718096' } }
    }
  }
});

// Area/line chart
new Chart(document.getElementById('areaChart'), {
  type: 'line',
  data: {
    labels: ['Mon','Tue','Wed','Thu','Fri','Sat','Sun'],
    datasets: [{
      label: 'Activity',
      data: [42, 68, 55, 82, 76, 45, 38],
      borderColor: colors.purple,
      backgroundColor: colors.purple + '25',
      borderWidth: 2.5,
      fill: true,
      tension: 0.4,
      pointRadius: 3,
    }]
  },
  options: {
    ...chartDefaults,
    plugins: { ...chartDefaults.plugins, legend: { display: false } },
    scales: {
      y: { grid: { color: '#f7fafc' }, ticks: { color: '#a0aec0' } },
      x: { grid: { display: false }, ticks: { color: '#a0aec0' } }
    }
  }
});
</script>
</body>
</html>
```

---

## Layout: Narrative/Vertical Infographic

Good for telling a data story top to bottom (e.g., "The State of X in 2024").

Structure:
1. Bold headline stat (the "hook")
2. Context bar chart or line chart
3. Breakdown donut/bars
4. Horizontal bar "ranking" chart
5. Key takeaways / callout boxes

---

## Layout: Comparison Infographic

Side-by-side comparison of two things (A vs B).

```html
<div style="display: grid; grid-template-columns: 1fr auto 1fr; gap: 1rem; align-items: center;">
  <div class="side" style="text-align: right;"><!-- Left side --></div>
  <div style="font-size: 1.5rem; font-weight: 900; color: #a0aec0;">VS</div>
  <div class="side"><!-- Right side --></div>
</div>
```

---

## Useful Chart.js Snippets

### Stacked Bar Chart
```javascript
datasets: [
  { label: 'Group A', data: [30, 40, 25], backgroundColor: '#4299e1', stack: 'stack' },
  { label: 'Group B', data: [20, 30, 45], backgroundColor: '#48bb78', stack: 'stack' },
]
// options: scales: { x: { stacked: true }, y: { stacked: true } }
```

### Custom Tooltip
```javascript
plugins: {
  tooltip: {
    callbacks: {
      label: (context) => ` ${context.dataset.label}: ${context.parsed.y.toLocaleString()}`,
      title: (items) => `📅 ${items[0].label}`
    }
  }
}
```

### Threshold Line (reference line)
```javascript
plugins: [{
  id: 'threshold',
  afterDraw(chart) {
    const { ctx, chartArea, scales } = chart;
    const y = scales.y.getPixelForValue(75); // threshold value
    ctx.save();
    ctx.strokeStyle = '#e53e3e';
    ctx.setLineDash([6, 4]);
    ctx.lineWidth = 2;
    ctx.beginPath();
    ctx.moveTo(chartArea.left, y);
    ctx.lineTo(chartArea.right, y);
    ctx.stroke();
    ctx.fillStyle = '#e53e3e';
    ctx.font = '11px sans-serif';
    ctx.fillText('Target: 75%', chartArea.right - 80, y - 6);
    ctx.restore();
  }
}]
```