# Automate RX style
Inspired by the [Airbnb JS style guide](https://github.com/airbnb/javascript) and [Google style guides](https://google.github.io/styleguide), I introduce you to the 1st-ever-made set of style, formatting, and best-practices for LL-AM

This is **very** incomplete, so don't take it seriously... yet

## Name

To explicitly communicate that this is not official, and not affiliated with Llamalab, and just 1 of infinitely many possible styles, I added "RX" which stands for "RudXain"

I couldn't think of a better name, please send me suggestions

Despite the "RX", this is not intended to be "my personal style". I may take the freedom to ignore some of these rules in my own AM-flows  

This is intended to be for everyone, by everyone, from everyone. Therefore, contributions are very welcome!

## Rules

### Naming

Variables:
- [snake_case](https://en.wikipedia.org/wiki/Snake_case)
- constants must be ALL UPPERCASE. Since all vars are mutable, we must take the same approach as in Python and Shell langs
- fiber IDs should be prefixed with `f_`. See [Hungarian notation](https://en.wikipedia.org/wiki/Hungarian_notation)
- "Select Text" blocks shouldn't have redundant info. Never use the exact name as the flow, add some useful variations

### Subroutines

- if a subroutine makes assumptions about 1 or more variables, you must document those assumptions. You wouldn't want users of your subroutine accidentally assigning a non-null value to a variable that's expected to be `null`, that could be catastrophic if the variable contains private data and the subroutine posts it publicly to a random server
