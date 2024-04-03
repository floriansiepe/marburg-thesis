[![Build Status](https://github.com/floriansiepe/marburg-thesis/workflows/template/badge.svg)](https://github.com/floriansiepe/marburg-thesis/actions)

# Disclaimer

This is any unoffical thesis template for the [Philipps University of Marburg](https://www.uni-marburg.de/ "Philipps Universität Marburg"). The author is not related in any form to the university and no guarrantee can be given, that the here implemented specifications meet a certain guide line, that might be valid for your department. **Before using it, make sure your department agrees with this template**.

---

# marburg-thesis

This LaTeX-template might be used to write a bachelor or master thesis at the Computer Science department at [Philipps University of Marburg](https://www.uni-marburg.de/ "Philipps Universität Marburg"). All the credits of this awesome work belong to [Andre Miedé](http://www.miede.de/ "Prof. Dr. Andre Miedé") (see [repo](https://bitbucket.org/amiede/classicthesis/wiki/Home)) and [Michael Bredel](http://www.bredel.at). However, mostly colors and logos have been changed to meet the Marburg style guide.

The documentation below is taken from the [Michael Bredel's thesis template repository](https://github.com/mbredel/thesis-template). Only links have been adapted and the chapter for Github Actions has been added.

## Table of contents

- [Disclaimer](#disclaimer)
- [marburg-thesis](#marburg-thesis)
  - [Table of contents](#table-of-contents)
  - [Configuration](#configuration)
    - [thesis.tex](#thesistex)
        - [Two-sided vs. one-sided](#two-sided-vs-one-sided)
        - [Bibliographies](#bibliographies)
        - [Language](#language)
        - [Table of content, figures, tables, listings, and acronyms](#table-of-content-figures-tables-listings-and-acronyms)
    - [hdathesis-config.tex](#hdathesis-configtex)
        - [Personal data](#personal-data)
      - [Umlauts](#umlauts)
    - [classicthesis-config.tex](#classicthesis-configtex)
  - [Expose](#expose)
  - [Usage](#usage)
    - [Writing abstracts](#writing-abstracts)
    - [Adding content](#adding-content)
    - [Adding graphics](#adding-graphics)
    - [Changing the Citation Style](#changing-the-citation-style)
    - [Compiling the LaTeX source code](#compiling-the-latex-source-code)
    - [Using Docker](#using-docker)
    - [Using Github Actions](#using-github-actions)
  - [Known issues](#known-issues)
  - [License](#license)
  - [Acknowledgements](#acknowledgements)

## Configuration

The LaTeX template can be modified and configured easily using a very limited number of files, namely _classicthesis-config.tex_, _hdathesis-config.tex_, and _thesis.tex_. Only use these three files to modify your LaTeX thesis. Please _DO NOT_ modify the actual LaTeX code for your thesis (as this becomes quite complex and consumes a lot of time). 
Please find a brief description of the various configuration options below:

### thesis.tex

The _thesis.tex_ file contains the basic structure and all the chapter-files that contain the actual content of your thesis. Thus, you have to modify this file in order to configure some basic stuff like the language of your thesis. The subsequent section ["Adding content"](#adding-content) explains how to add content.

##### Two-sided vs. one-sided

The default output of the LaTeX thesis template is a single-sided style that also has to be printed that way. In case you want to print two-sided, you have to add the _twoside_ option in the _\documentclass_ definition at line 35:

```
\documentclass[ openright,titlepage,numbers=noenddot,headinclude,twoside,%
                footinclude=true,cleardoublepage=empty,abstractoff,%
                BCOR=5mm,paper=a4,fontsize=11pt,%
                ngerman,american,%lockflag%
                ]{scrreprt}
``` 

You may also adapt the paper size (_paper=a4_) and the font size (_fontsize=11_) if necessary.

##### Bibliographies

By default all bibliographies that can be referenced in the thesis are put into the _bibliography.bib_ file in the root directory of the LaTeX sources. However, if you want to use additional bibliography files, you may add them to the bibliograph section (starting at line 47) in _thesis.tex_

```
%*************************************************************************
% Bibliographies
%*************************************************************************
\addbibresource{bibliography.bib}
.... ADD YOUR FILES HERE ...
```

##### Language

The default language of your thesis is German. If you want to switch to English, you have to modify the language selection from _ngerman_ to _american_ at line 63.

```
\selectlanguage{american} % ngerman, american
```

While this thesis template supports umlauts, i.e. ÄÖÜäöüß, in the main text of the thesis, there are some issues regarding umlauts on the title page (configured in the personal data at [hdathesis-config.tex](#hdathesis-configtex)). Please see the [umlauts](#umlauts "How to use umlauts in the personal data/on the tile page of the thesis") section for further details and possible solutions.

##### Table of content, figures, tables, listings, and acronyms

By default, the thesis templates prints a lot of table of content, i.e. for figures, tables, listings, and acronyms. You may want to remove such tables if you only have a very limited number, i.e. less than 3-5, of figures, tables, listings, and acronyms. Simply comment the related line in _thesis.tex_ starting at line 81.

```
%\cleardoublepage\include{frontbackmatter/Figures}
%\cleardoublepage\include{frontbackmatter/Tables}
%\cleardoublepage\include{frontbackmatter/Listings}
%\cleardoublepage\include{frontbackmatter/Acronyms}
```

### hdathesis-config.tex

The _hdathesis-config.tex_-file allows to configure the usual stuff needed for a thesis at h_da. Namely, you can configure the title of your thesis, your name, the names of your supervisors, dates, etc. Thus, you MUST touch this file and configure it accordingly.

##### Personal data

This is where you have to place all the personal stuff of your thesis, starting at line 7.

```
\newcommand{\myTitle}{A Classic Thesis Style\xspace}
\newcommand{\mySubtitle}{An Homage to The Elements of Typographic Style\xspace}
\newcommand{\myDegree}{Bachelor of Science (B.Sc)\xspace}
\newcommand{\myName}{Your Name\xspace}
\newcommand{\myId}{Matrikelnummer\xspace}
\newcommand{\myProf}{Prof. Dr.-Ing. XY\xspace}
\newcommand{\myOtherProf}{Prof. Dr. YX\xspace}
\newcommand{\myFaculty}{Fachbereich Mathematik \& Informatik\xspace}
\newcommand{\myUni}{Phillipps Universität Marburg\xspace}
\newcommand{\myLocation}{Marburg\xspace}
\newcommand{\myTime}{20. Dezember 2020\xspace}
\newcommand{\myVersion}{version 4.4\xspace}
```

#### Umlauts

This thesis template supports German umlauts in the main text. However, if you need umlauts on the title page, say in your title, your name, and your professor's name, you have to use the native LaTeX way of writing umlauts. Please see the following table:

| Umlaut | LaTeX way |
|--------|-----------|
| Ä      | {\\"A}     |
| Ö      | {\\"Ö}     |
| Ü      | {\\"Ü}     |
| ä      | {\\"a}     |
| ö      | {\\"o}     |
| ü      | {\\"u}     |
| ß      | {\ss}     |

To write the Title "TOR - Schießen mit Füßen" you have to write "TOR - Schie{\ss}en mit F{\"u}{\ss}en".

### classicthesis-config.tex

The _classicthesis-config.tex_-file allows you to configure stuff that comes with the classic-thesis style, like LaTeX packages used by classic thesis. This is quite advanced stuff already. Thus, you should touch this file only if you know what you are doing. Usually, you can leave the file as it is.

## Expose

This template also comes with a expose. This is usually the first document you work on and where you draft your research and proposed approaches. The _expose.tex_-file should set you up.

## Usage

In the following, we explain how to actually use, i.e. add content and compile, the thesis template to create a nice and shiny PDF file that will please your supervisor.

### Writing abstracts

Every thesis has to have two abstracts; one in German and one in English. Thus, there are two abstract files included in the _thesis.tex_-file. Boths files, called _AbstractDE.tex_ for the German abstract and _AbstractEN.tex_ for the English abstract, are located in the _./frontbackmatter/_ directory.

You have to modify both these files and place your abstract text in _AbstractDE.tex_ and _AbstractEN.tex_ respectively.

### Adding content

By default, the thesis template, i.e. the _thesis.tex_-file, references the _./chapters/thesis/main.tex_-file and _./chapters/thesis/appendix.tex_-file, which contains (includes) some default content files for chapters and appendix from the _./chapters/thesis/_-directory. You have to remove those includes and include your own files. Please note that it is best practice to put all your content in separate files.

```
%*************************************************************************
% Add your content here
%*************************************************************************
\include{chapters/thesis/chapter01}
\include{chapters/thesis/chapter02}
\include{chapters/thesis/chapter03}⏎
```

and

```
%*************************************************************************
% Add your appendix here
%*************************************************************************
\include{chapters/thesis/appendix01}
\include{chapters/thesis/appendix02}⏎
```

For the expose the folder name is `expose` instead of `thesis`.

You may also want to have a look at the _part(...)_ section. You may want to change the titles of the _part(...)_-sections. Alternatively, you remove the _part(...)_ section and the corresponding _cleardoublepage_ the line before.

### Adding graphics

Simlar to [Adding content](#adding-content), the graphics are placed in the folder `thesis` or `expose`. But instead of `chapters` you should look in the `gfx` folder.

### Changing the Citation Style

By default, this template uses the IEEE Alphabetic style for citatons. The IEEE citation style includes in-text citations in square brackets, which refer to the full citation listed in the reference list at the end of the paper. The reference list is organized alphabetically.

However, if you prefer to uses the old IEEE Numeric style for citations you can do so. To this end, you have to change lines 90 and 91 of _classicthesis-config.tex_:

```
 style=numeric-comp,%
 %style=alphabetic,%
```


### Compiling the LaTeX source code

You may compile the hda-thesis template using the ```pdflatex``` and the ```bibtex``` command. In addition, the thesis template repository contains a Makefile that allows you to compile the thesis template using the _make_ tool available on most Unix and Linux systems. Simply type:

```
$ make
```

to compile the LaTeX code into a PDF-file. Moreover, you may use

```
$ make clean
```

to remove all temporary files, which are produced during the compilation process. Finally,

```
$ make bz2
```

generates a bz2-package file, which contains all the source files of your LaTeX code. In case you need to create a PDF-version with embedded fonts you may use

```
$ make publish
```

### Using Docker

The h_da thesis template ships with two Dockerfiles that create [Docker](https://www.docker.com) container used to compile the LaTeX code. One container - built by the [Dockerfile.ci]( https://github.com/mbredel/thesis-template/blob/master/Dockerfile.ci) Docker file - is used by the CI to compile the thesis template and check its integrity at every commit. The other one - created by the [Dockerfile.local](https://github.com/mbredel/thesis-template/blob/master/Dockerfile.local) Docker file - might be used to build the Docker container that allows to compile the LaTeX code on your local machine without the need to install any LaTeX files.

In order to build the Docker image you have to type the following command:

```
$ docker build --tag marburg-thesis --file Dockerfile.local .
```

Creating the image requires a working (and hopefully fast) Internet connection. It may take several minutes to download the required base-images as well as all needed dependencies. You only have to create the image once. Once the image is created, you can run the Docker container by running the following command

```
$ docker run --volume $(pwd):/marburg-thesis/ marburg-thesis && docker rm $(docker ps -lq)
```

inside the root directory containing the LaTeX code. The command mounts the current directory into the Docker container, runs the "publish" make target, and thus compiles the LaTeX code into a PDF file. Finally, the command removes the container again, as it is not needed anymore. You may re-compile the LaTeX code by re-running the "docker run ..." command again.

For more information on Docker, please take a look at the [Docker documentation](https://docs.docker.com/).

### Using Github Actions

This thesis ships with multiple [Github Action workflows](https://github.com/floriansiepe/marburg-thesis/blob/master/.github/workflows) to build the thesis directly on Github. The following workflows are included:

- [latexmk](https://github.com/floriansiepe/marburg-thesis/blob/master/.github/workflows/build-with-latexmk.yml): Builds the thesis with latexmk on any push/pull request on any branch except master
- [Release with latexmk](https://github.com/floriansiepe/marburg-thesis/blob/master/.github/workflows/build-and-publish-release-with-latexmk.yml): Builds the thesis with latexmk on any `v*` tagged commit on the master branch and publishes the pdf on the Github release page

To configure `latexmk` see [.latexmkrc](https://github.com/floriansiepe/marburg-thesis/blob/master/latexmkrc).
## Known issues

* The LaTeX template is tested using [TeXLive](https://www.tug.org/texlive/) which is available for Linux and Windows.
* It has not been tested for [MiKTeX](https://miktex.org/) and [MacTeX](https://www.tug.org/mactex/) yet. Any input on these LaTeX distributions is very welcome.
* The LaTeX template only supports bachelor theses (by default)
* The thesis only supports German and (American) English

## License

The marburg LaTeX thesis template is just like its base template (h_da computer science department) is licenced under GPL v3.0

## Acknowledgements

* Many thanks to Sebastian Jung for his hints on the local Docker approach for compiling the LaTeX code.
