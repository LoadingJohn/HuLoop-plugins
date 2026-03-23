# Analytics Dashboard Plugin

Real-time analytics and insights generation for data analysis projects.

## Features

- 📊 **Generate Metrics**: Calculate statistics from JSON/CSV data
- 📈 **Create Reports**: Generate professional analytics reports
- 📉 **Trend Analysis**: Identify patterns and trends in data
- 🎯 **Performance Metrics**: Key performance indicator calculations

## Installation

```bash
/plugin install analytics-dashboard@huloop-plugins
```

## Quick Start

### Generate Metrics from Data

```bash
/generate-metrics sales_data.csv
```

This skill analyzes your data and returns:
- Statistical summaries (mean, median, std dev)
- Distribution analysis
- Category breakdowns
- Quality metrics

### Create Professional Reports

```bash
/create-report q1-performance html
```

Generates comprehensive reports with:
- Executive summaries
- Visual dashboards
- Detailed metrics
- Trend analysis
- Actionable insights

## Available Skills

### 1. Generate Analytics Metrics
- **Command**: `/generate-metrics`
- **Purpose**: Calculate statistics and metrics from data files
- **Input**: JSON or CSV files
- **Output**: Structured metric report

### 2. Create Analytics Report
- **Command**: `/create-report`
- **Purpose**: Generate formatted analytics reports
- **Formats**: Markdown, HTML, JSON
- **Features**: Visualizations, summaries, trends

## Data Format Requirements

### JSON Format
```json
{
  "data": [
    {"date": "2026-01-01", "value": 100, "category": "A"},
    {"date": "2026-01-02", "value": 150, "category": "B"}
  ]
}
```

### CSV Format
```csv
date,value,category
2026-01-01,100,A
2026-01-02,150,B
```

## Configuration

### Environment Variables

```bash
ANALYTICS_PRECISION=2          # Decimal places for metrics
REPORT_TEMPLATE=default        # Report template style
CHART_WIDTH=80                # Terminal chart width
```

### Output Directory

By default, reports are saved to `./reports/`. You can override:

```bash
REPORT_OUTPUT_DIR=/path/to/reports /plugin use analytics-dashboard
```

## Examples

### Example 1: Monthly Sales Analysis

```bash
# Generate metrics
/generate-metrics monthly_sales.csv

# Create detailed report
/create-report monthly-summary html
```

### Example 2: Performance Dashboard

```bash
# Analyze performance data
/generate-metrics performance_metrics.json group-by=department

# Generate trend report
/create-report performance-trends markdown include-charts
```

### Example 3: Period Comparison

```bash
# Compare Q1 vs Q2 data
/create-report quarterly-comparison markdown
```

## Troubleshooting

### "File not found" Error
- Ensure file path is correct and relative to current working directory
- Use absolute paths for clarity: `/full/path/to/data.csv`

### "Invalid format" Error
- Verify JSON is valid (use https://jsonlint.com)
- Check CSV headers match expected format
- Ensure numeric columns contain only numbers

### Report Generation Slow
- Large files (>10MB) may take time
- Consider filtering data before analysis
- Use `group-by` for aggregation

## Performance Notes

- Files up to 100MB: < 5 seconds
- Large datasets: Consider pre-aggregation
- Real-time dashboards: Use streaming data plugins

## Security

- No data is sent externally
- All processing is local
- Supports encrypted file input

## Contributing

Found a bug or have a feature request? Open an issue on [GitHub](https://github.com/LoadingJohn/HuLoop-plugins/issues).

## License

MIT License - See LICENSE file for details

## Support

- **Documentation**: See this README
- **Examples**: Check the `examples/` directory
- **Issues**: Report on GitHub
