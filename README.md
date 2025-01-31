
<!-- README.md is generated from README.Rmd via `devtools::build_readme()`. Please edit README.Rmd -->

# penguindown <img src="man/figures/thesisdown_hex.png" align="right" width=200 />

This project was inspired by the
[thesisdown](https://github.com/ismayc/thesisdown) package and is an
updated version of the Thesis template in `thesisdown` package, modified
to meet YSU Graduate College standards
[here](https://ysu.edu/academics/college-graduate-studies/current-students/thesis).
It was originally designed to be a standalone LaTeX document, then was
later updated to work with Sweave, and has now been translated to
`thesisdown`. See
[here](https://github.com/ismayc/thesisdown#customizing-thesisdown-to-your-institution)
for many examples of theses at other institutions.

Currently, the PDF version is fully-functional. The word version is
developmental, has no template behind it, and is essentially a call to
the appropriate functions in `bookdown`.

If you are new to working with `bookdown`/`rmarkdown`, please read over
the documentation available in the `gitbook` template at
<https://ismayc.github.io/thesisdown_book>.

The current output is here:

- [PDF](https://github.com/gjkerns/penguindown_book/blob/main/thesis.pdf)
  (Generating LaTeX file is available
  [here](https://github.com/gjkerns/penguindown_book/blob/main/_book/thesis.tex)
  with other files in the [book
  directory](https://github.com/gjkerns/penguindown_book/tree/main/_bookdown_files).)

Under the hood, the YSU LaTeX template is used to ensure that documents
conform precisely to submission standards. At the same time, composition
and formatting can be done using lightweight
[markdown](https://rmarkdown.rstudio.com/authoring_basics.html) syntax,
and **R** code and its output can be seamlessly included using
[rmarkdown](https://rmarkdown.rstudio.com).

### Using penguindown from `gjkerns`’ GitHub

Using {penguindown} has some prerequisites which are described below. To
compile PDF documents using **R**, you are going to need to have LaTeX
installed. By far the easiest way to install LaTeX on any platform is
with the [tinytex](https://yihui.name/tinytex/) R package:

``` r
install.packages(c('tinytex', 'rmarkdown'))
tinytex::install_tinytex()
# after restarting RStudio, confirm that you have LaTeX with
tinytex:::is_tinytex()
```

You may need to install a few extra LaTeX packages on your first attempt
to knit as well. Here is one such example of how to do so:

``` r
tinytex::tlmgr_install("babel-portuges")
```

To use {penguindown} from
[RStudio](https://www.rstudio.com/products/rstudio/download/):

1.  Ensure that you have already installed LaTeX and the fonts described
    above, and are using the latest version of
    [RStudio](https://www.rstudio.com/products/rstudio/download/). You
    can use `penguindown` without RStudio, but RStudio is probably the
    easiest tool for writing both R code and text in your thesis. It
    also provides a nice way to build your thesis while editing. We’ll
    proceed assuming that you have decided to use the RStudio workflow.

2.  Install the {bookdown}, {thesisdown}, and {penguindown} packages.
    Note that {thesisdown} and {penguindown} are not available on CRAN
    at the moment and that’s why `install.packages("thesisdown")` won’t
    work. Use `remotes::install_github()` as shown below instead to
    install the package.

    ``` r
    if (!require("remotes")) 
      install.packages("remotes", repos = "https://cran.rstudio.org")
    remotes::install_github("rstudio/bookdown")
    remotes::install_github("ismayc/thesisdown")
    remotes::install_github("gjkerns/penguindown")
    ```

          Note that you may need to restart RStudio at this point for
the following dialog to show up.

3.  Get started with the {penguindown} template. Create a new RStudio
    project with a {penguindown} template.

In RStudio, click on **File** \> **New Project** \> **New Directory**.
Then select **Thesis Project (YSU) using penguindown** from the dropdown
that will look something like the image below. You’ll see the graduation
cap as the icon on the left for the appropriate project type. Don’t
select the {thesisdown} version unless you are a student at Reed
College.

![](https://github.com/gjkerns/penguindown/raw/11d694fe37f4f0aa0e83663c9a03c058df375801/images/thesis_proj.png)

Next, give your project a name and specify where you’d like the files to
appear. In the screenshot below, the project name is `my_thesis` and it
will appear as a new folder on my Desktop.

![](https://raw.githubusercontent.com/gjkerns/penguindown/master/images/thesis_proj_name.png)

4.  After choosing which type of output you’d like in the YAML at the
    top of `index.Rmd`, **Knit** the `index.Rmd` file to get the book in
    PDF format.

### Day-to-day writing of your thesis

You need to edit the individual section R Markdown files to write your
thesis. It’s recommended that you version control your thesis using
GitHub if possible. RStudio can also easily sync up with GitHub to make
the process easier. While writing, you should `git commit` your work
frequently, after every major activity on your thesis. For example,
every few paragraphs or section of text, and after major step of
analysis development. You should `git push` at the end of each work
session before you leave your computer or change tasks. For a gentle,
novice-friendly guide to getting starting with using Git with R and
RStudio, see <https://happygitwithr.com/>.

## Rendering

To render your thesis into a PDF, open `index.Rmd` in RStudio and then
click the “knit” button. To change the output formats, look at the
`output:` field in `index.Rmd` and comment-out the formats you don’t
want.

The PDF file of your thesis will be deposited in the `_book/` directory,
by default.

## Components

The following components are ones you should edit to customize your
thesis:

### `_bookdown.yml`

This is the main configuration file for your thesis. You can change the
name of your outputted file here for your thesis and other options about
your thesis here.

### `index.Rmd`

This file contains all the meta information that goes at the beginning
of your document. You’ll need to edit the top portion of this file (the
YAML) to put your name on the first page, the title of your thesis, etc.

### `01-section.Rmd`, `02-section.Rmd`, etc.

These are the Rmd files for each section in your thesis. Write your
thesis in these. If you’re writing in RStudio, you may find the
[wordcount addin](https://github.com/benmarwick/wordcountaddin) useful
for getting word counts and readability statistics in R Markdown
documents.

### `bib/`

Store your bibliography (as bibtex files) here. We recommend using the
[citr addin](https://github.com/crsh/citr) and
[Zotero](https://www.zotero.org/) to efficiently manage and insert
citations.

### `csl/`

Specific style files for bibliographies should be stored here. A good
source for citation styles is
<https://github.com/citation-style-language/styles#readme>.

### `figure/` and `data/`

Store your figures and data here and reference them in your R Markdown
files. See the [bookdown book](https://bookdown.org/yihui/bookdown/) for
details on cross-referencing items using R Markdown.
