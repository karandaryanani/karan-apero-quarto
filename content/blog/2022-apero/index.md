---
date: 2022-10-05

title: Quarto, Hugo, Apero
subtitle: How to setup a minimal (but pretty) website in the modern era.
author: Cédric Batailler

show_post_date: true
show_author_byline: true

draft: true

summary: |
    Hello world!

format: hugo

freeze: auto
---

I recently noticed that I probably don't spent as much time writing as I should
if I wanted to improve. *This is the kind of thoughts you can get by doing a
PhD*. To adress this problem, I decided to call one of the best tool to
get better at something: practice! Here, an especially appropriate format when
it comes to writing appears to be blogging.

As a first post, I decided to offer a small tour of this website. Or rather,
of how it works. Let's go on an advanture!

# A fresh new start

{{< figure src="img/jan-kahanek-g3O5ZtRk2E4-unsplash.jpg" caption="Photo by Jan Kahánek." >}}

So, to start blogging. The first thing I needed was a website, or rather, a new
website. I had one before, but it did not feel nice anymore. Having to think
about the platform where I would show my pieces of thought was the occasion
to try to build a system that would work for me. Ideally, this system should
be minimal--meaning that it should have as few steps as possible between the
writing of a blog post and its posting, and it should be super easy to show
code running (because that's what I'd like to put here.

In the end, I decided to use some of the pieces of software that I had used
before and adopt trade some other. I would use [Quarto](https://quarto.org/)
to write the blog post and the code it contains, [Hugo](https://gohugo.io/) to
generate a static website, and to ditch my old fashioned Academic theme for
the refreshing [Apéro](https://github.com/hugo-apero/). Here how it works.

## Quarto to write and run the code

You will probably not be surprise that the first step of blogging is writing.

[Quarto](https://quarto.org/) is a newish piece of tech offered by the amazing
software engeneers at [Posit](https://www.rstudio.com/) (ex-RStudio) that will
help me with the writing. Basically, Quarto offers a way to combine text and
code to create documents. Basically, you can run R, Python, or Julia
in a document and decide whether you want it to become a Word document, a PDF
file, or even a markdown document. This would be the first block of my setup.

Indeed, I needed a way to turn code into a blog post. I decided to us Quarto
for to reasons: it is familiar and powerful. First, it is familiar. Quarto
looks a lot like the old [Rmarkdown](https://rmarkdown.rstudio.com/) format
I was used to[^1], which reduces by a fair amount the number of stuff that I
would have to learn. Second, it supports a lot of languages, and even though R
is--and will always remain--my first love, I have to say that I am looking
forward to playing with Python (now that I have figured out how to configure my
environment). Quarto will help me with this polyglot mindset.

In terms of integration with this website, each of my blog post have their own
folder which contains a quarto document document where I write the post (an
`"index.qmd"`). This document mixes both some writing and some code. What Quarto
does is that it runs the code and turn the project into a regular markdown
document (an `"index.md"` ).

In other words, a Quarto countaining a code chunk with
a `read_csv(...)` function in it, will render a markdown file that will show
the actual content of the csv I am opening.

If you want to know more about Quarto, and are familiar with rmarkdown, this
[blog post](https://www.apreshill.com/blog/2022-04-we-dont-talk-about-quarto/)
by Alison Hill is a great introduction.

Now that we have the content, we have to turn it into something nice.

## Hugo to write the website

<!-- REWRITE STARTING HERE ------------------------------------------------ -->

The problem here is to turn a some markdown files into a website. As far as I
know, websites on the Internet still requires some sort of html files so that a
browser can render them. The tool I decided to use is a
[static website generator](https://en.wikipedia.org/wiki/Static_site_generator)
called [Hugo](https://gohugo.io/).

The job of a static website generator, as the name suggests, is to build a website
whose content won't change very often. That would not be the case of your
regular social network which has a feed changing any time you go there. Static
website are mostly used for product pages, documentation, or blogs. A feature that
is especially interesting with a static website is that it does not require
a backend to run. Once the website built, it can live its live by itself
forever. This should hopefully reduce the need for me to learn new things to
put the blog online.

So, back to [Hugo](https://gohugo.io/). The basic idea here is that it will
take my collection of markdown files and turns them into a website. For Hugo
to do its job, The only things I have to do is organize my files onto my
computer in a way that is understable for Hugo. Basically, my blogposts needed
to be on a `content` folder, and I had to put a config file in the root
directory.

In a nutshell, now, all I had to do is run `hugo server` in a terminal for it
to build my website and serve it onto a local server. How convinient?

Note that, of course, there is a bit of tuning to do so that your website
actually looks like something. The first thing is to pick a theme. I
had run a website before with Hugo, and decided to ditch my old theme[^2] for
a fresh new one. I decided to go with the
[Apéro](https://github.com/hugo-apero/hugo-apero) theme because it was pretty,
but also because it was used by a looooot of people that inspire me
([Julia Silge](https://juliasilge.com/) or
[Jesse Mostipiak](https://www.jessemaegan.com/) to name a few).

To use the theme, the only thing I had to do is to put the it in a `/theme/`
folder where my website lives[^3]. Once done, Hugo simply requires you to
[set up the theme in the config file](https://gohugo.io/getting-started/configuration/#theme)
and that's it. My website was living on my computer.

<!-- REWRITE STARTING HERE ------------------------------------------------ -->

## Send everything online

{{< figure src="img/jeremy-bezanger-LUjQCeKE0K0-unsplash.png" caption="Photo by Jeremy Bezanger." >}}

So far, I have a system that worked perfectly ... on my computer. Because I
am not the most functionnal human being, I suspect that if my computer is the
only place where one can see my writing, I wouldn't care about it for a long
time for very long.

To share my website with the rest of the world, I am using two tools, and these
tools will be the last one I will talk about (for now): Github and Netlify.

[GitHub](https://github.com/) is probably one of the website I used the most.
GitHub serves two purposes in my workflow: it allows me to version any piece
of software I write and it hosts a copy of it. This is a place where my
website (or, rather, its source code) exists.
[Netlify](https://www.netlify.com/), on the other hand, is (self-) described
as a platform that allows me to use GitHub to serve my website. In short,
Netlify takes the website's source code, runs the `hugo` command, and
serves the results.

This setup allows any change I make on my computer to be pushed to GitHub if I
want to, and to be live on the Internet within a few minutes (if not seconds).

This setup kind of setup is not uncommon, and has the advantage to be very well
documented online. The Hugo team
[wrote about it](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/),
the Netlify
[wrote about it](https://docs.netlify.com/integrations/frameworks/hugo/), and
if you want to bypass the Hugo step and go straight from Quarto to Netlify,
well the Quarto team
[wrote about it](https://quarto.org/docs/publishing/netlify.html).

## Up to work!

Overall, setting up the website was a bit easier than I expected it. Already
having a website running with a lot of overlapping tech sure helped with the
process, but, in the end I think that I did spent more time looking for a
pretty theme than actually working on the putting the website online.

Now the only thing left to do is blogging. Remember, this was my original
motivation? If everything goes smoothly, you can expect me documenting
some of my project right here! Fingers crossed. 🤞

[^1]: Actually, Quarto and Rmarkdown play well together, and it was a 5 minutes
    job to convert an old Rmarkdown blog post into a new Quarto one.

[^2]: I used to run a website with the Academic theme which was very
    appropriate given my background. Recent changes of the project, however, added
    a tight integration to a publishing plateform that I didn't plan on using.
    To be honnest, I would not recommand using this theme now. The integration
    made the theme almost unusable.

[^3]: Actually, it is a simplification. I
    [forked](https://github.com/cedricbatailler/hugo-apero/) the original theme
    in Github so that I could make some minor tweaks, and I used this new repo as a
    [git subtree](https://www.atlassian.com/git/tutorials/git-subtree) in my
    project.