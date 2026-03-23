---
name: Generate Analytics Metrics
description: Calculate key performance metrics and statistics from data
version: 1.0.0
argument-hint: (data_file.json or data_file.csv)
allowed-tools: [Read, Bash, Grep]
---

# Generate Analytics Metrics

This skill analyzes data files and calculates comprehensive performance metrics including averages, medians, standard deviations, and distribution analysis.

## Usage

Activate with:
```
/generate-metrics data.json
```

## Capabilities

- **Statistical Analysis**
  - Mean, median, mode calculations
  - Standard deviation and variance
  - Percentile calculations
  - Distribution analysis

- **Data Type Support**
  - JSON objects and arrays
  - CSV files with headers
  - Raw numeric data

- **Output Formats**
  - Summary statistics table
  - JSON metric export
  - ASCII charts for visualization

## Example

```bash
/generate-metrics sales_2026.csv
```

Returns:
- Total records analyzed
- Numeric field summary (min, max, mean)
- Category distribution
- Time-based trends
- Data quality report

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| file | string | ✅ | Path to data file (JSON or CSV) |
| group-by | string | ❌ | Field to group metrics by |
| date-range | string | ❌ | Filter by date range (ISO format) |

## Output

Generates a structured metrics report with:
- **Summary**: Key statistics
- **Details**: Per-field analysis
- **Trends**: Time-series analysis if applicable
- **Quality**: Data completeness scores
