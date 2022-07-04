# RegEx Tutorial

Regular expression also known as RegEx is simply a pattern of characters that are used to validate character combinations inside of a coding language. In this tutorial we will take a regex pattern and break it down to help explain what it does.

## Summary

Below is a regex which takes the input and validates whether or not it is an email address or not.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

The anchor identifies the position of the characters rather then identifying the individual characters.

The begining of the string is identified by the caret `^` and the end of the string is identified by the dollar sign `$`

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

Here are some string anchor examples:

    ^ caret matches at the start of the string the regex pattern is applied to.

-     .$ matches f in [abc\ndef]

  $ dollar symbol matches at the end of the string the regex pattern is applied to.

-     ^. matches a in [abc\ndef]

  \A matches at the start of the string the regex pattern is applied to.

-     \A\w matches only a in abc

  \z matches at the end of the string the regex pattern is applied to.

-     \w\z matches f in abc\ndef but fails to match abc\ndef\n

  \z matches at the end of the string the regex pattern is applied to.

-     \w\Z matches f in abc\ndef but fails to match abc\ndef\n or abc\ndef\n\n

  \` (backslash backtick) matches at the start of the string the regex pattern is applied to.

-     \`\w matches only a in abc

### Quantifiers

A quantifier is a repitition operator. A quantifier lets the system know to match the preceding token a set number of times. The quantifier can be considered a lazy quantifier or a greedy quantifier. For more about lazy or greedy quantifiers please read [Greedy and Lazy Match](#greedy-and-lazy-match).

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

The plus symbol `+` matches one or more of the preceding tokens. In this example it will attempt to match `[a-z0-9_\.-]`. In regex if you have `[a-z]` then it matches any lowercase letter, `[0-9]` matches any digit, and `[_\.-]`matches the special charaters underscore, backslash, period, and hyphen. So in our example we are matching any lowercase letter, digit, and the special charaters underscore, backslash, period, and hyphen.

The two numbers within the curly brackets `{2,6}` will match a range of characters from two to six from the previous token. In this example it will match between 2 and 6 of the characters `[a-z\.]`. If we had only one number in the curly bracket like this `{2}` it would match exactly two characters. If we had a comma `,` and not a second number `{2,}` this indecates a match of 2 or more.

Other examples of quantifiers which are not included in this example are:

- The question mark `?`. This will match zero or one of the proceding token. This makes the token optional and makes the quantifier lazy.
- The asterisk `*`. This will match zero or more of the proceding token.

### OR Operator

The pipe symbol `|` is an alternation and it matches the expression before or after it. You can use the pipe symbol `|` to affect a single character or a whole expression.

### Character Classes

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

A character class or also known as a character set is defined by using square brackets `[]` around the character/characters you want to match. If you wanted to match the character `a` or an `e` we would use the character class `[ae]`. This character class will match either `a` or `e`. The order of the characters doesn't matter the results will be the same.

If you would want to match a range of numbers or letters like we are in our exaple you would use the hyphen symbol `-`. In our example we are matching a range of `0` and `9` with this expression `[0-9]` and the range between `a` and `z` using `[a-z]`. We can combine both expressions into one by placing them both inside one set of square brackets `[]` without spaces like this example `[a-z0-9]`.

There are certain named classes of characters that are predefined within the bracket expression `[: :]`.

Here is a few predefined character classes useing the bracket expression `[: :]`.

- `[:alnum:]`:

  - Matches a alphanumeric character `[a-zA-Z0-9]` or `[[:alpha:][:digit:]]`.

- `[:alpha:]`

  - Matches a alphabetic character `[a-zA-Z]`.

- `[:blank:]`

  - Matches a whitespace character, excluding line breaks `[ \t]`.

- `[:digit:]`

  - Matches a digit `[0-9]` (also written as `\d`).

- `[:graph:]`

  - Matches a visible character `[\x21-\x7E]`.

- `[:lower:]`

  - Matches a lowercase letter `[a-z]`

- `[:print:]`

  - Matches a visible character or the space character `[\x20-\x7E]`

- `[:punct:]`

  - Matches a punctuation character `[!"#$%&'()*+,\-./:;<=>?@[\]^_{|}~]`.

- `[:space:]`

  - Matches a whitespace character, including a line break `[ \t\r\n\v\f]` (also written as `/s`).

- `[:upper:]`

  - Matches a uppercase letter [A-Z]

- `[:xdigit:]`

  - matches a hexadecimal digit `[A-Fa-f0-9]`

The following are other type of character class that can be used

- The caret `^` is used to make the character a negated set by placing it as the first thing inside the expression like the following `[^abc]`. A negated set will match any character that is not in the negated set. The expression `[^abc]` will not match the characters `a`, `b`, and `c` and characters are case sesitive.

- The period symbol `.` will match any character except line breaks. in our example the `.` actually refers to the periods in the email and are not a character class.
- Match any `[/s/S]` will match any character.
- Word `/w` will match any word.
- Digit `/d` matches any number.
- Whitespace `\s` will match any character that leaves whitespace like spaces, tabs, line breaks, etc.
- Not word `/W` will match any character that is not a word.
- Not digit `/D` will match any character that is not a number.
- Not whitespace `\S` will match any character that is not a whitespace character.

### Flags

Flags follow the closing forward slash `/` of the expression, and it changes how the expression is interpreted.

We do not have any flags in our example expression.

These are some examples of flags.

- Global search `g` will store the index of the last match.
- Ignore case `i` will make the entire expression case-sensitive.
- Multiline `m` will cause the beginning and end anchors to match the start and end of a line instead of the whole string.
- Unicode `u` allows extended unicode escapes in the form \x{FFFFF}.
- Sticky `y` will only match from its last index position and ignores the global search flag.
- Dotall `s` causes dot (.) to match any character.

### Grouping and Capturing

Groups allow you to combine multiple tokens together and will be captured and executed as one group.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

With groups we can capture `a`, `b`, and `c` as one group and extracting a substring by wrapping them in a set of parenthesis `(abc)`.

In our example we use capture 3 groups: `([a-z0-9_\.-]+)`, `([\da-z\.-]+)`, and `([a-z\.]{2,6})`. By combining these tokens into groups it allows the substring to be verified before the at symbol `@`, another one before the back slash and period `\.`, and finally one more for the email domain name.

### Bracket Expressions

Bracket expressions are enclosed in square brackets `[]` and will match a specific set of single characters and certain predefined named classes within the square brackets `[]`.

Special characters lose their special meaning inside bracket expressions.

- The right square bracket `]` ends the bracket expression if it is not the first list item. If you would like to make the `]` character a list item you will need to put it first.
- The left square bracket with period `[.` represents the open collating symbol.
- The period with right square bracket `.]` represents the close collating symbol.
- The left square bracket with equal symbol `[=` represents the open equivalence class.
- The equal symbol with right square bracket `=]` represents the close equivalence class.
- The left square bracket with colon symbol `[:` represents the open character class symbol, and should be followed by a valid character class name.
- The colon symbol with right square bracket `:]` represents the close character class symbol.
- The hyphen symbol `-` represents the range if it’s not first or last in a list or the ending point of a range.
- The caret symbol `^` represents the characters not in the list. If you want to make the caret `^` character a list item, place it anywhere but first.

### Greedy and Lazy Match

Quantifiers can be either greeedy or lazy, by default quantifiers are greedy. A greedy quantifier will attempt to match as many characters as possible as it goes through the regex string. A lazy quantifier will attempt to match as few character as it goes through the regex string.

### Boundaries

The `\b` is an anchor like the caret `^` and the dollar sign `$`. It matches a position that is called a `word boundary`. The word boundary match is zero-length.

The following three positions are qualified as word boundaries:

- Before the first character in a string if the first character is a word character.

- After the last character in a string if the last character is a word character.

- Between two characters in a string if one is a word character and the other is not.

### Back-references

Back-references provide a convenient way to identify a repeated character or substring within a string. If the input string contains multiple occurrences of an arbitrary substring, you can match the first occurrence with a capturing group, and then use a backreference to match subsequent occurrences of the substring.

Here are some different types of Back-references:

- Numbered Back-references:

  - A numbered back-reference uses the syntax `\`_number_

    - Where _number_ is the ordinal position of the capturing group in the regular expression.

- Named Back-references:

  - A named back-reference uses the following syntax `\k<`_name_`>`

    - Where name is the name of a capturing group defined in the regular expression pattern.

- Named Numeric Back-references:

  - In a named back-reference with `\k`, name can also be the string representation of a number.
  - If _name_ is the string representation of a \__number_, and no capturing group has that name, `\k<`_name_`>` is the same as the backreference `\`_number_, where _number_ is the ordinal position of the capture.

### Look-ahead and Look-behind

Lookahead and lookbehind referred to as lookaround are useful when we would like to match something depending on the context before or after it.

- Look-ahead allows you look for a character but only if it followed by a specific character.
  - Positive Look-ahead:
    - In this example `X(?=Y)` regex will find `X` and check if there is `Y` immediately after it. If `X` is not before `Y` the potential match is skipped and the serach continues.
  - Negitive Look-ahead:
    - In this example `X(?!Y)` regex will find `X` and check if it is not followed by `Y`. If `X` is followed by `Y` the potential match is skipped and the serach continues.
- Look-behind allows you to look for a character but only if it is behind by a specific character.

  - Positive Look-behind:

    - In this example `(?<=Y)X` regex will find `X` and check if `Y` is immediately before it. If `Y` is not before `X` the potential match is skipped and the serach continues.

  - Negitive Look-behind:
    - In this example `(?<!Y)X` regex will find `X` and check if `Y` is not before it. If `Y` is before `X` the potential match is skipped and the serach continues.

## Author

Blake is a student enrolled in coding bootcamp out of the University of Minnesota to become a full stack web developer. [GitHub](https://github.com/smethersblake).
