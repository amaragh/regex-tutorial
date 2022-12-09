# Regex Tutorial: Matching a URL

Regular Expressions (Regex) are patterns that allow us to match strings, whether standalone, or as part or larger strings. This can be useful for validating data such as password or special IDs, or even for identifying or extracting strings that match certain patterns.

## Summary

I will be explaining a regex to match a URL. THere are different aspect sof regex included in the URL expression and I will be going into further detail to explain the different components that comprise this regex. Below is the sample I will be using for this review:

Regex to match a URL:
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)

## Regex Components

### Anchors

The `^` at the beginning of the expression indicates the expression should begin with what immediately follows the symbol. 

The `$` at the end of the expression indicates the end of the URL.

### Quantifiers

The `?` indicates that what immediately precedes this symbol is optional. 

The `+` indicates that one or more of the preceding code can be present.

Expressions such as `{m,n}` indicate that the preceding expression will be matched at least m times and at most, n times.

The symbol `*` means that the preceding code can be matched zero or more times.

See the below table for examples from the code snippet:

|Expression| Description|
|---|---|
|`https?`|Either `http` or `https` can be expected|
|`(https?:\/\/)?`| Not all URLs will begin with `http://` or `https://`|
|`[\da-z\.-]+`| The code between the square brackets immediately preceding the `+` can be repeated to produce one or more characters based on that logic |
|`{2,6}`| In the code snippet `([a-z\.]{2,6})`, we can expect to match the expression `[a-z\.]` at least twice and at most, 6 times. |

### Character Classes

In the above URL regex code snippet, we observe a few character classes wich are noted and explained below:

|Class|Description|
|--- |  ---   |
|`[]`| Match exactly one character|
|`\d`| Can also be written as `[0-9]`; one character from `0` to `9` will be matched.|
|`a-z`| Any value from `a` to `z` can be matched (must be lowercase).|

For example, in the following code excerpt from the URL regex, `[\da-z\.-]`, the combination of the 3 character classes from the above table, along with `\.` and `-`, means we can match exactly one character that could be either a digit from `0` to `9` OR a letter from `a` to `z` OR a period OR a dash.

Another character class we see is `\w` which can also be written as `[a-zA-Z0-9_]`. We can expect to match one or more characters from `a` to `z` OR `A` to `Z` OR `0` to `9` OR the literal underscore ( `_` ). 

### Grouping and Capturing

`()` treats multiple characters as a single unit. For example, `(https?:\/\/)` is taken as a group which either appears all together based on being followed by a `?`.

### Bracket Expressions

A bracket expression is enclosed within square brackets (`[]`). Only matches a single character based on the expression between the square brackets. More detail is given in the above section on [Character Classes](#character-classes).

### Greedy and Lazy Match

The expression `[\da-z\.-]+` can be considered greedy (the `+`, really) as the `+` will cause the regex engine to repeat the preceding snippet as much as possible. Remember, we defined `+` in the [Quantifiers](#quantifiers) section - the preceding code can be matched repeatedly. This can be problematic if the string we are searching across has multiple sections that can be matched by this exact code snippet as we could end up capturing the string between the intended matches as well.

## Author

I am a new fullstack developer who got my start in Rice University's FullStack Coding Bootcamp. Throughout this course, I have worked on several projects as we have built upon the skills learned week by week. You can view these projects by visiting my [GitHub profile](https://github.com/amaragh).