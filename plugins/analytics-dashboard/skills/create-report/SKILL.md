---
name: Create Analytics Report
description: Generate comprehensive analytics reports with visualizations and summaries
version: 1.0.0
argument-hint: (report_name) [format: html|markdown|json]
allowed-tools: [Read, Write, Bash, Glob]
---

# Create Analytics Report

This skill generates professional analytics reports from data files with embedded visualizations, summaries, and actionable insights.

## Usage

Activate with:
```
/create-report q1-sales markdown
```

## Report Types

- **Executive Summary**: High-level overview with key metrics
- **Detailed Analysis**: In-depth breakdowns with visualizations
- **Comparative**: Side-by-side comparison of multiple datasets
- **Trend Analysis**: Historical trends and forecasting

## Capabilities

- **Data Processing**
  - Multi-file aggregation
  - Period-over-period comparison
  - Anomaly detection
  - Forecasting

- **Visualization**
  - ASCII charts for terminal display
  - SVG/PNG support (in HTML format)
  - Interactive elements (in HTML format)
  - Data tables with sorting

- **Export Formats**
  - Markdown with embedded charts
  - HTML with styling
  - JSON for programmatic use
  - PDF (when available)

## Example

```bash
/create-report monthly-analytics html
```

Generates an HTML report with:
- Title and date range
- Executive summary
- Visual dashboards
- Detailed metrics tables
- Trends and insights
- Recommendations

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| name | string | ✅ | Report name/title |
| format | enum | ❌ | Output format (default: markdown) |
| include-charts | boolean | ❌ | Include visualizations (default: true) |
| include-raw-data | boolean | ❌ | Include raw data tables (default: false) |

## Output Location

Reports are saved to: `./reports/{name}-{date}.{format}`

## Sections Included

1. **Cover Page**: Title, date, author info
2. **Table of Contents**: Navigation guide
3. **Executive Summary**: Key findings
4. **Metrics Dashboard**: Visual overview
5. **Detailed Analysis**: Section-by-section breakdown
6. **Appendix**: Raw data, methodology notes
