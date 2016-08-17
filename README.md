## Instructions for Contributing to the CLC Documentation

To create a copy of our site on your GitHub account, click the **Fork** button in the upper-right area of the screen. Make any changes you want in your fork, and when you are ready to send those changes to us, go to the index page of your forked repository and click **New Pull Request** to let us know about it.

## Staging the site on GitHub Pages

If you want to see your changes staged without having to install anything locally, remove the CNAME file in this directory and
change the name of the fork to be:

    YOUR_GITHUB_USERNAME.github.io

Then make your changes.

When you visit [http://YOUR_GITHUB_USERNAME.github.io](http://YOUR_GITHUB_USERNAME.github.io) you should see a special-to-you version of the site that contains the changes you just made.

## Staging the site locally

Executing the commands below sets up your environment for running GitHub pages locally. You can then view any changes on a lightweight web server (Jekyll) that runs on your local machine.

This is definitely by far the fastest way to iterate on documentation changes and see them staged. However, you need to perform several installation steps first:

1. Install Ruby 2.2 or higher. If you're on Linux, run these commands:

```shell
    apt-get install software-properties-common
    apt-add-repository ppa:brightbox/ruby-ng
    apt-get install ruby2.2
    apt-get install ruby2.2-dev
```

2. Install the GitHub Pages package, which includes Jekyll:

```shell
	gem install github-pages
```

3. Clone our site:

```shell
	git clone https://github.com/gertisdemo/gertisdemo.github.io.git
```

4. Make any changes you want. Then, to see your changes locally:

```shell
	cd gertisdemo.github.io
	jekyll serve
```

Your copy of the site will then be viewable at: [http://localhost:4000](http://localhost:4000)
(or wherever Jekyll tells you).

The above instructions work on Mac and Linux.
[These instructions](https://martinbuberl.com/blog/setup-jekyll-on-windows-and-host-it-on-github-pages/) are for Windows users.

## GitHub help

If you're a bit rusty with git/GitHub, you might wanna read
[this](http://readwrite.com/2013/10/02/github-for-beginners-part-2) for a refresher.

## Common Tasks

### Edit Page Titles or Change the Left Navigation

Edit the yaml files in `/_data/` for the Guides, Reference, Samples, or Support areas.

You may have to exit and `jekyll clean` before restarting the `jekyll serve` to
get changes to files in `/_data/` to show up.

### Add Images

Put the new image in `/images/docs/` if it's for the documentation, and just `/images/` if it's for the website.

### Include code from another file

To include a file that is hosted on this GitHub repository, insert this code:

<pre>&#123;% include code.html language="&lt;LEXERVALUE&gt;" file="&lt;RELATIVEPATH&gt;" ghlink="&lt;PATHFROMROOT&gt;" %&#125;</pre>

* `LEXERVALUE`: The language in which the file was written; must be [a value supported by Rouge](https://github.com/jneen/rouge/wiki/list-of-supported-languages-and-lexers).
* `RELATIVEPATH`: The path to the file you're including, relative to the current file.
* `PATHFROMROOT`: The path to the file relative to root.

To include a file that is hosted in an external repository, make sure it is added to [/update-imported-docs.sh](https://github.com/kubernetes/kubernetes.github.io/blob/master/update-imported-docs.sh), and run it so that the file gets downloaded, then enter:

<pre>&#123;% include code.html language="&lt;LEXERVALUE&gt;" file="&lt;RELATIVEPATH&gt;" k8slink="&lt;PATHFROMK8SROOT&gt;" %&#125;</pre>

* `PATHFROMK8SROOT`: The path to the file relative to the root of [the Kubernetes repo](https://github.com/kubernetes/kubernetes/tree/release-1.2), e.g. `/examples/rbd/foo.yaml`

## Using tabs for multi-language examples

By specifying some inline CSV in a variable called `tabspec`, you can include a file
called `tabs.html` that generates tabs showing code examples in multiple languages.

<pre>&#123;% capture tabspec %&#125;servicesample
JSON,json,service-sample.json,/docs/user-guide/services/service-sample.json
YAML,yaml,service-sample.yaml,/docs/user-guide/services/service-sample.yaml&#123;% endcapture %&#125;
&#123;% include tabs.html %&#125;</pre>

In English, this would read: "Create a set of tabs with the alias `servicesample`,
and have tabs visually labeled "JSON" and "YAML" that use `json` and `yaml` Rouge syntax highlighting, which display the contents of
`service-sample.{extension}` on the page, and link to the file in GitHub at (full path)."

Example file: [Pods: Multi-Container](http://kubernetes.io/docs/user-guide/pods/multi-container/).

## Use a global variable

The `/_config.yml` file defines some useful variables you can use when editing docs.

* `page.githubbranch`: The name of the GitHub branch on the CLC repository that is associated with this branch of the documentation. e.g. `release-x`
* `page.version` The version of CLC associated with this branch of the docs. e.g. `vx`
* `page.docsbranch` The name of the GitHub branch on the CLC documentation repository that you are currently using. e.g. `master`

This keeps the documentation you are editing aligned with the CLC version you are talking about. For example, if you define a link like the one below, you will never have to worry about it going stale in future documentation branches:

<pre>View the README [here](http://releases.k8s.io/&#123;&#123;page.githubbranch&#125;&#125;/cluster/addons/README.md).</pre>

That, of course, will send users to:

[http://releases.k8s.io/release-1.2/cluster/addons/README.md](http://releases.k8s.io/release-1.2/cluster/addons/README.md)

(Or whatever Kubernetes release that documentation branch is associated with.)

## Branch structure

The current version of the CLC documentation web site is served out of the `master` branch.

All versions of the site that relate to past and future versions will be named after their CLC release number. For example, [the old branch for the 1.1 documentation is called `release-1.1`](https://github.com/kubernetes/kubernetes.github.io/tree/release-1.1).

Changes in the "docsv2" branch (where we are testing a revamp of the docs) are automatically staged here:
http://k8sdocs.github.io/docs/tutorials/

Changes in the "release-1.1" branch (for k8s v1.1 docs) are automatically staged here:
http://kubernetes-v1-1.github.io/

Changes in the "release-1.3" branch (for k8s v1.3 docs) are automatically staged here:
http://kubernetes-v1-3.github.io/

Editing of these branches will kick off a build using Travis CI that auto-updates these URLs; you can monitor the build progress at [https://travis-ci.org/kubernetes/kubernetes.github.io](https://travis-ci.org/kubernetes/kubernetes.github.io).

## Partners
Partners can get their logos added to the partner section of the [community page](http://k8s.io/community) by following the below steps and meeting the below logo specifications. Partners will also need to have a URL that is specific to integrating with Kubernetes ready; this URL will be the destination when the logo is clicked.

* The partner product logo should be a transparent png image centered in a 215x125 px frame. (look at the existing logos for reference)
* The logo must link to a URL that is specific to integrating with Kubernetes, hosted on the partner's site.
* The logo should be named *product-name*_logo.png and placed in the `/images/community_logos` folder.
* The image reference (including the link to the partner URL) should be added in `community.html` under `<div class="partner-logos" > ...</div>`.
* Please do not change the order of the existing partner images. Append your logo to the end of the list.
* Once completed and tested the look and feel, submit the pull request.

## Thank you!
