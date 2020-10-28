# Git hooks :anchor:

This repository contains two useful git hooks which help with workflows pertaining to `python`, `shell`, `R` and `org-mode` developments. 

## Overview :book:

### 1. Pre-commit hook

`pre-commit.sh` contains a useful hook which is, from its name, a workflow that is executed before every commit. The various functions and dependencies in the shell script are described below:

| Function                   | Description                                                                                                         | Dependencies                                      |
| :-------------             | :-------------                                                                                                      | :-----                                            |
| update_python_dependencies | Updates `requirements.txt` to maintain log of python dependencies                                                   | [poetry](https://github.com/python-poetry/poetry) |
| format_shell_scripts       | Formats all shell scripts with consistent indents                                                                   | [shfmt](https://github.com/mvdan/sh)              |
| format_R_scripts           | Formats all R scripts for clean code                                                                                | [styler](https://github.com/r-lib/styler)         |
| convert_org_to_md          | Converts a specific `org` file to github-flavored `markdown`, adds a `TOC` and cleans up `TODO` and `DONE` markers | [pandoc](https://github.com/jgm/pandoc)           |

In addition, we provide a `main` function where the user can decide which of the above functions to use; as well as fine-tune the input parameters.

### 2. Pre-push hook

`pre-push.sh` contains a simpler hook which, from its name, executes a workflow before pushing commits upstream. Here, we provide only one function:

| Function       | Description                                                                                                                                   | Dependencies                                      |
| :------------- | :-------------                                                                                                                                | :-----                                            |
| mirror_branch  | Mirrors a named branch with another main branch. This could be useful to keep one branch up-to-date with another while still offering new features.  | -                                                 |

The names of the main and mirror branches can be specified in the `main` function.

## Usage :cyclone:

In order to initialize both hooks, simply copy both hooks to `./git/hooks/` and remove the `.sh` extension. For example:

```shell
$ cp /path/to/pre-commit.sh ./git/hooks/pre-commit
$ cp /path/to/pre-push.sh ./git/hooks/pre-push
```

These hooks are generally non-invasive, ie. they exit gracefully if dependencies or staged changes are missing. The hooks have been tested to show that they do not interfere with the overall commit or push process in case of any failures.

## Bugs/Issues :bug:

In case of bugs or suggestions for improvements, feel free to open a GitHub issue.

<!--  LocalWords:  Pre md github ie
 -->
