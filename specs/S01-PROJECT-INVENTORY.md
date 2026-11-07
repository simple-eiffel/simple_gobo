# S01: PROJECT INVENTORY - simple_gobo

**Document**: S01-PROJECT-INVENTORY.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## Project Structure

```
simple_gobo/
├── library/
│   ├── argument/
│   │   ├── src/           -- Argument parsing classes
│   │   ├── example/       -- Usage examples
│   │   └── test/          -- Unit tests
│   ├── common/
│   │   ├── example/       -- Hello world, etc.
│   │   └── test/          -- Test infrastructure
│   └── free_elks/
│       └── src/
│           └── elks/
│               ├── encoding/       -- Character encoding
│               ├── kernel/         -- Core types
│               └── kernel/exceptions/  -- Exception hierarchy
├── research/              -- 7S research documents
├── specs/                 -- Specification documents
└── simple_gobo.ecf        -- ECF configuration
```

## Source Files

### Argument Library (library/argument/src/)
| File | Purpose |
|------|---------|
| ap_parser.e | Main parser with help option |
| ap_basic_parser.e | Core parsing engine |
| ap_option.e | Base option class |
| ap_flag.e | Boolean flag option |
| ap_boolean_option.e | Boolean with value |
| ap_integer_option.e | Integer parameter |
| ap_string_option.e | String parameter |
| ap_enumeration_option.e | Enumerated values |
| ap_display_help_flag.e | Help display handler |
| ap_error.e | Error representation |
| ap_error_handler.e | Error handling |
| ap_constants.e | Parsing constants |
| ap_alternative_options_list.e | Alternative option sets |
| ap_option_comparator.e | Option sorting |
| ap_option_with_parameter.e | Options requiring params |

### Free ELKS (library/free_elks/src/)
- Encoding classes (10+)
- Kernel types (50+)
- Exception hierarchy (20+)

## Configuration Files

| File | Purpose |
|------|---------|
| simple_gobo.ecf | Main ECF |
| argument.ecf | Argument library ECF |
| free_elks.ecf | Free ELKS ECF |

## Test Files

- library/argument/test/unit/ap_test_parser.e
- library/argument/test/example/ap_etest_example.e
- library/common/test/integration/test_integration.e
