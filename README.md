# Automate RX style
Inspired by the [Airbnb JS style guide](https://github.com/airbnb/javascript) and [Google style guides](https://google.github.io/styleguide), I introduce you to the 1st-ever-made set of style, formatting, and best-practices for [LL](https://llamalab.com)-[AM](https://llamalab.com/automate)

This is **very** incomplete, so don't take it seriously... yet

## Repo Name

To explicitly communicate that this is not official, and not affiliated with Llamalab, and just 1 of infinitely many possible styles, I added "RX" which stands for "RudXain"

I couldn't think of a better name, please send me suggestions

Despite the "RX", this is not intended to be "my personal style". I may take the freedom to ignore some of these rules in my own AM-flows  

This is intended to be for everyone, by everyone, from everyone. Therefore, contributions are very welcome!

## Naming

Variables:
- [snake_case](https://en.wikipedia.org/wiki/Snake_case)
- Constants must be ALL UPPERCASE. Since all vars are mutable, we must take the same approach as in Python and Shell langs
- Fiber IDs should be prefixed with `f_`. See [Hungarian notation](https://en.wikipedia.org/wiki/Hungarian_notation)
- ["Process text selection"](https://llamalab.com/automate/doc/block/process_text.html) blocks shouldn't have redundant info. Never use the exact name as the "Flow Beginning", add some useful variations. Example: If the flow is named "Uppercase and Lowercase converter", the block-title should be "change capitalization" if the next dialogue is a "Choice block". Or "to lowercase" and "TO UPPERCASE" if each fiber converts to 1 capitalization (and there's no "Choice")

## Subroutines

- Use these blocks to mark the entry-points of "backend logic" (non UI stuff). This is known as [modular programming](https://en.wikipedia.org/wiki/Modular_programming). However, if the entry-point is extremely obvious (e.g. when it's just 1 var-set), you can save blocks (and get better performance) by not adding it.
- If a subroutine makes assumptions about 1 or more variables, you must document those assumptions. You wouldn't want users of your subroutine accidentally assigning a non-null value to a variable that's expected to be `null`, that could be catastrophic if the variable contains private data and the subroutine posts it publicly to a random server

## Appendix

Just RTD (Read The Docs). If you learn more about AM, and practice coding in it, you'll learn best practices _automagically!_

## Linters

Currently, the AST implementation of AM-flows is subject to change without warning. This means that making linters/formatters that are forwards-compatible is almost impossible ([Source](https://groups.google.com/g/automate-user/c/_8xuZW7j5Ps/m/g-XtwOIAAgAJ))

If AM had a public API that was [LSP](https://en.wikipedia.org/wiki/Language_Server_Protocol)-compliant, then it would be possible to parse and analyse \*.flo files
