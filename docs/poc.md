---
---
The goal of this POC is to find out whether it is feasible and meaningful for EST to create future documentation for projects/products that use open source software on GitHub using the [GitHub Pages](https://pages.github.com/) mechanism for generating HTML out of markdown "on the fly". For CLC, it was a requirement to brand the Kubernetes documentation and deliver parts of the K8S documentation together with a branded K8S dashboard.

To achieve this, we checked whether and how the following tasks can be achieved:

* TOC
{:toc}

## Task 1: Fork the K8S documentation repository and apply Fujitsu branding

It was possible to fork the `kubernetes.io` repository and apply Fujitsu branding. The mechanism that K8S uses to generate their documentation web site can be reused under the following circumstances:

A new organization (clcdocs) was created. First, we tried to set up a GitHub Pages project (gh-pages) in the dashboard repository of EST on GitHub. However, in this case no left navigation could be achieved because K8S uses relative paths for their links.

The landing page can be accessed (in anology to K8S) with the following link:  https://clcdocs.github.io

The Fujitsu branding and the new landing page was achieved as follows:

* A new SASS stylesheet (`branding.sass`) was added and referenced in `styles.sass`.

* The `index.html` (the landing page) was modified, lots of K8S stuff was removed.

* The `CNAME` file was removed (K8S uses the `CNAME` file to set up a subdomain with their DNS provider. Therefore, the K8S domain name is https://kubernetes.io,  whereas `.github.` is appended to “our” domain name).

* The header and footer (`head-header.html` and `footer.html`) that appear on every page were adapted. In the header, an additional button was defined so that there are now links to the K8S documentation and the CLC documentation home page.

* The following images were changed/added:

  * favicon.png
  * features.png
  * fujitsu_transparent.svg
  * nav_logo.svg
  * nav_logo2.svg

The clcdocs repository can now be used for CLC as well as for other Fujitsu open source projects. Further adaptions to the styles are easibly feasible.

## Task 2: Strip down the K8S content for CLC purposes

This can be achieved by editing the `yaml` files in which the content of the web site is defined.
However, there are the following drawbacks:

* links in the original K8S documentation must be checked everywhere.

* The content itself must be checked and edited. For example, references to the GCE must be removed.

* Rebasing with the original K8S repository becomes impossible. The above actions would have to be repeated every time the repository is synchronized with the master.

## Task 3: Deliver the K8S dashboard documentation in Fujitsu branding

Since the dashboard is to be available in Fujitsu branding, the documentation should also be delivered in Fujitsu branding. The major issue with the dashboard documentation is that it contains screenshots ([dashboard tour`](/docs/dashboard/ui/)). One solution to this could be to reuse the `ui.md` file and create a separate one (e.g. `ui-fujitsu.md`) and include the branded screenshots there.

But this would mean duplication of content - which we wanted to avoid. Since it is not possible to work with the original K8S sources and re-brand them, we should not spend the effort to re-brand the dashboard documentation, but focus on contributing to the K8S documentation.

## Task 4: Avoid the duplication of content

This was one of the most challenging tasks. It is related to Task 2 and Task 5, which turned out to be impossible to achieve with a reasonable amount of effort.

## Task 5: Rebase with the K8S repository

If we work with a fork of the K8S repository and strip down the K8S documentation to what is supported by CLC, we will never be able to stay in sync with the original repository. Rebasing with the K8S repository always ends up in numerous merge conflicts - and the actions mentioned in Task 2 always have to be repeated.

## Task 6: Include documentation created with DitaWorks on the GitHub Pages

For PDF documentation generated out of our XML sources, this is no problem at all ([PDF access](/docs/clc-pdf-manuals/clc-pdfs/)).

For HTML content, the following process can be used:

1. Generate the HTML files in DitaWorks.
2. In the clcdocs repository, create a markdown page with the Table of Contents (TOC) for the HTML files. Take the `index.html` file generated with DitaWorks as the basis. An example can be found [here](/docs/clc-overview-html/overview/).
3. Leave the structure as is in the HTML files including images, references, etc.
4. Add the TOC markdown page to the `.yaml` file defining the content of the left-hand navigation bar.

## Conclusion

It is not possible to use a fork of the K8S repository and rebrand it for Fujitsu. The branded repository cannot stay in sync with the K8S repository.

It is feasible and easily reachable to set up a GitHub Pages repository for EST documentation or whole projects. For an example, refer to the [clcdocs repository](/docs/poc/demo-repo/).

A landing page for different projects with links to project-specific documentation could be created and the mechanisms implemented by K8S for generating the documentation.

For open-source projects and maybe for any upcoming new projects, project-specific documentation should be created in markdown format only. For existing projects and existing documentation, it makes sense to generate HTML and then convert to markdown using a [converter](http://pandoc.org/try/). I could not find any useful converter for XML to markdown though.

In any case, the generated markdown files must each be checked for correct formatting.

In case that conditions and shared text must be used in the documentation (e.g. in CT-MG), creating documentation in markdown format does not make sense.

Here is a link to a good page explaining the markdown syntax:
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
