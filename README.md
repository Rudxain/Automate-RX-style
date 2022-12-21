# AM RX style
Inspired by the [Airbnb JS style guide](https://github.com/airbnb/javascript) and [Google style guides](https://google.github.io/styleguide), I introduce you to the 1st-ever-made set of style, formatting, and best-practices for [LL](https://llamalab.com)-[AM](https://llamalab.com/automate)

## Repo Name

To explicitly communicate that this is not official, and not affiliated with Llamalab, and just 1 of infinitely many possible styles, I added "RX" which stands for "RudXain"

I couldn't think of a better name, please send me suggestions

Despite the "RX", this is not intended to be "my personal style". I may take the freedom to ignore some of these rules in my own AM-flows  

This is intended to be for everyone, by everyone, from everyone. Therefore, contributions are very welcome!

## Naming

Variables:
- [snake_case](https://en.wikipedia.org/wiki/Snake_case)
- Constants must be ALL UPPERCASE. Since all vars are mutable, we must take the same approach as in Shell langs
- private/local vars must be suffixed with `_`. AM syntax doesn't allow `_` as prefix
- The more vars declared, the more descriptive their names should be. There are no doc-comments, and AM has name-completion, so don't be afraid of long names, except if they take too much space in the flowchart preview 
- Fiber IDs should be prefixed with `f_`. See [Hungarian notation](https://en.wikipedia.org/wiki/Hungarian_notation)
- ["Process text selection"](https://llamalab.com/automate/doc/block/process_text.html) blocks shouldn't have redundant info. Never use the exact name as the "Flow Beginning", add some useful variations. Example: If the flow is named "Uppercase and Lowercase converter", the block-title should be "to lowercase" and "TO UPPERCASE" if each fiber converts to 1 capitalization (and there's no "Choice" blocks)

## Expressions

- Use [Yoda Style](https://en.wikipedia.org/wiki/Yoda_conditions) when appropriate. AM has no assignment-expressions, but there are expression-previews.
A good example is when checking types: Imagine you have multiple blocks, all saying `type(var) = ...` in their previews, it's so frustrating when the preview doesn't show **which** types are being checked!
But we may argue the same about vars: image you had multiple vars, all being checked against the same type, and all you can see is `"number" = type(...` everywhere. It's so frustrating not knowing what vars are being checked!
- Use parentheses when appropriate. The docs aren't clear about operator precedence and associativity, so please reduce ambiguity in the meantime
- **Always** use parentheses in nested ternaries
- Use `++` for string concatenation. Only use interpolation if there's an expression between text literals.
This makes it look cleaner and allows name-completion. Interpolations can't always have name-completions

## Comments

Since AM doesn't support comments _per-se_, we have to emulate them.

- Expressions:
The best way is to use a ternary operator, [like in this flow](https://llamalab.com/automate/community/flows/40004). You can place comments on either side, unlike `&&` and `||` ops

- Blocks:
You can add unconnected "Log Append"s, but that increases the block count, forcing some non-premium users to delete those blocks.
Another option is to include block-docs in the flow description, but that may not have enough space.
If you need **much more space**, you should host the docs elsewhere (this speeds-up downloads, because the .flo is smaller), and add a link in the desc

## Formatting

- Place blocks near each other, such that their connection paths are as short as possible
- If multiple paths of similar colors are overlapping, try to find a way to separate them. This is useful to disambiguate connections, especially for colorblind people

## Subroutines

- Use these blocks to mark the entry-points of "backend logic" (non UI stuff). This is known as [modular programming](https://en.wikipedia.org/wiki/Modular_programming). However, if the entry-point is extremely obvious (e.g. when it's just 1 var-set), you can save blocks (and get better performance) by not adding it.
- If a subroutine makes assumptions about 1 or more variables, you must document those assumptions. You wouldn't want users of your subroutine accidentally assigning a non-null value to a variable that's expected to be `null`, that could be catastrophic if the variable contains private data and the subroutine posts it publicly to a random server

## Appendix

Just RTD (Read The Docs). If you learn more about AM, and practice coding in it, you'll learn best practices _automagically!_

## Linters

Currently, the AST implementation used in \*.flo files is subject to change, without warning. This means that making linters/formatters that are forwards-compatible is almost impossible ([Source](https://groups.google.com/g/automate-user/c/_8xuZW7j5Ps/m/g-XtwOIAAgAJ))

If AM had a public API similar to [LSP](https://en.wikipedia.org/wiki/Language_Server_Protocol), then it would be possible to parse and analyse \*.flo files
