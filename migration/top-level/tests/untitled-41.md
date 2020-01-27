# POSIX Extended Regular Expression Syntax \(quick reference\)

This article lays out POSIX Extended Regular Expression syntax implemented by ThousandEyes for page content verification in HTTP Server tests.  For those wanting a more comprehensive article on this regular expression syntax, along with testing and troubleshooting guidelines, please see [this article](https://success.thousandeyes.com/ViewArticle?articleIdParam=kA0E0000000CmnCKAS).

## Single-character expressions

| .  | matches any character  |
| :--- | :--- |
| \[x-y\]  | matches any character found in the range of x-y  |
| \[abcdefg\]  | matches any character found in the bracketed list  |
| \d  | matches any digit character \(0-9\)  |
| \w  | matches any alphanumeric character, including underscore  |
| \s  | matches any whitespace character  |
| \n  | matches a newline character  |
| x\|y  | matches x OR y  |
| \  | escape character  |
| \W  | non-alphanumeric character  |
| \D  | non-digit character  |
| \S  | non-whitespace character  |
| \[^abcdefg\] | matches any character NOT found in the bracketed list |

## Repeaters

| {n} | previous expression matches exactly n times |
| :--- | :--- |
| {n,}  | previous expression matches at least n times |
| {,m} | previous expression matches at most m times |
| {n,m} | previous expression matches between n and m times \(inclusive\)  |
| \* | previous expression matches 0 or more times |
| ?  | previous expression matches 0 or 1 times |
| +  | previous expression matches 1 or more times |

## Patterns

| \( | start of pattern |
| :--- | :--- |
| \) | end of pattern |

## Boundaries

| ^ | beginning of line \(only valid when used at the beginning of a pattern\) |
| :--- | :--- |
| $  | end of line \(only valid when used at the end of a pattern\) |
| \\` | beginning of input \(start of the page\) |
| \' | end of input \(end of the page\) |
| \b | word boundary |

