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
- lookaheads: parts that ensure that something specified does or does not occur later in the password, e.g. (?=)
- character classes: groups of characters, e.g. [a-z]
- quantifier: specifies a number of times something must appear, e.g. {8,256}

As you read the explanation below, consider the expression from two angles:
- it may contain only certain types characters, e.g. it cannot contain a space or newline
- it must contain certain types of characters, e.g. it must contain a digit

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Character Class and Quantifier](#character-class-and-quantifier)
- [Look-ahead](#look-ahead)

## Regex Components

### Anchors
^ beginning of the string under consideration
$ end of the string under consideration

The expression begins with ^ and ends with $. This concerns what the password cannot have: it may not have anything outside what is specified in the expression. This means that the expression will only match an entire string, i.e. if the expression matched only numbers
- it would match 12345 
- it would not match the numeric portions of ABC12345 or 12345PDQ

### Quantifiers

This expression users two Quantifiers to specific the length of the password.
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

The major Character Class in this expression specifies the characters that MAY be in the password, without saying what MUST be in the password
[a-zA-Z\d!@#$%^&*()_-+=:;<,>.?/~]
specifies that the password must be made up of any combination of lowercase, uppercase, digit, and special characters. With only this Character Class, the following would match
- only numbers
- only numbers and lowercase letters

For how to specify what the password MUST contain, refer to [Look-ahead](#look-ahead)

### Character Class and Quantifier
Combining a Character Class and a Quantifier is a way to match a specific number of characters

[a-zA-Z\d!@#$%^&*()_-+=:;<,>.?/~]{8,256}

means: at least 8, and no more than 256, characters which are any mix of uppercase, lowercase, special, and numeric characters. 

### Look-ahead

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
