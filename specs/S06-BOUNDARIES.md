# S06: BOUNDARIES - simple_gobo

**Document**: S06-BOUNDARIES.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## System Boundaries

```
+---------------------------------------------+
|              Application Layer              |
|    (CLI tools using simple_gobo)            |
+---------------------------------------------+
                     |
                     v
+---------------------------------------------+
|              simple_gobo                     |
|  +---------------+  +-------------------+   |
|  | Argument      |  | Free ELKS         |   |
|  | Library       |  | - Encoding        |   |
|  | - AP_PARSER   |  | - Kernel          |   |
|  | - AP_OPTION   |  | - Exceptions      |   |
|  +---------------+  +-------------------+   |
+---------------------------------------------+
                     |
                     v
+---------------------------------------------+
|           EiffelStudio Runtime              |
|    (Kernel, GC, Platform Abstractions)      |
+---------------------------------------------+
                     |
                     v
+---------------------------------------------+
|              Operating System               |
|    (Command line, File system, Locale)      |
+---------------------------------------------+
```

## Interface Boundaries

### Public API (Exported)

**Argument Library**
- AP_PARSER: Full parser class
- AP_BASIC_PARSER: Core parser
- AP_OPTION hierarchy: Option types
- AP_ERROR, AP_ERROR_HANDLER: Error handling

**Free ELKS**
- ENCODING classes: Text encoding
- Kernel extensions: Type enhancements
- Exception hierarchy: Error types

### Internal Implementation (Not Exported)

- Parsing state machines
- Platform-specific encoding implementations
- Word wrapper for help text

## Data Boundaries

### Input
- Command-line arguments (ARRAY [STRING])
- Text for encoding conversion
- Configuration parameters

### Output
- Parsed parameters (DS_LIST [STRING])
- Option values
- Help text (STRING)
- Encoded/decoded text

## Trust Boundaries

- Application trusted to validate semantic correctness
- simple_gobo validates syntactic correctness
- OS provides command-line arguments
