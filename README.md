# wsg

A simple website generator for POSIX environments.
It has no dependencies.

To use it, run `./script/generate`.
It will place the website in `./build/htdocs`.

The files inside `template` and `content` are processed by macros.

## Templates

The simplest macros are for replacing text.
Text values that are globally available:

|Macro                 |Text                 |
|----------------------|---------------------|
| **SITE_DESCRIPTION** | website description |
| **SITE_NAME**        | website name        |
| **PAGE_URL**         | URL of current page |

### Quoting

To mark text not to be interpreted as a macro, quote it between **<\`** and **\`>**.
These are intented for writing pages in **HTML** plain markup, not Markdown.
You can customize them in the `macros` file.

### Macros

Macros are used for defining and creating page templates:

| Macro     | Description                                                       |
|-----------|-------------------------------------------------------------------|
| `define`  | create a new macro.                                               |
| `include` | includes a new file in the output.                                |
| `dnl`     | ignores the rest of the line and the following newline character. |
| `ifdef`   | tests if a macro is already defined.                              |
| `ifelse`  | tests arbitrary conditionals.                                     |

#### Printing

Macros uses for printing and debugging:

| Macro      | Description                                      |
|------------|--------------------------------------------------|
| `errprint` | prints its arguments to the standard error.      |
| `dumpdef`  | a debugging aid that prints current definitions. |

These macros are a subset of [the m4 processor][m4].
You could have more of them by editing the `macros` file.
Read your system's `M4(1)` manual for more information.

[m4]: https://pubs.opengroup.org/onlinepubs/9699919799/utilities/m4.html
