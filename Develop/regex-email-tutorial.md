# email regular expression walkthrough

A regular expression, also known as a regex, are a series of meta and literal characters (discussed later) that establish the parameters for a search pattern for parsing text. This can be used not just for finding specific strings of characters, or finding and replacing strings. It can even be used in conjunction with typical coding to do such tasks as validating email for a database, such as one found in MySQL or Graphql. While we won't go over how this done, we will examine the regular expression that would be used in such a situation 

## Summary

Briefly summarize the regEx you will be describing and what you will explain. Include a code snippet of the regEx. Replace this text with your summary.

This regEx is used for finding email. There can be many reasons why a user or designer may need to find an email, whether it's creating an account, finding contact information, or something else entirely. However varied a specific email may be, there are certain immutable components that they require, and by using a combination of the meta-characters and literal characters in the regEx below, it can be universally applicable for whatever uses you may have. In this tutorial we'll break down the various parts to explain how the parts work together to find any email.
'/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/'

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Glossary](#glossary)
## Regex Components

### Anchors
Anchors, represented using the '^' symbol and the '$' symbol, don't actually match characters, but instead matches the positioning of characters. In this case, we add the anchor '^' to the beginning and the expression and the '$' to the end so that the regEx doesn't overlap groups or leave portions of an email out.

### Quantifiers
Qualifiers are a group of various meta characters that determine HOW MANY instances of characters, group, or character classes are required to match it. for this regEx, '+' is used to connect the email name to the @ literal character, which is then followed by the provider/service name, and finally the TLD name. Another quantifier, '{}' is used to determine the range of character length. In this specific regEx, it is looking for a character length ranging from 2 to 6 from the character set '[a-z\]'

### Character Sets
A character set, otherwise known as a character class, distinguish between various characters based on what their purpose is, or what they represent. For example, in our regEx, we have the expression '\d' which is used to find numbers or 'digits.' 

### Flags
regEx searches for matches by line. While this specific one won't need one by itself, by add 'g' to the end outside of the expression it will search for matches globally, but without such a flag, this expression will not. 

### Grouping and Capturing
Briefly mentioned under the quantifiers section, this regEx is made of multiple groups. The first group '([a-z0-9_\.-]+)' finds the first section of the email name. for example, if we had an email called 'dilbert@fakeemail.com' this first group would match 'diblert'. The second group '([\da-z\.-]+)' would match the provider 'fakeemail' and the last group, '([a-z\.]{2,6})' would match the TLD 'com'. While ordinarily a '.' is a meta character, the '\' cancels it out, making it read as a literal character.

### Bracket Expressions
While expressions in parenthesis '()' can be backreferenced (which we will cover later), bracket expressions denoted using '[]' cannot. In this regEx, the bracket expression that is part of the first group, '[a-z0-9_\.-]' matches any letter a-z, any numbers '0-9' as well as any of these special characters turned literal characters: '-', '_', and '.' The bracket expression in the second group, '[\da-z\.-]' matches a singular digit from 0-9 like the previous group, as well as any characters from 'a-z', as well as the special character turned literal character '.' Finally, the third bracket expression, '[a-z\.]' doesn't need to find any numbers since it is finding a TLD and thus is only trying to find any characters ranging from 'a-z' as well as the special character turned literal, '.'

### Greedy and Lazy Match
Greedy and Lazy matches are types of quantifiers. Greedy matches try to do as much as they can, and will only match something smaller when it can't find what its looking for in its entirety. Meanwhile, lazy matches does as little as they can, and will only find the minimal amount of matches as it can, unless specified otherwise. This regEx only has greedy quantifiers, specifically '+' which matches as many times as possible/needed, and the second greedy quantifier, '{2,6}' does the same thing, except restricted to the last group. 

## Author
Brendan Ahearn is an aspiring Fullstack Developer specializing in javascript

Find more of my projects at my profile [here](https://github.com/Arcanaut)




