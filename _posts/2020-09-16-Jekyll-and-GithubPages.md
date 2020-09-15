---
layout: post
title: Lab 2 - A Site of Your Own
---

# Creating a Github Pages Website

## Introduction

Recently flat HTML platforms [like Jekyll](https://jekyllrb.com/) have been getting lots of buzz: they load quickly and don't have all the overhead of a database-driven platform like Wordpress. Some digital humanities scholars [have advocated for "minimal computing"](https://go-dh.github.io/mincomp/about/) as an ethos for the field moving forward:

> We use “minimal computing” to refer to computing done under some set of significant constraints of hardware, software, education, network capacity, power, or other factors…By operating at this intersection between choice and necessity minimal computing forces important concepts and practices within the DH community to the fore. In this way minimal computing is also an critical movement, akin to environmentalism, asking for balance between gains and costs in related areas that include social justice issues and de-manufacturing and reuse, not to mention re-thinking high-income assumptions about “e-waste” and what people do with it. Minimal computing thus relates to issues of aesthetics, culture, environment, global relationships of power and knowledge production, and other economic, infrastructural and material conditions.

Websites build through frameworks like Jekyll can be more complicated to set up than "out of the box" systems like Wordpress, but once they're set up they are easy to use and require fewer resources from end users to load and access. 

As we learn about Jekyll and Github Pages, we will largely follow Barry Clark's tutorial, [Build A Blog With Jekyll And GitHub Pages](https://www.smashingmagazine.com/2014/08/build-blog-jekyll-github-pages/), though some details have changed since 2014. A few years ago I recorded a screencast of this process for an undergrad class, and it might also be helpful as you work on your site this coming week, particularly since it can be paused, rewound, and so forth:

<iframe width="560" height="315" src="https://www.youtube.com/embed/qiJETQz7Phs" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## Step 1: Set up a Github Account

This part should be done, but it's a necessary prelude to building a Jekyll site on Github pages. So if you don't yet have a Github account, [see last week's lab](https://f20idh.ryancordell.org/2020/09/10/Github/). 

## Step 2: Find a Theme You Like and Fork It

As of last year, all Jekyll themes should work with Github pages, though some require more tinkering than others. Check out [this list of Jekyll themes on Github](https://github.com/topics/jekyll-theme?o=desc&s=stars), sorted by how many people like them. Find one you like, but make sure it's a theme that supports blogging. The easiest way to know is to see if there's a folder titled `_posts` in the repository after you fork it.  We can work during the semester to customize these themes, so it doesn't need to be perfect: just good enough. When you click on a theme name in this list you'll see its files. Most of these pages will include a link to a sample site, which will give you a sense of what your site would  look like.

Once you've found a theme you like, we will fork the repository. Don't worry if that phrase sounds like nonsense: we'll do it together and I'll explain what it means.

## Step 3: Review Your Site's Structure

Once everyone has their own Github Pages repository, we will spend some time studying the structure of a Jekyll website together. I will show you where to find the files for static pages, blog posts, and basic configuration files.

## Step 4: Edit the \_config.yml File

The \_config.yml file includes all the basic configurations for a Jekyll website. We need to customize these for each of your individual sites. We will work through this together as well.

## Step 5: Find an Application for Editing Markdown

### Option 1: Authorize Prose

There are different ways to edit the files for your Github Pages account. You can simply edit files directly (I'll show you this today) and you can sync the files with your desktop and use an application on your computer (I'll show you this in the future if you like. [Prose.io](https://prose.io/) is a useful application for editing the files online, and that's what we'll use today and next Monday for learning how to edit your website using Markdown.

### Option 2: Use a Free Markdown App 

If you use Github Desktop to sync your repository to your local hard drive, you can use one of these apps to edit your site's files:

+ [Macdown](http://macdown.uranusjr.com/) (Mac)
+ [Mou](http://25.io/mou/) (Mac)
+ [Markdownpad](http://markdownpad.com/) (Windows XP-8)
+ [Markdown Edit](http://markdownedit.com/) (Windows)
+ [Ghostwriter](http://wereturtle.github.io/ghostwriter/) (Windows & Linux)
+ [Remarkable](https://remarkableapp.github.io/) (Linux)
+ a bit more complicated to get started with, but [Atom](https://atom.io/) is more full-featured than some of those above (Mac, Windows, Linux)

## Step 6: Edit at Least One Page

We will work together to edit at least one of your site's pages, so that you know what to do to edit others going forward. To work with Jekyll's content you'll need to know how to use the Markdown text convention (see below). 

## Step 7: Create a Sample Post

We will work together to create one sample post, which will be much like editing a page save some different metadata in the header. Here too you'll use the Markdown text conventions to edit your posts (see below). 

## Step 8: Customize Your Pages and Begin Blogging

## Other Jekyll/Github Pages Resources

1. Other [Jekyll themes](http://jekyllthemes.org/) that will work with Github Pages, though they might require a bit more tinkering. 
2. Amanda Visconti's [Jekyll/Github Pages tutorial](https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages) at the _Programming Historian_


# Composing in Markdown

Writing pages and posts for Jekyll requires writing using the conventions of Markdown. I ask you to do this because Markdown offers a gentle introduction to textual markup—think TEI, for a more DH-specific version of markup, and because in this class I want you to be thoughtful about the medium in which you choose to write. We will do our writing for this class not in Word or another WYSIWYG (What You See Is What You Get) editor, but in a range of possible application and using the Markdown syntax. I don't expect every one of you to become Markdown devotees (though a few often do in my classes), but I do expect you to attend thoughtfully to your own technologies and habits of composition by exploring an alternative mode to what you are likely used to. 

## What is Markdown?

Markdown is a lightweight standard for writing in plain text while encoding the **structure of your document** for later representation in a format like Word, PDF, or HTML. If you have ever marked up a text using HTML or XML tags, Markdown works quite similarly, but uses simple typographical symbols to encode text rather than longer HTML  or XML tags. There are a number of *affordances* to working in Markdown, including:

1. **Simplicity.** Because Markdown is a plain-text system of encoding structural elements typographically—rather than, as in proprietary formats like `docx`, though hidden, underlying code—Markdown files are small in size and simple to compose. You do not need to interrupt your writing to format your document while writing in Markdown.
2. **Flexibility.** When writing in Markdown you encode directions for styling your text, but you do not style it directly. Because of this, an `md` file can be easily converted to many other standard file types, including `html` or `pdf`. You can easily convert a single `.md` file into a range of other formats, giving you flexibility when you want to publish your writing. 
3. **Durability.** Unlike files composed in specific version of proprietary software, Markdown files are, essentially, plain text files. This means they can be opened by a wide range of applications and they will look essentially the same, and that they are not subject to the vicissitudes of software updates or platform dependencies. You can open and edit a Markdown file on virtually any computer, and you will likely be able to do well into the future. Even if the conventions of Markdown are no longer understood, the central text you write in it should remain widely compatible and portable.
4. **Mobility.** Because Markdown is composed using basic typographical characters, it's very easy to use on mobile platforms such as phones or tablets. For example, my favorite note-taking app, [Bear](https://bear.app/) allows you to compose in Markdown and access your notes through a Desktop and Mobile interface. There are a number of applications for composing in Markdown while on the go, including mobile versions of some of the desktops apps I recommend here.   

As with any medium, of course, there are also *limitations* to writing in Markdown, such as:

1. You have less granular control over the appearance of your text than you would in a full featured word processor. In order to ensure the flexibility and durability of Markdown, its grammar is relatively constrained. While you can indicate text should be `bold` or formatted in a `numbered list` using Markdown, for instance, you could indicate that one paragraph's font should be 2 points larger than another. 
2. You typically have to convert Markdown files into another format before publication. This is not *quite* true on the web, where some frameworks like GitHub Pages can understand Markdown (as expressed in a Jekyll website) directly, but usually the production stage for a Markdown document involves converting your `md` file into another format, thus converting Markdown's structural encoding into actual stylistic representation.

## Markdown References

Below I will describe the most common Markdown syntax, but for additional reference you can consult:

+ The [Markdown Wikipedia page](https://en.wikipedia.org/wiki/Markdown), which includes a very handy chart of the syntax.
+ John Gruber's [introduction to Markdown](https://daringfireball.net/projects/markdown/syntax). Gruber developed the standard and knows what he's talking about!
+ This [interactive Markdown tutorial](http://www.markdowntutorial.com/), which will teach you the syntax in a few minutes.
+ You can also download [the Markdown versions of our class website pages](https://github.com/rccordell/s19rm) (all generated directly from Markdown) or [the Markdown for this very lab](https://github.com/rccordell/s19rm/blob/master/_posts/2019-01-09-Lab1-Markdown.md) if you'd like to compare what you see in your browser with the marked-up text that created it (click the `Raw` button to see the Markdown [without GitHub's styling](https://raw.githubusercontent.com/rccordell/s19rm/master/_posts/2019-01-09-Lab1-Markdown.md)).

In short, in Markdown your text will not include any visible stylistic variations such as italics or bold text; Markdown is a *plain text* format. However, many Markdown Editors will be able to preview the way your documents will look like when they're styled.

## Applications for Writing in Markdown

One advantage to this flat-text format is that you can write valid Markdown in many, many editors, including the free text editors (such as TextEdit on the Mac or Wordpad on the PC) that come with most computers. You can also write in Markdown in some rich text editors such as [Scrivener](https://www.literatureandlatte.com/scrivener.php), though their support for the standard can be uneven. 

There are many dedicated Markdown composition applications with additional features, such as syntax highlighting or the ability to preview what your documents. 

### Free Markdown Applications:

+ [Macdown](http://macdown.uranusjr.com/) (Mac)
+ [Mou](http://25.io/mou/) (Mac)
+ [Markdownpad](http://markdownpad.com/) (Windows XP-8)
+ [Markdown Edit](http://markdownedit.com/) (Windows)
+ [Ghostwriter](http://wereturtle.github.io/ghostwriter/) (Windows & Linux)
+ [Remarkable](https://remarkableapp.github.io/) (Linux)
+ [Hashify](http://hashify.me/IyBUaXRsZQ==) (online) 
+ a bit more complicated to get started with, but [Atom](https://atom.io/) is more full-featured than some of those above (Mac, Windows, Linux)
+ It's not specifically a Markdown application, but [Prose.io](http://prose.io/) allows you to edit files in a Github repository and commit them all online.

### Paid Markdown Applications

They can be pricey, but there are some beautifully-designed, paid Markdown-writing applications out there. I can't list them all, but here are two popular ones:   
  
+ [Ulysses](https://ulysses.app/) (Mac only) is beautifully designed and a joy to use. It was my go-to application for awhile but I moved away from it because of its non-standard implementation of a few Markdown elements, such as links and images. Others don't like their subscription payment model.
+ My current, (cross platform_ favorite is [iA Writer](https://ia.net/writer). It is also well designed, though not quite as elegant as Ulysses. But it requires only one payment to use and implements Markdown in a standard way, so that my writing is more broadly compatible with other systems. 

To compose pages and blog posts for Jekyll using these desktop applications, you will need to sync a local folder on your computer to your Github repository.

## Markdown Syntax

Here are the very basics for writing in Markdown. If you use one of the editors above with a preview feature, you'll be able to see what you're doing as you type.

1. If you want your text to be italicized, then *enclose it in single asterisks* or _in underlines_. (i.e. \*enclose it in single asterisks\* or \_in underlines\_).
2. If you want your text to be bold, then **enclose it in double asterisks**. (i.e. \*\*enclose it in double asterisks\*\*).
3. To start a new paragraph, simply hit return twice, so that you see a single line space in between paragraphs.
4. To start a new line without a paragraph break, add two spaces to the end of the first line and then hit return once.
5. To create a hyperlink, enclose the \[words you want linked in brackets and the link in parentheses following\]\(http://ryancordell.org/\), which results in a link like this: [words you want linked in brackets and the link in parentheses following](http://ryancordell.org/).   

You can also create headlines of descending sizes, lists (numbered or bulleted), footnotes, block quotations, embedded images, and more. See the reference materials above for details on these other elements.