---
layout: post
title: Lab 4 - Cleaning Data
---

When we [looked at spreadsheets last week](https://f20idh.ryancordell.org/2020/09/22/Data-and-Metadata/), we very quickly realized how messy historical datasets can be, and we began to think about the potential benefits—and potential peril—of "cleaning" data. If we want to analyze data in aggregate, we may want to regularize some categories or correct historical errors in data collection. Katie Rawson and Trevor Muñoz helpfully [complicate this impulse](https://dhdebates.gc.cuny.edu/read/untitled-f2acf72c-a469-49d8-be35-67f9ac1e3a60/section/07154de9-4903-428e-9c61-7a92a6f22e51), and so today while we learn one strategy for cleaning data, we'll also talk about how to make the decision: to clean or not to clean.

We will be learning about Regular Expressions today using the online resource [RegEx 101](https://regex101.com/), which allows you to test expressions and breaks down precisely what they're doing in the Explanation and Match Information panels.

### Helpful RegEx Resources

1. Doug Knox's ["Understanding Regular Expressions"](http://programminghistorian.org/lessons/understanding-regular-expressions) tutorial at the Programming Historian provides a nice introduction into the basics of RegEx for cleaning historical data.
2. This [Regular Expressions Quick Start](http://www.regular-expressions.info/quickstart.html) gives a useful overview of the core RegEx you'll need for today's work, and the larger resource delves into details for the future.
3. Once you understand the basics of RegEx matching, this [cheat sheet](http://web.mit.edu/hackl/www/lab/turkshop/slides/regex-cheatsheet.pdf) may help you recall precisely the characters you need for particular patterns. 

### What are Regular Expressions?

In brief, regular expressions (RegEx) provide a way to abstractly describe the structure of texts. Using RegEx, you can specify patterns that will allow you to quickly make changes across a dataset, rather than correcting data line by line. Regex is not tied to a particular tool or platform. You can use regex in most programming languages, as well as in the "search and replace" functions of many spreadsheet or database applications. In other words, having a general understanding of regex is a portable skill that could prove useful in a variety of ways as you move into DH work.

So what does it mean to "abstractly describe the structure of texts?" Well, let's say I have a spreadsheet full of email addresses from different domains, providers, etc. (e.g. r.cordell@northeastern.edu, r.cordell@neu.edu, rccordell@gmail.com). We can read each of these and recognize them as email addresses, but we might also look across them to think about what formal textual pattern constitutes an email address: 

1. a series of upper- and/or lower-case letters, digits, or symbols (from a set of allowed symbols);
2. An `@` symbol
3. a series of upper- and/or lower-case letters, digits, of symbols
4. A period
5. a series of three letters

In fact this only describes US-based email addresses, as those from other countries can have longer suffixes (e.g. `.co.uk`), but this gives you a sense of how you might outline the abstract structure of text strings that we would recognize as email address. In RegEx you might search the following to find email addresses: 

`
([A-Za-z0-9._%+-]+)@([A-Za-z0-9-]+)\.([A-Za-z]{2,4})
`

To understand what this is doing, let's use [Regular Expressions 101](https://regex101.com/). Type an email address or two into the "Test String" box and then copy and paste that RegEx above into the regular expression box. Did it work, or not? We will walk through how this matching happens and troubleshoot any that don't work together. We'll also experiment with other RegEx that would have accomplished the same task.

### A Note on Using RegEx

I don't use RegEx everyday. I don't have its intricacies memorized. Typically I will use RegEx when faced with a problem that requires me to standardize some aspect of a dataset to solve. When I encounter those problems, however, I typically need to refer to a RegEx guide to remind myself precisely what symbols translate to what textual patterns. Which is to say: you don't need to memorize RegEx syntax in order to find them useful. What's most essential is that you are able to identify what kinds of problems RegEx might help you work through. 

### Cleaning Data

In the next section, we will be thinking about how to approach cleaning a dataset using RegEx. We will focus on the `publish_places` field from a spreadsheet of book titles, and move on to some values in the crew lists data we saw last week. To start, however, let's just paste the values below into the "Text String" box at [Regular Expressions 101](https://regex101.com/). 

`
[Chanhassen, MN]
Washington [D.C.]
San Francisco, Calif
Paramus, N.J
[Chanhassen, Minn.?]
New York, N.Y., U.S.A
"Redmond, Wash"
"Upper Saddle River, N.J"
[San Francisco, CA]
`

Our goal is to figure out what RegEx would convert these idiosyncratic addresses into a standard pattern: city name in one column, and two-letter state abbreviation in another. With such a diverse set of patterns, we probably can't write a single RegEx that would convert them all in one fell swoop. But within the actual dataset there are many examples of each of these patterns, so it would be to our benefit to develop a few RegEx that will help us clean the data in a few steps rather than line by line. As we work, we'll want to consider:

1. What consistent textual patterns can we describe abstractly in each line, and perhaps between lines?
2. What steps would we need to follow—and in what order—to convert these values into two columns with the city name in column one and the state abbreviation in column two?
3. Are there any aspects of the text we cannot describe through RegEx and might require hand cleaning?

What fields in the [Nineteenth-Century Whaling Crews](https://docs.google.com/spreadsheets/d/1XuaCaCcY4Lk64TG-XJhefRrgDPhV6_RIVuyU78EOYTo/copy) data might be useful for exploring RegEx?

### Basic search-replace operations

The following guide to basic RegEx operators was (very lightly) adapted from Prof. Schmidt's RegEx exercise in the 2015 Humanities Data Analysis Course

#### Basic Operators:

##### `*`, `?` and `+`

+ `*` matches the preceding character **any number of times,* including no times at all.
+ `+` matches the preceding expression **at least one time.**
+ `?` matches the preceding expression exactly **zero or one times.**

##### `[]`

You can use brackets to indicate a **range** of characters. Suppose you are searching through the Schmidt family records, but learn that 18th century families often spelled the name "Schmitt." The regular expression `Schmi[td]t` would match either spelling. 

##### `()`

Parenthesis let you group a set of characters together. That is useful with replacements, described below: but it also lets you apply the operators above to **groups** of words.

Suppose you have a document full of references to John Quincy Adams, but that it sometimes calls him "John Q. Adams" and sometimes "John Quincy Adams." If you want to standardize, you want to make the whole "uincy" field optional. You can do this by searching for the following regex:

`John Q(uincy)?.? Adams`

Note that you need the period too, or else it won't match for `John Q. Adams`.

##### `.`

One last special character is the period, which matches *any single character*. The previous regex, for John Q. Adams, 

The most capacious regex of all is `.*` which tells the parser to match "any character any number of times." There are situations where this can be useful, particularly inside another regex.

##### `^`

If typed after an opening square bracket, the caret negates the character class inside the brackets. Thus `f[^i]at` would match `feat` but not `fiat`.

##### `{}`

For most cases, `*`, `+`, or `?` will work to capture an expression. But if you want to specify a particular number of times, you can use angle brackets. So to find Santa Claus, you could type `(Ho){3}`. (Just to clarify: that is totally Ben Schmidt's joke, not Ryan Cordell's).

#### Replacements

The syntax for replacing a regex will change from language to language, but the easiest substitution is to replace a regex by a string. I'll use here perl syntax, which gives the name of the operation (`s/` for substitute, `m/` for "match") separated by forward slashes. More recent languages or text editors may have a different syntax, but the important thing is that any substituting regex has two primary parts; the field to be matched, and its substitution.

#### Escaping special characters

Sometimes, of course, you'll actually want to search for a bracket, parenthesis, or other special character that appear in the text of your data.

To describe a literal bracket in a regex, you use the so-called "escape character": the
backslash, `\`. "Escaping" a character means putting a backslash in front of it, so that it takes a special meaning. To represent a literal period, for example, you'd have to specify the regex `\.`. The backslash is hardly ever used in normal writing, so it makes a safe choice for this: but you can always "escape" even the backslash itself, by prefacing it with another backslash: `\\`

#### Group matches

In addition to escaping those special characters, regexes also allow you to create *other* special characters.

The most powerful ones, and the ones best worth knowing, take their meaning from the context of the regular expression. 

When you use parentheses in a regex, it doesn't only create a group for matching: it also sets aside that group for future reference. Those can be accessed by escaping a digit from one to ten.

That means that you can replace a string contextually.

If you wanted to replace every occurrence of "ba" in a text with "ab," say, you could simply run the following substitution:

`s/ba/ab/`

But what if you actually want to swap any two letters?

`s/(b)(a)/\2\1/` does the same thing, but more generally. You could put anything into the parentheses.

Say you wanted to reformat a list of names from Firstname Lastname format to `Lastname, Firstname`. 

The regex `s/(.*) (.*)/\2, \1/` matches any characters, followed by a space, followed by any characters, and replaces them with the second group and the first group.

#### Creating other special characters.
Other important special characters come from prefacing letters.

* `\n`: a "newline"
* `\t`: a **tab**


In addition, other special characters will match a whole **range** of letters.
Usually, there would be a way to write these as a regular expression on their own:
but it can be very helpful to have a more succinct version. Some of the most useful are:

* `\w`: Any **word** character. (The same as `[A-Za-z]`).
* `\W`: Any **non-word** character. (The same as [^A-Z-a-z])
* `\d`: Any **numeric** (digit) character.
* `\D`: Any **non-numeric** (digit) character.

(If you are working in non-English languages, there are unicode extensions that work off the special character `\p` (or `\P` to designate the inverse of a selection). `\p{L}` matches
any unicode letter, for example. See [the unicode web site](http://www.unicode.org/reports/tr18/) for more on this.)

