# 7S-04: SIMPLE-STAR - simple_gobo

**Document**: 7S-04-SIMPLE-STAR.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## Ecosystem Integration

### Dependencies (Incoming)

simple_gobo is a foundation library with no simple_* dependencies.

### Dependents (Outgoing)

Libraries that use simple_gobo:

| Library | Usage |
|---------|-------|
| simple_oracle | CLI argument parsing |
| claude_tools | Command-line interface |
| Various CLI tools | AP_PARSER for options |

### Integration Patterns

1. **Argument Parsing Pattern**
```eiffel
class MY_CLI
inherit
    AP_PARSER
create
    make
feature
    make
        do
            precursor
            create verbose_flag.make ('v', "verbose")
            options.force_last (verbose_flag)
            parse_arguments
        end
    verbose_flag: AP_FLAG
end
```

2. **Encoding Usage**
```eiffel
local
    l_encoding: ENCODING
do
    l_encoding := {SYSTEM_ENCODINGS}.utf8
    -- use for text conversion
end
```

### API Compatibility

- Follows Gobo naming conventions (AP_*, DS_*, KL_*, etc.)
- Integrates with EiffelStudio's test framework
- Compatible with all simple_* libraries

### Shared Patterns

- Uses Design by Contract throughout
- Void-safe implementation
- No external C dependencies for core functionality
