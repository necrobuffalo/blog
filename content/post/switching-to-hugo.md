+++
date = "2017-04-11T17:10:41-07:00"
title = "Switching to Hugo"

+++

I've been meaning to blog more for quite a while but haven't gotten around to it. Sometimes the ideas come and I just get caught up in fighting with Jekyll or debating whether it's worth the money to set up Ghost again. But I have several assignments due in the next few days and not a lot of time to do them in, so obviously now is the time to procrastinate by trying a new method. Hugo it is![^1]

It took me a bit to find the Getting Started guide. I'd expected it to be under Tutorials on the website, but it was in a separate section, and I didn't notice until after I was led to it by another tutorial. Not a huge deal for me, I still found what I was looking for fairly quickly.

# Installation
Pulled down the latest binary release from GitHub, expanded it, dropped it in my path. Definitely preferable to installing a gem, at least for me personally. I'm not much of a Rubyist, I don't know what gem does and where it puts files, and I shy away from installing things that might have side effects I don't understand unless it's in OS package form.

# Setup
Setup was just as easy as installation. Following instructions, I ran `hugo new site blog` and got a nice clean slate. Hugo doesn't include themes, so at this point I wandered off looking for one and grabbed the darkest one I could find on the theme gallery.[^2] The way themes are handled makes this possible - clone the repository in your `themes` directory and then pass the directory name as a flag. Easier than needing to clone a new theme elsewhere and move old posts into it or perform surgery on your current theme. Once I had my theme ready I started up the server with `hugo serve --theme=darksimplicity --buildDrafts` The server reloads automatically when content changes on disk, including the configuration file.

Starting a new post is also super streamlined. `hugo new post/switching-to-hugo.md` gave me a new file with all the front matter already filled out. I did need to change the casing of the title, but that's fine - maybe I'll even switch to lowercased titles anyway.

The configuration file required minor tinkering at worst. I changed the title and the base URL and that was about it, apart from one change I'll talk about in the Deployment section.

# Deployment
Hugo provides a tutorial on how to deploy to GitHub Pages. There's two ways you can do it - via a `/docs` folder on your master branch or via the separate `gh-pages` branch. Putting generated files in master feels slighly unhygienic, but for a small personal project I'd rather that than have to deal with deploy scripts, so I went with the first option. This meant one last change to my `config.toml`, adding the line `publishDir = "docs"`.
I dropped the standard GitHub Pages CNAME file into `/static`, generated everything with `hugo --theme=darksimplicity`, committed, and pushed my changes. I then changed the source on the project settings page to use `/docs` for the project page. I got a little caught up here because my CNAME was missing a newline at the end and the site was appearing in a broken state at `blog.taron.rip/blog/`[^3] but that's not Hugo's fault.

# Verdict
I had two major pain points with Jekyll, theme management and not being able to autogenerate front matter. Hugo addresses both of these. There's slightly more overhead since Hugo isn't natively supported by GitHub Pages, but for me this is fine - the overhead occurs after writing and not before. At some point maybe I'll also investigate hosting with Netlify, but for now I'm going to put that aside. Between the simplicity and the fact that using it is free, I think I'll be sticking with Hugo for a while.

[^1]: In my defense, I'm taking a writing course this term and badly need the practice.
[^2]: Gotta keep the goth stereotype going, y'know.
[^3]: I'm not actually sure if this was resolved by adding the newline or just time.