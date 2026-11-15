# S05: CONSTRAINTS - simple_gobo

**Document**: S05-CONSTRAINTS.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## Technical Constraints

### Option Naming

1. **Short Form**
   - Must be alphanumeric character
   - Single character only
   - Case-sensitive

2. **Long Form**
   - Alphanumeric characters and hyphens
   - No double hyphens
   - No leading/trailing hyphens
   - Minimum 1 character

### Parsing Rules

1. **Short Options**
   - Introduced by single hyphen: `-v`
   - Can be bundled: `-abc` = `-a -b -c`
   - Parameter follows immediately or space: `-f file` or `-ffile`

2. **Long Options**
   - Introduced by double hyphen: `--verbose`
   - Parameter with equals: `--file=name`
   - Parameter with space: `--file name`

3. **Terminator**
   - `--` stops option processing
   - Remaining args become parameters

### Uniqueness Constraints

- No duplicate short forms in same option set
- No duplicate long forms in same option set
- Alternative option lists have separate namespaces

### Error Handling

- Unknown options generate errors
- Missing required parameters generate errors
- Surplus occurrences generate errors
- Missing mandatory options generate errors

## Platform Constraints

### Encoding Support

| Platform | Supported Encodings |
|----------|---------------------|
| Windows | Code pages, UTF-8/16/32 |
| Unix/Linux | UTF-8, locale-based |
| macOS | UTF-8, locale-based |

### Performance Constraints

- Parsing is O(n) where n = number of arguments
- Help text generation is O(m) where m = number of options

## Memory Constraints

- Options are stored in DS_ARRAYED_LIST
- Parameters are stored in DS_ARRAYED_LIST
- No explicit memory limits
