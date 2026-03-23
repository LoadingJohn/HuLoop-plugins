# Data Processor Plugin

Advanced data transformation and processing capabilities for ETL workflows.

## Features

- ✅ **Validate Data**: Check data quality and format compliance
- 🔄 **Transform Data**: Convert between JSON, CSV, XML, YAML, TSV, JSONL
- 🔗 **Field Mapping**: Map and transform fields during conversion
- 🎯 **Batch Processing**: Process multiple files efficiently
- 📋 **Schema Detection**: Automatically detect data schemas

## Installation

```bash
/plugin install data-processor@huloop-plugins
```

## Quick Start

### Validate Your Data

```bash
/validate-data users.csv user_schema.json
```

Checks for:
- Missing required fields
- Invalid data types
- Format violations
- Duplicate entries
- Data quality issues

### Transform Data Formats

```bash
/transform-data orders.csv --to json --map field_mapping.json
```

Converts:
- CSV ↔ JSON
- JSON ↔ XML
- CSV ↔ YAML
- Any → Any supported format

## Available Skills

### 1. Validate Data
- **Command**: `/validate-data`
- **Purpose**: Validate data against schemas
- **Input**: Data file + optional schema
- **Output**: Validation report

### 2. Transform Data
- **Command**: `/transform-data`
- **Purpose**: Convert and transform data
- **Input**: Source file + target format
- **Output**: Converted data file

## Supported Formats

| Format | Extension | Use Case |
|--------|-----------|----------|
| JSON | .json | APIs, structured data |
| CSV | .csv | Spreadsheets, reports |
| XML | .xml | Configuration, documents |
| YAML | .yaml/.yml | Config files, specs |
| TSV | .tsv | Tab-separated data |
| JSONL | .jsonl | Streaming, line-delimited |

## Validation Rules

### Type Validation
```json
{
  "name": "string",
  "age": "number",
  "active": "boolean",
  "created_at": "date"
}
```

### Pattern Validation
```json
{
  "email": "^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$",
  "phone": "^[0-9]{10}$"
}
```

### Range Validation
```json
{
  "age": {"min": 0, "max": 150},
  "score": {"min": 0, "max": 100}
}
```

## Field Mapping

Create a `mapping.json` file:

```json
{
  "mappings": {
    "first_name": "firstName",
    "last_name": "lastName",
    "email_address": "email",
    "phone_number": "phone"
  },
  "transforms": {
    "email": "lowercase",
    "phone": "clean_phone",
    "created_at": "parse_date"
  },
  "filters": {
    "status": "active"
  }
}
```

Then apply:
```bash
/transform-data users.csv --to json --map mapping.json
```

## Examples

### Example 1: CSV to JSON with Validation

```bash
# Create schema
cat > user_schema.json << 'EOF'
{
  "name": "string",
  "email": "email",
  "age": "number",
  "status": "string"
}
EOF

# Validate
/validate-data users.csv user_schema.json

# Transform
/transform-data users.csv --to json
```

### Example 2: Clean and Reformat Data

```bash
# Define transformations
cat > clean_mapping.json << 'EOF'
{
  "mappings": {
    "customer_id": "id",
    "customer_name": "name"
  },
  "transforms": {
    "email": "lowercase",
    "phone": "clean_phone",
    "created": "parse_date"
  }
}
EOF

# Apply transformation
/transform-data raw_customers.csv --to json --map clean_mapping.json
```

### Example 3: Data Pipeline

```bash
# 1. Validate source data
/validate-data source.csv schema.json

# 2. Transform to target format
/transform-data source.csv --to json --map mappings.json --output target.json

# 3. Validate output
/validate-data target.json schema.json
```

## Performance

- Small files (<1MB): Instant
- Medium files (1-100MB): <1 minute
- Large files (>100MB): Progress indicator shown

## Data Privacy

- All processing is local
- No data sent to external services
- Supports encrypted file processing

## Troubleshooting

### "Invalid format" Error
- Check file extension matches content
- Validate syntax (use jsonlint, xmllint)
- Ensure proper encoding (UTF-8)

### "Type mismatch" Error
- Review schema definitions
- Check actual data types
- Use auto-fix option: `/validate-data file.csv schema.json --auto-fix`

### "Mapping not found" Error
- Verify field names in mapping file
- Check source file column names
- Use case-sensitive matching

## Best Practices

1. **Always validate** before transforming
2. **Create schemas** for consistency
3. **Test mappings** on small samples first
4. **Keep mapping files** for documentation
5. **Version control** your schemas and mappings

## Contributing

Issues and feature requests: [GitHub Issues](https://github.com/LoadingJohn/HuLoop-plugins/issues)

## License

MIT License - See LICENSE file for details
