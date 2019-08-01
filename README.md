# The UChicago Data 8 Jekyll textbook

This repository holds UChicago's fork of the Data 8 Berkeley textbook.

To date (summer of 2019) there should be no *content* changes in the publishing branch, `gh-pages`, rather only changes to [\_config.yml](_config.yml) to point to UChicago's Jupyterhub and to define the correct host. No deployment steps are needed as it is handled by Github Pages. 

## Adaptation to pandas

The branch `pandas` is intended to contain work to adapt the textbook to the [pandas](https://pandas.pydata.org/) library, (in lieu of the Berkeley Data 8 class library, [datascience](https://github.com/data-8/datascience)).

### To note

In support of the latest version of [Jupyter Book](https://jupyter.org/jupyter-book/), all pages generated from Jupyter Notebooks must be rebuilt. This does not necessarily require supervision &ndash; `jupyter-book build` will just do this. However, as such, they may come out looking *slightly* different.

Most important, the process for indicating to Jupyter Book / Jekyll that a cell should be hidden has changed. Rather than responding to a first-line comment such as `# HIDDEN`, the pipeline requires that such cells are **tagged** in the notebook. To merely hide the cell input, tag the cell: `hidecode`. More typically, to hide the cell's input and output entirely, tag it: `removecell`.

### Current status

Chapters 1 through 4 have been rebuilt, and adapted to `pandas` where necessary, (sections 1.3, 1.3.1, 1.3.2 and 3.4).

Rebuilding of Chapter 5 has not yet been committed; (however, its contents, as built by a previous version of `jupyer-book`, are nonetheless fine).

Chapter 6 has been partially rebuilt and adapted to `pandas` (sections 6, 6.1 and 6.2). Sections 6.3 and 6.4 remain to be adapted.

Chapters following 6 remain to be rebuilt as well.

See below for the changelog of work performed to date to rebuild and adapt this textbook:

  f3bd408 regenerated Gemfile.lock
  6b85083 Pandas rewrite and rebuild of chapter 6.2: Selecting Rows
  6597b49 Pandas rewrite and rebuild of chapter 6.1: Sorting Rows
  c2946d1 Pandas rewrite and rebuild of chapter 6 introduction as "DataFrames"
  1992a43 rebuild of chapter 04
  6032aeb Pandas rewrite and rebuild of chapter 3.4 as Introduction to DataFrames
  2eccab4 rebuild for chapter 3.3: Calls
  bbb7ede rebuild for chapter 3.2.1: Growth
  23f87e1 rebuild for chapter 3.2: Names
  4c540f1 rebuild for chapter 3.1: Expressions
  4da536f tweaked docstring in example in chapter 1.3.2
  8e89b4f Pandas rewrite and rebuild for chapter 1.3.2: Another Kind of Character
  c29098e Pandas rewrite and rebuild for chapter 1.3.1: Literary Characters
  ae8eb1b build of chapter 1.3 introduction: Plotting the Classics
  f433d5a Pandas rewrite for chapter 1.3 introduction: Plotting the Classics
  1a52374 update base template jekyllmd.tpl to support jupyter-book updates
  3daee41 fixed Makefile help errors

### Process outline

See the original documentation, and its links, below, for more general information.

(Note: Because we have *not* attempted to host this textbook anywhere but through Github Pages, our deploy process is as simple as pushing content changes in the `_build/` directory to the `gh-pages` branch. The section regarding the custom domain, inferentialthinking.com, does not currently apply.)

This work was performed using:

* Python library `jupyter` version `1.0.0`
* Python library `jupyter-book` version `0.5.1`
* Docker image `emdupre/jupyter-book` version `6886a2e14fe5`

Following the general procedure:

1. Start the Jupyter server: `jupyter notebook`
1. To update an (interactive) textbook page, update its Jupyter notebook under the `content/` directory
1. To generate the plain-text (Markdown) format of this page from that notebook: `jupyter-book build .`
1. Optional: preview the published content locally (see below)
1. Commit changes under directories `content/` and in `_build/`

Files changed typically include at least a Markdown (`.md`) file; and, if this page is interactive and backed by a Jupyter notebook, then a notebook (`.ipynb`) file as well. Builds of notebooks containing graphs may also generate images, such as `.png` files.

If you push to a branch for which Github pages is configured, (typically `gh-pages`), then the live Web site will update promptly.

#### Previewing published output via Docker container

##### One-time set-up

Retrieve the Docker image:

  docker pull emdupre/jupyter-book

Optionally, create a Web server script (say, `serve`):

  #!/bin/sh
  SCRIPT="$(readlink -f "$0")"
  REPO="$(dirname "$SCRIPT")"
  
  docker run --rm --security-opt label:disable  \
     -v "$REPO":/srv/jekyll \
     -p 4000:4000 \
     -it -u 1000:1000 \
     emdupre/jupyter-book bundle exec jekyll serve --host 0.0.0.0

##### Running the server

Run the script:

  ./serve

or the underlying `docker run` command (above).

A preview of the published content is then available at `http://0.0.0.0:4000/textbook/`.

[See also](https://jupyter.org/jupyter-book/guide/03_build.html#building-your-site-locally-with-containers-docker)


Everything below this line is from the original data8 textbook README.

-------

All textbook content is primarily stored in Jupyter notebooks in the `content/` folder.
This can be converted to Jekyll-ready markdown and served on github pages.

## How this repository is deployed to `inferentialthinking.com`

The Data 8 textbook has a slightly more complex deploy process. This is because
[GitHub doesn't work well for using a custom domain name for an organization's non-root
repository](https://help.github.com/articles/custom-domain-redirects-for-github-pages-sites/).

So, here's how the textbook deploy works:

* The textbook at `inferentialthinking.com` is actually being served from this repository:

  https://github.com/inferentialthinking/inferentialthinking.github.io

  **You should not ever directly edit the inferentialthinking.github.io repository**
* Updates to the textbook should be made at **this** repository (`github.com/data-8/texbook`)
* When you make a change to this repository and push it to the `data-8/textbook` gh-pages
  branch, these changes should automatically be copied to https://github.com/inferentialthinking/inferentialthinking.github.io.
* This is done with CircleCI, and the [configuration for this can be found](.circleci/config.yml)

## Building the textbook
Here are steps to get started building the textbook on your own machine:

1. **Install the jupyter-book command line tool**. This allows you to create
   and modify Jupyter Books:

   ```
   pip install jupyter-book
   ```

2. **Follow the build instructions on the Jupyter Book guide**. The guide
   has information for how to use the Jupyter Book CLI to build this book.
   You can find the [Jupyter Book build instructions here](https://jupyter.org/jupyter-book/guide/03_build.html#build-the-books-markdown).

**To preview your built site** using Jekyll on your computer, follow
the steps on the [Jupyter Book guide](https://jupyter.org/jupyter-book/guide/03_build.html#build-the-books-site-html-locally-optional).

## Relevant files

An explanation of the various files in this textbook can be found in
the [Jupyter Book guide](https://jupyter.org/jupyter-book/guide/01_overview.html#a-quick-tour-of-a-jupyter-book).
