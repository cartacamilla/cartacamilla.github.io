---
layout: post
read_time: true
show_date: true
title: Building My Personal Website with Jekyll
date: 2025-08-19 10:00:00 -0000
description: A step-by-step guide on creating a personal website with Jekyll, from template selection to customization and deployment
img: /posts/20250819/jekyll_website_building.png
tags: [web development, jekyll, tutorial]
author: Camilla Carta
github: 
mathjax: no
---

### Introduction

Creating a personal website always felt like a massive hurdle for me, especially without relying on platforms like [Wix](https://www.wix.com/), [SquareSpace](https://www.squarespace.com/), or [WordPress](https://wordpress.com/). I wanted something that looked polished, that I could maintain myself without too much effort, and that I could host independently. At the same time, I saw this as a learning opportunity — to gain fine control over the code and understand how HTML, CSS, and static sites actually work.

I was also happy sticking with a static website (at least for now) but wanted a few dynamic features, like an automated contact form and the ability to leave comments under posts. And last but not least, I wanted ideally everything to be open-source and free.

In this post, I’ll walk you through how I built my own website using one of the many freely available Jekyll templates. I’ll share the steps I followed and give you the guidance you need to get started with your own Jekyll-powered site.

### Why Jekyll?

Jekyll is a **static site generator**, which means it takes your content and templates and converts them into a fully static website that can be hosted anywhere. Static sites are fast and easy to maintain, making them ideal for blogs, portfolios, and project pages.

There are several other popular static site generators you might encounter, such as [Hugo](https://gohugo.io/), [Gatsby](https://www.gatsbyjs.com/docs/glossary/static-site-generator/), [Eleventy](https://www.11ty.dev/), and [Next.js](https://nextjs.org/docs/pages/building-your-application/rendering/static-site-generation) (when used in static mode). Each has its strengths: Hugo is known for incredible build speed, Gatsby excels at React integration, and Eleventy is lightweight and flexible.

In my case, I chose Jekyll because of its simplicity and stability, its tight integration with GitHub Pages (which makes deployment effortless), and its large library of themes and plugins. It strikes a nice balance between having control over the code and providing an approachable workflow, especially for someone who wants to focus on learning and customizing without getting lost in too many frameworks.

### Starting from a Template

I tried **many** Jekyll templates before settling on this one, which had most of the features I was looking for. Since I am not an expert in HTML and CSS, I needed something that worked more or less out of the box.
 
In the end, I chose the [Adam Blog 2.0](https://weathered-bread-8229.on.fleek.co/) template, which is GNU licensed and available on [GitHub](https://github.com/the-mvm/the-mvm.github.io).

Templates provide a ready-made structure including HTML, CSS, and JavaScript, which makes it easier to focus on customizing the design rather than building everything from scratch. I personalized the branding, colors, and layout to match my style, and that process resulted in the website you are visiting now.

I find the design pleasing to look at, and the template comes with several built-in features, such as support for Disqus comments under posts and basic SEO integration with Google Analytics. I am still exploring some of these features to see how best to use them. I am not fully convinced by Disqus for example, as it is closed-source, requires a paid plan to remove ads, and raises some privacy concerns.

The template's README contains detailed instructions for installation and customization, so if you are interested in using it, feel free to check it out.

### Installing Jekyll on Linux (Ubuntu and Arch)

Setting up Jekyll on Linux requires a few dependencies. I am currently using Arch Linux, but I will also provide instructions for Ubuntu, as it is the more popular distribution.

- Install Ruby, Bundler, and essential build tools:

```bash
# Specific to Arch Linux
sudo pacman -S --needed ruby ruby-bundler base-devel libffi zlib openssl git protobuf

# Specific to Ubuntu Linux
sudo apt update
sudo apt install -y ruby-full build-essential zlib1g-dev git
```

- Add the Ruby gems bin directory to your `PATH` by adding this line to your `~/.profile` file (adjust the Ruby version if needed):

```bash

# Specific to Arch Linux
echo 'export PATH=$PATH:$HOME/.local/share/gem/ruby/3.4.0/bin/' >> ~/.profile

# Specific to Ubuntu Linux
echo '# Install Ruby Gems to ~/gems' >> ~/.profile
echo 'export GEM_HOME="$HOME/gems"' >> ~/.profileecho '# Install Ruby Gems to ~/gems' >> ~/.profile
echo 'export GEM_HOME="$HOME/gems"' >> ~/.profile
echo 'export PATH="$PATH:$HOME/gems/bin"' >> ~/.profile

echo 'export PATH="$PATH:$HOME/gems/bin"' >> ~/.profile

source ~/.profile
```

- (Optional but recommended) Configure Bundler for project-local gems:

```bash
# keep gems inside the project (nice & reproducible)
bundle config set path '.bundle'

# on some Arch setups, this avoids “precompiled linux gem” mismatches
bundle config set force_ruby_platform true

# make sure the lock knows your platform
bundle lock --add-platform x86_64-linux
```

- Install Jekyll, Bundler and Protobuf:

{% include code_header.html %}
```bash
gem install jekyll bundler google-protobuf
```

- Install all gems and serve the website locally:

```bash

bundle install

bundle exec jekyll serve
```

- Visit http://127.0.0.1:4000/ in your browser to see your website running live. Changes to your files should appear immediately.


### Deploying Your Site on GitHub Pages

Creating a GitHub Page is pretty straightforward. These are the steps I followed to deploy my site. 

#### Create a GitHub repo

If you are using a Jekyll template, you can fork the template repo and rename it. Otherwise, you can create a repo from scratch.

The repo containing your website must be named following the convention `your_username.github.io`. This is the address your website will be deployed to.
If you want a custom domain, you need to create one (and pay for it). For my domain, I use [InfoManiak](https://www.infomaniak.com/en/domains). 

Once the repository is created, you can clone it locally and work offline, testing your site as described in the previous sections.

#### Customizing the Template

Once the template is running locally, the fun part begins: making it truly yours. The template already provides a solid layout and basic functionality, but I wanted the colors and overall branding to reflect my personal style.

Customizing the template mostly involves editing the **CSS files** in the `asset` folder, particularly the `main.css` file. The template conveniently prodives the color palette as variables at the top of the file, so you can easily swap colors by copying theier hex values from any color picking tool. The fonts are also ready to be customized, which makes it really easy to give the site a personal touch. 

The template includes a built-in light and dark theme switch, so  both themes can be customized in the same place and work immediately without any additional setup.

Another key file for customization is the `_config.yaml` file. Here you can update site-wide settings such as the title, description, and logo, as well as configure some template features like the analytics ID, Disqus ID and Mailchimp newsletter setup, and your contact information. Also, do not forget to modify the `url` to your GitHub domain.

I also used the website as an opportunity to experiment with vectorized art with [Inkscape](https://inkscape.org/), which was a fun way to create custom graphics. 

All changes I make are tracked using GitHub, which not only serves as version control system but also automatically publishes the website to my personal domain. 

#### Publishing Your Site

When you push your local changes to GitHub, your website will be updated automatically, usually within 10 minutes. GitHub Pages supports sites up to 1GB in size and 100GB of bandwidth per month, so keep these limits in mind. Also, only personal (non-commercial) sites are allowed!

### Next Steps

Now that the website is up and running, I am exploring ways to add more interactivity and engagement. One of my next goals is to find a suitable **comments system** that respects privacy and works well with a static site. While the template includes Disqus, I am considering open-source alternatives to maintain full control over user data.

Another area I want to enhance is the **newsletter**. I am looking into simple and privacy-friendly tools that can integrate smoothly with Jekyll, allowing readers to subscribe without requiring complex setups. These additions will help turn the website into a more interactive and engaging platform while keeping it lightweight and maintainable.

### Conclusion

Building this website is a fun and educational journey. From choosing a Jekyll template to customizing the design, learning about CSS, and experimenting with vector graphics, every step up to now has taught me something new. Seeing the site come to life on my own domain is incredibly satisfying.  

It’s still a work in progress. I am exploring ways to integrate comments and a newsletter to make the site more interactive, while keeping it lightweight and maintainable.

If you are curious about web development or want a fully customizable, lightweight website, starting from a Jekyll template is a great option. With some patience, a bit of CSS tweaking, and GitHub for deployment, you can have a professional-looking site up and running in a very short time.
