# 7S-02: STANDARDS - simple_gobo

**Document**: 7S-02-STANDARDS.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## Applicable Standards

### Command-Line Conventions

1. **POSIX Argument Syntax**
   - Short options: `-a`, `-abc` (bundled)
   - Long options: `--option`, `--option=value`
   - Parameter terminator: `--`
   - Reference: IEEE Std 1003.1 (POSIX)

2. **GNU Argument Conventions**
   - Long option names with hyphens
   - Optional and required parameters
   - Help text formatting

### Character Encoding Standards

1. **Unicode**
   - UTF-8 encoding/decoding
   - UTF-16/UTF-32 support
   - Reference: Unicode Standard

2. **Code Pages**
   - Windows code pages (1252, etc.)
   - Unix locale handling
   - Reference: Platform-specific

### Eiffel Standards

1. **ECMA-367**
   - Eiffel language specification
   - Design by Contract semantics

2. **ELKS (Eiffel Library Kernel Standard)**
   - Kernel class interfaces
   - Collection hierarchies

## Implementation Compliance

| Standard | Compliance Level | Notes |
|----------|------------------|-------|
| POSIX args | Full | Short/long options supported |
| GNU args | Partial | Most conventions followed |
| Unicode | Full | UTF-8/16/32 conversion |
| ECMA-367 | Full | DBC throughout |
| ELKS | Extended | Free ELKS additions |
