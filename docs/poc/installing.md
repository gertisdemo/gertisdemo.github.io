---
---

If you want to run GitHub pages locally, you can set up your environment for viewing you changes on a lightweight web server ([Jekyll](http://www.jekyllrb.com)) that runs on your local machine. This is by far the fastest way to iterate on documentation changes and see them staged. However, you need to perform several installation steps first.

#### Installation on Linux

1) Install Ruby 2.2 or higher. Jekyll is built from the Ruby coding language. Ruby Gems makes setting up Ruby software like Jekyll easy. Ruby is a package manager.
Run these commands:

```shell
apt-get install software-properties-common
apt-add-repository ppa:brightbox/ruby-ng
apt-get install ruby2.2
apt-get install ruby2.2-dev
```

2) Install the GitHub Pages package, which includes Jekyll (the static site generator):

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
