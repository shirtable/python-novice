This branch uses pelican to build HTML from the lesson source. The development branch containing the lesson source has been pulled into this branch as a git subtree. In this way, the lesson source branch(es) aren't crufted up by pelican config files and can be added as submodules to a workshop website.


Building HTML
=============
To build and view the HTML built from the lesson source, follow these steps:

```
# install pelican and markdown
$ pip install pelican markdown

# build
$ make html
$ make serve # spins up webserver at localhost:8000
```
