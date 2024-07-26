# Password Complexity RegEx

This gist explains the use of a regular expression to implement a common password complexity requirement
- minimum length of 8 characters
- at least one uppercase character
- at least one lowercase character
- at least one number
- at least one "special" character, such as #,$,%

## Summary

Behold, the regular expression, in its complete and inscrutable glory!
^(?=.*[A-Z])(?=.*[a-z])(?=.*\d)(?=.*[.!#])[a-zA-Z\d.!#]{8,256}$

This expression has the following parts:
- beginning and ending anchors, e.g ^ and $
- lookaheads: parts that ensure that something specified does or does not occur later in the string, e.g. (?=)
- character classes: groups of characters, e.g. [a-z]
- quantifier: specifies a number of times something must appear, e.g. {8,256}

Consider the expression from two angles:
- it must have certain aspects
- it may not contain characters other than what is specified

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
- [Look-ahead](#look-ahead)

## Regex Components

### Anchors
^ beginning of the string
$ end of the string

The expression begins with ^ and ends with $. This concerns what the string cannot have: it may not have anything that doesn't match what is specified in the expression. This means that the expression will only match an entire string, i.e. if the expression matched only numbers, it would 12345 and would not match the numeric portions of A12345 or 12345Q.

### Quantifiers

This expression users two Quantifiers. 
- The number before the comma means "at least this many" of what came before the quantifier"
- The number after the comma means "no more than this many" of what came before the quantifier"
- {8,256} the complete quantifier means "at least 8 and no more than 256 of what came before the quantifier"

As for "what came before the quantifier, read on!

### Character Classes
Characters between square brackets are Character Classes, e.g. [a-z].
Character classes can match specific characters, e.g. [aeiou] would match any vowel
Our expression doesn't care which individual characters are used. Instead, it matches the types of characters exemplified in the following character classes
- [a-z] a lowercase character
- [A-Z] an uppercase character
- [!@#$%^&*()_-+=:;<,>.?/~] an assortment of special characters
- \d or 0-9 any digit
- [a-z\d] a combination of character types can make up a single Character Class, i.e. "a character that matches anything in the brackets"

The major Character Class in this expression specifies the characters that MAY be in the string, without saying what MUST be in the string
[a-zA-Z\d.!#]
specifies that the string must be made up of any combination of lowercase, uppercase, digit, and special characters. With only this Character Class, the following would match
- only numbers
- only numbers and lowercase letters

For how to specify what the string MUST contain, refer to [Look-ahead](#look-ahead)

### Character Class + Quantifier
Combining a Character Class and a Quantifier is a way to match a specific number of characters. In this expression

[a-zA-Z\d.!#]{8,256}

means: at least 8 and no more than 256 the characters in the brackets, which include uppercase, lowercase, special, and numeric characters. This 

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
