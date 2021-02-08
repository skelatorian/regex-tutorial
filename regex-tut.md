# Regex Tutorial

This tutorial explains how a specific regular expression, or regex, functions by breaking down each part of the expression and describing what it does.

## Summary

A regex, which is short for regular expression, is a sequence of characters that defines a specific search pattern. When included in code or search algorithms, regular expressions can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. They are also frequently used to validate input.

For example, the following regular expression can be used to verify that user input is a valid email address:

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Each component of this regex has a unique responsibility to make sure that a user enters an email address that begins with an unspecified number of characters preceding the @ symbol, followed by a domain.



The table of contents below will explain what each section of this code does and more.

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

* `^and$`	-^start / $end of the string
    * `^` Matches the beginning of the string, or the beginning of a line if the multiline flag (m) is enabled.
    * `$` Matches the end of the string, or the end of a line if the multiline flag (m) is enabled.

* `\b\B`	-word, not-word boundary
    * `\b` Matches a word boundary position between a word character and non-word character or position (start / end of string).
    * `\B` Matches any position that is not a word boundary.
    ** See Boundaries for more detailed information
    
 ### Quantifiers

A quantifier is appended to a character (or a character class, or a [...] set etc) and specifies how many we need.

* `a*a+a?`	-0 or more, 1 or more, 0 or 1
    * "+" Matches 1 or more of the preceding token.
    * "*" Matches 0 or more of the preceding token.
    * "?" Matches 0 or 1 of the preceding token, effectively making it optional.

* `a{5}a{2,}`   -Looks for exactly five, two or more
* `{2,6}`  	    -Forces the input of characters between two & six characters long.
* `a+?a{2,}?`	  -Match as few as possible
* `ab|cd`	      -Match with ab or cd

### OR Operator

* `|` The logical OR (||) operator (logical disjunction) for a set of operands is true if and only if one or more of its operands is true. It is typically used with Boolean (logical) values. When it is, it returns a Boolean value. However, the || operator actually returns the value of one of the specified operands, so if this operator is used with non-Boolean values, it will return a non-Boolean value.


### Character Classes

With a “character class”, also called “character set”, you can tell the regex engine to match only one out of several characters. Simply place the characters you want to match between square brackets. If you want to match an a or an e, use [ae]. You could use this in gr[ae]y to match either gray or grey. A character class matches only a single character. gr[ae]y does not match graay, graey or any such thing. The order of the characters inside a character class does not matter. The results are identical.



* `[ABC]` Characters inside brackets will match any character in the set.
* `[^ABC]` Adding a caret will match any character that is not in the set.
* `[A-Z]` Add a dash between two characters will select a Range.
* `.` Will Match any characters expect linebreaks. Its like a wildcard and will accpet any input.
* `[\s\S]` A character set that can be used to match any character, including line breaks, without the dotall flag. An alternative is [^] carrot in brackets, but it is not supported in all browsers.
* `\w` Matches any word character (alphanumeric & underscore). Only matches low-ascii characters (no accented or non-roman characters).
* `\W` Matches any character that is not a word character (alphanumeric & underscore).
* `\d` Matches any digit character (0-9)
* `\p` Matches a character in the specified unicode category.


### Flags

Expression flags changes how the  expression is interpreted.
Flags will follow the closing forward slash of the expression.


* `i` (Insensitive) Makes the whole expression case-insensitive
* `g` (Global) Does not return after the first match, restarting the subsequent searches from the end of the previous match.
* `m` (Multiline flag) when enabled ^ and $ will match the start and end of a line, instead of the whole string.


### Grouping and Capturing

This operator is very useful when we need to extract information from strings or data using your preferred programming language. Any multiple occurrences captured by several groups will be exposed in the form of a classical array: we will access their values specifying using an index on the result of the match.

* `(ABC)` Capturing groups multiple tokens together to create a capture group for extracting a set of substring or using a backreference.
* `(?<name>ABC)` Name for capturing group captures groups of a specific name.
* `\1` A numeric reference.
* `(?:ABC)` Groups multiple tokens together without creating a capture group.


### Bracket Expressions

The main purpose of bracket expressions is that they adapt to the user’s or application’s locale. A locale is a collection of rules and settings that describe language and cultural conventions, like sort order, date format, etc.



### Greedy and Lazy Match

The quantifiers ( * + {}) are greedy operators, so they expand the match as far as they can through the provided text.

* 'Greedy'  
    A Greedy quantifier tells the engine to match as many instances of its quantified token or subpattern as possible. This behavior is called greedy.

* 'Lazy' It means: “repeat minimal number of times”.
    A lazy quantifier tells the engine to match as few of the quantified tokens as needed. As you'll see in the table below, a regular quantifier is made lazy by appending a ? question mark to it.

Visit https://www.rexegg.com/regex-quantifiers.html for more information.

### Boundaries

The `\b` represents an anchor like caret (it is similar to $ and ^) matching positions where one side is a word character (like \w) and the other side is not a word character (for instance it may be the beginning of the string or a space character.

Characters that are matched by the short-hand character class `\w` are the characters that are treated as word characters by word boundaries.

It comes with its negation, `\B` This matches all positions where \b doesn’t match and could be if you'd want to find a search via patterns.

### Back-references

Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag.


For Example: `<([A-Z][0-9]*)\b[^>]*>.*?</\1>` This regex contains only one pair of parentheses, which capture the string matched by `[A-Z][0-9]*`. This is the opening HTML tag. The backreference `\1` references the first capturing group. `\1` matches the exact same text that was matched by the first capturing group. The `/` before it is a literal character. It is simply the forward slash in the closing HTML tag that we are trying to match.

### Look-ahead and Look-behind

* `(?=ABC)` is a postive lookahead and it matches a group after the main expression without including it in the result.
* `(?!ABC)` is a negitive lookahead and it specifies a group that can not match after the main expression (if it matches, the result is discarded)

* `(?<=ABC>)` is a postive lookbehind and matches a group before the main expression without including it in the result.
* `(?<!ABC)` is a negitive lookbehind and Specifies a group that can not match before the main expression (if it matches, the result is discarded).

Lookaheads and lookbehinds forces the main expressions to be what you have defined it as. Without it being exactly what it is it will not be accepted as a valid input.

Visit https://www.regular-expressions.info/lookaround.html for more information.

## Author

Lynh Le - Junior Full Stack Developer

My Github: https://github.com/Skelatorian