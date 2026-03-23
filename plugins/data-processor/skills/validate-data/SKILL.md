---
name: Validate Data
description: Validate and sanitize data files for quality and format compliance
version: 1.0.0
argument-hint: (data_file) [schema.json]
allowed-tools: [Read, Bash, Write]
---

# Validate Data

This skill validates data files against schemas, checks for formatting issues, and ensures data quality standards are met.

## Usage

Activate with:
```
/validate-data users.json users_schema.json
```

## Validation Checks

- **Type Validation**: Ensure correct data types
- **Format Validation**: Email, phone, date formats
- **Range Validation**: Numeric and string length bounds
- **Required Fields**: Check mandatory fields present
- **Uniqueness**: Detect duplicate entries
- **Referential Integrity**: Cross-table consistency

## Capabilities

- **Schema Support**
  - JSON Schema format
  - Custom validation rules
  - Type definitions

- **Issue Detection**
  - Invalid entries
  - Missing required fields
  - Format mismatches
  - Duplicate records
  - Orphaned references

- **Output**
  - Validation report with line numbers
  - Error categorization
  - Fix suggestions
  - Sanitized data output

## Example

```bash
/validate-data customers.csv schema.json
```

Returns:
- Total records scanned
- Valid records count
- Errors found (with locations)
- Warnings about data quality
- Corrected dataset option

## Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| file | string | ✅ | Data file to validate |
| schema | string | ❌ | Schema file for validation |
| auto-fix | boolean | ❌ | Attempt to fix issues (default: false) |
| strict-mode | boolean | ❌ | Enforce strict validation (default: true) |

## Output

Generates validation report with:
- **Summary**: Pass/fail and statistics
- **Errors**: Detailed error listing
- **Warnings**: Data quality issues
- **Suggestions**: How to fix issues
- **Report**: Can be saved to file
