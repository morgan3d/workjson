# WorkJSON

WorkJSON is the JSON format extended with commonly requested features
needed for getting real work done:

  - Optional trailing commas on arrays and objects
  - C++ single and multline comments
  - `Backtick` multiline strings
  - Explicit plus sign permitted on numbers
  - Numbers with bare leading or trailing decimal
  - NaN, Infinity, -Infinity
  - Hexadecimal numbers
  - Optional unquoted object keys (using [A-Za-z_0-9]+ characters only)

You can use WorkJSON as a parser only in order to make your program
more robust to slightly malformed JSON input. Or you can use it as
both a parser and writer to make your program better able to represent
numeric constants while staying close enough to vanilla JSON for
most editors and tools to work well.

This repo contains single-file JavaScript and Python drop-in
replacements for the system JSON libraries. The JavaScript version is
only 2 kB when minified.

The WorkJSON parser is 100% backwards compatible to vanilla JSON parsers
as long as your input has no characters in the Unicode private
use area \uE000 through \uF8FF.

The output of the WorkJSON writer is backwards compatible to 
vanilla JSON as long as you don't use NaN or Infinity values, which 
standard JSON writers cannot process anyway.

The implementation is designed to use only regexps and a vanilla
JSON parser to simplify porting and minimize code size.

The current version does not support unescaped double quotes within
single-quoted or multiline strings.


# Other Libraries

WorkJSON was originally released in the
[quadplay](https://github.com/morgan3d/quadplay) fantasy console
as "BetterJSON". Since there is an older npm package by that name,
I renamed my library to WorkJSON to avoid a collision.

WorkJSON is similar to [JSON5](https://json5.org/) but is about 10x
smaller. The primary difference is that WorkJSON intentionally does
not support unicode in unquoted keys.

[YAML](https://yaml.org/) is a markdown-like superset of JSON.
WorkJSON is compatible with YAML. It is generally a better format than
JSON, but many projects, I choose the lighter weight and more widely
supported JSON ecosystem, using WorkJSON to remove the rough edges of
JSON.
