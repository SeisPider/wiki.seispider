+++
date = "2017-08-02T16:24:01+08:00"
title =  "Combining PDFs at the command line"
+++
Combining multiple PDFs into one file is easy. Just turn to the command line and run Ghostscript. It's a quick and effective way to mash PDF files together.

# Introduction
There may be times for whatever reason, that you need to mash a bunch of PDFs into a single file. While there are a number of Linux utilities -- both command line and graphical -- one of the quickest and most efficient ways to do this is with a piece of software called Ghostscript.

## Haven't heard of Ghostscript?
If that's you, then it's not surprising. Ghostscript is one of those little-known, unsung tools which you come to appreciate when you have to use it. Ghostscript is a command line application that lets you view, print, and (to a small degree) manipulate Postscript and PDF files. You can also use it to convert those files to other formats. The best part is that Ghostscript comes bundled with most Linux distributions. You don't need to install any new software.

# Combining PDFs
Just open a terminal window and type something like the following:
```
gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=output.pdf pdffile1.pdf pdffile2.pdf
```
Here’s what all of those options mean:

* -gs -- starts Ghostscript
* -dBATCH -- once the PDF files have been combined, stop running. If you don’t include this option, Ghostscript will just keep running
* -dNOPAUSE -- forces Ghostscript to process each file without pausing for confirmation
* -q -- stops Ghostscript from displaying messages while it works
* -sDEVICE=pdfwrite -- uses Ghostscript's PDF writer to work on the files
* -sOutputFile=output.pdf -- saves the resulting PDF file with the name that you specified, for example output.pdf
Obviously, pdffile1.pdf and pdffile2.pdf are the names of the PDF files that you want to combine. You’re not limited to two files. And you’re not limited to the commands that are listed above. You can add any of Ghostscript’s PDF options to the command line — see the Ghostscript documentation for details.

# Drawbacks
Using Ghostscript has its drawbacks. It spits out a bare bones PDF. And that file will be large. By default, Ghostscript doesn't compress PDFs. To get around that, you really need to use some of Ghostscript's PDF options,

As well, some people may find typing long, dense strings of options at the command line to be a bit of a chore.

# Saving keystrokes
You can avoid having to type a lot of text every time you want to combine PDFs by creating a command that encapsulates all of the Ghostscript options that you want to use. To do this, open the file .bashrc (found in your /home directory) in a text editor. Then, add the following at the end of the file:

```
alias pdfmerge='gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=./output.pdf'
```
Again, you're not limited to the command string above. You can use any of Ghostscript's PDF options.

When you want to combine PDF files, just type pdfmerge followed by the names of the files that you want to mash together. The resulting file will be named output.pdf, and will be saved to your /home directory.

Final thoughts
While you might only use this feature rarely, Ghostscript's ability to combine PDF files is quick, efficient, and effective. It just demonstrates how powerful the command line can be.
