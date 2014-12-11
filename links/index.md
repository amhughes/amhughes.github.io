---
layout: page
title: Links
modified: 2014-07-31T13:23:02.362000-04:00
excerpt: "A collections of links relating to my various projects."
image:
  feature: sample-image-3.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

<section id="table-of-contents" class="toc">
  <header>
    <h3>Overview</h3>
  </header>
<div id="drawer" markdown="1">
*  Auto generated table of contents
{:toc}
</div>
</section><!-- /#table-of-contents -->

## Installation

Minimal Mistakes now requires [Jekyll](http://jekyllrb.com/) 2.2+. Make sure to run `gem update jekyll` if you aren't on the latest version or `gem install jekyll` if this is your first time installing it.

If you are creating a new Jekyll site using Minimal Mistakes follow these steps:

1. Fork the [Minimal Mistakes repo](http://github.com/mmistakes/minimal-mistakes/fork).
2. Clone the repo you just forked and rename it.
3. [Install Bundler](http://bundler.io) `gem install bundler` and Run `bundle install` to install all dependencies (Jekyll, [Jekyll-Sitemap](https://github.com/jekyll/jekyll-sitemap), [Octopress](https://github.com/octopress/octopress), etc)
4. Update `config.yml`, add navigation, and replace demo posts and pages with your own. Full details below.

If you want to use Minimal Mistakes with an existing Jekyll site follow these steps:

1. [Download Minimal Mistakes](https://github.com/mmistakes/minimal-mistakes/archive/master.zip) and unzip.
2. Rename `minimal-mistakes-master` to something meaningful ie: `new-site`
3. Run `bundle install` to install all dependencies (Jekyll, [Jekyll-Sitemap](https://github.com/jekyll/jekyll-sitemap), [Octopress](https://github.com/octopress/octopress), etc)
4. Remove demo posts/pages and replace with your own posts, pages, and any other content you want to move over.
5. Update posts' and pages' YAML to match variables used by Minimal Mistakes. Full details below.
6. Update `_config.yml` and add navigation links. Full details below.

**Pro-tip:** Delete the `gh-pages` branch after cloning and start fresh by branching off `master`. There is a bunch of garbage in `gh-pages` used for the theme's demo site that I'm guessing you won't want.
{: .notice}

---

## Scaffolding

How Minimal Mistakes is organized and what the various files are. All posts, layouts, includes, stylesheets, assets, and whatever else is grouped nicely under the root folder. The compiled Jekyll site outputs to `_site/`.

{% highlight text %}
minimal-mistakes/
├── _includes/
|    ├── _author-bio.html        # bio stuff layout. pulls optional owner data from _config.yml
|    ├── _browser-upgrade.html   # prompt to install a modern browser for < IE9
|    ├── _disqus_comments.html   # Disqus comments script
|    ├── _footer.html            # site footer
|    ├── _head.html              # site head
|    ├── _navigation.html        # site top navigation
|    ├── _open-graph.html        # Twitter Cards and Open Graph meta data
|    └── _scripts.html           # site scripts
├── _layouts/
|    ├── home.html               # homepage layout
|    ├── page.html               # page layout
|    ├── post-index.html         # post index layout
|    └── post.html               # single post layout
├── _posts/                      # MarkDown formatted posts
├── _sass/                       # Sass stylesheets
├── _templates/                  # used by Octopress to define YAML variables for new posts/pages
├── about/                       # sample about page
├── assets/
|    ├── css/                    # compiled stylesheets
|    ├── fonts/                  # webfonts
|    ├── js/
|    |   ├── _main.js            # main JavaScript file, plugin settings, etc
|    |   ├── plugins/            # scripts and jQuery plugins to combine with _main.js
|    |   ├── scripts.min.js      # concatenated and minified _main.js + plugin scripts
|    |   └── vendor/             # vendor scripts to leave alone and load as is
|    └── less/
├── images/                      # images for posts and pages
├── 404.md                       # 404 page
├── feed.xml                     # Atom feed template
├── index.md                     # sample homepage. lists 5 latest posts
├── posts/                       # sample post index page. lists all posts in reverse chronology
└── theme-setup/                 # theme setup page. safe to remove
{% endhighlight %}

---

## Site Setup

A quick checklist of the files you'll want to edit to get up and running.

### Site Wide Configuration

`_config.yml` is your friend. Open it up and personalize it. Most variables are self explanatory but here's an explanation of each if needed:

#### title

The title of your site... shocker!

Example `title: My Awesome Site`

#### url

Used to generate absolute urls in `sitemap.xml`, `feed.xml`, and for generating canonical URLs in `<head>`. When developing locally either comment this out or use something like `http://localhost:4000` so all assets load properly. *Don't include a trailing `/`*.

Examples:

{% highlight yaml %}
url: http://mmistakes.github.io/minimal-mistakes
url: http://localhost:4000
url: http://mademistakes.com
url:
{% endhighlight %}

#### Google Analytics and Webmaster Tools

Google Analytics UA and Webmaster Tool verification tags can be entered under `owner` in `_config.yml`. For more information on obtaining these meta tags check [Google Webmaster Tools](http://support.google.com/webmasters/bin/answer.py?hl=en&answer=35179) and [Bing Webmaster Tools](https://ssl.bing.com/webmaster/configure/verify/ownership) support.

### Navigation Links

To set what links appear in the top navigation edit `_data/navigation.yml`. Use the following format to set the URL and title for as many links as you'd like. *External links will open in a new window.*

{% highlight yaml %}
- title: Portfolio
  url: /portfolio/

- title: Made Mistakes
  url: http://mademistakes.com  
{% endhighlight %}

---

## Adding New Content with Octopress

While completely optional, I've included Octopress and some starter templates to automate the creation of new posts and pages. To take advantage of it start by installing the [Octopress](https://github.com/octopress/octopress) gem if it isn't already.

{% highlight bash %}
$ gem install octopress --pre
{% endhighlight %}

### New Post

Default command

{% highlight bash %}
$ octopress new post "Post Title"
{% endhighlight %}

Default works great if you want all your posts in one directory, but if you're like me and want to group them into subfolders like `/posts`, `/portfolio`, etc. Then this is the command for you. By specifying the DIR it will create a new post in that folder and populate the `categories:` YAML with the same value.

{% highlight bash %}
$ octopress new post "New Post Title" --dir posts
{% endhighlight %}

### New Page

To create a new page use the following command.

{% highlight bash %}
$ octopress new page new-page/
{% endhighlight %}

This will create a page at `/new-page/index.md`

---

## Layouts and Content

Explanations of the various `_layouts` included with the theme and when to use them.

### Post and Page

These two layouts are very similar. Both have an author sidebar, allow for large feature images at the top, and optional Disqus comments. The only real difference is the post layout includes related posts at the end of the page.

### Post Index Page

A [sample index page]({{ site.url }}/posts/) listing all posts grouped by the year they were published has been provided. The name can be customized to your liking by editing a few references. For example, to change **Posts** to **Writing** update the following:

* In `_config.yml` under `links:` rename the title and URL to the following:
{% highlight yaml %}
  links:
  - title: Writing
    url: /writing/
{% endhighlight %}
* Rename `posts/index.md` to `writing/index.md` and update the YAML front matter accordingly.
* Update the **View all posts** link in the `post.html` layout found in `_layouts` to match title and URL set previously.

### Feature Images

A good rule of thumb is to keep feature images nice and wide so you don't push the body text too far down. An image cropped around around 1024 x 256 pixels will keep file size down with an acceptable resolution for most devices. If you want to serve these images responsively I'd suggest looking at the [Jekyll Picture Tag](https://github.com/robwierzbowski/jekyll-picture-tag) plugin[^plugins].

[^plugins]: If you're using GitHub Pages to host your site be aware that plugins are disabled. You'll need to build your site locally and then manually deploy if you want to use this sweet plugin.

The post and page layouts make the assumption that the feature images live in the `images/` folder. To add a feature image to a post or page just include the filename in the front matter like so. It's probably best to host all your images from this folder, but you can hotlink from external sources if you desire.

{% highlight yaml %}
image:
  feature: feature-image-filename.jpg
  thumb: thumbnail-image.jpg #keep it square 200x200 px is good
{% endhighlight %}

To add attribution to a feature image use the following YAML front matter on posts or pages. Image credits appear directly below the feature image with a link back to the original source if supplied.

{% highlight yaml %}
image:
  feature: feature-image-filename.jpg
  credit: Michael Rose #name of the person or site you want to credit
  creditlink: http://mademistakes.com #url to their site or licensing
{% endhighlight %}

### Thumbnails for OG and Twitter Cards

Feature and thumbnail images are used by [Open Graph](https://developers.facebook.com/docs/opengraph/) and [Twitter Cards](https://dev.twitter.com/docs/cards) as well. If you don't assign a thumbnail the default graphic *(default-thumb.png)* is used. I'd suggest changing this to something more meaningful --- your logo or avatar are good options.

**Pro-Tip**: You need to [apply for Twitter Cards](https://dev.twitter.com/docs/cards) before they will begin showing up when links to your site are shared.
{:.notice}
