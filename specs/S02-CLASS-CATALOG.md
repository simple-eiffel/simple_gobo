# S02: CLASS CATALOG - simple_gobo

**Document**: S02-CLASS-CATALOG.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## Core Classes

### Argument Parsing

| Class | Type | Description |
|-------|------|-------------|
| AP_PARSER | Effective | Full parser with help option |
| AP_BASIC_PARSER | Effective | Core parsing without predefined options |
| AP_OPTION | Deferred | Base class for all options |
| AP_FLAG | Effective | Simple boolean flag (-v) |
| AP_BOOLEAN_OPTION | Effective | Boolean with explicit value |
| AP_INTEGER_OPTION | Effective | Integer-valued option |
| AP_STRING_OPTION | Effective | String-valued option |
| AP_ENUMERATION_OPTION | Effective | Enumerated value option |
| AP_OPTION_WITH_PARAMETER | Deferred | Base for parameterized options |
| AP_DISPLAY_HELP_FLAG | Effective | Built-in help display |
| AP_ERROR | Effective | Parsing error representation |
| AP_ERROR_HANDLER | Effective | Error collection and reporting |
| AP_ALTERNATIVE_OPTIONS_LIST | Effective | Mutually exclusive option groups |
| AP_OPTION_COMPARATOR | Effective | For sorting options in help |
| AP_CONSTANTS | Effective | Parsing constants |

### Encoding (Free ELKS)

| Class | Type | Description |
|-------|------|-------------|
| ENCODING | Effective | Base encoding handler |
| ENCODING_I | Deferred | Implementation interface |
| ENCODING_IMP | Effective | Platform-specific impl |
| ENCODING_HELPER | Effective | Conversion utilities |
| SYSTEM_ENCODINGS | Effective | System default encodings |
| CODE_PAGE_CONSTANTS | Effective | Windows code page IDs |
| UNICODE_CONVERSION | Effective | Unicode utilities |

### Kernel Extensions

| Class | Type | Description |
|-------|------|-------------|
| ANY (extended) | Effective | Base class extensions |
| ARRAY (extended) | Effective | Array enhancements |
| EXCEPTION hierarchy | Various | Exception types |

## Inheritance Hierarchy

```
AP_OPTION (deferred)
├── AP_FLAG
│   └── AP_DISPLAY_HELP_FLAG
├── AP_BOOLEAN_OPTION
└── AP_OPTION_WITH_PARAMETER (deferred)
    ├── AP_STRING_OPTION
    ├── AP_INTEGER_OPTION
    └── AP_ENUMERATION_OPTION

AP_BASIC_PARSER
└── AP_PARSER
```
