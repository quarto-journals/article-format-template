# article-format-template (AFT)

Template for creating a new journal article format for Quarto.


## Creating a custom format

- Use this template repo to create a new repository for your format
- Once you are acquainted with the content, remove the resource that are there as example (see below)
- Keep and tweak the template partials that you need
- Add any resource your format will need
- Modify `_extension.yml`
- Modify the skeleton `template.qmd`

## Structure

Format extension files are in `_extensions`. We are using namespace `quarto-journals` and for this template repo our format will be called `aft`.

`_extensions\quarto-journals\aft` contains the following

### Format Metadata

This is in `_extension.yml` is where all the metadata about the format are defined so that Quarto knows what to use. 


### Partials

In `partials` are the `.tex` files that will be used as Pandoc's template. We provide here all the partials supported by Quarto and custom one for this format. 
Quarto allows to provide partials to ease the process of tweaking the default latex Pandoc's template and keeping it up to date. 

This template repo contains all the relevant partials that you can use with Quarto _as example_.

**Only keep the partials that you need to tweak for the format you are creating**

## `.quartoignore`

This files must contain any other folder and file that should not be downloaded to user project when `quarto template install` is used.
`style-guide` folder in this repo is among those.

### Other files

Some resources are included as examples and can be removed

- Example `te.bst` file has been downloaded from https://www.economics.utoronto.ca/osborne/latex/TEBST.HTM (http://econtheory.org/technical/te.bst) - Licence [LPPL](https://www.latex-project.org/lppl/)

- `aft.cls` is a copy of `article.cls`, the one provided in LaTeX installation renamed as example.  (at `kpsewhich article.cls`) (Licence LaTeX Project Public License)

- `custom.scss` is a style file to have a custom theme for our HTML format

- `filter.lua` and `shortcodes.lua` are Lua Filter to use within our format and made available to Quarto by our Extension.

- `bibliography.bib` is provided as example for `template.qmd`