# pure nushell bible

A fork of dylanaraps awesome [pure bash bible](https://github.com/dylanaraps/pure-bash-bible) with pure nushell alternatives added in.

The nushell script format goes as follows:

```nu
# Comments
command here
# -> output
```

# Table of Contents

<!-- vim-markdown-toc GFM -->

* [FOREWORD](#foreword)
* [STRINGS](#strings)
    * [Trim leading and trailing white-space from string](#trim-leading-and-trailing-white-space-from-string)
    * [Trim all white-space from string and truncate spaces](#trim-all-white-space-from-string-and-truncate-spaces)
    * [Use regex on a string](#use-regex-on-a-string)
    * [Split a string on a delimiter](#split-a-string-on-a-delimiter)
    * [Change a string to lowercase](#change-a-string-to-lowercase)
    * [Change a string to uppercase](#change-a-string-to-uppercase)
    * [Reverse a string case](#reverse-a-string-case)
    * [Trim quotes from a string](#trim-quotes-from-a-string)
    * [Strip all instances of pattern from string](#strip-all-instances-of-pattern-from-string)
    * [Strip first occurrence of pattern from string](#strip-first-occurrence-of-pattern-from-string)
    * [Strip pattern from start of string](#strip-pattern-from-start-of-string)
    * [Strip pattern from end of string](#strip-pattern-from-end-of-string)
    * [Percent-encode a string](#percent-encode-a-string)
    * [Decode a percent-encoded string](#decode-a-percent-encoded-string)
    * [Check if string contains a sub-string](#check-if-string-contains-a-sub-string)
    * [Check if string starts with sub-string](#check-if-string-starts-with-sub-string)
    * [Check if string ends with sub-string](#check-if-string-ends-with-sub-string)
* [ARRAYS](#arrays)
    * [Reverse an array](#reverse-an-array)
    * [Remove duplicate array elements](#remove-duplicate-array-elements)
    * [Random array element](#random-array-element)
    * [Cycle through an array](#cycle-through-an-array)
    * [Toggle between two values](#toggle-between-two-values)
* [LOOPS](#loops)
    * [Loop over a range of numbers](#loop-over-a-range-of-numbers)
    * [Loop over a variable range of numbers](#loop-over-a-variable-range-of-numbers)
    * [Loop over an array](#loop-over-an-array)
    * [Loop over an array with an index](#loop-over-an-array-with-an-index)
    * [Loop over the contents of a file](#loop-over-the-contents-of-a-file)
    * [Loop over files and directories](#loop-over-files-and-directories)
* [FILE HANDLING](#file-handling)
    * [Read a file to a string](#read-a-file-to-a-string)
    * [Read a file to an array (*by line*)](#read-a-file-to-an-array-by-line)
    * [Get the first N lines of a file](#get-the-first-n-lines-of-a-file)
    * [Get the last N lines of a file](#get-the-last-n-lines-of-a-file)
    * [Get the number of lines in a file](#get-the-number-of-lines-in-a-file)
    * [Count files or directories in directory](#count-files-or-directories-in-directory)
    * [Create an empty file](#create-an-empty-file)
    * [Extract lines between two markers](#extract-lines-between-two-markers)
* [FILE PATHS](#file-paths)
    * [Get the directory name of a file path](#get-the-directory-name-of-a-file-path)
    * [Get the base-name of a file path](#get-the-base-name-of-a-file-path)
* [VARIABLES](#variables)
    * [Assign and access a variable using a variable](#assign-and-access-a-variable-using-a-variable)
    * [Name a variable based on another variable](#name-a-variable-based-on-another-variable)
* [ESCAPE SEQUENCES](#escape-sequences)
    * [Text Colors](#text-colors)
    * [Text Attributes](#text-attributes)
    * [Cursor Movement](#cursor-movement)
    * [Erasing Text](#erasing-text)
* [PARAMETER EXPANSION](#parameter-expansion)
    * [Indirection](#indirection)
    * [Replacement](#replacement)
    * [Length](#length)
    * [Expansion](#expansion)
    * [Case Modification](#case-modification)
    * [Default Value](#default-value)
* [BRACE EXPANSION](#brace-expansion)
    * [Ranges](#ranges)
    * [String Lists](#string-lists)
* [CONDITIONAL EXPRESSIONS](#conditional-expressions)
    * [File Conditionals](#file-conditionals)
    * [File Comparisons](#file-comparisons)
    * [Variable Conditionals](#variable-conditionals)
    * [Variable Comparisons](#variable-comparisons)
* [ARITHMETIC OPERATORS](#arithmetic-operators)
    * [Assignment](#assignment)
    * [Arithmetic](#arithmetic)
    * [Bitwise](#bitwise)
    * [Logical](#logical)
    * [Miscellaneous](#miscellaneous)
* [ARITHMETIC](#arithmetic-1)
    * [Simpler syntax to set variables](#simpler-syntax-to-set-variables)
    * [Ternary Tests](#ternary-tests)
* [TRAPS](#traps)
    * [Do something on script exit](#do-something-on-script-exit)
    * [Ignore terminal interrupt (CTRL+C, SIGINT)](#ignore-terminal-interrupt-ctrlc-sigint)
    * [React to window resize](#react-to-window-resize)
    * [Do something before every command](#do-something-before-every-command)
    * [Do something when a shell function or a sourced file finishes executing](#do-something-when-a-shell-function-or-a-sourced-file-finishes-executing)
* [PERFORMANCE](#performance)
    * [Disable Unicode](#disable-unicode)
* [OBSOLETE SYNTAX](#obsolete-syntax)
    * [Shebang](#shebang)
    * [Command Substitution](#command-substitution)
    * [Function Declaration](#function-declaration)
* [INTERNAL VARIABLES](#internal-variables)
    * [Get the location to the `bash` binary](#get-the-location-to-the-bash-binary)
    * [Get the version of the current running `bash` process](#get-the-version-of-the-current-running-bash-process)
    * [Open the user's preferred text editor](#open-the-users-preferred-text-editor)
    * [Get the name of the current function](#get-the-name-of-the-current-function)
    * [Get the host-name of the system](#get-the-host-name-of-the-system)
    * [Get the architecture of the Operating System](#get-the-architecture-of-the-operating-system)
    * [Get the name of the Operating System / Kernel](#get-the-name-of-the-operating-system--kernel)
    * [Get the current working directory](#get-the-current-working-directory)
    * [Get the number of seconds the script has been running](#get-the-number-of-seconds-the-script-has-been-running)
    * [Get a pseudorandom integer](#get-a-pseudorandom-integer)
* [INFORMATION ABOUT THE TERMINAL](#information-about-the-terminal)
    * [Get the terminal size in lines and columns (*from a script*)](#get-the-terminal-size-in-lines-and-columns-from-a-script)
    * [Get the terminal size in pixels](#get-the-terminal-size-in-pixels)
    * [Get the current cursor position](#get-the-current-cursor-position)
* [CONVERSION](#conversion)
    * [Convert a hex color to RGB](#convert-a-hex-color-to-rgb)
    * [Convert an RGB color to hex](#convert-an-rgb-color-to-hex)
* [CODE GOLF](#code-golf)
    * [Shorter `for` loop syntax](#shorter-for-loop-syntax)
    * [Shorter infinite loops](#shorter-infinite-loops)
    * [Shorter function declaration](#shorter-function-declaration)
    * [Shorter `if` syntax](#shorter-if-syntax)
    * [Simpler `case` statement to set variable](#simpler-case-statement-to-set-variable)
* [OTHER](#other)
    * [Use `read` as an alternative to the `sleep` command](#use-read-as-an-alternative-to-the-sleep-command)
    * [Check if a program is in the user's PATH](#check-if-a-program-is-in-the-users-path)
    * [Get the current date using `strftime`](#get-the-current-date-using-strftime)
    * [Get the username of the current user](#get-the-username-of-the-current-user)
    * [Generate a UUID V4](#generate-a-uuid-v4)
    * [Progress bars](#progress-bars)
    * [Get the list of functions in a script](#get-the-list-of-functions-in-a-script)
    * [Bypass shell aliases](#bypass-shell-aliases)
    * [Bypass shell functions](#bypass-shell-functions)
    * [Run a command in the background](#run-a-command-in-the-background)
    * [Capture function return without command substitution](#capture-the-return-value-of-a-function-without-command-substitution)
* [AFTERWORD](#afterword)

<!-- vim-markdown-toc -->

<br>

<!-- CHAPTER START -->
# FOREWORD

A collection of pure `bash` alternatives to external processes and programs. The `bash` scripting language is more powerful than people realise and most tasks can be accomplished without depending on external programs.

Calling an external process in `bash` is expensive and excessive use will cause a noticeable slowdown. Scripts and programs written using built-in methods (*where applicable*) will be faster, require fewer dependencies and afford a better understanding of the language itself.

The contents of this book provide a reference for solving problems encountered when writing programs and scripts in `bash`. Examples are in function formats showcasing how to incorporate these solutions into code.

### Nushell Foreword

Nushell has a lot of built-in functionality that makes manipulating data really easy. Data structure types, typed inputs and outputs, and easy to remember function names. Nushell sets itself apart as a scripting language because of all of this functional utility. 

Nushell also tries to optimize wherever possible. For structured data especially, nushell pipelines in such a way to minimize computation. Such as getting the first 5 lines from a file (no need to read the entire file).

Bash is super important and nushell will not be able to fully replace it. The main point of writing these nushell alternatives to the bash functions is to show the strengths of nushell and where bash can fall short. Also, hopefully this convinces someone that they should try out nushell as a scripting language or shell. It's an incredibly powerful tool you can have at your fingurtips.

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# STRINGS

## Trim leading and trailing white-space from string

This is an alternative to `sed`, `awk`, `perl` and other tools. The
function below works by finding all leading and trailing white-space and
removing it from the start and end of the string. The `:` built-in is used in place of a temporary variable.

**Example Function:**

```sh
trim_string() {
    # Usage: trim_string "   example   string    "
    : "${1#"${1%%[![:space:]]*}"}"
    : "${_%"${_##*[![:space:]]}"}"
    printf '%s\n' "$_"
}
```

**Example Usage:**

```shell
$ trim_string "    Hello,  World    "
Hello,  World

$ name="   John Black  "
$ trim_string "$name"
John Black
```

### Nushell Version

This is a built-in command to nushell.

**Example Usage:**

```nu
"    Hello,  World    " | str trim
# -> Hello,  World

let name = "   John Black  "
$name | str trim
# -> John Black
```

## Trim all white-space from string and truncate spaces

This is an alternative to `sed`, `awk`, `perl` and other tools. The
function below works by abusing word splitting to create a new string
without leading/trailing white-space and with truncated spaces.

**Example Function:**

```sh
# shellcheck disable=SC2086,SC2048
trim_all() {
    # Usage: trim_all "   example   string    "
    set -f
    set -- $*
    printf '%s\n' "$*"
    set +f
}
```

**Example Usage:**

```shell
$ trim_all "    Hello,    World    "
Hello, World

$ name="   John   Black  is     my    name.    "
$ trim_all "$name"
John Black is my name.
```

### Nushell Version

There's two easy ways to do this in nushell. You can split the string with whitespace or do a simple regex replace.

```nu
# Method 1
# Use '' for a string literal
"    Hello,    World    " | split row --regex '\s+' | str join " "
# -> Hello, World

# Method 2
let name = "   John   Black  is     my    name.    "
$name | str replace --regex --all '\s+' " "
# -> John Black is my name.
```

## Use regex on a string

The result of `bash`'s regex matching can be used to replace `sed` for a
large number of use-cases.

**CAVEAT**: This is one of the few platform dependent `bash` features.
`bash` will use whatever regex engine is installed on the user's system.
Stick to POSIX regex features if aiming for compatibility.

**CAVEAT**: This example only prints the first matching group. When using
multiple capture groups some modification is needed.

**Example Function:**

```sh
regex() {
    # Usage: regex "string" "regex"
    [[ $1 =~ $2 ]] && printf '%s\n' "${BASH_REMATCH[1]}"
}
```

**Example Usage:**

```shell
$ # Trim leading white-space.
$ regex '    hello' '^\s*(.*)'
hello

$ # Validate a hex color.
$ regex "#FFFFFF" '^(#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$'
#FFFFFF

$ # Validate a hex color (invalid).
$ regex "red" '^(#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$'
# no output (invalid)
```

### Nushell Version

Nushell has built-in regex tooling. The `parse` command gives you a way to split up a string into groups, and you also have `str replace --regex` or `split string --regex`.

```nu
# Trim leading white-space.
# Use '' for string literal (characters don't need to be escaped)
'    hello' | str replace --regex --all '^\s*(.*)' ""
# hello

# Validate a hex color.
"#FFFFFF" | parse --regex '^(#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$'
# ->
# ╭───┬──────────┬──────────╮
# │ # │ capture0 │ capture1 │
# ├───┼──────────┼──────────┤
# │ 0 │ #FFFFFF  │ FFFFFF   │
# ╰───┴──────────┴──────────╯

# Validate a hex color and get the hex value
# We name a group here to make it easier to select
# The ? at the end makes `get` return nothing if the function fails
"#FFFFFF" | parse --regex '^(?<color>#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$' | get color.0?
# -> #FFFFFF

# Validate a hex color (invalid).
"#FFFFFF" | parse --regex '^(?<color>#?([a-fA-F0-9]{6}|[a-fA-F0-9]{3}))$' | get color.0?
# ->
```

## Split a string on a delimiter

**CAVEAT:** Requires `bash` 4+

This is an alternative to `cut`, `awk` and other tools.

**Example Function:**

```sh
split() {
   # Usage: split "string" "delimiter"
   IFS=$'\n' read -d "" -ra arr <<< "${1//$2/$'\n'}"
   printf '%s\n' "${arr[@]}"
}
```

**Example Usage:**

```shell
$ split "apples,oranges,pears,grapes" ","
apples
oranges
pears
grapes

$ split "1, 2, 3, 4, 5" ", "
1
2
3
4
5

# Multi char delimiters work too!
$ split "hello---world---my---name---is---john" "---"
hello
world
my
name
is
john
```

### Nushell Version

This is a built-in nushell function, `split row` or `split column`.

```nu
"apples,oranges,pears,grapes" | split row ","
# ->
# ╭───┬─────────╮
# │ 0 │ apples  │
# │ 1 │ oranges │
# │ 2 │ pears   │
# │ 3 │ grapes  │
# ╰───┴─────────╯

"1, 2, 3, 4, 5" | split column ", "
# ╭───┬─────────┬─────────┬─────────┬─────────┬─────────╮
# │ # │ column1 │ column2 │ column3 │ column4 │ column5 │
# ├───┼─────────┼─────────┼─────────┼─────────┼─────────┤
# │ 0 │ 1       │ 2       │ 3       │ 4       │ 5       │
# ╰───┴─────────┴─────────┴─────────┴─────────┴─────────╯

# Multi char delimiters work too!
"hello---world---my---name---is---john" | split row "---" 
# ╭───┬───────╮
# │ 0 │ hello │
# │ 1 │ world │
# │ 2 │ my    │
# │ 3 │ name  │
# │ 4 │ is    │
# │ 5 │ john  │
# ╰───┴───────╯
```

## Change a string to lowercase

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
lower() {
    # Usage: lower "string"
    printf '%s\n' "${1,,}"
}
```

**Example Usage:**

```shell
$ lower "HELLO"
hello

$ lower "HeLlO"
hello

$ lower "hello"
hello
```

### Nushell Version

This is a built-in function in nushell. There are a few cases nushell supports: camel, kebab, snake, title, pascal, screaming snake, upcase, and downcase. The function is `str <case>-case`

**Example Usage:**

```nu
"HELLO" | str downcase
# -> hello

"HeLlO" | str downcase
# -> hello

"hello" | str downcase
# -> hello
```

## Change a string to uppercase

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
upper() {
    # Usage: upper "string"
    printf '%s\n' "${1^^}"
}
```

**Example Usage:**

```shell
$ upper "hello"
HELLO

$ upper "HeLlO"
HELLO

$ upper "HELLO"
HELLO
```

### Nushell Version

This is a built-in function in nushell. There are a few cases nushell supports: camel, kebab, snake, title, pascal, screaming snake, upcase, and downcase. The function is `str <case>-case`

**Example Usage:**

```nu
"HELLO" | str upcase
# -> hello

"HELLO" | str upcase
# -> hello

"HELLO" | str upcase
# -> HELLO
```

## Reverse a string case

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
reverse_case() {
    # Usage: reverse_case "string"
    printf '%s\n' "${1~~}"
}
```

**Example Usage:**

```shell
$ reverse_case "hello"
HELLO

$ reverse_case "HeLlO"
hElLo

$ reverse_case "HELLO"
hello
```

### Nushell Version

Performing this operation is slightly more complicated. This method categorizes each character based on if it is already lower, inverts each character, then concatenates.

The goal of this method is to show how you can chain simple functions to perform complex operations.

**Example Usage:**

```nu
def "str invertcase" []: string -> string {
    (
        $in 
        | split chars 
        | wrap "char" 
        | upsert lower {|x| ($x.char | str downcase) == $x.char } 
        | upsert invert {|x| 
            if ($x.lower) { 
                $x.char | str upcase 
            } else { 
                $x.char | str downcase 
            }
        } 
        | get invert | str join ""
    )
}

"hello" | str invertcase
# -> HELLO

"HeLlO" | str downcase
# -> hElLo

"hello" | str downcase
# -> HELLO
```

## Trim quotes from a string

**Example Function:**

```sh
trim_quotes() {
    # Usage: trim_quotes "string"
    : "${1//\'}"
    printf '%s\n' "${_//\"}"
}
```

**Example Usage:**

```shell
$ var="'Hello', \"World\""
$ trim_quotes "$var"
Hello, World
```

### Nushell Version

This can be accomplished with regex or simple string replacements.

**Example Usage:**

```nu
let var = "'Hello', \"World\""
$var | str replace --all '"' "" | str replace --all "'" ""
# -> Hello, World
```

## Strip all instances of pattern from string

**Example Function:**

```sh
strip_all() {
    # Usage: strip_all "string" "pattern"
    printf '%s\n' "${1//$2}"
}
```

**Example Usage:**

```shell
$ strip_all "The Quick Brown Fox" "[aeiou]"
Th Qck Brwn Fx

$ strip_all "The Quick Brown Fox" "[[:space:]]"
TheQuickBrownFox

$ strip_all "The Quick Brown Fox" "Quick "
The Brown Fox
```

### Nushell Version

This is built-in to the nushell command `str replace`. To replace all instances, just add the flag `--all`. 

**Example Usage:**

```nu
"The Quick Brown Fox" | str replace --all --regex "[aeiou]"
# -> Th Qck Brwn Fx

"The Quick Brown Fox" | str replace --all " "
# -> TheQuickBrownFox

"The Quick Brown Fox" | str replace --all "Quick "
# -> The Brown Fox
```

## Strip first occurrence of pattern from string

**Example Function:**

```sh
strip() {
    # Usage: strip "string" "pattern"
    printf '%s\n' "${1/$2}"
}
```

**Example Usage:**

```shell
$ strip "The Quick Brown Fox" "[aeiou]"
Th Quick Brown Fox

$ strip "The Quick Brown Fox" "[[:space:]]"
TheQuick Brown Fox
```

### Nushell Version

This is a built-in nushell command, `str replace`. To have it only replace the first one, just do not pass in `--all`

**Example Usage:**

```nu
"The Quick Brown Fox" | str replace -r '[aeiou]' ""
# -> Th Quick Brown Fox

"The Quick Brown Fox" " " | str replace " " ""
# -> TheQuick Brown Fox
```

## Strip pattern from start of string

**Example Function:**

```sh
lstrip() {
    # Usage: lstrip "string" "pattern"
    printf '%s\n' "${1##$2}"
}
```

**Example Usage:**

```shell
$ lstrip "The Quick Brown Fox" "The "
Quick Brown Fox
```

### Nushell Version

There are two methods to do this, either using regex or checking if the string starts with the substring with `str starts-with`. The example will show `str starts-with` since there have been other regex examples.

**Example Usage:**

```nu
def "str lstrip" [ss: string]: string -> string {
    # This can be rewritten into a one-liner, but this looks nicer
    let val = $in
    if (not ($val | str starts-with $ss)) {
        $val
    } else {
        ($val | str substring ($ss | str length)..)
    }
}

"The Quick Brown Fox" | str lstrip "The "
# -> Quick Brown Fox
```

## Strip pattern from end of string

**Example Function:**

```sh
rstrip() {
    # Usage: rstrip "string" "pattern"
    printf '%s\n' "${1%%$2}"
}
```

**Example Usage:**

```shell
$ rstrip "The Quick Brown Fox" " Fox"
The Quick Brown
```

### Nushell Version

There are two methods to do this, either using regex or checking if the string starts with the substring with `str ends-with`. The example will show `str ends-with` since there have been other regex examples.

**Example Usage:**

```nu
def "str rstrip" [ss: string]: string -> string {
    # This can be rewritten into a one-liner, but this looks nicer
    let val = $in
    if (not ($val | str ends-with $ss)) {
        $val
    } else {
        # Substring supports negative indices
        ($val | str substring ..((($ss | str length) + 1) * -1))
    }
}

"The Quick Brown Fox" | str rstrip " Fox"
# -> The Quick Brown
```

## Percent-encode a string

**Example Function:**

```sh
urlencode() {
    # Usage: urlencode "string"
    local LC_ALL=C
    for (( i = 0; i < ${#1}; i++ )); do
        : "${1:i:1}"
        case "$_" in
            [a-zA-Z0-9.~_-])
                printf '%s' "$_"
            ;;

            *)
                printf '%%%02X' "'$_"
            ;;
        esac
    done
    printf '\n'
}
```

**Example Usage:**

```shell
$ urlencode "https://github.com/dylanaraps/pure-bash-bible"
https%3A%2F%2Fgithub.com%2Fdylanaraps%2Fpure-bash-bible
```

### Nushell Version

This is a built-in nushell function, `url encode`.

**Example Usage:**

```nu
"https://github.com/DarkKronicle/pure-bash-bible" | url encode --all
# -> https%3A%2F%2Fgithub%2Ecom%2FDarkKronicle%2Fpure%2Dbash%2Dbible
```

## Decode a percent-encoded string

**Example Function:**

```sh
urldecode() {
    # Usage: urldecode "string"
    : "${1//+/ }"
    printf '%b\n' "${_//%/\\x}"
}
```

**Example Usage:**

```shell
$ urldecode "https%3A%2F%2Fgithub.com%2Fdylanaraps%2Fpure-bash-bible"
https://github.com/dylanaraps/pure-bash-bible
```

### Nushell Version

This is a built-in nushell function, `url decode`.

**Example Usage:**

```nu
"https%3A%2F%2Fgithub%2Ecom%2FDarkKronicle%2Fpure%2Dbash%2Dbible" | url decode
# -> https://github.com/DarkKronicle/pure-bash-bible
```

## Check if string contains a sub-string

**Using a test:**

```shell
if [[ $var == *sub_string* ]]; then
    printf '%s\n' "sub_string is in var."
fi

# Inverse (substring not in string).
if [[ $var != *sub_string* ]]; then
    printf '%s\n' "sub_string is not in var."
fi

# This works for arrays too!
if [[ ${arr[*]} == *sub_string* ]]; then
    printf '%s\n' "sub_string is in array."
fi
```

**Using a case statement:**

```shell
case "$var" in
    *sub_string*)
        # Do stuff
    ;;

    *sub_string2*)
        # Do more stuff
    ;;

    *)
        # Else
    ;;
esac
```

### Nushell Version

This is a built-in nushell function, `str contains` or `in`.

**Example Usage:**

```nu
"input string" | str contains "strINg" --ignore-case
# -> true

# Works in lists
["hello" "world" "I" "am" "here"] | str contains 'e'
# ->
# ╭───┬───────╮
# │ 0 │ true  │
# │ 1 │ false │
# │ 2 │ false │
# │ 3 │ false │
# │ 4 │ true  │
# ╰───┴───────╯

# You can get a bit fancier and wrap into a table
["hello" "world" "I" "am" "here"] | wrap input | upsert result {|x| $x.input | str contains 'e' }
# ->
# ╭───┬───────┬────────╮
# │ # │ input │ result │
# ├───┼───────┼────────┤
# │ 0 │ hello │ true   │
# │ 1 │ world │ false  │
# │ 2 │ I     │ false  │
# │ 3 │ am    │ false  │
# │ 4 │ here  │ true   │
# ╰───┴───────┴────────╯

# Works in tables
# We use the spread operator (...) with the input columns to check each
[[ColA ColB]; [hello world], [hi there]] | str contains 'e' ...($in | columns)
# ->
# ╭───┬───────┬───────╮
# │ # │ ColA  │ ColB  │
# ├───┼───────┼───────┤
# │ 0 │ true  │ false │
# │ 1 │ false │ true  │
# ╰───┴───────┴───────╯
```

## Check if string starts with sub-string

```shell
if [[ $var == sub_string* ]]; then
    printf '%s\n' "var starts with sub_string."
fi

# Inverse (var does not start with sub_string).
if [[ $var != sub_string* ]]; then
    printf '%s\n' "var does not start with sub_string."
fi
```

### Nushell Version

This is a built-in nushell function, `str starts-with`.

**Example Usage:**

```nu
"hello world" | str starts-with "he"
# -> true
```

## Check if string ends with sub-string

```shell
if [[ $var == *sub_string ]]; then
    printf '%s\n' "var ends with sub_string."
fi

# Inverse (var does not end with sub_string).
if [[ $var != *sub_string ]]; then
    printf '%s\n' "var does not end with sub_string."
fi
```

### Nushell Version

This is a built-in nushell function, `str ends-with`.

**Example Usage:**

```nu
"hello world" | str ends-with "ld"
# -> true
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# ARRAYS

## Reverse an array

Enabling `extdebug` allows access to the `BASH_ARGV` array which stores
the current function’s arguments in reverse.

**CAVEAT**: Requires `shopt -s compat44` in `bash` 5.0+.

**Example Function:**

```sh
reverse_array() {
    # Usage: reverse_array "array"
    shopt -s extdebug
    f()(printf '%s\n' "${BASH_ARGV[@]}"); f "$@"
    shopt -u extdebug
}
```

**Example Usage:**

```shell
$ reverse_array 1 2 3 4 5
5
4
3
2
1

$ arr=(red blue green)
$ reverse_array "${arr[@]}"
green
blue
red
```

### Nushell Version

Arrays in nushell are a first-class citizen. A ton of functions perform operations on lists. Creating and altering them is super easy.

To reverse an array, nushell has the command `reverse`.

**Example Usage:**

```nu
["the" "quick" "brown" "fox"] | reverse
# ->
# ╭───┬───────╮
# │ 0 │ fox   │
# │ 1 │ brown │
# │ 2 │ quick │
# │ 3 │ the   │
# ╰───┴───────╯

"Arrays are awesome in nushell!" | split row -r '\s+' | reverse | str join " "
# -> nushell! in awesome are Arrays
```

## Remove duplicate array elements

Create a temporary associative array. When setting associative array
values and a duplicate assignment occurs, bash overwrites the key. This
allows us to effectively remove array duplicates.

**CAVEAT:** Requires `bash` 4+

**CAVEAT:** List order may not stay the same.

**Example Function:**

```sh
remove_array_dups() {
    # Usage: remove_array_dups "array"
    declare -A tmp_array

    for i in "$@"; do
        [[ $i ]] && IFS=" " tmp_array["${i:- }"]=1
    done

    printf '%s\n' "${!tmp_array[@]}"
}
```

**Example Usage:**

```shell
$ remove_array_dups 1 1 2 2 3 3 3 3 3 4 4 4 4 4 5 5 5 5 5 5
1
2
3
4
5

$ arr=(red red green blue blue)
$ remove_array_dups "${arr[@]}"
red
green
blue
```

### Nushell Version

Nushell has the `uniq` command.

**Example Usage:**

```nu
[1 1 2 2 3 3 3 3 3 4 4 4 4 4 5 5 5 5 5 5] | uniq
# ->
# ╭───┬───╮
# │ 0 │ 1 │
# │ 1 │ 2 │
# │ 2 │ 3 │
# │ 3 │ 4 │
# │ 4 │ 5 │
# ╰───┴───╯

[red red green blue blue] | uniq --count
# ->
# ╭───┬───────┬───────╮
# │ # │ value │ count │
# ├───┼───────┼───────┤
# │ 0 │ red   │     2 │
# │ 1 │ green │     1 │
# │ 2 │ blue  │     2 │
# ╰───┴───────┴───────╯
```

## Random array element

**Example Function:**

```sh
random_array_element() {
    # Usage: random_array_element "array"
    local arr=("$@")
    printf '%s\n' "${arr[RANDOM % $#]}"
}
```

**Example Usage:**

```shell
$ array=(red green blue yellow brown)
$ random_array_element "${array[@]}"
yellow

# Multiple arguments can also be passed.
$ random_array_element 1 2 3 4 5 6 7
3
```

### Nushell Version

There are two main methods for this. The naive way is to grab a random element is to shuffle the array and then grab the first N. The other way is to generate a random index.

```nu
seq 1 20 | shuffle | first 5
# ->
# ╭───┬────╮
# │ 0 │ 17 │
# │ 1 │ 15 │
# │ 2 │  6 │
# │ 3 │  2 │
# │ 4 │ 16 │
# ╰───┴────╯

# The < here makes the range exclusive
[the quick brown fox] | get (random int 0..<($in | length))
# -> quick
```

## Cycle through an array

Each time the `printf` is called, the next array element is printed. When
the print hits the last array element it starts from the first element
again.

```sh
arr=(a b c d)

cycle() {
    printf '%s ' "${arr[${i:=0}]}"
    ((i=i>=${#arr[@]}-1?0:++i))
}
```

### Nushell Version

Because nushell is mainly functional, it's hard to do complex control flows within a one-liner. In a normal script, we can use `while` and `for`. `for` allows for easy enumeration of elements in an array.

```nu

let arr = [a b c d e f]

while (true) {
    for $x in $arr {
        print $x
    }
}
```

## Toggle between two values

This works the same as above, this is just a different use case.

```sh
arr=(true false)

cycle() {
    printf '%s ' "${arr[${i:=0}]}"
    ((i=i>=${#arr[@]}-1?0:++i))
}
```

### Nushell Version

The same as above, but if just true/false you can simply negate the value.

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# LOOPS

## Loop over a range of numbers

Alternative to `seq`.

```shell
# Loop from 0-100 (no variable support).
for i in {0..100}; do
    printf '%s\n' "$i"
done
```

### Nushell Version

With a control flow, you can use `for`, but nushell gives you the ability to use each or par-each (parallel each).

**Usage Example:**

```nu
# Simply do something with the numbers 1 to 10
seq 1 10 | each {|x| $x * 2 - 1}
# ->
# ╭───┬────╮
# │ 0 │  1 │
# │ 1 │  3 │
# │ 2 │  5 │
# │ 3 │  7 │
# │ 4 │  9 │
# │ 5 │ 11 │
# │ 6 │ 13 │
# │ 7 │ 15 │
# │ 8 │ 17 │
# │ 9 │ 19 │
# ╰───┴────╯

# Or par-each (order not guarenteed)
seq 1 10 | par-each {|x| $x * 2 - 1}
# ->
# ╭───┬────╮
# │ 0 │ 17 │
# │ 1 │ 13 │
# │ 2 │ 15 │
# │ 3 │  7 │
# │ 4 │ 19 │
# │ 5 │  9 │
# │ 6 │  1 │
# │ 7 │  5 │
# │ 8 │  3 │
# │ 9 │ 11 │
# ╰───┴────╯

# You can also do a for loop
for $x in 0..10 {
    print $x
}
```

## Loop over a variable range of numbers

Alternative to `seq`.

```shell
# Loop from 0-VAR.
VAR=50
for ((i=0;i<=VAR;i++)); do
    printf '%s\n' "$i"
done
```

### Nushell Version

Nushell allows you to put variables pretty much anywhere. It follows precedence of parenthesis, so you can always add more.

```nu
let var = 50

# [0, var)
0..<$var | each { print $"The number is ($in)" }

# [1, var]
1..$var | each { print $"The number is ($in)" }

for $i in 1..$var {
    print $"The number is ($in)"
}
```

## Loop over an array

```shell
arr=(apples oranges tomatoes)

# Just elements.
for element in "${arr[@]}"; do
    printf '%s\n' "$element"
done
```

### Nushell Version

The same as the above examples. `each`, `par-each`, `for` (a lot of stuff is lists in nushell).

## Loop over an array with an index

```shell
arr=(apples oranges tomatoes)

# Elements and index.
for i in "${!arr[@]}"; do
    printf '%s\n' "${arr[i]}"
done

# Alternative method.
for ((i=0;i<${#arr[@]};i++)); do
    printf '%s\n' "${arr[i]}"
done
```

### Nushell Version

Nushell has the function `enumerate`.

```nu
[a b c d e f] | enemerate { print $"Index ($in.index) is ($in.item)" }
```

## Loop over the contents of a file

```shell
while read -r line; do
    printf '%s\n' "$line"
done < "file"
```

### Nushell Version

To get lines of some string, just use `lines`. When opening a file, nushell puts it into structured data if it's supported (json, toml, yml, etc), so you can pass in `--raw` to avoid that.

```nu
open LICENSE.md --raw | lines | split words | each { length }
# ->
# ╭────┬────╮
# │  0 │  4 │
# │  1 │  0 │
# │  2 │  6 │
# │  3 │  0 │
# │  4 │ 13 │
# │  5 │ 11 │
# │  6 │ 10 │
# │  7 │ 11 │
# │  8 │ 13 │
# │  9 │  9 │
# │ 10 │  0 │
# │ 11 │ 13 │
# │ 12 │  7 │
# │ 13 │  0 │
# │ 14 │ 13 │
# │ 15 │ 10 │
# │ 16 │ 12 │
# │ 17 │ 12 │
# │ 18 │ 12 │
# │ 19 │ 16 │
# │ 20 │  1 │
# ╰────┴────╯
```

## Loop over files and directories

Don’t use `ls`.

```shell
# Greedy example.
for file in *; do
    printf '%s\n' "$file"
done

# PNG files in dir.
for file in ~/Pictures/*.png; do
    printf '%s\n' "$file"
done

# Iterate over directories.
for dir in ~/Downloads/*/; do
    printf '%s\n' "$dir"
done

# Brace Expansion.
for file in /path/to/parentdir/{file1,file2,subdir/file3}; do
    printf '%s\n' "$file"
done

# Iterate recursively.
shopt -s globstar
for file in ~/Pictures/**/*; do
    printf '%s\n' "$file"
done
shopt -u globstar
```

### Nushell

`ls` is a built-in command to nushell, so is `glob`.

```nu
# Using glob for raw file names
glob **/*.json | par-each { path-expand } | wrap file | upsert has-e { open $in.file --raw | str contains 'e' }

# Do fancy stuff with ls (gotta love types!)
ls | where modified < 2day
ls | where size > 1MiB
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# FILE HANDLING

**CAVEAT:** `bash` does not handle binary data properly in versions `< 4.4`.

## Read a file to a string

Alternative to the `cat` command.

```shell
file_data="$(<"file")"
```

## Read a file to an array (*by line*)

Alternative to the `cat` command.

```shell
# Bash <4 (discarding empty lines).
IFS=$'\n' read -d "" -ra file_data < "file"

# Bash <4 (preserving empty lines).
while read -r line; do
    file_data+=("$line")
done < "file"

# Bash 4+
mapfile -t file_data < "file"
```

## Get the first N lines of a file

Alternative to the `head` command.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
head() {
    # Usage: head "n" "file"
    mapfile -tn "$1" line < "$2"
    printf '%s\n' "${line[@]}"
}
```

**Example Usage:**

```shell
$ head 2 ~/.bashrc
# Prompt
PS1='➜ '

$ head 1 ~/.bashrc
# Prompt
```

## Get the last N lines of a file

Alternative to the `tail` command.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
tail() {
    # Usage: tail "n" "file"
    mapfile -tn 0 line < "$2"
    printf '%s\n' "${line[@]: -$1}"
}
```

**Example Usage:**

```shell
$ tail 2 ~/.bashrc
# Enable tmux.
# [[ -z "$TMUX"  ]] && exec tmux

$ tail 1 ~/.bashrc
# [[ -z "$TMUX"  ]] && exec tmux
```

## Get the number of lines in a file

Alternative to `wc -l`.

**Example Function (bash 4):**

```sh
lines() {
    # Usage: lines "file"
    mapfile -tn 0 lines < "$1"
    printf '%s\n' "${#lines[@]}"
}
```

**Example Function (bash 3):**

This method uses less memory than the `mapfile` method and works in `bash` 3 but it is slower for bigger files.

```sh
lines_loop() {
    # Usage: lines_loop "file"
    count=0
    while IFS= read -r _; do
        ((count++))
    done < "$1"
    printf '%s\n' "$count"
}
```

**Example Usage:**

```shell
$ lines ~/.bashrc
48

$ lines_loop ~/.bashrc
48
```

## Count files or directories in directory

This works by passing the output of the glob to the function and then counting the number of arguments.

**Example Function:**

```sh
count() {
    # Usage: count /path/to/dir/*
    #        count /path/to/dir/*/
    printf '%s\n' "$#"
}
```

**Example Usage:**

```shell
# Count all files in dir.
$ count ~/Downloads/*
232

# Count all dirs in dir.
$ count ~/Downloads/*/
45

# Count all jpg files in dir.
$ count ~/Pictures/*.jpg
64
```

## Create an empty file

Alternative to `touch`.

```shell
# Shortest.
>file

# Longer alternatives:
:>file
echo -n >file
printf '' >file
```

## Extract lines between two markers

**Example Function:**

```sh
extract() {
    # Usage: extract file "opening marker" "closing marker"
    while IFS=$'\n' read -r line; do
        [[ $extract && $line != "$3" ]] &&
            printf '%s\n' "$line"

        [[ $line == "$2" ]] && extract=1
        [[ $line == "$3" ]] && extract=
    done < "$1"
}
```

**Example Usage:**

```shell
# Extract code blocks from MarkDown file.
$ extract ~/projects/pure-bash/README.md '```sh' '```'
# Output here...
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# FILE PATHS

## Get the directory name of a file path

Alternative to the `dirname` command.

**Example Function:**

```sh
dirname() {
    # Usage: dirname "path"
    local tmp=${1:-.}

    [[ $tmp != *[!/]* ]] && {
        printf '/\n'
        return
    }

    tmp=${tmp%%"${tmp##*[!/]}"}

    [[ $tmp != */* ]] && {
        printf '.\n'
        return
    }

    tmp=${tmp%/*}
    tmp=${tmp%%"${tmp##*[!/]}"}

    printf '%s\n' "${tmp:-/}"
}
```

**Example Usage:**

```shell
$ dirname ~/Pictures/Wallpapers/1.jpg
/home/black/Pictures/Wallpapers

$ dirname ~/Pictures/Downloads/
/home/black/Pictures
```

## Get the base-name of a file path

Alternative to the `basename` command.

**Example Function:**

```sh
basename() {
    # Usage: basename "path" ["suffix"]
    local tmp

    tmp=${1%"${1##*[!/]}"}
    tmp=${tmp##*/}
    tmp=${tmp%"${2/"$tmp"}"}

    printf '%s\n' "${tmp:-/}"
}
```

**Example Usage:**

```shell
$ basename ~/Pictures/Wallpapers/1.jpg
1.jpg

$ basename ~/Pictures/Wallpapers/1.jpg .jpg
1

$ basename ~/Pictures/Downloads/
Downloads
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# VARIABLES

## Assign and access a variable using a variable

```shell
$ hello_world="value"

# Create the variable name.
$ var="world"
$ ref="hello_$var"

# Print the value of the variable name stored in 'hello_$var'.
$ printf '%s\n' "${!ref}"
value
```

Alternatively, on `bash` 4.3+:

```shell
$ hello_world="value"
$ var="world"

# Declare a nameref.
$ declare -n ref=hello_$var

$ printf '%s\n' "$ref"
value
```

## Name a variable based on another variable

```shell
$ var="world"
$ declare "hello_$var=value"
$ printf '%s\n' "$hello_world"
value
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# ESCAPE SEQUENCES

Contrary to popular belief, there is no issue in utilizing raw escape sequences. Using `tput` abstracts the same ANSI sequences as if printed manually. Worse still, `tput` is not actually portable. There are a number of `tput` variants each with different commands and syntaxes (*try `tput setaf 3` on a FreeBSD system*). Raw sequences are fine.

## Text Colors

**NOTE:** Sequences requiring RGB values only work in True-Color Terminal Emulators.

| Sequence | What does it do? | Value |
| -------- | ---------------- | ----- |
| `\e[38;5;<NUM>m` | Set text foreground color. | `0-255`
| `\e[48;5;<NUM>m` | Set text background color. | `0-255`
| `\e[38;2;<R>;<G>;<B>m` | Set text foreground color to RGB color. | `R`, `G`, `B`
| `\e[48;2;<R>;<G>;<B>m` | Set text background color to RGB color. | `R`, `G`, `B`

## Text Attributes

**NOTE:** Prepend 2 to any code below to turn it's effect off
(examples: 21=bold text off, 22=faint text off, 23=italic text off).

| Sequence | What does it do? |
| -------- | ---------------- |
| `\e[m` | Reset text formatting and colors. |
| `\e[1m` | Bold text. |
| `\e[2m` | Faint text. |
| `\e[3m` | Italic text. |
| `\e[4m` | Underline text. |
| `\e[5m` | Blinking text. |
| `\e[7m` | Highlighted text. |
| `\e[8m` | Hidden text. |
| `\e[9m` | Strike-through text. |


## Cursor Movement

| Sequence | What does it do? | Value |
| -------- | ---------------- | ----- |
| `\e[<LINE>;<COLUMN>H` | Move cursor to absolute position. | `line`, `column`
| `\e[H` | Move cursor to home position (`0,0`). |
| `\e[<NUM>A` | Move cursor up N lines. | `num`
| `\e[<NUM>B` | Move cursor down N lines. | `num`
| `\e[<NUM>C` | Move cursor right N columns. | `num`
| `\e[<NUM>D` | Move cursor left N columns. | `num`
| `\e[s` | Save cursor position. |
| `\e[u` | Restore cursor position. |


## Erasing Text

| Sequence | What does it do? |
| -------- | ---------------- |
| `\e[K` | Erase from cursor position to end of line.
| `\e[1K` | Erase from cursor position to start of line.
| `\e[2K` | Erase the entire current line.
| `\e[J` | Erase from the current line to the bottom of the screen.
| `\e[1J` | Erase from the current line to the top of the screen.
| `\e[2J` | Clear the screen.
| `\e[2J\e[H` | Clear the screen and move cursor to `0,0`.


<!-- CHAPTER END -->

<!-- CHAPTER START -->
# PARAMETER EXPANSION

## Indirection

| Parameter | What does it do? |
| --------- | ---------------- |
| `${!VAR}` | Access a variable based on the value of `VAR`.
| `${!VAR*}` | Expand to `IFS` separated list of variable names starting with `VAR`. |
| `${!VAR@}` | Expand to `IFS` separated list of variable names starting with `VAR`. If double-quoted, each variable name expands to a separate word. |


## Replacement

| Parameter | What does it do? |
| --------- | ---------------- |
| `${VAR#PATTERN}` | Remove shortest match of pattern from start of string. |
| `${VAR##PATTERN}` | Remove longest match of pattern from start of string. |
| `${VAR%PATTERN}` | Remove shortest match of pattern from end of string. |
| `${VAR%%PATTERN}` | Remove longest match of pattern from end of string. |
| `${VAR/PATTERN/REPLACE}` | Replace first match with string.
| `${VAR//PATTERN/REPLACE}` | Replace all matches with string.
| `${VAR/PATTERN}` | Remove first match.
| `${VAR//PATTERN}` | Remove all matches.

## Length

| Parameter | What does it do? |
| --------- | ---------------- |
| `${#VAR}` | Length of var in characters.
| `${#ARR[@]}` | Length of array in elements.

## Expansion

| Parameter | What does it do? |
| --------- | ---------------- |
| `${VAR:OFFSET}` | Remove first `N` chars from variable.
| `${VAR:OFFSET:LENGTH}` | Get substring from `N` character to `N` character. <br> (`${VAR:10:10}`: Get sub-string from char `10` to char `20`)
| `${VAR:: OFFSET}` | Get first `N` chars from variable.
| `${VAR:: -OFFSET}` | Remove last `N` chars from variable.
| `${VAR: -OFFSET}` | Get last `N` chars from variable.
| `${VAR:OFFSET:-OFFSET}` | Cut first `N` chars and last `N` chars. | `bash 4.2+` |

## Case Modification

| Parameter | What does it do? | CAVEAT |
| --------- | ---------------- | ------ |
| `${VAR^}` | Uppercase first character. | `bash 4+` |
| `${VAR^^}` | Uppercase all characters. | `bash 4+` |
| `${VAR,}` | Lowercase first character. | `bash 4+` |
| `${VAR,,}` | Lowercase all characters. | `bash 4+` |
| `${VAR~}` | Reverse case of first character. | `bash 4+` |
| `${VAR~~}` | Reverse case of all characters. | `bash 4+` |


## Default Value

| Parameter | What does it do? |
| --------- | ---------------- |
| `${VAR:-STRING}` | If `VAR` is empty or unset, use `STRING` as its value.
| `${VAR-STRING}` | If `VAR` is unset, use `STRING` as its value.
| `${VAR:=STRING}` | If `VAR` is empty or unset, set the value of `VAR` to `STRING`.
| `${VAR=STRING}` | If `VAR` is unset, set the value of `VAR` to `STRING`.
| `${VAR:+STRING}` | If `VAR` is not empty, use `STRING` as its value.
| `${VAR+STRING}` | If `VAR` is set, use `STRING` as its value.
| `${VAR:?STRING}` | Display an error if empty or unset.
| `${VAR?STRING}` | Display an error if unset.


<!-- CHAPTER END -->

<!-- CHAPTER START -->
# BRACE EXPANSION

## Ranges

```shell
# Syntax: {<START>..<END>}

# Print numbers 1-100.
echo {1..100}

# Print range of floats.
echo 1.{1..9}

# Print chars a-z.
echo {a..z}
echo {A..Z}

# Nesting.
echo {A..Z}{0..9}

# Print zero-padded numbers.
# CAVEAT: bash 4+
echo {01..100}

# Change increment amount.
# Syntax: {<START>..<END>..<INCREMENT>}
# CAVEAT: bash 4+
echo {1..10..2} # Increment by 2.
```

## String Lists

```shell
echo {apples,oranges,pears,grapes}

# Example Usage:
# Remove dirs Movies, Music and ISOS from ~/Downloads/.
rm -rf ~/Downloads/{Movies,Music,ISOS}
```

<!-- CHAPTER END -->


<!-- CHAPTER START -->

# CONDITIONAL EXPRESSIONS

## File Conditionals

| Expression | Value  | What does it do? |
| ---------- | ------ | ---------------- |
| `-a`       | `file` | If file exists.
| `-b`       | `file` | If file exists and is a block special file.
| `-c`       | `file` | If file exists and is a character special file.
| `-d`       | `file` | If file exists and is a directory.
| `-e`       | `file` | If file exists.
| `-f`       | `file` | If file exists and is a regular file.
| `-g`       | `file` | If file exists and its set-group-id bit is set.
| `-h`       | `file` | If file exists and is a symbolic link.
| `-k`       | `file` | If file exists and its sticky-bit is set
| `-p`       | `file` | If file exists and is a named pipe (*FIFO*).
| `-r`       | `file` | If file exists and is readable.
| `-s`       | `file` | If file exists and its size is greater than zero.
| `-t`       | `fd`   | If file descriptor is open and refers to a terminal.
| `-u`       | `file` | If file exists and its set-user-id bit is set.
| `-w`       | `file` | If file exists and is writable.
| `-x`       | `file` | If file exists and is executable.
| `-G`       | `file` | If file exists and is owned by the effective group ID.
| `-L`       | `file` | If file exists and is a symbolic link.
| `-N`       | `file` | If file exists and has been modified since last read.
| `-O`       | `file` | If file exists and is owned by the effective user ID.
| `-S`       | `file` | If file exists and is a socket.

## File Comparisons

| Expression | What does it do? |
| ---------- | ---------------- |
| `file -ef file2` | If both files refer to the same inode and device numbers.
| `file -nt file2` | If `file` is newer than `file2` (*uses modification time*) or `file` exists and `file2` does not.
| `file -ot file2` | If `file` is older than `file2` (*uses modification time*) or `file2` exists and `file` does not.

## Variable Conditionals

| Expression | Value | What does it do? |
| ---------- | ----- | ---------------- |
| `-o`       | `opt` | If shell option is enabled.
| `-v`       | `var` | If variable has a value assigned.
| `-R`       | `var` | If variable is a name reference.
| `-z`       | `var` | If the length of string is zero.
| `-n`       | `var` | If the length of string is non-zero.

## Variable Comparisons

| Expression | What does it do? |
| ---------- | ---------------- |
| `var = var2` | Equal to.
| `var == var2` | Equal to (*synonym for `=`*).
| `var != var2` | Not equal to.
| `var < var2` | Less than (*in ASCII alphabetical order.*)
| `var > var2` | Greater than (*in ASCII alphabetical order.*)

<!-- CHAPTER END -->

<!-- CHAPTER START -->

# ARITHMETIC OPERATORS

## Assignment

| Operators | What does it do? |
| --------- | ---------------- |
| `=`       | Initialize or change the value of a variable.

## Arithmetic

| Operators | What does it do? |
| --------- | ---------------- |
| `+` | Addition
| `-` | Subtraction
| `*` | Multiplication
| `/` | Division
| `**` | Exponentiation
| `%` | Modulo
| `+=` | Plus-Equal (*Increment a variable.*)
| `-=` | Minus-Equal (*Decrement a variable.*)
| `*=` | Times-Equal (*Multiply a variable.*)
| `/=` | Slash-Equal (*Divide a variable.*)
| `%=` | Mod-Equal (*Remainder of dividing a variable.*)

## Bitwise

| Operators | What does it do? |
| --------- | ---------------- |
| `<<` | Bitwise Left Shift
| `<<=` | Left-Shift-Equal
| `>>` | Bitwise Right Shift
| `>>=` | Right-Shift-Equal
| `&` | Bitwise AND
| `&=` | Bitwise AND-Equal
| `\|` | Bitwise OR
| `\|=` | Bitwise OR-Equal
| `~` | Bitwise NOT
| `^` | Bitwise XOR
| `^=` | Bitwise XOR-Equal

## Logical

| Operators | What does it do? |
| --------- | ---------------- |
| `!` | NOT
| `&&` | AND
| `\|\|` | OR

## Miscellaneous

| Operators | What does it do? | Example |
| --------- | ---------------- | ------- |
| `,` | Comma Separator | `((a=1,b=2,c=3))`


<!-- CHAPTER END -->

<!-- CHAPTER START -->
# ARITHMETIC

## Simpler syntax to set variables

```shell
# Simple math
((var=1+2))

# Decrement/Increment variable
((var++))
((var--))
((var+=1))
((var-=1))

# Using variables
((var=var2*arr[2]))
```

## Ternary Tests

```shell
# Set the value of var to var2 if var2 is greater than var.
# var: variable to set.
# var2>var: Condition to test.
# ?var2: If the test succeeds.
# :var: If the test fails.
((var=var2>var?var2:var))
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# TRAPS

Traps allow a script to execute code on various signals. In [pxltrm](https://github.com/dylanaraps/pxltrm) (*a pixel art editor written in bash*)  traps are used to redraw the user interface on window resize. Another use case is cleaning up temporary files on script exit.

Traps should be added near the start of scripts so any early errors are also caught.

**NOTE:** For a full list of signals, see `trap -l`.


## Do something on script exit

```shell
# Clear screen on script exit.
trap 'printf \\e[2J\\e[H\\e[m' EXIT
```

## Ignore terminal interrupt (CTRL+C, SIGINT)

```shell
trap '' INT
```

## React to window resize

```shell
# Call a function on window resize.
trap 'code_here' SIGWINCH
```

## Do something before every command

```shell
trap 'code_here' DEBUG
```

## Do something when a shell function or a sourced file finishes executing

```shell
trap 'code_here' RETURN
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# PERFORMANCE

## Disable Unicode

If unicode is not required, it can be disabled for a performance increase. Results may vary however there have been noticeable improvements in [neofetch](https://github.com/dylanaraps/neofetch) and other programs.

```shell
# Disable unicode.
LC_ALL=C
LANG=C
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# OBSOLETE SYNTAX

## Shebang

Use `#!/usr/bin/env bash` instead of `#!/bin/bash`.

- The former searches the user's `PATH` to find the `bash` binary.
- The latter assumes it is always installed to `/bin/` which can cause issues.

**NOTE**: There are times when one may have a good reason for using `#!/bin/bash` or another direct path to the binary.


```shell
# Right:

    #!/usr/bin/env bash

# Less right:

    #!/bin/bash
```

## Command Substitution

Use `$()` instead of `` ` ` ``.

```shell
# Right.
var="$(command)"

# Wrong.
var=`command`

# $() can easily be nested whereas `` cannot.
var="$(command "$(command)")"
```

## Function Declaration

Do not use the `function` keyword, it reduces compatibility with older versions of `bash`.

```shell
# Right.
do_something() {
    # ...
}

# Wrong.
function do_something() {
    # ...
}
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# INTERNAL VARIABLES

## Get the location to the `bash` binary

```shell
"$BASH"
```

## Get the version of the current running `bash` process

```shell
# As a string.
"$BASH_VERSION"

# As an array.
"${BASH_VERSINFO[@]}"
```

## Open the user's preferred text editor

```shell
"$EDITOR" "$file"

# NOTE: This variable may be empty, set a fallback value.
"${EDITOR:-vi}" "$file"
```

## Get the name of the current function

```shell
# Current function.
"${FUNCNAME[0]}"

# Parent function.
"${FUNCNAME[1]}"

# So on and so forth.
"${FUNCNAME[2]}"
"${FUNCNAME[3]}"

# All functions including parents.
"${FUNCNAME[@]}"
```

## Get the host-name of the system

```shell
"$HOSTNAME"

# NOTE: This variable may be empty.
# Optionally set a fallback to the hostname command.
"${HOSTNAME:-$(hostname)}"
```

## Get the architecture of the Operating System

```shell
"$HOSTTYPE"
```

## Get the name of the Operating System / Kernel

This can be used to add conditional support for different Operating
Systems without needing to call `uname`.

```shell
"$OSTYPE"
```

## Get the current working directory

This is an alternative to the `pwd` built-in.

```shell
"$PWD"
```

## Get the number of seconds the script has been running

```shell
"$SECONDS"
```

## Get a pseudorandom integer

Each time `$RANDOM` is used, a different integer between `0` and `32767` is returned. This variable should not be used for anything related to security (*this includes encryption keys etc*).


```shell
"$RANDOM"
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# INFORMATION ABOUT THE TERMINAL

## Get the terminal size in lines and columns (*from a script*)

This is handy when writing scripts in pure bash and `stty`/`tput` can’t be
called.

**Example Function:**

```sh
get_term_size() {
    # Usage: get_term_size

    # (:;:) is a micro sleep to ensure the variables are
    # exported immediately.
    shopt -s checkwinsize; (:;:)
    printf '%s\n' "$LINES $COLUMNS"
}
```

**Example Usage:**

```shell
# Output: LINES COLUMNS
$ get_term_size
15 55
```

## Get the terminal size in pixels

**CAVEAT**: This does not work in some terminal emulators.

**Example Function:**

```sh
get_window_size() {
    # Usage: get_window_size
    printf '%b' "${TMUX:+\\ePtmux;\\e}\\e[14t${TMUX:+\\e\\\\}"
    IFS=';t' read -d t -t 0.05 -sra term_size
    printf '%s\n' "${term_size[1]}x${term_size[2]}"
}
```

**Example Usage:**

```shell
# Output: WIDTHxHEIGHT
$ get_window_size
1200x800

# Output (fail):
$ get_window_size
x
```

## Get the current cursor position

This is useful when creating a TUI in pure bash.

**Example Function:**

```sh
get_cursor_pos() {
    # Usage: get_cursor_pos
    IFS='[;' read -p $'\e[6n' -d R -rs _ y x _
    printf '%s\n' "$x $y"
}
```

**Example Usage:**

```shell
# Output: X Y
$ get_cursor_pos
1 8
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# CONVERSION

## Convert a hex color to RGB

**Example Function:**

```sh
hex_to_rgb() {
    # Usage: hex_to_rgb "#FFFFFF"
    #        hex_to_rgb "000000"
    : "${1/\#}"
    ((r=16#${_:0:2},g=16#${_:2:2},b=16#${_:4:2}))
    printf '%s\n' "$r $g $b"
}
```

**Example Usage:**

```shell
$ hex_to_rgb "#FFFFFF"
255 255 255
```


## Convert an RGB color to hex

**Example Function:**

```sh
rgb_to_hex() {
    # Usage: rgb_to_hex "r" "g" "b"
    printf '#%02x%02x%02x\n' "$1" "$2" "$3"
}
```

**Example Usage:**

```shell
$ rgb_to_hex "255" "255" "255"
#FFFFFF
```


# CODE GOLF

## Shorter `for` loop syntax

```shell
# Tiny C Style.
for((;i++<10;)){ echo "$i";}

# Undocumented method.
for i in {1..10};{ echo "$i";}

# Expansion.
for i in {1..10}; do echo "$i"; done

# C Style.
for((i=0;i<=10;i++)); do echo "$i"; done
```

## Shorter infinite loops

```shell
# Normal method
while :; do echo hi; done

# Shorter
for((;;)){ echo hi;}
```

## Shorter function declaration

```shell
# Normal method
f(){ echo hi;}

# Using a subshell
f()(echo hi)

# Using arithmetic
# This can be used to assign integer values.
# Example: f a=1
#          f a++
f()(($1))

# Using tests, loops etc.
# NOTE: ‘while’, ‘until’, ‘case’, ‘(())’, ‘[[]]’ can also be used.
f()if true; then echo "$1"; fi
f()for i in "$@"; do echo "$i"; done
```

## Shorter `if` syntax

```shell
# One line
# Note: The 3rd statement may run when the 1st is true
[[ $var == hello ]] && echo hi || echo bye
[[ $var == hello ]] && { echo hi; echo there; } || echo bye

# Multi line (no else, single statement)
# Note: The exit status may not be the same as with an if statement
[[ $var == hello ]] &&
    echo hi

# Multi line (no else)
[[ $var == hello ]] && {
    echo hi
    # ...
}
```

## Simpler `case` statement to set variable

The `:` built-in can be used to avoid repeating `variable=` in a case statement. The `$_` variable stores the last argument of the last command. `:` always succeeds so it can be used to store the variable value.

```shell
# Modified snippet from Neofetch.
case "$OSTYPE" in
    "darwin"*)
        : "MacOS"
    ;;

    "linux"*)
        : "Linux"
    ;;

    *"bsd"* | "dragonfly" | "bitrig")
        : "BSD"
    ;;

    "cygwin" | "msys" | "win32")
        : "Windows"
    ;;

    *)
        printf '%s\n' "Unknown OS detected, aborting..." >&2
        exit 1
    ;;
esac

# Finally, set the variable.
os="$_"
```

<!-- CHAPTER END -->

<!-- CHAPTER START -->
# OTHER

## Use `read` as an alternative to the `sleep` command

Surprisingly, `sleep` is an external command and not a `bash` built-in.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
read_sleep() {
    # Usage: read_sleep 1
    #        read_sleep 0.2
    read -rt "$1" <> <(:) || :
}
```

**Example Usage:**

```shell
read_sleep 1
read_sleep 0.1
read_sleep 30
```

For performance-critical situations, where it is not economic to open and close an excessive number of file descriptors, the allocation of a file descriptor may be done only once for all invocations of `read`:

(See the generic original implementation at https://blog.dhampir.no/content/sleeping-without-a-subprocess-in-bash-and-how-to-sleep-forever)

```shell
exec {sleep_fd}<> <(:)
while some_quick_test; do
    # equivalent of sleep 0.001
    read -t 0.001 -u $sleep_fd
done
```

## Check if a program is in the user's PATH

```shell
# There are 3 ways to do this and either one can be used.
type -p executable_name &>/dev/null
hash executable_name &>/dev/null
command -v executable_name &>/dev/null

# As a test.
if type -p executable_name &>/dev/null; then
    # Program is in PATH.
fi

# Inverse.
if ! type -p executable_name &>/dev/null; then
    # Program is not in PATH.
fi

# Example (Exit early if program is not installed).
if ! type -p convert &>/dev/null; then
    printf '%s\n' "error: convert is not installed, exiting..."
    exit 1
fi
```

## Get the current date using `strftime`

Bash’s `printf` has a built-in method of getting the date which can be used in place of the `date` command.

**CAVEAT:** Requires `bash` 4+

**Example Function:**

```sh
date() {
    # Usage: date "format"
    # See: 'man strftime' for format.
    printf "%($1)T\\n" "-1"
}
```

**Example Usage:**

```shell
# Using above function.
$ date "%a %d %b  - %l:%M %p"
Fri 15 Jun  - 10:00 AM

# Using printf directly.
$ printf '%(%a %d %b  - %l:%M %p)T\n' "-1"
Fri 15 Jun  - 10:00 AM

# Assigning a variable using printf.
$ printf -v date '%(%a %d %b  - %l:%M %p)T\n' '-1'
$ printf '%s\n' "$date"
Fri 15 Jun  - 10:00 AM
```

## Get the username of the current user

**CAVEAT:** Requires `bash` 4.4+

```shell
$ : \\u
# Expand the parameter as if it were a prompt string.
$ printf '%s\n' "${_@P}"
black
```

## Generate a UUID V4

**CAVEAT**: The generated value is not cryptographically secure.

**Example Function:**

```sh
uuid() {
    # Usage: uuid
    C="89ab"

    for ((N=0;N<16;++N)); do
        B="$((RANDOM%256))"

        case "$N" in
            6)  printf '4%x' "$((B%16))" ;;
            8)  printf '%c%x' "${C:$RANDOM%${#C}:1}" "$((B%16))" ;;

            3|5|7|9)
                printf '%02x-' "$B"
            ;;

            *)
                printf '%02x' "$B"
            ;;
        esac
    done

    printf '\n'
}
```

**Example Usage:**

```shell
$ uuid
d5b6c731-1310-4c24-9fe3-55d556d44374
```

## Progress bars

This is a simple way of drawing progress bars without needing a for loop
in the function itself.

**Example Function:**

```sh
bar() {
    # Usage: bar 1 10
    #            ^----- Elapsed Percentage (0-100).
    #               ^-- Total length in chars.
    ((elapsed=$1*$2/100))

    # Create the bar with spaces.
    printf -v prog  "%${elapsed}s"
    printf -v total "%$(($2-elapsed))s"

    printf '%s\r' "[${prog// /-}${total}]"
}
```

**Example Usage:**

```shell
for ((i=0;i<=100;i++)); do
    # Pure bash micro sleeps (for the example).
    (:;:) && (:;:) && (:;:) && (:;:) && (:;:)

    # Print the bar.
    bar "$i" "10"
done

printf '\n'
```

## Get the list of functions in a script

```sh
get_functions() {
    # Usage: get_functions
    IFS=$'\n' read -d "" -ra functions < <(declare -F)
    printf '%s\n' "${functions[@]//declare -f }"
}
```

## Bypass shell aliases

```shell
# alias
ls

# command
# shellcheck disable=SC1001
\ls
```

## Bypass shell functions

```shell
# function
ls

# command
command ls
```

## Run a command in the background

This will run the given command and keep it running, even after the terminal or SSH connection is terminated. All output is ignored.

```sh
bkr() {
    (nohup "$@" &>/dev/null &)
}

bkr ./some_script.sh # some_script.sh is now running in the background
```

## Capture the return value of a function without command substitution

**CAVEAT:** Requires `bash` 4+

This uses local namerefs to avoid using `var=$(some_func)` style command substitution for function output capture.

```sh
to_upper() {
  local -n ptr=${1}

  ptr=${ptr^^}
}

foo="bar"
to_upper foo
printf "%s\n" "${foo}" # BAR
```

<!-- CHAPTER END -->
