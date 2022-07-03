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

### Quantifiers

A quantifier is a repitition operator. A quantifier lets the system know to match the preceding token a set number of times. The quantifier can be considered a lazy quantifier or a greedy quantifier. For more about lazy or greedy quantifiers please read [Greedy and Lazy Match](#greedy-and-lazy-match).

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

The plus symbol `+` matches one or more of the preceding tokens. In this example it will attempt to match `[a-z0-9_\.-]`. In regex if you have `[a-z]` then it matches any lowercase letter, `[0-9]` matches any digit, and `[_\.-]`matches the special charaters underscore, backslash, period, and hyphen. So in our example we are matching any lowercase letter, digit, and the special charaters underscore, backslash, period, and hyphen.

The two numbers within the curly brackets `{2,6}` will match a range of characters from two to six from the previous token. In this example it will match between 2 and 6 of the characters `[a-z\.]`. If we had only one number in the curly bracket like this `{2}` it would match exactly two characters. If we had a comma `,` and not a second number `{2,}` this indecates a match of 2 or more.

Other examples of quantifiers which are not included in this example are:

- The question mark `?`. This will match zero or one of the proceding token. This makes the token optional and makes the quantifier lazy.
- The asterisk `*`. This will match zero or more of the proceding token.

### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
