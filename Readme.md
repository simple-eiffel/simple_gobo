<p align="center">
  <img src="https://raw.githubusercontent.com/simple-eiffel/claude_eiffel_op_docs/main/artwork/LOGO.png" alt="simple_ library logo" width="400">
</p>

# simple_gobo

**[Documentation](https://simple-eiffel.github.io/simple_gobo/)** | **[GitHub](https://github.com/simple-eiffel/simple_gobo)** | **[Upstream Gobo](https://github.com/gobo-project/gobo)**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Eiffel](https://img.shields.io/badge/Eiffel-25.02-blue.svg)](https://www.eiffel.org/)
[![Gobo](https://img.shields.io/badge/Gobo-2024-green.svg)](https://github.com/gobo-project/gobo)
[![SCOOP](https://img.shields.io/badge/SCOOP-inline%20separate-orange.svg)]()

GitHub Gobo (2024) integration for the Simple Eiffel ecosystem, providing SCOOP inline separate parsing support.

Part of the [Simple Eiffel](https://github.com/simple-eiffel) ecosystem.

## Status

**Production** - Required dependency for SCOOP-capable parsing

## Overview

EiffelStudio 25.02 bundles Gobo from 2021, which lacks support for modern SCOOP syntax. GitHub Gobo (2024) includes full support for inline separate blocks:

```eiffel
-- SCOOP inline separate (ECMA-367 3rd edition)
separate a_worker as l_worker do
    l_worker.do_work
end

-- Multiple region variant
separate a_w1 as l_w1, a_w2 as l_w2 do
    l_w1.sync_with (l_w2)
end
```

## Features

- **SCOOP Inline Separate**: Full grammar support for `separate...as...do...end`
- **ET_INLINE_SEPARATE_* Classes**: 9 AST classes for SCOOP constructs
- **EiffelStudio Compatible**: Use with `GOBO_EIFFEL=ise`
- **Latest Gobo**: 2024 version with all language features

## Installation

1. Set environment variables:
```bash
export SIMPLE_GOBO=/path/to/simple_gobo
export GOBO_LIBRARY=$SIMPLE_GOBO/library
export GOBO_EIFFEL=ise
```

2. Add to ECF:
```xml
<library name="gobo_regexp" location="$GOBO_LIBRARY/regexp/library.ecf"/>
<library name="gobo_tools" location="$GOBO_LIBRARY/tools/library.ecf"/>
```

## Libraries Using simple_gobo

| Library | Components Used |
|---------|-----------------|
| simple_eiffel_parser | kernel, structure, utility, time, string, lexical, parse, regexp, tools |
| simple_regex | kernel, regexp, string, structure, utility |
| simple_json | kernel, structure |
| simple_xml | kernel, structure, string |
| simple_decimal | math |
| simple_validation | regexp |

## Upstream Relationship

This is a mirror of [gobo-eiffel/gobo](https://github.com/gobo-project/gobo). To update:

```bash
cd /path/to/simple_gobo
git pull origin master
```

## License

MIT License - See [License.md](License.md) for details.

---

For detailed integration instructions, see [SIMPLE_GOBO_README.md](SIMPLE_GOBO_README.md).