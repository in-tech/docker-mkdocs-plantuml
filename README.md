mkdocs (docker image)
=====================

Mkdocs including PythonMarkdown PlantUML extension as well as:

* [mkdocs-material](https://squidfunk.github.io/mkdocs-material/)
* [mkdocs-git-authors-plugin](https://github.com/timvink/mkdocs-git-authors-plugin)
* [mkdocs-git-revision-date-localized-plugin](<https://github.com/timvink/mkdocs-git-revision-date-localized-plugin>)
* [mkdocs-pdf-export-plugin](https://github.com/zhaoterryy/mkdocs-pdf-export-plugin)
* [mkdocs-enumerate-headings-plugin](https://github.com/timvink/mkdocs-enumerate-headings-plugin)

This image will provide you mkdocs. Some examples of its usage:

Create a new project
--------------------

    docker run -it --rm -v `pwd`:/data intechdigital/mkdocs new my-project

Serve your project
------------------

As you are inside a docker container, you will need to set the host to `0.0.0.0`:

    cd my-project
    docker run --rm -v `pwd`:/data -p 8000:8000 intechdigital/mkdocs serve -a 0.0.0.0:8000

or just

    docker run --rm -v `pwd`:/data -p 8000:8000 intechdigital/mkdocs

Compile your docs to HTML
-----------------------

    cd my-project
    docker run -it --rm -v `pwd`:/data intechdigital/mkdocs build

If you want to generate them in another place, mount `/data/site` as a volume:

    docker run -it --rm -v `pwd`:/data -v $HOME/Desktop/site:/data/site intechdigital/mkdocs build

PlantUML Usage
--------------

Inside your project file

    site_name: My Site Name
    markdown_extensions:
        - plantuml_markdown:
            server: ''

See the following site for uml usage:
[https://github.com/mikitex70/plantuml-markdown](https://github.com/mikitex70/plantuml-markdown)
