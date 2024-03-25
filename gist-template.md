# REGEX Tutorial 

Fundamentals Regex validation for Dates

## Summary

This is a brief tutorial on the use of Regex. The sequence of mathcing a data in the format of YYYY-MM-DD ^\d{4}\-(0?[1-9]|1[012])\-(0?[1-9]|[12][0-9]|3[01])$

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

* The '^' symbol is an anchor that denotes the start of the string. 
* The '$' symbol is an anchor that denotes the end of the string.
* The use of both anchors (^...$) are used to test whether or not a string fully matches the pattern


### Quantifiers

Quantifiers in regular expressions specify how many instances of a character or group should be matched. They control the repetition of the preceding element. In the expression above the '{4} is used to match the four instances of '\d' which represents digit. The '?' matches zero or one instance of the preceding element. It makes the preceding element optioonal. 
For example the '0?' matches zero or one instance fo the digit 0. It's used to allow months or days with a leading zero. 
For example: 
* '0?[1-9]' allows the numbers 1-9 or 01-09, '1[012]' allows the numbers 10-12 for the month
* '0?[1-9]' alllows the numbers 1-9 or 01-09, '[12][0-9]' alllows the numbers 10-29, and '3[01]' alllows 30-31 for the days


### OR Operator

The '|' acts as an OR Operator allowing mulitple alternatives to be specified. It  matches either the expression on its left or right.
For example:
* '(0?[1-9]|1[012])' allows either the dates the left side which woulld include the numbers 1-9 or the right which would include 10-12.

### Character Classes

Character classes distinguish kinds of characters such as, for example, distinguishing between letters and digits.
*  \d: Matches any digit from 0 to 9. It is a shorthand for the character class [0-9].
* 0-9: Represents a range of characters from '0' to '9'. It matches any single digit.
* [01]: Matches either '0' or '1'. It's used to represent the first digit of the month (either 0 for January or 1 for the months from February to December).
* [12]: Matches either '1' or '2'. It's used to represent the first digit of the day (either 1 or 2).

### Grouping and Capturing

Grouping and capturing are fundamental concepts in regular expressions that involve enclosing parts of a pattern in parentheses () to create groups. These groups serve several purposes:

1. Grouping: Parentheses are used to group elements together within a regular expression. This is particularly useful when applying quantifiers or alternation (|) to a group of characters. It allows you to specify the scope of these operators.

2. Capturing: Groups also serve as capture groups, meaning that when a match is found for the entire regular expression, the substrings that match the individual groups are captured or extracted. These captured substrings can be referenced later for further processing or replacement.

In the regex expression above:
* The (0?[1-9]|1[012]): This is a group that matches the month part of a date. It consists of two alternatives separated by |.
* (0?[1-9]|[12][0-9]|3[01]): This is a group that matches the day part of a date. It also consists of three alternatives separated by |.
* In this regex, the groups (0?[1-9]|1[012]) and (0?[1-9]|[12][0-9]|3[01]) are capturing groups. If a string matches the entire regex, these groups will capture the month and day parts of the date respectively. This capturing allows you to access these specific parts of the date for further processing or validation.

### Bracket Expressions

Bracket Expressions, denoted by square brackets [...], allow you to specify a set of characters from which one character must match. For instance, [12][0-9] will match 10-19 and 20-29.

### Greedy and Lazy Match
1. Greedy: As Many As Possible (longest match)
By default, a quantifier tells the engine to match as many instances of its quantified token or subpattern as possible. This behavior is called greedy.

2. Lazy: As Few As Possible (shortest match)
In contrast to the standard greedy quantifier, which eats up as many instances of the quantified token as possible, a lazy (sometimes called reluctant) quantifier tells the engine to match as few of the quantified tokens as needed. As you'll see in the table below, a regular quantifier is made lazy by appending a ? question mark to it.

For Example:
The '0?[1-9]' would allow for the numbers with or with a '0' in front of it. For March you could have '03'  or '3'. With the '?' it alllows 
### Boundaries

The metacharacter \b is an anchor like the caret and the dollar sign. It matches at a position that is called a “word boundary”. This match is zero-length.  There are no boundaries in this expression.

### Back-references


Back-references allow you to refer back to previously captured groups within a regular expression. They are typically used in scenarios where you want to match a repeated occurrence of a specific pattern or to enforce consistency in the matched text. There are no back references in this expression. If you wanted to use back-referencing it would look like this: 
'^(\d{4})\-(0?[1-9]|1[012])\-(0?[1-9]|[12][0-9]|3[01])\s+\1\-\2\-\3'
In this modified regular expression, \1, \2, and \3 refer back to the first, second, and third captured groups respectively. This pattern would match strings like "2024-03-25 2024-03-25", ensuring that the same year, month, and day are repeated.


### Look-ahead and Look-behind
 
Lookahead and lookbehind are types of capture groups that traverse text until a specific pattern occurs. There are neither in the example above

## Author

Matt Cook is a current student at OSU full-stack Web Developer Bootcamp Program. Github: [https://github.com/mcook2323]