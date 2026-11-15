# 7S-03: SOLUTIONS - simple_gobo

**Document**: 7S-03-SOLUTIONS.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## Existing Solutions Comparison

### Argument Parsing

| Solution | Language | Pros | Cons |
|----------|----------|------|------|
| Gobo AP | Eiffel | Native, DBC | Large library |
| getopt | C | Standard, portable | No Eiffel binding |
| argparse | Python | Excellent API | Wrong language |
| clap | Rust | Modern, typed | Wrong language |

### Character Encoding

| Solution | Language | Pros | Cons |
|----------|----------|------|------|
| Gobo Free ELKS | Eiffel | Native, void-safe | Bundled dependency |
| iconv | C | Universal | Requires binding |
| ICU | C++ | Comprehensive | Heavy, complex |
| .NET Encoding | C# | Rich API | Wrong platform |

## Why simple_gobo?

1. **Native Eiffel**: No foreign function calls for common operations
2. **Design by Contract**: Full DBC support with preconditions/postconditions
3. **Void Safety**: All code is void-safe
4. **Ecosystem Integration**: Works seamlessly with other simple_* libraries
5. **MIT License**: Permissive license from Gobo project

## Trade-offs

- **Size**: Gobo is large, but we bundle only needed components
- **Learning Curve**: Gobo conventions differ slightly from EiffelBase
- **Maintenance**: Tracks upstream Gobo releases

## Recommendation

Use simple_gobo for:
- CLI tools requiring argument parsing
- Text processing requiring encoding conversion
- Test infrastructure needing standardized patterns
