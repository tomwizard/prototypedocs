# POSIX Extended Regular Expression Syntax

ThousandEyes implements the POSIX Extended Regular Expression syntax implemented by Unix utilities such as awk and egrep for content-checking in ThousandEyes HTTP Server tests and other Web Layer tests which use the HTTP Server view. The instructions and examples below are provided to help users create regular expressions to use the Verify Content feature of HTTP Server tests.

For more in-depth coverage of the POSIX extended regular expression syntax implemented by ThousandEyes, consult one of the many [online](http://www.regular-expressions.info/posix.html) [references](http://www.boost.org/doc/libs/1_64_0/libs/regex/doc/html/boost_regex/syntax/basic_extended.html).

## What is a regular expression?

A regular expression is a pattern which is evaluated against a target. The evaluation of a regular expression returns either a match or no match.

Regular expressions contain literals, special operators, and boundaries, which are combined to make patterns. We'll run through a quick synopsis and example of each below.

## Single Characters

Standard characters match themselves \(literal matches\).  Additionally, there are special characters for matching digits, words, and special characters. You can use a list of characters to match, or specify a class of characters. Each expression will match exactly one time, unless a repeater is used following the pattern.

| a | matches the letter a |
| :--- | :--- |
| .  | matches any character |
| \[a-g\]  | matches any character found in the range of a-g |
| \[abcdefg\]  | matches any character found in the bracketed list |
| \d  | matches any digit character, equivalent to \[0-9\] |
| \w  | matches any alphanumeric character, including underscore |
| \s  | matches any whitespace character |
| \n  | matches a newline character |
| x\|y  | matches x OR y |
| \  | escape character, used to match literally special character |
| \W  | non-alphanumeric character |
| \D  | non-digit character |
| \S  | non-whitespace character |
| \[^abcdefg\] | matches any character NOT found in the bracketed list |

## Patterns

A pattern is a group of characters.  A simple pattern can be a single character or a character class, along with special operators, such as repeaters or alternates. The following examples show some of these simple patterns:

| a{5} | matches any sequence of the letter a repeated 5 times |
| :--- | :--- |
| \d{8}  | matches any series of 8 consecutive digits. |
| ab\|cde | matches a sequence containing abde or acde, but not abcde |

Patterns can be grouped or nested using parentheses, and can contain repeaters, alternates or negation, or tied by to a boundary by an anchor:

| last\supdated\s\d{8} | Matches the text "last updated \#\#\#\#\#\#\#\#" |
| :--- | :--- |
| \b\(\(\d{1,3}\)\.?\){4} | matches any series of 3 groups of digits separated by . characters |
| ^\s\*\(\w+\s+\)+\w\s\*$ | matches any full line where there are 2 or more words separated by spaces |

## Special Operators

### Special Characters

The following characters are special within regular expressions:

```text
.[]{}()\*+?|^$
```

Matching these characters literally requires escaping using the backslash character. For example, the . \(dot\) character matches any character, by default. To search for a literal dot character it must be escaped:

```text
\.
```

Similarly, to search for a backslash character, specify two consecutive backslash characters \(\\\) in your expression.

### Repeaters

Any pattern within a regular expression can be repeated. There are several types of repeat options:

| {n} | previous expression matches exactly n times |
| :--- | :--- |
| {n,}  | previous expression matches at least n times |
| {,m} | previous expression matches at most m times |
| {n,m} | previous expression matches between n and m times \(inclusive\)  |
| \* | previous expression matches 0 or more times, equivalent to {0,} |
| ?  | previous expression matches 0 or 1 times, equivalent to {0,1} |
| +  | previous expression matches 1 or more times, equivalent to {1,} |

### Negation

A match can be created by not matching a list of characters \(for example, \[A-Za-z\]\). Negate the characters inside the list by using a ^ \(caret\) character before the list, such as:

```text
[^A-Za-z]
```

The above expression will match any character not in the list of alphabetic characters \(upper- and lower-case\).

### Alternation

Alternation refers to using OR logic. To alternate between two sets of characters, use the '\|' \(pipe\) character.

### Boundaries and Anchors

There are two types of boundaries which can be specified in a regular expression: line and buffer boundaries.

**Buffer \(Input\) boundary**

A buffer boundary refers to the entire content retrieved - ie, the entire page retrieved during an HTTP server test.

| \\` | Matches at the start of the input \(page\) |
| :--- | :--- |
| \'  | matches at the end of the input \(page\) |
| \A | Matches at the start of the input \(equivalent to \\`\) |
| \z | Matches at the end of the input \(equivalent to \'\) |
| \Z | matches at the end of the input, with newlines ignored \(equivalent to \n\*\z\) |

**Line boundary**

A line boundary refers to content found on an individual line of input - on most systems, a line boundary is marked by a newline character found within the input. When working with line boundaries, if you're only interested in a line that matches some exact text, use the caret \(^\) character to specify the beginning of a line, and the dollar sign \($\) character to specify the end of a line.

| ^ | Matches at the start of a line found in input. |
| :--- | :--- |
| $  | Matches at the end of a line found in input. |

**Word boundary**

\b matches a word boundary \(the beginning and end of a word\).

## Unicode characters

 Web pages utilizing Unicode characters typically use UTF-8 encoding. UTF-8 encodes characters using strings of between one and four bytes. To match the a UTF-8 encoded character, you need to match the byte representation of the character. For example, the Unicode character ž is UTF-8 encoded as the two-byte sequence C5 BE. To match it with a regular expression, use \xC5\xBE

To find a byte representation of a character, check a [UTF-8 character table](http://www.fileformat.info/info/charset/UTF-8/list.htm) or an [online converter](https://r12a.github.io/apps/conversion/). Or find a [character](http://www.ltg.ed.ac.uk/~richard/utf-8.cgi?mode=bytes) from a byte representation.

## Operator precedence

Who remembers the _BEDMAS_ acronym from 8th grade math class, signifying order of operations in basic arithmetic? \(_Bracket, Exponent, Division, Multiplication, Addition, Subtraction_\). Yes, as with most computing technology, we need to be aware of order of operations, aka operator precedence.

| Operator description | Operator symbol\(s\) |
| :--- | :--- |
| Escaped characters |  \ |
| Bracketed character set | \[ \] |
| Grouping | \( \) |
| Extended regex duplication |  \* + ? {m,n} |
| Concatenation | no operator; any two adjacent regular expressions |
| Anchoring |  ^ $ |
| Alternation | \| |

## Things to keep in mind

### Case Sensitivity

Regular expressions are case-sensitive. "This is a Test" is not equivalent to "this is a test".

### HTML markup

Because a ThousandEyes Web Layer test is reading content from web servers, be aware of any HTML markup in the target you're attempting to match with the regular expression. Use the View Source option in your browser to check the content for HTML characters.  For example, the string:

foo bar

could be represented by the HTML:

foo&nbsp;bar

which would NOT match the following regular expressions:

foo bar  
​foo.bar  
foo\sbar

### Expression testing

We strongly recommend validating your regular expression prior to creating your test, particularly if assigning a content Alert Rule to the test.

* Use an online regular expression validator such as [Regular Expressions 101](https://regex101.com/) or [other validators](http://regex.larsolavtorvik.com/#posix). 
* If using linux or a Mac, try retrieving the web page using the curl command, and piping the page content to egrep:  
  

  ```text
  $ curl -s target_web_page_URL | egrep 'pattern'
  ```

  
   If the commands display output, then lines matching the query will be returned. if no output was displayed, then there was no match.

* A [sample page](http://www.columbia.edu/~fdc/utf8/) of UTF-8 encoded characters can be helpful for testing.

