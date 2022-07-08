# article-format-template (AFT)

Template for creating a new journal article format for Quarto.

This repository is a [Github Repository Template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template) that you should use as a starter to create a new extension format. Click on the "Use this template" button at the top ! 

## Structure of this repository

Format extension files are in `_extensions` and for this template repo our format will be called `aft`.

### `_extensions\aft` 

In this folder you'll find everything that defines the extensions which could be installed using `quarto install extension` or be part of the template when using `quarto use template`

#### Format Metadata

This is in `_extension.yml` is where all the metadata about the format are defined so that Quarto knows what to use.

> **Adapt this file for you own template**

#### Partials

In `partials`, there are the `.tex` files that will be used as Pandoc's template. We provide here all the partials supported by Quarto and custom one for this format. Quarto allows to provide partials to ease the process of tweaking the default latex Pandoc's template and keeping it up to date.

This template repo contains all the relevant partials that you can use with Quarto _as example_. We only tweaked `title.tex` to show the usage of a custom partials called `_custom.tex`

> **Only keep the partials that you need to tweak for the format you are creating**

If you need to completely change the default template (i.g customizing partials is not enough), then you need to provide your own template to Pandoc based on [`template.tex`](https://github.com/quarto-dev/quarto-cli/blob/main/src/resources/formats/pdf/pandoc/template.tex) and also using partials or not. This can be provided using the `template` YAML key in `_extension.yml` for Quarto to use it. 

> **This is considered advanced configuration as it will be harder to maintain than only using partials but could be required for some specific format. Be aware that this may lead to loose some Pandoc or Quarto features tied to default `template.tex` content if you remove some specific parts**

#### Lua Filters

Most of the time, custom formats will need Lua filters to provide specific feature like cross format supports or provides custom shortcodes through the Quarto extension mechanism. Those filters will be available to the user and could be used in the custom formats (according to `_extensions` metadata). 

We have provided two examples: 

    - `color-text.lua`, a Lua filter used to add color to inline text for PDF and HTML outputs using the same Markdown syntax
    - `shorcodes.lua`, a Lua filter which follow [Quarto custom shortcodes](https://quarto.org/docs/authoring/shortcodes.html#custom-shortcodes) guidelines to provide a `{{< LaTeX >}}` shortcode to nicely print LaTeX in PDF and HTML. 

> **Remove or replace with your own Lua filters**

#### Format resources

Resources required by the format needs to be available. We have provided two examples: 

- `te.bst` is a biblio style file for demo. It has been downloaded from https://www.economics.utoronto.ca/osborne/latex/TEBST.HTM (http://econtheory.org/technical/te.bst) - Licence [LPPL](https://www.latex-project.org/lppl/)

- `aft.cls` is a dummy class file for this example format. It is a copy of official `article.cls`, the one provided in LaTeX installation (i.e at `kpsewhich article.cls`) and renamed as example (Licence LaTeX Project Public License)

- `custom.scss` is a style file to have a custom theme for our HTML format so that our Lua filter feature `color-tex.lua` works.

Those files are referenced within the `_extension.yml` to be used with our example format.

> **Remove and replace with your own resources**

### `.quartoignore` 

Sometimes it is useful to have some files only needed for reference or for development. They should be available in the source repository but not downloaded to the user when `quarto use template` is used.

> **Use `.quartoignore` to register such file and folder (one file or folder per line)**

### `style-guide` folder

For `quarto-journals` format, use `style-guide` folder to include any documentation and resourced used for format creation, like a journal style guide or original `.tex` template. This folder is already added in `.quartoignore` in this example repo.

> **Remove, rename or add to this folder**

### `template.qmd`

This file is the template document that shows how to use the custom format. It will be downloaded with other resource by `quarto use template`, and even offered to be renamed if the name `template.qmd` is used. 

This file will usually use the custom format (here `aft-pdf` and `aft-html`) and show how to use the template. When you'll copy this template, you should be able to render this document to the demo format. 

> **Adapt this file to provide a suitable template for your custom format**

### Other files

Other files are needed by the template and are usually user provided - they are not part of the custom format. 

Here `bibliography.bib` is here to demo the usage of the bst file from the custom format.

> **Remove this file and provide a suitable one for your template**

## Checklist: Creating a custom format

Here is the checklist to help you know what to modify:

- Use this template repo to create a new repository for your format (Click on "Use this template" to create new github repo)
- Once you are acquainted with the content, remove the resources that are there only as example (see above)
- Keep only the template partials that you need to tweak, and add custom ones if needed
- Add any Lua filters for shortcodes and other that would be useful to create the expected output format
- Add any external resource your format will need, and that should be part of the extension format that will be downloaded,
- Check `_extension.yml` is updated correctly
- Modify the skeleton `template.qmd` to your format and add any required resources to be downloaded to user.
- Check `.quartoignore` is updated which everything that should not be downloaded.

<!-- TO KEEP IN YOUR NEW FORMAT --> 

## Usage

Download the extensions and its template `.qmd` using

````powershell
quarto use template quarto-journals/article-format-template
````

Install the extension format only using 

````powershell
quarto install extension quarto-journals/article-format-template
````
