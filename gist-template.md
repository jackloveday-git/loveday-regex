# Loveday Regex Tutorial
To create a tutorial that explains how a specific regular expression, or regex, functions by breaking down each part of the expression and describing what it does.


## Summary:
Regex is a method of text which lets you search for patterns to verify data input.
```
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
```
* This is a regular expression to match a URL


## Table of Contents:
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


## Regex Components:

### Anchors:
Characters used in Regex Expressions that will let the user match data that begins/ends with these anchors.
- `$`:        Matches to a string that ENDS with the word before this character
- `^`:        Matches ANY string that starts with the word

- Examples:
```
goodbye       Matches ANY string that has the EXACT text 'goodbye'
World$        Matches ANY string ending with 'World'
^Hello        Matches ANY string starting with 'Hello'
```

### Quantifiers:
Characters within our regular expressions that with show how many times a character or classes to be showed in the input.
- `*`:        Matches string that has the 'anterior' followed by a ZERO, or more of the last character
- `+`:        Matches string that has the 'anterior' followed by ONE or more of the last character
- `?`:        Matches string that has the 'atnerior' followed by ZERO or one of the last character
- `{}`:       Matches string that has the 'anterior' followed by how many of the 'n' in the brackets of the last character in the string
- `()*`:      Matches string that has ANY 'anterior' characters followed by zero or more copies of the string within the brackets

- Examples:
```
xyz*          Matches string that has 'xy' followed by ZERO or more 'z' characters
xyz?          Matches string that has 'xy' followed by ZERO or more 'z' characters
xyz+          Matches string that has 'xy' followed by ONE or more 'z' characters
xyz{2}        ''    ''    ''    ''    ''   followed by TWO 'z' characters
xyz{2,}       ''    ''    ''    ''    ''   followed by TWO or MORE 'z' characters
x(yz)*        ''    ''    ''    ''    'x'  followed by ZERO or MORE copies of sequence 'yz'
```

### OR Operator:
OR Operators match on a choice of regular expressions.
If you put the character for the 'Alternation Operator' between any TWO characters in the regular expression, the result matches to the union that those two characters match.

- `(|)`:      Matches string that has ANY 'anterior' characters followed by the characters on the left or right of the bar
- `[]`:       Matches string that has ANY 'anterior' characters without any characters within the brackets

- Examples:
```
x(y|z)        Matches string that has 'x' followed by 'y', or 'z' (and captures y or z)
x[yz]         Matches string that has 'x', but without capturing 'y' or 'z'
```

### Character Classes:
Uses Classes with our ReGex Engine to match only ONE out of serveral specific characters.
- `\d`:       Matches a single character that is a digit
- `\w`:       Matches a word character (any alphanumeric character plus underscore)
- `\s`:       Matches a whitespace character (including tabs and line brakes)
- `.`:        Matches any character

- Examples:
```
.           Matches any character
\d          Matches single any digit 0-9
\w          Matches single any character that is a-z
\s          Matches ` `
\D          Matches single non-digit character
\W          Matches single any non-character that is a-z
\S          Matches single non ` `
```

### Flags:
Optional parameters that we can add to an expression to make it search differently. 
Each flag is declared by a single 'alpha character', and serves different purposes in modifying the expression's searching behavior.

- `g`:      Global, won't return after the first match, which restarts any subsequest searches from the end of the previous match
- `m`:      Multi-line, when enabled, Anchors will match the start and end of a line, instead of the whole string
- `i`:      Insensitive, makes the whole expression 'case-insensitive'

- Examples:
```
/Hello/g    Matches all 'Hello' in the test
/Hello/m    Matches beginning, and ending, of each line with 'Hello', instead of the whole string 'Hello' by itself
/Hello/i    Matches all 'hello', and ignores case variation (hElLo, hellO, etc)
```

### Grouping and Capturing:
Unifies a pattern or string that is matched in a full block.

- `()`:     Parentheses creates a 'capture group'
- `(?:)`:   Using `?:` disables the capturing group
- `(?<>)`:  Using `?<>` puts a name to the group

- Examples:
```
x(yz)           parentheses create a capturing group with value yz
x(?:yz)*        using ?: we disable the capturing group
x(?<bar>yz)     using ?<bar> we put a name to the group
```

### Bracket Expressions:
Are characters enclosed by a bracket `[]` matching ANY single character within them.

- `[]`:         Matching ANY single character within the brackets
- `[]%`:        Matching string inside the brackets before the `%`
- `[^]`:        Matching ANY string that does not gave a letter from within the brackets

- Examples:
```
[xyz]           Matches a string that etiher has 'x', or 'x y', or 'x z'
[x-y]           Similar to case above
[u-zU-Z0-9]     A string that represents a SINGLE hexadecimal digit, does not care about case
[0-9]%          A string that has a character in range of 0-9, before the %
[^a-zA-Z]       A string that has a letter from 'a to z', or from 'A to Z'
```

### Greedy and Lazy Match:
Quantifiers that expand the match as far as possible through the text. 

- `* + {}`:     Any one of these character can be used as a 'Quantifier'

- Examples:
```
<.+?>           Matches ANY character that is included ONE, or MORE, time(s) inside `<` and `>`, then expands
<[^<>]+>        Matches ANY character, and expects `<` or `>` ONE, or MORE, time(s) included inside `<` and `>`
```

### Boundaries:
Not actual characters, but are the places BETWEEN characters. 
A Boundary should be considered as a 'border' between any adjacent characters.

- `\b`:         Position that bounds a word, it denotes a place between a word and non-word character
- `\B`:         Exact opposite of a word boundary, ignoring `\b`, and will match any spot a boundry does not
- `*`:          Match between a word and word character, as well as non-words and characters

- Examples:
```
`Hello World` has 12 total Boundaries with 8 Word Boundaries as seen below:
|H|e|l|l|o| |W|o|r|l|d|
N W W W W N N W W W W N:  'N' = Nonword & 'W' = Word Boundaries

\bxyz\b         Matches a "whole words only search" for string `xyz`
\Bxyz\B         Matches ONLY if the pattern is fully surrounded by word characters i.e. `txyzt`
```

### Back-references:
Using Grouping, you may capture the group which is saved in memory for later use.
'Backreferencing' is the refernce of a captured match, saved in memory.

Examples:
```
([xyz])\1              Using \1 to match the same text that was matched by the first capturing group
([uwx])([yz])\2\1      We can use \2 to identify the same text that was matched by the second(+) capturing group
(?<bar>[xzy])\k<bar>   We put the bar to the group and we reference it later (\k<foo>). The result is the same of the first regex
```

### Look-ahead and Look-behind:
Are `start and end` zero length assertions, but they will match characters then ends the match, and returns only the result.

```
h(?=t)       Matches 'h' only if is followed by 't', but 't' will not be part of the match
(?<=t)h      Matches 'h' only if is preceded by an 't', but 't' will not be part of the match

NEGATION OPERATOR

h(?!t)       Matches 'h' only if is not followed by 't', but 't' will be cut off
(?<!t)h      Matches 'h' only if is not preceded by an 't', but 't' will be cut off
```

## Author:

Name: Jack Loveday
Github: [GitHub Profile](https://github.com/jackloveday-git)
