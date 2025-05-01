# PP3

## Goal
In this exercise, we will explore how to handle, render and display text-based information from our terminal.
As ancient as this may seem, the foundation of effective software engineering is a familiarity with the concepts of programmatic text-processing. 
We will generate different artifacts using four different _description-languages_. 
After this exercise, you should be able to decide for yourselves, when to use which and have a fundamental understanding of how they are supposed to work.

**Important:** Start a stopwatch when you begin and work uninterruptedly for 90 minutes. Once time is up, stop immediately and document the point where you had to pause.

---

## Workflow
Remember the standard workflow. 
If in doubt, revisit [PP1](https://github.com/MaxClerkwell/PP1)

1. **Fork** the repository
2. **Modify and Commit** your solution
3. **Submit your link for Review**

If you get stuck, use the [Github-Discussions of this Repository](https://github.com/MaxClerkwell/PP3/discussions)!

## Tasks

### Prerequisits: Linux, SSH and vim 
> This task is not part of the measured time within this practical exercise!

By now you should already have access to one local linux machine. 
Whether this is a Raspberry Pi, a Desktop-PC or a WSL para-virtualized system on your Windows computer doesn't make any difference.
If you are unsure about how to log in, you can [check out this video tutorial](https://www.youtube.com/watch?v=Z0ggeNzEhzY).
Make sure, that you are wellversed in utilizing your filesystem with `cd`, `ls`, `cat`, `mkdir` and `rm`, as well as navigating through textfiles with `vim`, by revisiting the `vimtutor` you should've finished by the end of [PP2](https://github.com/MaxClerkwell/PP2).

---

### Task 1: SVG
The scalable-vector-graphics format is a commonly used description language for diagrams. 
You will probably use this file format throughout your professional career and your studies multiple times, therefore we want to explore this format here.

As usual for description languages, the actual content is a regular textfile, that get's rendered on display by a sepecific rendering software. 
In case of SVG, the software that renders the actual picture is embedded in a lot of other tools, such as browsers, or image software. 

An SVG file is an XML-based text file that describes two-dimensional vector graphics. 
The basic structure of an SVG file includes the following components:

#### XML Declaration

```xml
<?xml version="1.0" encoding="UTF-8"?>
```

This optional line declares the XML version and character encoding used in the file.

#### SVG Root Element

```xml
<svg xmlns="http://www.w3.org/2000/svg"
     version="1.1"
     width="800mm" height="600mm"
     viewBox="-400 -300 800 600">
  <!-- SVG content goes here -->
</svg>
```

##### Attributes:

- `xmlns`: Defines the XML namespace for SVG elements.
- `version`: Specifies the SVG version being used.
- `width` and `height`: Set the dimensions of the SVG canvas.
- `viewBox`: Establishes the coordinate system and aspect ratio.

#### Optional Metadata Elements

Within the `<svg>` element, you can include metadata to provide additional information about the SVG content:

```xml
<title>Title of the SVG</title>
<desc>Description or alternative text for the content.</desc>
```

- `<title>`: Provides a title for the SVG, which can improve accessibility.
- `<desc>`: Offers a description of the SVG content, also aiding accessibility.

#### Graphical Elements

Inside the `<svg>` element, you can define various graphical elements such as:

- `<rect>`: Draws rectangles.
- `<circle>`: Draws circles.
- `<path>`: Defines complex shapes.
- `<text>`: Adds text elements.

Each of these elements can have attributes to define their appearance and position.

#### Example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg"
     version="1.1"
     width="800mm" height="600mm"
     viewBox="-400 -300 800 600">
  <title>Sample SVG</title>
  <desc>A simple example of an SVG file structure.</desc>
  <rect x="10" y="10" width="100" height="50" fill="blue" />
</svg>
```

This example creates an SVG canvas with a blue rectangle positioned at (10,10) with a width of 100 units and a height of 50 units.

For more detailed information on SVG structure and elements, you can refer to the [W3C SVG 2 Specification](https://www.w3.org/TR/SVG2/struct.html).

**Install vim on your local machine and open a new file, called `example.svg`. Write the SVG-code to include a straight line, a circle and a rectangle. When done, use your browser to open the file.**

<details>
    <summary>Your SVG Code</summary>
     
```xml
<?xml version="1.0" encoding="UTF-8"?>
<svg xmlns="http://www.w3.org/2000/svg"
     version="1.1"
     width="800mm" height="600mm"
     viewBox="0 0 800 600">
  <title>SVG Example</title>
  <desc>SVG with a straight line, a circle, and a rectangle.</desc>
  <line x1="50" y1="50" x2="200" y2="50" stroke="black" stroke-width="2"/>
  <circle cx="150" cy="150" r="40" fill="green" stroke="black" stroke-width="2"/>
  <rect x="250" y="100" width="120" height="60" fill="blue" stroke="black" stroke-width="2"/>
</svg>
```
     
</details>

### Task 2: Markdown
You have already discovered _markdown_ in these `README.md` files. 
It is an easy and lightweight syntax, to instruct a display software to render text in a given way.

**Answer the following questions:**

<details>
    <summary>How does prepending hashes (<code>#</code>) affect the display?</summary>
When you add hashes `#` in front of a line in Markdown, it creates a heading. The number of hashes shows the level of the heading. For example:

- `#` creates the largest heading (like a title)
- `##` is a subheading
- `###` is a smaller subheading

It helps to organize the structure of the document.
</details>
<details>
    <summary>How do you mark italic or bold font?</summary>
To format text in italic, use one asterisk `*` or one underscore `_` around the text:  

- `*italic*` or `_italic_` → *italic*

To format text in **bold**, use two asterisks `**` or two underscores `__`:  

- `**bold**` or `__bold__` → **bold**

You can also mix them:  

- `***bold and italic***` → ***bold and italic***
</details>
<details>
    <summary>Which different ways are there to generate listings and tables?</summary>
Listings:

- Unordered lists (bullet points):
  - Use `-`, `*`, or `+` in front of list items:
    - Item 1
    - Item 2

- Ordered lists (numbered):
  1. First item  
  2. Second item

#### Tables:

You can create tables using pipes `|` and hyphens `-`:

```
| Name   | Voltage | Current |
|--------|---------|---------|
| Motor  | 12V     | 1.5A    |
| LED    | 5V      | 0.02A   |
```

This will render as a neat table when viewed on a Markdown viewer.
</details>

### Task 3: LaTeX
While markdown is great for light-weight rendering text within a limited context such as a browser or phone, when it comes to more complex and professional rendering, the `LaTeX` toolset is the standard for creating `.pdf` files. 
`LaTeX` is usually not rendered _on the fly_, meaning while it is being displayed. 
A special software which we call _compiler_ is used to generate a parametrized documents. 
If you are running a local WSL, make sure to install `texlive-full` before continuing with the next steps. 
This may take up to 30 minutes, since it's a large software package. 
To check whether the installation was sucessful, run `pdflatex --version`.
The output should look something like this:
```sh
user@machine:~$ pdflatex --version
pdfTeX 3.141592653-2.6-1.40.25 (TeX Live 2023/Debian)
kpathsea version 6.3.5
Copyright 2023 Han The Thanh (pdfTeX) et al.
There is NO warranty.  Redistribution of this software is
covered by the terms of both the pdfTeX copyright and
the Lesser GNU General Public License.
For more information about these matters, see the file
named COPYING and the pdfTeX source.
Primary author of pdfTeX: Han The Thanh (pdfTeX) et al.
Compiled with libpng 1.6.43; using libpng 1.6.43
Compiled with zlib 1.3; using zlib 1.3
Compiled with xpdf version 4.04
```
If you are using the lecture-server, make sure to visit the [SCP tutorial](https://github.com/STEMgraph/301394c2-6efb-4677-aaff-47091fb8145d) first. 
Otherwise, you might have a hard time opening the generated `.pdf`-document.

Create a new directory on the linux machine that texlive is installed at, navigate into it and open a file with the name `main.tex`.
Simply copy the following text into it:
```tex
\documentclass{article}             % Sets the document class to "article"
\usepackage[utf8]{inputenc}         % Allows you to use UTF-8 input encoding

\title{Minimal LaTeX Project}       % Sets your document title
\author{Your Name}                  % Sets your name as the author
\date{\today}                       % Sets the date to the day you compile

\begin{document}                    % Begins the document content

\maketitle                          % Generates the title using the above information

Hello, world!                       % This is where your content goes

\end{document}                      % Ends the document
```
Save and close the document. 
Now run the following command to create a `.pdf`-file from it:
```sh
pdflatex -jobname=example.pdf main.tex
```
After it finishes, us `ls` to inspect the directory. 

**Answer the following questions:**

<details>
    <summary>Which files were generated by the LaTeX compiler?</summary>
    After compiling the `.tex` file, LaTeX usually creates several files:

- `example.pdf` — the output PDF document  
- `main.aux` — stores information for cross-referencing  
- `main.log` — contains a log of the compilation process   

These files help LaTeX manage things like references, table of contents, and error tracking.

</details>

<details>
    <summary>How do you change the name of the pdf-file?</summary>
    To change the name of the generated PDF file, you use the `-jobname` flag in the `pdflatex` command. For example:

```bash
pdflatex -jobname=myfile main.tex
```

This will create a PDF file called `myfile.pdf` instead of the default `main.pdf`.

</details>

### Task 4: Displaying your pdf
1) If you worked on the lecture-machine, use the `scp` command to copy your `.pdf`-file to your desktop. There you can display it with every regular `.pdf`-viewer
2) If you worked in the WSL: run `sudo apt install xpdf -y` to install the `xpdf`-viewer. Run `xpdf <your pdf path>` to open the document.

**Answer the following questions:**

<details>
    <summary>What changes in your pdf, if you change the documentclass to <code>book</code></summary>

- The **title page** is placed on a new page by default.
- Page numbering usually starts with Roman numerals (i, ii, iii…) before the main content.
- Chapters are available as a command (`\chapter{...}`), and structure is more suited for longer documents like theses or textbooks.
- Margins and spacing may also change slightly.
</details>
<details>
    <summary>What changes in your pdf, if you add <code>\section{Intro}</code> after <code>\maketitle</code></summary>

- A new **section heading** called “Intro” appears right after the title.
- It is formatted in bold and larger than normal text.
- It also affects the document structure and can be used to create a **table of contents** later.

</details>


### Task 5: 
If you are running on a Windows machine, make sure to install `vim` for Windows from the [official `vim` repository](https://github.com/vim/vim-win32-installer/releases).
Scroll down until you see the _Assets_ and use the `_64.exe` or `_x86.exe`, depending on your system. 
If you run MacOS or Linux natively, make sure you have `vim` installed via your package-manager. 

Open a terminal-session and create a new directory within your users home-directory called `html`.
Use `vim` to open a new file within it called: `index.html`.

Copy the following text into it:
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Minimal HTML Example</title>
  </head>
  <body>
    <p>Hello, world!</p>
  </body>
</html>
```
Depending on your system, run the following command to open the rendered file:
Windows:
```sh
start index.html
```
MacOS
```sh
open index.html
```
Linux
```sh
xdg-open index.html
```
If you are running in WSL, make sure to install the `w3m` browser before by executing `sudo apt install w3m -y`.


**Answer the following questions:**
<details>
  <summary>What happens if you exchange the <code>&lt;p&gt;&lt;/p&gt;</code> for <code>&lt;h1&gt;&lt;/h1&gt;</code>?</summary>

- The **text "Hello, world!"** will be displayed as a **main heading** (h1).
- **h1** is the highest-level heading in HTML, so it will be **larger** and **bolded** by default, and it will stand out more compared to a paragraph (`<p>`).

</details>

<details>
    <summary>How can you generate a listing of items?</summary>



To create a **listing of items** in HTML, you can use **unordered lists** (`<ul>`) or **ordered lists** (`<ol>`). Here’s an example:

- **Unordered list (bullets)**:

    ```html
    <ul>
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ul>
    ```

- **Ordered list (numbers)**:

    ```html
    <ol>
      <li>First item</li>
      <li>Second item</li>
      <li>Third item</li>
    </ol>
    ```



</details>

<details>
    <summary>How can you create a table in this document?</summary>


To create a **table**, you can use the `<table>`, `<tr>`, `<th>`, and `<td>` elements. Here's an example:

```html
<table border="1">
  <tr>
    <th>Header 1</th>
    <th>Header 2</th>
  </tr>
  <tr>
    <td>Row 1, Cell 1</td>
    <td>Row 1, Cell 2</td>
  </tr>
  <tr>
    <td>Row 2, Cell 1</td>
    <td>Row 2, Cell 2</td>
  </tr>
</table>
```

This will generate a table with two columns and two rows of data.

</details>


---

**Remember:** Stop working after 90 minutes and record where you stopped!

88 Minutes in Total
