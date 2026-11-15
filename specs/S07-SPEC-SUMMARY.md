# S07: SPEC SUMMARY - simple_gobo

**Document**: S07-SPEC-SUMMARY.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## Executive Summary

simple_gobo integrates the Gobo Eiffel Library into the simple_* ecosystem, providing essential infrastructure for command-line argument parsing and character encoding.

## Key Components

| Component | Purpose | Status |
|-----------|---------|--------|
| Argument Library | CLI option parsing | Complete |
| Free ELKS | Kernel extensions | Complete |
| Test Infrastructure | Testing support | Complete |

## Core Capabilities

### Argument Parsing
- Short options (-v, -abc)
- Long options (--verbose)
- Required and optional parameters
- Alternative option sets
- Automatic help generation
- Error handling and reporting

### Character Encoding
- UTF-8, UTF-16, UTF-32 support
- Windows code pages
- Unix locale handling
- Encoding conversion

## API Highlights

```eiffel
-- Basic usage
local
    parser: AP_PARSER
    verbose: AP_FLAG
do
    create parser.make
    create verbose.make ('v', "verbose")
    verbose.set_description ("Enable verbose output")
    parser.options.force_last (verbose)
    parser.parse_arguments

    if verbose.was_found then
        -- handle verbose mode
    end
end
```

## Quality Attributes

- **Design by Contract**: Full preconditions/postconditions
- **Void Safety**: All code void-safe
- **SCOOP Compatible**: Concurrency-ready
- **Well Tested**: Comprehensive test suites

## Dependencies

- EiffelStudio 25.02+
- No external C libraries for core functionality
