# S04: FEATURE SPECS - simple_gobo

**Document**: S04-FEATURE-SPECS.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## AP_PARSER Features

### Initialization
| Feature | Signature | Description |
|---------|-----------|-------------|
| make | make | Create parser with help option |

### Access
| Feature | Signature | Description |
|---------|-----------|-------------|
| help_option | AP_DISPLAY_HELP_FLAG | The built-in help flag |

## AP_BASIC_PARSER Features

### Initialization
| Feature | Signature | Description |
|---------|-----------|-------------|
| make | make | Create parser without predefined options |

### Access
| Feature | Signature | Description |
|---------|-----------|-------------|
| options | DS_LIST [AP_OPTION] | List of available options |
| alternative_options_lists | DS_LIST [AP_ALTERNATIVE_OPTIONS_LIST] | Alternative option sets |
| parameters | DS_LIST [STRING] | Non-option arguments |
| application_description | STRING | App description for help |
| parameters_description | STRING | Parameters description |
| error_handler | AP_ERROR_HANDLER | Error handler |
| last_option_parameter | detachable STRING | Last parsed parameter |
| all_options | DS_LIST [AP_OPTION] | All options including alternatives |

### Configuration
| Feature | Signature | Description |
|---------|-----------|-------------|
| set_application_description | (STRING) | Set app description |
| set_parameters_description | (STRING) | Set params description |
| set_error_handler | (AP_ERROR_HANDLER) | Set error handler |

### Status Report
| Feature | Signature | Description |
|---------|-----------|-------------|
| has_long_option | (STRING): BOOLEAN | Check for long option |
| has_short_option | (CHARACTER): BOOLEAN | Check for short option |
| valid_options | BOOLEAN | Are all options valid? |

### Parsing
| Feature | Signature | Description |
|---------|-----------|-------------|
| parse_arguments | | Parse command line |
| parse_array | (ARRAY [STRING]) | Parse array of strings |
| parse_list | (DS_LIST [STRING]) | Parse list of strings |

### Help
| Feature | Signature | Description |
|---------|-----------|-------------|
| full_help_text | STRING | Complete help text |
| full_usage_instruction | STRING | Usage line |

## AP_OPTION Features

### Access
| Feature | Signature | Description |
|---------|-----------|-------------|
| short_form | CHARACTER | Short option character |
| long_form | detachable STRING | Long option name |
| description | STRING | Help description |
| is_mandatory | BOOLEAN | Is option required? |
| was_found | BOOLEAN | Was option parsed? |
| occurrences | INTEGER | Times option appeared |

### Status
| Feature | Signature | Description |
|---------|-----------|-------------|
| has_short_form | BOOLEAN | Has short form? |
| has_long_form | BOOLEAN | Has long form? |
| needs_parameter | BOOLEAN | Requires parameter? |
| allows_parameter | BOOLEAN | Accepts parameter? |
