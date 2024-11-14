# RegEx

## Regular Expression Patterns

Brackets are used to find a range of characters:

| Expression | Description                                                                                      |
|------------|--------------------------------------------------------------------------------------------------|
| [abc]      | Find one character from the options between the brackets : Matches either an a, b or c character |
| [^abc]     | Find one character NOT between the brackets : Matches any character except for an a, b or c      |
| [0-9]      | Find one character from the range 0 to 9                                                         |
| [^a-z]     | Matches any characters except those in the range a-z.                                            |
| [a-zA-Z]   | Matches any characters between a-z or A-Z. You can combine as much as you please.                |
| (?:...)    | Match everything enclosed                                                                        |
| (...)      | Capture everything enclosed                                                                      |

## Metacharacters

Metacharacters are characters with a special meaning:

| Metacharacter | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------| 
| \|            | Find a match for any one of the patterns separated by \| as in: cat\|dog\|fish                                                      |
| .             | Find just one instance of any character : Matches any character other than newline (or including line terminators with the /s flag) |
| ^             | Finds a match as the beginning of a string as in: ^Hello                                                                            |
| $             | Finds a match at the end of the string as in: World$                                                                                |
| \d            | Find a digit                                                                                                                        |
| \D            | Matches anything other than a decimal/digit.                                                                                        |
| \s            | Find a whitespace character                                                                                                         |
| \S            | Matches anything other than a space, tab or newline.                                                                                |
| \b            | Find a match at the beginning of a word like this: \bWORD, or at the end of a word like this: WORD\b                                |
| \uxxxx        | Find the Unicode character specified by the hexadecimal number xxxx                                                                 |
| \w            | Matches any letter, digit or underscore. Equivalent to [a-zA-Z0-9_].                                                                |
| \W            | Matches anything other than a letter, digit or underscore. Equivalent to [^a-zA-Z0-9_]                                              |

## Quantifiers

Quantifiers define quantities:

| Quantifier | Description                                                    |
|------------|----------------------------------------------------------------| 
| n+         | Matches any string that contains at least one n                |
| n*         | Matches any string that contains zero or more occurrences of n |
| n?         | Matches any string that contains zero or one occurrences of n  |
| n{x}       | Matches any string that contains a sequence of X n's           |
| n{x,y}     | Matches any string that contains a sequence of X to Y n's      |
| n{x,}      | Matches any string that contains a sequence of at least X n's  |

## References

https://www.w3schools.com/java/java_regex.asp
