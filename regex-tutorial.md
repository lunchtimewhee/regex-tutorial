# Regex Tutorial -- Matching an Email

There are many different ways that you can write validation into JavaScript, but one of the easiest ways is using "Regular Expressions", or "Regex".

## Summary

Here, we will go over an example Regex for validating email addresses. This is what our Regex expression will ultimately look like -- it looks complicated, but it's not as bad as you think!

```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```

## Table of Contents

- [Anchors](#anchors)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Quantifiers](#quantifiers)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Flags](#flags)
- [Advanced Regex](#advanced-regex)
- [Resources](#resources)
- [Author](#author)

&nbsp;&nbsp;

### Regex Components
The first part is the outside of the Regex -- we use '/' characters to wrap the code, as a Regex is considered a literal. 
```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/
```
&nbsp;&nbsp;

### Anchors
The next parts that wrap our Regex expression are the anchors -- '^' and '$'.

Any Regex in between these two anchor tags will be used in the comparison. 

&nbsp;&nbsp;

### Grouping and Capturing
Regex expressions can be separated into different sections using parentheses (), each with its own rules. In this case, we can see that there are 3 sets of parentheses that would split an email address into 3 parts. name@companyname.domain. 

 
```
Name:
([a-z0-9_\.-]+)
```


```
Company Name: 
([\da-z\.-]+)
```


```
Domain: 
([a-z\.]{2,6})
```

Grouping can actually be split into capturing and non-capturing categories, but for the sake of this tutorial, we will only be looking at the capturing category. By default, grouping is capturing. However, if you would like to make grouping non-capturing, you can add a '?:' phrase at the beginning of an expression inside the parentheses.

&nbsp;&nbsp;

### Bracket Expressions
Bracket expressions are used to create rules within the Regex, denoted by brackets []. Ranges of characters that we want to allow to be matched are put into the brackets. Each character only need to be included once to be used in the match. For example, the bracket expression "[abc]" will match "aaa" or "ba".

Usually, you'll see hyphens "-" used to select groups of letters or numbers. "[a-z]", for example, will include all lower case letters from a to z. For both lower and uppercase letters, you would have to use [a-zA-Z]. Below are a few other examples:

1. [a-zA-Z] — All letters, upper or lower case. 
2. [0-9] — All numbers.
3. [_\.-] — Underscores, hyphens and periods allowed. A backslash "\" is used to capture the ".", as "." is a special character in Regex. 

&nbsp;
Below are the bracket expressions and what they mean for our email example:

```
Name -- Accepts all lowercase letters, all numbers, _, ., -.  
([a-z0-9_\.-])
```


```
Company Name -- Accepts all numbers (\d = [0-9]), all lowercase letters, ., -
([\da-z\.-])
```


```
Domain -- Accepts all lowercase letters, .
([a-z\.]{2,6})
```
&nbsp;&nbsp;

### Character Classes
Character Classes are shorthand ways of denoting a character set in bracket expressions. Earlier we saw that "\d" is the equivalent to "[0-9]", or all numbers. Below are some other examples:

1. \. — Any character except newline character \n
2. \d — Equivalent to [0-9], or all numbers
3. \\w — Equivalent to [A-Za-z0-9_], or all lowercase and uppercase characters, all numbers and _
4. \\s — Matches spaces, tabs and link breaks.

```
Company Name -- Accepts all numbers (\d = [0-9]), all lowercase letters, ., -
([\da-z\.-])
```


&nbsp;&nbsp;

### Quantifiers
Quantifiers determine the limits of the string that your Regex is being compared to, and come AFTER the [] bracket expression. Usually, these are used to indicate the minimum and maximum number of characters allowed.


Below is a list of other symbols used as quantifiers:

1. \* — Matches the pattern zero or more times

2. \+ — Matches the pattern one or more times

3. ? — Matches the pattern zero or one time

4. {} — Curly brackets can provide three different ways to set limits for a match:

&emsp;&emsp;a. { n } — Matches the pattern exactly n number of times

&emsp;&emsp;b. { n, } — Matches the pattern at least n number of times

&emsp;&emsp;c. { n, x } — Matches the pattern from a minimum of n number of times to a maximum of x number of times  

&nbsp;
```
Name -- + means that at least 1 match has to occur (at least one valid character required)  
([a-z0-9_\.-]+)
```


```
Company Name -- + means that at least 1 match has to occur (at least one valid character required) 
([\da-z\.-]+)
```


```
Domain -- {2,6} means that there's a min of 2 characters, max of 6 characters. Ex. .com, .gov
([a-z\.]{2,6})
```

&nbsp;


### Greedy and Lazy Match
Quantifiers by default are Greedy -- This means that they try to match as many of the pattern as possible. In this example, we only want the Regex to match as much as possible. 

```
Domain -- {2,6} means that there's a min of 2 characters, max of 6 characters. Ex. .com, .gov
([a-z\.]{2,6})
```


The other option is Lazy -- add a ? after the quantifier to make the Regex match as few times as possible.

&nbsp;&nbsp;


### Flags
You can actually include a flag AFTER the ending slash "/" in the regex. This flag will allow for certain shorthand searches. The most common ones include: 

1. g — Global -- Test against all possible matches in string.
2. i — Case-insensitive -- Ignore upper and lower case when matching.
3. m — Multi-line -- Any input with line breaks should be treated as having multiple lines.

Example -- If we wanted our email Regex to not worry about case at all:
```
/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/i
```

&nbsp;&nbsp;

### Advanced Regex:
These are more advanged topics that can be utilized in Regexes, but will ultimately not be needed for a simpler email example like the one that we have been working on. If you would like to learn more, you can review MDN Web Docs for more information.

1. Boundaries

2. Back-references

3. Look-ahead and Look-behind

&nbsp;&nbsp;

### Resources
[MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)
[Eloquent JavaScript](https://eloquentjavascript.net/09_regexp.html)


&nbsp;&nbsp;

### Author
Anthony Li
https://github.com/lunchtimewhee

