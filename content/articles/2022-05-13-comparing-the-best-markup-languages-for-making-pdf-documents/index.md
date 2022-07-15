---
title: Comparing the Best Markup Languages for Making PDF Documents
date: '2022-05-13'
slug: comparing-the-best-markup-languages-for-making-pdf-documents
tags: ["foss", "markup"]
bibliography: ../../../static/bibliography.bib
csl: ../../../static/citations/apa-no-initials.csl
link-citations: true
reference-section-title: References
---

PDF is rightfully the standard output format for documents.
All word processors can output to PDF, but it is difficult to convert PDF to files word processors can edit.
Most people use “what you see is what you get” word processors like Microsoft Word, Google Docs, or LibreOffice Writer.
This type of word processor is convenient but it is also limited and unprofessional.
It is easier to get into, but it is harder to use in the long run.
This is the problem with all “what you see is what you get” programs: they do not follow the “[separation of content and presentation](https://en.wikipedia.org/wiki/Separation_of_content_and_presentation)” design principle.

Markup word processors are practical and professional alternatives.
However, there are so many of them and all of them are different.
It can be tirelessly difficult to choose the correct one.
It took me a surprisingly long time to choose the correct one for my uses.
And it took me even more time to create [the proper templates](https://github.com/amarakon/amaryaml) for easier use.
Nevertheless, they are still much easier to use in the long run as once you set everything up, the actual usage is simple.
Currently, the best markup word processors are Groff, LaTeX, Markdown, R Markdown, and Quarto.
I will go over the pros and cons of each one so that you can make the best decision.
I do not recommend using any other program than the ones listed in this post because these are the only good ones.

# Groff

Groff (GNU troff) is a document formatting system included with all GNU operating systems.
This makes it very convenient since you do not even have to install it.
Other markup word processors require you to install their packages and these packages can potentially have hundreds of dependencies in total.
Not everyone wants to install them and not everyone has enough storage space to do so.
You can use the `groff_ms` macro package by passing the `-ms` flag to create PDF documents.
It is equally convenient to render the document: running `groff -ms <file>.ms -T pdf > <file>.pdf` will quickly render it.
Other markup word processors take longer to render documents because they are more complex
It is commonly used to create man pages with the `groff_man` macro package.

The main problem with Groff is that it does not have enough features.
Not everything is possible in Groff.
For example: you can create mathematical equations but some of them are not possible.
LaTeX—and all of the other markup languages that use LaTeX to render math (Markdown, R Markdown, Quarto)—can possibly create any mathematical equation.
Groff lacks many other features including templates and geometry margin customization.
All of the documents you create with Groff will look the same, so only consider using it if you like the default appearance.

The syntax for writing Groff documents is also annoying.
All things that must be defined (like section headers and paragraphs) have to be defined using periods and capital letters.
Formatted text (like bold and italics) have to be put on separate lines.
Other than that, the syntax is fine.
But because of Groff’s flaws, Groff documents’ source code cannot be read easily in plain text.

# LaTeX

LaTeX is the golden standard for making PDF documents, and for good reasons.
It is the very first important markup word processor.
Almost all of the others are based on LaTeX.
And for that, I have to give credit where credit is due.
it does not have any major faults but it is good at pretty much everything.
LaTeX documents can be rendered with `pdflatex`.
Consider `xelatex` instead if you want to use a system font.

LaTeX is exceptional at math typesetting.
Most people will always write math on paper.
This has its benefits but it is not impossible to have a nicely formatted and professional document with any math equations.
All of the symbols—including plus and minus signs—are the perfect size as defined by the math font.
Try creating anything like this without using LaTeX:

<div class="figure">

<img src="https://i.stack.imgur.com/vsn9C.png" alt="Complex math made by LaTeX"  />
<p class="caption">
Figure 1: Complex math made by LaTeX
</p>

</div>

LaTeX’s formatting is exceptional too.
You can easily define everything with just a few commands.
These include page size, text alignment, font size.
It is much easier than having to toggle buttons in a graphical user interface.
Its line and page breaking is the best out of any typesetting program.

<div class="figure">

<img src="https://i.stack.imgur.com/MgSAz.png" alt="LaTeX line and page breaking"  />
<p class="caption">
Figure 2: LaTeX line and page breaking
</p>

</div>

As mentioned before, none of LaTeX’s faults are major.
The biggest problem with it is its commands.
All commands use backslashes, which means you have to stretch your pinkie tirelessly often.
Additionally, you have to use some commands just to make a working document.
You cannot compile a document from just simple plain text.
Its syntax is also generally too complicated at times.
From my experience, a LaTeX file (`.tex`) usually has twice the amount of lines compared to an identical Markdown file (`.md`).

# Markdown

Markdown is a widely used markup language that is used for more than just PDF documents.
If you want to use Markdown for PDF documents, you need to install LaTeX and the document converter Pandoc.
No other packages are required to convert a Markdown file to a PDF file.
Pandoc first converts the Markdown file to a LaTeX file.
Then, it runs `pdflatex`—or, if defined in the YAML front matter, `xelatex`.
Because of this extra step, Markdown documents always take longer to render than LaTeX documents.

Markdown’s syntax is much easier to learn and it is shorter too, because it was designed to be readable in plain text format.
This is why LaTeX files usually have twice the amount of lines compared to identical Markdown files.
Commands that should always be used in LaTeX (`\begin{document}... \end{document}`, `\maketitle`) are automatically applied in Markdown.
You do not have to write any commands, meaning you can write only completely plain text.
Common commands that are used repeatedly in LaTeX (`\section{}`, `\textbf{}`, `\textit{}`) can be replaced with shorter Markdown commands.
To write italics in LaTeX, you need to write `\textit{<text>}`.
To write italics in Markdown, you need to write `*<text>*`.
Not only does this make Markdown **easier** than LaTeX, it also makes it **faster**.
Pure LaTeX code can still be used for LaTeX commands that do not have alternative Markdown commands.

The biggest downside with Markdown is that [making tables](https://www.markdownguide.org/extended-syntax/#tables) is painful.
It is just as tedious as with LaTeX, but LaTeX is expected to be that way.
Markdown has its own way of making tables but it is not human-readable.
It is strange and surprising that Markdown tables do not follow the Markdown philosophy.
Moreover, line breaks and lists in tables require the use of [grid tables](https://disco.uv.es/disco_docs/wikibase/doc/cat/pandoc_manual_2.7.3.wiki?93).
Grid tables are extremely complicated, require too much time to make, and they have to be lined perfectly.
One small downside with Pandoc’s Markdown is that code blocks with syntax highlighting are impossible.
On the contrary, code blocks with syntax highlighting work decently in most Markdown interpreters or compilers.
Most people do not need to use code blocks though, so this is a minor issue.

# R Markdown

R Markdown adds another layer of simplicity to the source code.
It is similar to Markdown but it has more features.
In order to use R Markdown, you need to have R and the *rmarkdown* package, LaTeX, and Pandoc.
It has two more requirements than Markdown.
R Markdown requires the most storage space out of all of the markup processors mentioned in this article.
As you can imagine, its rendering process has one more step than Markdown.
This makes its rendering time even longer than Markdown; the longest of all the programs here.
First, it uses Knitr to “knit” the specified `.Rmd` file to the identical `.knit.md` file.
Then pandoc does the rest of the work.
Just like Markdown, R Markdown uses a YAML front matter at the top of the source code to define the document options.

What makes R Markdown’s front matter stand out is that it has an extra option: `output:`.
The `output:` option obviously defines the output format.
This article is only about PDF documents (`pdf_document`), but keep in mind that R Markdown can be used for just about anything.
This includes slideshows (`beamer_presentation`), HTML (`html_document`), GitHub (`github_document`).
The *bookdown* R package can be used to add alternative output formats that make it possible to conveniently reference section headers, figures, tables, and equations ([Xie et al., 2020](#ref-rmarkdown-cookbook-s4.7)).
For example, use `output: bookdown::pdf_document2` instead of `output: pdf_document`.

Unlike Markdown, R Markdown can display code blocks with excellent syntax highlighting.
It can also run the code specified if you use code chunks instead of code blocks.
You must specify the programming language for the correct syntax highlighting and to actually run the code.
There are many ways it is beneficial to run code in the document.
The most common language to use in R Markdown documents is R.
This allows certain output that is simply impossible with plain Markdown.
It also allows it to overcome the biggest downside Markdown has: tables.

As an alternative to Markdown and Pandoc’s methods of making tables, R Markdown can use R packages to make tables.
This is much more efficient and generally easier.
You do not have to worry about alignment, readability, and typos.
It is more professional too, as you would make them programmatically instead of using plain text.
The most common R function to create tables is `kable`, which is from the *knitr* package that is installed as a dependency of *rmarkdown*.
Other packages include *flextable*, *huxtable*, *reactable*, *xtable*, *pander*.
The package I use is *pander*.
`kable` is flawed because even though it is simple, it still does not support proper line breaks and lists.
This is why I prefer `pander`.

R Markdown has the best documentation out of all the markup word processors in this article.
R Markdown has many excellent books such as *[R Markdown Cookbook](https://bookdown.org/yihui/rmarkdown-cookbook/)* that easily explain R Markdown like you are five years old.
When searching for answers to common problems—especially on StackOverflow, most results will be for R Markdown.
This is true even when searching for LaTeX, Markdown, or Quarto specifically.
Most R packages have documentation at rdocumentation.org.
R Markdown documentation managed to teach me more about LaTeX, Markdown, and Quarto than all of those programs’ documentation themselves.

# Quarto

Quarto is best understood as an alternative to R Markdown.
R Markdown struggles from requiring too many packages, thus consuming too much storage.
It also takes a long time to fully render the `.Rmd` file to the `.pdf` file.
Quarto’s render time is shorter than R Markdown’s but longer than Markdown’s.
It also has native support for Python, R, Julia, and Observable.
R Markdown does not have native support for Python, Julia, or Observable.
R Markdown is designed for R users, while Quarto is designed for all users.
R Markdown has better documentation and is more versatile than Quarto.
I do not recommend Quarto because it is new, undeveloped, and not special enough for me to make the switch.
Users of R Markdown should not use Quarto unless they have a specific reason to do so.

# References

<div id="refs" class="references csl-bib-body hanging-indent" line-spacing="2">

<div id="ref-rmarkdown-cookbook-s4.7" class="csl-entry">

Xie, Yihui, Dervieux, Christophe, & Riederer, Emily. (2020). *R markdown cookbook* (1st ed., pp. 38–39). Chapman & Hall/CRC.

</div>

</div>
