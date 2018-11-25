-   [Introduction](#introduction)
-   [Bibliographies](#bibliographies)
    -   [BibLaTeX](#biblatex)
    -   [Google Scholar Search Portal](#google-scholar-search-portal)
    -   [Obtaining a citation from Google
        Scholar](#obtaining-a-citation-from-google-scholar)
    -   [Navigating Citation Options](#navigating-citation-options)
    -   [Copying the BibLaTeX
        Citation.](#copying-the-biblatex-citation.)
    -   [Structuring a `.bib` file](#structuring-a-.bib-file)
-   [RMarkdown YAML for including a
    bibliography](#rmarkdown-yaml-for-including-a-bibliography)
-   [Citing Papers, Software, and
    Websites](#citing-papers-software-and-websites)
    -   [Citing a Paper](#citing-a-paper)
    -   [Citing the *R* programming
        language](#citing-the-r-programming-language)
    -   [Citing *R* Packages](#citing-r-packages)
    -   [Citing Websites](#citing-websites)
-   [Adding References to a Document](#adding-references-to-a-document)
-   [References](#references)

Introduction
============

Within `rmarkdown` (Allaire et al. 2018), we are able to use
[BibLaTeX](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management)
to automatically generate bibliographies. Bibliographies store the
references to different resources that were consulted when creating the
report. Previously, these bibliographies may have been created with the
assistance of web sites like
[mendeley](https://www.mendeley.com/?interaction_required=true),
[refworks](https://www.refworks.com/), or
[zotero](https://www.zotero.org/).

The goal of this document is to expand upon the web-based citation
documentation for `rmarkdown` by RStudio (2014).

Bibliographies
==============

BibLaTeX
--------

[BibLaTeX](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management)
is a way to structure citations used within a paper. You can obtain
citation entries for scholarly works from [Google
Scholar](https://scholar.google.com/) using the “BibTeX” entry. In the
subsequent sections, we’ll work through an example where we obtain
citation information for a paper and include it within an `rmarkdown`
report.

Google Scholar Search Portal
----------------------------

Just like with regular ol’ Google, type into the search bar either the
full paper names or just the key terms that you are interested in.

<img src="img/scholar/google_scholar.PNG" width="1025" style="display: block; margin: auto;" />

Obtaining a citation from Google Scholar
----------------------------------------

Once you found the paper you were looking for, press the `Cite` button.

<img src="img/scholar/google_scholar_search_result.PNG" width="1025" style="display: block; margin: auto;" />

Navigating Citation Options
---------------------------

From the citation menu, there are many different export options. In our
case, we’ll opt for the `BibTeX` option.

<img src="img/scholar/google_scholar_cite_options.PNG" width="1025" style="display: block; margin: auto;" />

Copying the BibLaTeX Citation.
------------------------------

From here, use either `CNTRL` + `C` (Windows/Linux) or `CMD` + `C`
(macOS) to copy the citation.

<img src="img/scholar/google_scholar_bibtex.PNG" width="1025" style="display: block; margin: auto;" />

Structuring a `.bib` file
-------------------------

Bibliography information is stored in a `.bib` file, which is just a
regular text file.

Here is what the `bibliography.bib` file would look like with the
citation obtained in the previous example in addition to another
citation that already existed.

    @incollection{tversky1985framing,
      title={The framing of decisions and the psychology of choice},
      author={Tversky, Amos and Kahneman, Daniel},
      booktitle={Environmental Impact Assessment, Technology Assessment,
                 and Risk Analysis},
      pages={107--129},
      year={1985},
      publisher={Springer}
    }
    @book{ho1987,
      title={Rational choice: Contrast between economics and psychology.},
      author={Hogarth, Robin M and Reder, Melvin W},
      year={1987},
      publisher={University of Chicago Press}
    }

RMarkdown YAML for including a bibliography
===========================================

The header information for the RMarkdown file gains one additional entry
that corresponds to the `.bib` bibliography file generated previous.

    ---
    title: "Example Biblography heading"
    output: html_document
    bibliography: bibliography.bib
    ---

Citing Papers, Software, and Websites
=====================================

Citing a Paper
--------------

Inside of the document, you can use:

-   `[@tversky1985framing]` to obtain both the author names and a year
    in parentheses.
    -   “Choice is important **(Tversky and Kahneman 1985)**.”
-   `[-@tversky1985framing]` provides only a year in parentheses
    -   Tversky and Kahneman says, “Choice is important **(1985)**.”
-   `[see @tversky1985framing, pg. 15]` provides context for the
    citation.
    -   “Choice is important” **(see Tversky and Kahneman 1981,
        pg. 15)**.
-   `@tversky1985framing` provides the author names with only the year
    in parentheses.
    -   From **Tversky and Kahneman (1985)**, we know that “choice is
        important.”

**Example:** Everyone should read the Tversky and Kahneman (1981) paper.

Citing the *R* programming language
-----------------------------------

When you first open *R*, you are prompted in the startup text with a
paragraph on how to cite *R* and its package:

> R is a collaborative project with many contributors. Type
> ‘contributors()’ for more information and ‘citation()’ on how to cite
> R or R packages in publications.

Typing `citation()` gives:

    ## 
    ## To cite R in publications use:
    ## 
    ##   R Core Team (2018). R: A language and environment for
    ##   statistical computing. R Foundation for Statistical Computing,
    ##   Vienna, Austria. URL https://www.R-project.org/.
    ## 
    ## A BibTeX entry for LaTeX users is
    ## 
    ##   @Manual{,
    ##     title = {R: A Language and Environment for Statistical Computing},
    ##     author = {{R Core Team}},
    ##     organization = {R Foundation for Statistical Computing},
    ##     address = {Vienna, Austria},
    ##     year = {2018},
    ##     url = {https://www.R-project.org/},
    ##   }
    ## 
    ## We have invested a lot of time and effort in creating R, please
    ## cite it when using it for data analysis. See also
    ## 'citation("pkgname")' for citing R packages.

We’re interested in the **BibLaTeX** entry. That is, we want to copy
into our `.bib` file these lines:

    @Manual{,
      title = {R: A Language and Environment for Statistical Computing},
      author = {{R Core Team}},
      organization = {R Foundation for Statistical Computing},
      address = {Vienna, Austria},
      year = {2018},
      url = {https://www.R-project.org/},
    }

Note, we’ll need to add a “name” right after the `@Manual{` in order to
refer to this entry. Thus, a complete entry would be given by:

    @Manual{R:2018, # <-- Add name to reference (Remove the # and everything to the right)
      title = {R: A Language and Environment for Statistical Computing},
      author = {{R Core Team}},
      organization = {R Foundation for Statistical Computing},
      address = {Vienna, Austria},
      year = {2018},
      url = {https://www.R-project.org/},
    }

From there, we can use the previous citing syntax of `@R:2018` to
reference the entry. Note that *R* is a powerful language produced by R
Core Team (2018) that we used to conduct our analysis.

Citing *R* Packages
-------------------

We can also generate citations for *R* packages that are **installed**
by using `citation("pkgname")`. For example, the citation for `ggplot2`
would be given by:

    citation("ggplot2")

    ## 
    ## To cite ggplot2 in publications, please use:
    ## 
    ##   H. Wickham. ggplot2: Elegant Graphics for Data Analysis.
    ##   Springer-Verlag New York, 2016.
    ## 
    ## A BibTeX entry for LaTeX users is
    ## 
    ##   @Book{,
    ##     author = {Hadley Wickham},
    ##     title = {ggplot2: Elegant Graphics for Data Analysis},
    ##     publisher = {Springer-Verlag New York},
    ##     year = {2016},
    ##     isbn = {978-3-319-24277-4},
    ##     url = {http://ggplot2.org},
    ##   }

We’ll again copy the **BibLaTeX** code and add a name to the citation
entry:

    @Book{ggplot2:Wickham:2016, # <- Reference Name (Delete # and everything to the right)
      author = {Hadley Wickham},
      title = {ggplot2: Elegant Graphics for Data Analysis},
      publisher = {Springer-Verlag New York},
      year = {2016},
      isbn = {978-3-319-24277-4},
      url = {http://ggplot2.org},
    }

And the rest of the story is the same regarding accessing the citation
through a reference. For example, we have:

-   `@ggplot2:Wickham:2016` generates `Wickham (2016)`
-   `[@ggplot2:Wickham:2016]` generates `(Wickham 2016)`
-   `[-@ggplot2:Wickham:2016]` generates `(2016)`

Wickham (2016) provides the ability to use the grammar of graphics to
generate visualizations for data.

Citing Websites
---------------

As a majority of content is on the web, there are different ways to cite
websites. The following template should work for cases where you need to
cite a news article, blog post, web API documentation, and so on. For a
beginning entry, consider the [STAT
385](http://stat385.stat.illinois.edu) website.

    @misc{STAT385:website:2018,
          title  = {{STAT 385 FA 2018 Course Website}},
          author = {{James Balamuta}},
          year   = {2017},
          note   = {\url{http://stat385.stat.illinois.edu}, Last accessed November 13, 2018)}
    }

Another example would be the RMarkdown documentation for bibliographies.

    @misc{RStudio:rmarkdown:citations,
          title  = {{Bibliographies and Citations}},
          author = {{RStudio}},
          year   = {2014},
          note   = {\url{https://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html}, Last accessed November 13, 2018)}
    }

Adding References to a Document
===============================

By default, the bibliography will be added at the end of the document.
It is customary to provide a header to the documents reference section
by using a single-level heading with the name “References”, e.g.

    # References

References
==========

Allaire, JJ, Yihui Xie, Jonathan McPherson, Javier Luraschi, Kevin
Ushey, Aron Atkins, Hadley Wickham, Joe Cheng, and Winston Chang. 2018.
*Rmarkdown: Dynamic Documents for R*.
<https://CRAN.R-project.org/package=rmarkdown>.

R Core Team. 2018. *R: A Language and Environment for Statistical
Computing*. Vienna, Austria: R Foundation for Statistical Computing.
<https://www.R-project.org/>.

RStudio. 2014. “Bibliographies and Citations.”

Tversky, Amos, and Daniel Kahneman. 1981. “The Framing of Decisions and
the Psychology of Choice.” *Science* 211 (4481). American Association
for the Advancement of Science: 453–58.

Wickham, Hadley. 2016. *Ggplot2: Elegant Graphics for Data Analysis*.
Springer-Verlag New York. <http://ggplot2.org>.
