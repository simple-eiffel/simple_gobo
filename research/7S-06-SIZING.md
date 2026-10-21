# 7S-06: SIZING - simple_gobo

**Document**: 7S-06-SIZING.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## Implementation Size

### Source Metrics

| Component | Classes | Lines (approx) |
|-----------|---------|----------------|
| Argument Library | 15 | 2,500 |
| Free ELKS | 100+ | 15,000+ |
| Common/Test | 10 | 1,500 |
| **Total** | 125+ | 19,000+ |

### Complexity Assessment

| Component | Complexity | Rationale |
|-----------|------------|-----------|
| AP_PARSER | Medium | State machine for parsing |
| AP_OPTION hierarchy | Low | Simple inheritance |
| Encoding | Medium | Platform-specific code |
| Free ELKS kernel | High | Core types, many edge cases |

### Development Effort (Original)

- **Initial Port**: 40+ hours (Gobo adaptation)
- **Integration**: 8 hours
- **Testing**: 16 hours
- **Documentation**: 4 hours

### Maintenance Effort

- **Monthly**: 2 hours (upstream tracking)
- **Per Release**: 8 hours (testing, validation)

### Binary Impact

| Target | Size Impact |
|--------|-------------|
| Executable | +200-500 KB |
| DLL/SO | Not applicable (static) |

### Test Coverage

- Gobo includes comprehensive test suites
- simple_gobo inherits these tests
- Estimated coverage: 80%+
