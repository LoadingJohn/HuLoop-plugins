---
name: Transform Data
description: Convert and transform data between formats (JSON, CSV, XML) with field mapping
version: 1.0.0
argument-hint: (input_file) --to (output_format) [--map mapping.json]
allowed-tools: [Read, Write, Bash, Glob]
---

# Transform Data

This skill converts data between multiple formats and applies field transformations using mapping rules.

## Usage

Activate with:
```
/transform-data users.csv --to json --map field_mapping.json
```

## Supported Formats

- **JSON**: Structured object/array format
- **CSV**: Comma-separated values
- **XML**: Extensible markup language
- **YAML**: YAML format
- **TSV**: Tab-separated values
- **JSONL**: JSON Lines format

## Transformation Capabilities

- **Format Conversion**: Convert between any supported format
- **Field Mapping**: Rename, select, compute fields
- **Data Filtering**: Apply conditions to rows
- **Aggregation**: Group and summarize data
- **Flattening**: Convert nested to flat structure
- **Nesting**: Create hierarchical structures

## Example Mapping File

```json
{
  "mappings": {
    "first_name": "firstName",
    "last_name": "lastName",
    "email_address": "email"
  },
  "transforms": {
    "email": "lowercase",
    "phone": "clean_phone"
  },
  "filters": {
    "status": "active"
  }
}
```

## Examples

### CSV to JSON
```bash
/transform-data sales.csv --to json
```

### JSON to XML
```bash
/transform-data data.json --to xml --map mappings.json
```

### CSV to JSONL
```bash
/transform-data records.csv --to jsonl --filters status=active
```

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| file | string | ✅ | Input data file |
| --to | string | ✅ | Target format |
| --map | string | ❌ | Field mapping configuration |
| --filter | string | ❌ | Filter conditions |
| --output | string | ❌ | Output file path |

## Supported Transformations

- `lowercase`: Convert text to lowercase
- `uppercase`: Convert text to uppercase
- `trim`: Remove whitespace
- `clean_phone`: Format phone numbers
- `clean_email`: Normalize email format
- `parse_date`: Parse date strings
- `concat`: Combine fields

## Output

Generates transformed data file with:
- Converted format
- Applied mappings
- Filtered records
- Transformation summary
- Error report if any
