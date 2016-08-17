## Instructions for Contributing to the CLC Documentation

To create a copy of our site on your GitHub account, click the **Fork** button in the upper-right area of the screen. Make any changes you want in your fork, and when you are ready to send those changes to us, go to the index page of your forked repository and click **New Pull Request** to let us know about it.

### Staging the Site on GitHub Pages

If you want to see your changes staged without having to install anything locally, change the name of the fork as follows:

    YOUR_GITHUB_USERNAME.github.io

Then make your changes.

When you visit [http://YOUR_GITHUB_USERNAME.github.io](http://YOUR_GITHUB_USERNAME.github.io) you will see a special-to-you version of the site that contains the changes you just made.

### Staging the Site Locally

If you want to run GitHub pages locally, you can set up your environment for viewing you changes on a lightweight web server ([Jekyll](http://www.jekyllrb.com)) that runs on your local machine. This is by far the fastest way to iterate on documentation changes and see them staged. However, you need to perform several installation steps first.

#### Installation on Linux

1) Install Ruby 2.2 or higher. Run these commands:

```shell
apt-get install software-properties-common
apt-add-repository ppa:brightbox/ruby-ng
apt-get install ruby2.2
apt-get install ruby2.2-dev
```

2) Install the GitHub Pages package, which includes Jekyll:

```shell
gem install github-pages
```

3) Clone the CLC documentation repository:

```shell
git clone https://github.com/gertisdemo/gertisdemo.github.io.git
```

4) Make any changes you want. To see your changes locally, go to the directory containing the source code of your clone, and run Jekyll:

```shell
cd gertisdemo.github.io
jekyll serve
```

Your copy of the site can then be viewed at [http://localhost:4000](http://localhost:4000) (or wherever Jekyll tells you).

#### Installation on Windows

Follow [these instructions](https://martinbuberl.com/blog/setup-jekyll-on-windows-and-host-it-on-github-pages/) for installing Jekyll and GitHub Pages on Windows.

### Working with the Documentation Repository

For an introduction to the CLC demo repository, refer to [this](../docs/poc/demo-repo/).
