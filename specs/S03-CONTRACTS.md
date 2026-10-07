# S03: CONTRACTS - simple_gobo

**Document**: S03-CONTRACTS.md
**Library**: simple_gobo
**Status**: BACKWASH (reverse-engineered from implementation)
**Date**: 2026-01-23

---

## AP_PARSER Contracts

### Class Invariant
```eiffel
invariant
    help_option_not_void: help_option /= Void
```

### Creation
```eiffel
make
    -- Create parser with predefined help option
ensure
    help_option_exists: help_option /= Void
```

## AP_BASIC_PARSER Contracts

### Class Invariant
```eiffel
invariant
    options_not_void: options /= Void
    no_option_is_void: not options.has_void
    alternative_options_lists_not_void: alternative_options_lists /= Void
    application_description_not_void: application_description /= Void
    parameters_description_not_void: parameters_description /= Void
    parameters_not_void: parameters /= Void
```

### Feature Contracts

```eiffel
set_application_description (a_string: STRING)
    require
        a_string_not_void: a_string /= Void
    ensure
        application_description_set: application_description = a_string

parse_arguments
    require
        valid_options: valid_options

parse_array (an_array: ARRAY [STRING])
    require
        an_array_not_void: an_array /= Void
        no_void_argument: not STRING_ARRAY_.has_void (an_array)
        valid_options: valid_options

parse_list (a_list: DS_LIST [STRING])
    require
        a_list_not_void: a_list /= Void
        no_void_argument: not a_list.has_void
        valid_options: valid_options

valid_long_form (a_string: STRING): BOOLEAN
    ensure
        void_string_are_never_valid: (a_string = Void) implies not Result

full_help_text: STRING
    ensure
        full_help_text_not_void: Result /= Void

all_options: DS_LIST [AP_OPTION]
    ensure
        all_options_not_void: Result /= Void
```

## AP_OPTION Contracts (Deferred Base)

```eiffel
has_short_form: BOOLEAN
    -- Does this option have a short form?

short_form: CHARACTER
    require
        has_short_form: has_short_form

has_long_form: BOOLEAN
    -- Does this option have a long form?

long_form: detachable STRING
```

## Encoding Contracts

```eiffel
class ENCODING
invariant
    code_page_valid: code_page >= 0
```
