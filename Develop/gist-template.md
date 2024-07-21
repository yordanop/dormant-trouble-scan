# HTML tags and Regex

 Regular expressions (regex) are powerful tools for pattern matching in strings. By the end of this tutorial, you will have a clear understanding of each component of the regex and how it works together to identify and capture HTML tags.

## Summary

The regex pattern we'll be dissecting is:


    /^<([a-z]+)([^<]+)*(?:>(.*)<\/\1>|\s+\/>)$/


This pattern matches an HTML tag, including its attributes and inner content. It ensures the tag is correctly formed and captures essential parts such as the tag name, attributes, and content.

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


### Anchors

Anchors are used to specify the position within the string where the match should occur.

    ^

The caret (^) is an anchor that asserts the position at the start of a line. In our regex, it ensures that the match begins right at the start of the string.


    $

The dollar sign ($) is an anchor that asserts the position at the end of a line. In our regex, it ensures that the match ends at the end of the string.

### Quantifiers

    *

The asterisk (*) matches the preceding element zero or more times. 

In our regex:

    ([^<]+)* 

means that the pattern within the parentheses (one or more characters that are not <) can repeat zero or more times.

    +

The plus sign matches the preceding element one or more times. 

In our regex : 

    [a-z]+ 
    
ensures that the tag name consists of one or more lowercase letters.

### OR Operator

    |

The OR operator provides a choice between two alternatives. It matches the pattern before or after the operator. In our regex, 

    (?:>(.*)<\/\1>|\s+\/>) 
    
uses the OR operator to match either the content within the tags or a self-closing tag. This allows the regex to handle both standard and self-closing HTML tags.

### Character Classes

    [a-z]

Character classes allow you to match any one of a set of characters. They are defined by placing the characters to be matched inside square brackets. 
In our regex: 

    [a-z] 

matches any lowercase letter from a to z, ensuring that the tag name is composed of letters only.

### Flags

Regex flags are optional parameters that modify the behavior of the regex. Common flags include:

i for case-insensitive matching.
g for global matching.
m for multi-line matching.
Our regex does not use any flags, but understanding them can be useful for more complex patterns.

### Grouping and Capturing

    ( ... )

Parentheses are used for grouping and capturing parts of the regex match. Grouping allows you to apply quantifiers to a section of the pattern and to use back-references. 
In our regex: 

    ([a-z]+) captures the tag name, 
    ([^<]+)* captures the attributes, and 
    (.*) captures the content between the tags. 
    
These captured groups can be referred to later in the regex using back-references.

### Bracket Expressions

    [^<]

A bracket expression containing a caret as the first character matches any character that is not listed. 

In our regex:  

    [^<] 

matches any character except the opening angle bracket <.

### Greedy and Lazy Match

    *

The asterisk is a greedy quantifier, meaning it tries to match as much as possible. 
In our regex: 

    (.*)

is greedy and captures all characters until the last occurrence of the closing tag.

### Boundaries

    ^ and $

Boundaries are used to anchor the regex pattern to specific positions within the string. The caret matches the start of the line, and the dollar sign matches the end of the line. These boundaries ensure that our regex matches the entire string from start to finish.

### Back-references

    \1

A back-reference matches the same text as most recently matched by the corresponding capturing group. 
In our regex: 

    <\/\1> refers back to ([a-z]+) 
    
ensuring that the closing tag matches the opening tag. This ensures that the HTML tag is properly closed with the same tag name.

### Look-ahead and Look-behind

Look-ahead and look-behind are assertions that match a group of characters only if they are (or are not) followed or preceded by another group of characters. Although not used in our regex, they can be powerful tools in pattern matching. For example:

Positive Look-ahead: (?=...)
Negative Look-ahead: (?!...)
Positive Look-behind: (?<=...)
Negative Look-behind: (?<!...)

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
