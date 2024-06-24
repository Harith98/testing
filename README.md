# API Management Docs

This repository is used to maintain the "API Management" documentation. You can find the rendered results on the documentation site:

*Azure hosted*
- N/A

*Github Page*
- https://pages.code.bbraun.io/IT-BS-MuleSoft/mulesoft-docs/

## Maintaining Documentation

In general, **all documentation shall be written in [Markdown](https://github.github.com/gfm/#what-is-markdown-)**, and in particular
[GitHub Flavored Markdown](https://github.github.com/gfm/) shall be used.

Markdown offers the opportunity for digital product teams to create structured documentation which is readable without any renderer and can
be put easily besides the product team's source code. Thus the documentation is also version controlled and always set in context to the
product without any media-break.

In addition it's recommended to use GitFlow for reviewing and publishing changes.

Documentation can then be rendered to different formats, like HTML or PDF over Continuous Integration and published to a website/document
management system with the help of Continuous Delivery.

## Writing in Markdown

It is recommended to use a lean IDE, like [VSCode](https://code.visualstudio.com/), which features Markdown editing out of the box, and in
addition the [Markdown All-in-One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) extension.

A comprehensive guide [How to write Markdown in VSCode](https://code.visualstudio.com/docs/languages/markdown), available on the VSCode
website dives into features like *Preview* or *Outline*.

Valuable and comprehensive resources are, for a start the [GitHub Basic Writing and Formatting Syntax
Guide](https://docs.github.com/en/github/writing-on-github/basic-writing-and-formatting-syntax), followed by the [GitHub Mastering Markdown
Guide](https://guides.github.com/features/mastering-markdown).

## Style Guide

- Headlines/section titles should use `title case` styling. E.g.: `Description of the Service`. Helper: [https://titlecaseconverter.com](https://titlecaseconverter.com)

## Jekyll Site Rendering

The content of this repository gets rendered and published as a static website using [Jekyll](https://jekyllrb.com) as a static site generator.

Jekyll converts the markdown files into HTML pages and generates a navigation structure for it. To be able to do this Jekyll needs a bit of
additional metadata on each page. This is called [Front Matter](https://jekyllrb.com/docs/front-matter/).

### Front Matter Metadata

The [Front Matter](https://jekyllrb.com/docs/front-matter/) is a block of YAML on top of the markdown file:

```yaml
---
layout: default
title: Writing Documentation
---
```

This tells Jekyll how to render and where to place the file in the generated site. Here for example `layout` defines which layout template
Jekyll should use and `title` is the title of the page used for the HTML `title` tag and for the navigation structure.

#### Just the Docs Theme

On top of Jekyll the site uses the [Just the Docs](https://pmarsceill.github.io/just-the-docs/) theme to create a nice looking layout and
navigation structure.

##### Navigation Structure

The theme is able to create a navigation structure with three levels. Nesting pages is done with additional *Front Matter* attributes:

```yaml
---
grand_parent: Guidelines
parent: Security
nav_order: 1
---
```

Check the [theme documentation](https://pmarsceill.github.io/just-the-docs/docs/navigation-structure/) on details about this feature.

##### Automatic Table of Contents

The theme allows to generate a *Table of Contents* based on the markdown sections automatically. To enable this, put the following block
into your page:

```html
<details closed markdown="block">
  <summary>
    Table of contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>
```

You can place `{: .no_toc }` below a headline to exclude it from the generated ToC:

```
# Main Title
{: .no_toc }
```

#### Document Stamping

The build process "stamps" the each markdown file with the modification date, file name and Git commit SHA each time a pull request gets
merged into the `master` branch. Jekyll renders this information as a metadata block on the bottom of the generated page.

To enable this, to the following *Front Matter* attributes to your page:

```yaml
file:
date:
commit:
```

The build process will then fill them with the appropriate data.

Using this is mandatory for content pages but should be omitted for `index.md` files used as section start pages.

## Git Workflow

To update the documentation create a branch starting from `master` and merge updates from your branch back into `master` using a pull request.

## Using the Development Container

This repository contains a [Development Container](https://code.visualstudio.com/docs/remote/containers) configuration. You can use this to
start working on the documentation in a preconfigured environment including the required Jekyll setup.

Before using the devcontainer make sure you have `Git Credential Manager` installed. The Git Credential Manager stores Personal Access Tokens (PAT) and makes them available to the container.

- [Windows: Install Git Credential Manager](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git?platform=windows)
- [Linux: Install Git Credential Manager](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git?platform=linux#git-credential-manager)
- [Mac: Install Git Credential Manahger](https://docs.github.com/en/get-started/getting-started-with-git/caching-your-github-credentials-in-git?platform=mac#git-credential-manager)
  
This is required for the container to pull the theme gem from https://code.bbraun.io/Digital-Foundation/bbraun-jekyll-theme.

When opening the repository in *VS Code* it will ask to reopen it in a container (Docker required). Accepting this for the first time will
take some time to build the container but any further start will happen instantly.

As zscaler is interceptring the request and serves its own certificate we have to import it into the trust store
```sh
sudo cp zscaler_root_ca.pem /usr/local/share/ca-certificates/zscaler.crt
```

Afterwards run 
```sh
sudo update-ca-certificates
```

After the first start you need to update the Ruby Gems for Jekyll:

```sh
bundle install
```

Then start the development server:

```sh
bundle exec jekyll serve
```

Accept the offering to open `http://localhost:4000` in a local browser. You can now start to edit the documentation and preview the rendered
changes.
