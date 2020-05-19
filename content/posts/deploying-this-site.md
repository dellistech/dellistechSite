---
title: "Deploying This Site"
date: 2020-05-18T18:20:19-06:00
---

 It's been a long time coming, but I figured having a place to throw project write-ups, tutorials, and general notes and updates
would come in handy. So I'm officially entering the world of blogging about 15 years late to the party. 
Hopefully I can kick this off without getting too meta. For the first post, I'm going to write about the services that make up this blog. 


## Rationale
I know I felt like it wouldn't be nearly as much fun to just use a pre-built blog such as WordPress or Blogger. After all, I do like to tinker.
I'd also noticed a trend of super light and minimal static blogs popping up on [Hacker News](http://news.ycombinator.com) and thought that might
be a good place to start. After all, most of them seemed to just be Markdown files checked into a git repo, and I am a huge fan of plaintext-ing
all the things. (Mostly due to my Stockholm Syndrome at the hands of Vim.)


Ultimately, I wanted to play around with static site generators, and a blog seemed like the perfect excuse. 
Not to mention that with services like [Netlify](https://www.netlify.com/), I could host a small personal blog for free.
Hugo has a ton of free and premium themes, as well as the ability to write your own if you so choose.  


## Why Hugo?

I ended up going with Hugo because it just handles most of the backend and gets out of the way. While I am just getting started with the blog, 
I can take advantage of Hugo's LiveReload to fiddle with formatting in near-real time. And when I get a little more familiar or want to post a quick update from mobile, it's all just a git push away.

In just an afternoon of tinkering, I had a blog setup and ready to go.

## Getting started with Hugo
While Hugo isn't exactly a single click setup, it isn't too difficult to get up and running, either. 
First, you need to install Hugo.

If you are on Windows and already using [Chocolaty](https://chocolatey.org/), the following one-liner should get you up and running:

``` powershell
choco install hugo -confirm
```

(And if you aren't already using Chocolaty, I highly recommend it. Read about why [here](https://chocolatey.org/docs/why))

Installation on MacOS is a similar story. I'm going to assume you are using [Homebrew](https://brew.sh/). It's as easy as:

``` shell
brew install hugo
``` 
... and you're off to the races. 

Once installed, verify opening a terminal and typing:

``` shell
hugo version
```

You should see something like this:

``` shell
Hugo Static Site Generator v0.70.0/extended windows/amd64 BuildDate: unknown
```

## Create a Hugo site
Hugo has its own command line utility that does a lot of the boilerplate for you. First, you create a new site template:

``` shell
hugo new site <sitename>
```

That should create a new directory with whatever site name you chose. 

## Theme installation

As I wrote earlier, there are hundreds of free themes available, each with varying levels of user-friendliness to get working. You can check them out [here](https://themes.gohugo.io/). 

I ended up going with [HPSTR](https://themes.gohugo.io/hpstr-hugo-theme/), which is a Hugo port of the theme by the same name by Michael Rose.
It looks clean, simple and minimal to me, and wasn't too big of a pain to get started. I just followed the directions [here](https://dldx.org/hpstr-hugo-theme/theme-setup/). 
HPSTR also comes with some example posts in the exampleSite directory that you can use as an example for how to embed different types of content in blog posts. 

I don't feel right adding Google Analytics or anything to my site, but it is nice to see that it's integrated in the theme if you needed it. 

## Adding content

Adding new pages is pretty easy too. Just type:

``` shell
hugo new posts/<post.md>
```

Hugo will add a small header with the post title, date, and a `draft` flag.
Just write your article below in Markdown format, then delete the `draft` flag to mark the post as ready to publish. [Here](https://guides.github.com/features/mastering-markdown/) is a quick reference on Markdown format to get started.

Once you've written your article, just push your changes to your GitHub repo. I'm not going to go over Git basics here, but [this](https://git-scm.com/docs/gittutorial) is a good tutorial for the uninitiated. Keeping your whole blog in a Git repo is important for the next step...


## Netlify

Netlify is dead simple after initial setup. Just sign up for a free account using your GitHub or GitLab account, authorize Netlify to connect to your Github account, and pick your site repo for a new Netlify site. 
If all goes well, it should build and deploy. Netlify will assign a random domain name to your site, but you can point your own domain to your Netlify site.  

The free tier is limited to 300 build minutes per month. My first build was a total of 10 seconds, so I don't anticipate any issues with running out of free build time. 

## Wrapping up

That's about it for the blog service stack. I am looking forward to tinkering with the site as time goes on. This is a really powerful and flexible setup that should be able to evolve along with my needs. 
Hopefully this brief introduction can be of some help if anyone wants to set up their own static site blog.