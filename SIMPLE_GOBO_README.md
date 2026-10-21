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

## Why This Exists

EiffelStudio 25.02 bundles Gobo from **2021**, which lacks support for modern SCOOP syntax:

```eiffel
-- SCOOP inline separate (Eiffel ECMA-367 3rd edition)
separate a_worker as l_worker do
    l_worker.do_work
end

-- Multiple region variant
separate a_w1 as l_w1, a_w2 as l_w2 do
    l_w1.sync_with (l_w2)
end
```

GitHub Gobo (2024) includes full support for this syntax via:
- Grammar rules: `Inline_separate_instruction`, `Inline_separate_argument`
- AST classes: `ET_INLINE_SEPARATE_INSTRUCTION`, `ET_INLINE_SEPARATE_ARGUMENT`, `ET_INLINE_SEPARATE_ARGUMENT_LIST`, etc.

## The Problem We Solved

| Component | EiffelStudio 25.02 | GitHub Gobo 2024 |
|-----------|-------------------|------------------|
| Gobo Version | ~2021 | 2024 (current) |
| SCOOP inline `separate...as...do` | Not supported | Full support |
| `ET_INLINE_SEPARATE_*` classes | Missing | Present (9 classes) |

The `simple_eiffel_parser` library uses Gobo's parser. Without modern Gobo, it couldn't parse SCOOP inline separate syntax, leaving gaps in `simple_kb` ingestion.

## How It Was Built

### 1. Clone from GitHub
```bash
git clone https://github.com/gobo-project/gobo.git /d/prod/simple_gobo
```

### 2. Set Environment Variables

**Windows (PowerShell as Admin):**
```powershell
[Environment]::SetEnvironmentVariable("SIMPLE_GOBO", "D:\prod\simple_gobo", "User")
[Environment]::SetEnvironmentVariable("GOBO_LIBRARY", "D:\prod\simple_gobo\library", "User")
[Environment]::SetEnvironmentVariable("GOBO_EIFFEL", "ise", "User")
```

**Linux/macOS:**
```bash
export SIMPLE_GOBO=/path/to/simple_gobo
export GOBO_LIBRARY=$SIMPLE_GOBO/library
export GOBO_EIFFEL=ise
```

### 3. Update ECF Files

Libraries that use Gobo need ECF updates:

```xml
<!-- Before (ISE bundled Gobo 2021) -->
<library name="gobo_regexp" location="$ISE_LIBRARY/contrib/library/gobo/library/regexp/library.ecf"/>

<!-- After (GitHub Gobo 2024) -->
<library name="gobo_regexp" location="$GOBO_LIBRARY/regexp/library.ecf"/>
```

## Libraries Updated

The following simple_* libraries were migrated to use `$GOBO_LIBRARY`:

| Library | Gobo Components Used |
|---------|---------------------|
| simple_eiffel_parser | kernel, structure, utility, time, string, lexical, parse, regexp, tools |
| simple_regex | kernel, regexp, string, structure, utility |
| simple_json | kernel, structure |
| simple_xml | kernel, structure, string |
| simple_decimal | math |
| simple_validation | regexp |

## Verification

SCOOP parsing tests were added to `simple_eiffel_parser`:

```eiffel
test_scoop_inline_separate
    -- Test: `separate <expr> as <var> do ... end`

test_scoop_multiple_inline_separate
    -- Test: `separate expr1 as var1, expr2 as var2 do ... end`
```

Both tests pass, confirming GitHub Gobo correctly parses SCOOP inline separate syntax.

## KB Ingestion Results

With SCOOP-capable parsing:

| Metric | Before | After |
|--------|--------|-------|
| Parse Errors | 265 | 138 |
| Classes Indexed | ~4,000 | 4,613 |
| Features Indexed | ~75,000 | 87,780 |

## Key Gobo Components

```
simple_gobo/library/
├── kernel/       -- Core utilities (KL_*)
├── structure/    -- Data structures (DS_*)
├── string/       -- String utilities (ST_*)
├── lexical/      -- Lexer generation
├── parse/        -- Parser generation
├── regexp/       -- Regular expressions (RX_*)
├── tools/        -- Eiffel parser (ET_*) <-- SCOOP support here
├── math/         -- Decimal arithmetic
├── time/         -- Date/time utilities
├── utility/      -- General utilities (UT_*)
└── xml/          -- XML processing
```

The critical SCOOP support is in `library/tools/src/eiffel/`:
- `ast/instruction/et_inline_separate_instruction.e`
- `ast/instruction/et_inline_separate_argument.e`
- `ast/instruction/et_inline_separate_argument_list.e`
- `parser/et_eiffel_parser.y` (grammar with `Inline_separate_instruction` rules)

## Installation

1. Clone or extract to `/d/prod/simple_gobo`
2. Set environment variables (see above)
3. Restart terminal/IDE to pick up new variables
4. Update ECF files to use `$GOBO_LIBRARY` paths

## Relationship to Upstream

This is a **direct clone** of [gobo-project/gobo](https://github.com/gobo-project/gobo). We do not fork or modify it. When Gobo updates, we can pull the latest changes:

```bash
cd /d/prod/simple_gobo
git pull origin master
```

## Why Not Just Use ISE Bundled Gobo?

1. **Version lag**: ISE bundles an older Gobo snapshot
2. **Missing features**: SCOOP inline separate syntax not supported
3. **No easy update path**: Can't update bundled version independently
4. **Environment control**: `$GOBO_LIBRARY` lets us choose which version to use

## License

Gobo is MIT licensed. See [License.md](License.md) in this directory.

The Simple Eiffel integration documentation is also MIT licensed.

---

## Technical Details

### SCOOP Inline Separate Grammar (from et_eiffel_parser.y)

```yacc
Inline_separate_instruction: E_SEPARATE Inline_separate_arguments E_AS Inline_separate_aliases E_DO Compound E_END
    ;

Inline_separate_argument: Expression
    ;

Inline_separate_argument_list: Inline_separate_argument
    | Inline_separate_argument_list ',' Inline_separate_argument
    ;
```

### AST Classes Added

| Class | Purpose |
|-------|---------|
| `ET_INLINE_SEPARATE_INSTRUCTION` | AST node for the instruction |
| `ET_INLINE_SEPARATE_ARGUMENT` | Single separate argument |
| `ET_INLINE_SEPARATE_ARGUMENT_ITEM` | Argument with alias |
| `ET_INLINE_SEPARATE_ARGUMENT_LIST` | Multiple arguments |
| `ET_INLINE_SEPARATE_ARGUMENT_COMMA` | Comma-separated list handling |

### Verification Command

```bash
grep -r "Inline_separate" /d/prod/simple_gobo/library/tools/src/eiffel/
# Returns 12+ occurrences confirming SCOOP support
```
