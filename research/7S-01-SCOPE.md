# 7S-01: SCOPE - simple_gobo

**Document**: 7S-01-SCOPE.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## Problem Domain

simple_gobo integrates the Gobo Eiffel Library into the simple_* ecosystem, providing:

1. **Argument Parsing** - Command-line argument parsing with options, flags, and parameters
2. **Free ELKS** - Extended kernel library with encoding, exceptions, and utility classes
3. **Common Utilities** - Shared test infrastructure and example frameworks

The library addresses the need for robust, standards-compliant foundation libraries that enhance Eiffel's built-in capabilities.

## Target Users

- **CLI Application Developers**: Building command-line tools requiring argument parsing
- **Library Authors**: Needing encoding/decoding utilities (UTF-8, code pages)
- **Test Writers**: Requiring standardized test infrastructure
- **Cross-platform Developers**: Needing portable file system operations

## Boundaries

### In Scope
- Command-line argument parsing (short and long options)
- Character encoding/decoding
- Exception handling infrastructure
- Basic data structures (from Gobo)
- Test framework integration

### Out of Scope
- GUI applications
- Network operations
- Database access
- Advanced parsing (XML, JSON - separate libraries)

## Dependencies

- EiffelStudio kernel libraries
- Gobo Eiffel Library (bundled)

## Integration Points

- Provides AP_PARSER for CLI tools
- Provides encoding utilities for text processing
- Integrates with EiffelStudio test framework
