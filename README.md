# Crypto Template
Quick and simple template for cryptographic papers, formatted either in LNCS or ACM format, available on [GitHub](https://github.com/emanuelegiunta/crypto_template), originally forked from [Matteo's template](https://github.com/matteocam/lncs-latex-template)

## Installation
In order to use the following template into a empty project/shared repository named `<prj_name>`, first clone this git repo into a local repository and then execute the `install` script
```
    $ git clone git@github.com:emanuelegiunta/crypto_template.git <prj_name>
    $ cd <prj_name>
    $ ./install
```
The installation procedure will ask for a project name (usage of space ` ` is not supported, please use `_` instead) and whether some submodules are required through yes or no questions. Debug mode should only be used for testing purposes.
Finally to link the resulting local repository to your global/shared one, provide an SSH link to the (empty) remote repository you wish to store your project in.

**For Advanced Users**: If you wish to perform changes before the initial commit, you can refuse the auto-push. Be aware though that pushing directly would include this project's history, which is likely undesired. A way to remove it is to soft-reset to root and then commit after the installation through the following commands
```
    $ git reset --soft <commit_hash>
    $ git commit --amend -m "<your_first_commit_message>"
```

## Structure
This template is designed to keep logically indipendendent portions of the document in separate files to minimize conflicts and keep a cleaner commit history. More secifically each project is divided into the following files

1. `main.tex`: Includes all parts of this template and sections. Sections and Subsections' titles should stay here, followed by an `\input{...}`, rather than in those files containing the section body.

2. `sections/`: Should contain sections files imported in `main.tex`. To minimize conflicts it's recommended to use a file per section or subsection

3. `settings/flags.tex`: Contains several flags which allow to easily control the document version. A flag `flag` is by default False, and can be set to True with `\flagtrue`. More in detail, currently supported flags are:
    - `FullVersion`: If true, render the paper in LNCS eprint version (wide page)
    - `Comments`: If true, comments are displayed in the main document
    - `TableOfContents`: If true, generate a Table of Contents after the title
    - `Anonymous`: If true hides authors' names
    - `LNCS`/`ACM`: One and only one of these flags can be true. Specifies if the paper is in LNCS formatting style or in ACM style

4. `settings/settings.tex`: For document class, package inclusion and template specific adjustments. Any global impostation (`tikz`, `pgfplots`, ...) should appear here.

5. `settings/commands.tex`: List of macros. Custom macros should be placed on top of the document.

6. `settings/metadata.tex`: Authors and Institution metadata. Currently this information has to be manually inserted both according to the LNCS and ACM package (if both style are required).

7. `settings/bibliography.bib`: List of references.

8. `beamer.tex`: Create a beamer presentation using given metadata and custom commands. Beamer style can be modified in `settings.tex` in the document class section.