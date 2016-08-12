---
---
The goal of this POC is to find out whether it is feasible and meaningful for EST to create future documentation for projects/products that use open source software on GitHub using the GitHub Pages mechanism for generating HTML out of markdown "on the fly". For CLC, it was a requirement to brand the Kubernetes documentation and deliver parts of the K8S documentation together with a branded K8S dashboard.

To achieve this, we checked whether and how the following tasks can be achieved:
1. Fork the K8S documentation repository and create a landing page that can be used for CLC as well as for other Fujitsu open source projects
2. Strip down the K8S content for CLC purposes
3. Deliver the K8S dashboard documentation in Fujitsu-branding
4. Avoid the duplication of content
5. Rebase with the K8S repository – maybe automatically solve merge conflicts
6. Include documentation created with DitaWorks on the GitHub Pages


* TOC
{:toc}

## Task 1: Fork the K8S documentation repository and apply Fujitsu branding

The repo can be forked and the mechanism that K8S uses to generate their documentation web site is feasible under the following circumstances:

A new organization had to be created because otherwise no left-hand navigation could be achieved, because K8S uses relative paths for their links. It was not possible to use a project-specific gh-pages in the dashboard repo of EST on GitHub. The landing page can be accessed (in anology to K8S) with the following link:  https://clcdocs.github.io

The Fujitsu branding and the new landing page was achieved as follows:
* A new SASS stylesheet (`branding.sass`) was added and referenced in styles.sass.

* The `index.html` (the landing page) was modified, lots of K8S stuff was removed.

* The `CNAME` file was removed (K8S uses the `CNAME` file to set up a subdomain with their DNS provider). Therefore, the K8S domain name is https://kubernetes.io,  whereas `.github.` is appended to “our” domain name.

* The header and footer (`head-header.html` and `footer.html`) that appear on every page were adapted. In the header, an additional button was defined so that there are now links to the K8S documentation and the CLC documentation home page.

* The following images were changed/added:

  * favicon.png
  * features.png
  * fujitsu_transparent.svg
  * nav_logo.svg
  * nav_logo2.svg

## Task 2: Strip down the K8S content

This can be achieved by editing the `yaml` files. However, links in the original K8S documentation must be checked everywhere. In addition, the content itself must be checked and edited. For example, references to the GCE must be removed.

**Problem**: Rebasing with the original K8S doc repo becomes impossible. The above actions would have to be repeated every time the repo is synchronized with the master.

## Task 3: Deliver the K8S dashboard documentation in Fujitsu branding

The major issue here is that screenshots are included in the `ui.md` file (this is the "dashboard tour"). One solution to this could be to reuse the `ui.md` file and create a separate one (e.g. `ui-fujitsu.md`) and include the branded screenshots there.

But this would mean duplication of content - which we wanted to avoid. Since it is not possible to work with the original K8S sources and re-brand them, we should not spend the effort to re-brand the dashboard documentation, but focus on contributing to the K8S documentation.

## Task 4: Avoid the duplication of content

This is one of the challenging parts. It is related to Task 2 and Task 5, which imho is not possible with a reasonable amount of effort.

## Task 5: Rebase with the K8S repository

If we work with a fork of the K8S repo and strip down the K8S docu to what is supported by CLC, we will never be able to rebase with the original repo, because we will always end up in numerous merge conflicts.

## Task 6: Include documentation created with DitaWorks on the GitHub Pages

For PDF documentation generated out of our XML sources, this is no problem at all.

For HTML content, the following process could be used:

1. Generate the HTML files in DitaWorks.
2. In the doc repo, create a markdown page with the Table of Contents (TOC) for the HTML files. Take the `index.html` file generated with DitaWorks as the basis. An example can be found [here](/docs/clc-overview-html/overview/).
3. Leave the structure as is in the HTML files including images, references, etc.
4. Add the TOC markdown page to the `.yaml` files used for the TOC in the left-hand navigation bar of the documentation pages.

## Conclusion

It is feasible and easily reachable to set up a GitHub Pages repository for EST documentation or whole projects.

A landing page for different projects with links to project-specific documentation could be created and the mechanisms implemented by K8S for generating the documentation.

For open-source projects and maybe for any upcoming new projects, project-specific documentation should be created in markdown format only. For existing projects and existing documentation, there are some converters available, for example:

* XML to markdown: ###
* HTML to markdown: ###

Here is a link to a good page explaining the markdown syntax:
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet


In any case, the generated markdown files must each be checked for correct formatting.

In case that conditions and shared text must be used in the documentation (e.g. in CT-MG), creating documentation in markdown format does not make sense.

I have set up this [demo repository](/docs/poc/demo-repo/) for showing what can be done and how to work with the GitHub Pages.
