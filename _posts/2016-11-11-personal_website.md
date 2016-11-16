---
title:  "How is this website built? (Jekyll and Minimal-mistakes theme)"
date:   2016-11-15
layout: single
author_profile: true
comments: true
---

This whole website is built using [**Jekyll**](https://jekyllrb.com/) and theme [**minimal-mistakes**](https://mmistakes.github.io/minimal-mistakes/). 
I had no experience of HTML or CSS language, but still managed to get the website to work. That's just how easy it is to work with **Jekyll**.

I wouldn't go through every step of the process in great detail as that would be too much text. But I'll refer you to corresponding documents which will likely guide you through each of them. 


### Other resource:
- Learning about Github Pages: [Github hosting](http://jmcglone.com/guides/github-pages/)

## Step 1: install _Jekyll_ and _minimal-mistakes_ theme and generate template website

### install _Jekyll_
Type in terminal `gem install jekyll` for installation.    
This should work fine when you have all the dependencies installed. If you run into any issue, go to page [jekyll install](https://jekyllrb.com/docs/installation/).

### install _minimal-mistakes_
It takes a little more work to install the theme.   
You need to first generate a jekyll folder: `jekyll new anyname`. Then a folder named `anyname` is going to be created in your current directory, and it contains all the basic files to make a website.   
Then follow the steps described in [install minimal-mistakes](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/). It basically involves adding some lines to some files in `anyname`, or replacing a file with their version on Github, and removing some files.  
After you run `bundle install`, all the dependencies of **minimal-mistakes** should be successfully installed.


Type `bundle exec jekyll serve`, and then a template website will be locally hosted at [localhost:4000/](localhost:4000/).

It should look something like this:   
![fresh site](/pics/website_tut/fresh.png)

Now there are a lot of stuff you can do. 
Like setting up site title on topleft corner, changing author name, biography, adding social sharings etc. You can find corresponding fields of all of these in `_config.yml` (refer to [configuration](https://mmistakes.github.io/minimal-mistakes/docs/configuration/)).

## Step 2: add pages

Website pages are specified in file `_data/navigation.yml`:

```yml
main:
  - title: "Quick-Start Guide"
    url: /docs/quick-start-guide/
  - title: "Posts"
    url: /year-archive/
  - title: "Categories"
    url: /categories/
  - title: "Tags"
    url: /tags/
  - title: "Pages"
    url: /page-archive/
  - title: "Collections"
    url: /collection-archive/
  - title: "External Link"
    url: https://google.com
```

Each `-` corresponds to one page tab:

- `title` is the page title
- `url` is the link to the file that contains contents of the page

For example if you want to add a new tab `Blogs`, you can add the following two lines to `navigation.yml`:

```yml
	- title: "Blogs"
	  url: /Blogs/
```

Then you make a new directory `/_pages/`, create inside a markdown file `blogs.md` containing:

```md
---
title:  "Blogs"
layout: archive
permalink: /Blogs/
author_profile: true
comments: true
---

This is my blog page.
```

Be sure the `permalink:` matches the `url` in `navigation.yml` file.
Generate the website again, and look what's new:   
![blogs](/pics/website_tut/blog.png)

That's basically how a new webpage tab is added.

## Step 3: add posts
Right now your Blog page is just a single page. Next, we are going to add posts to this page.

### Posts
Posts should be kept in `_posts` folder and named after `YEAR-MONTH-DAY-filename.md` so that _minimal-mistakes_ can correctly identify them.

An example post markdown file:

```md
---
layout: single
title:  "My first post"
date:   2016-11-11
---

my first post looks just fine
```

where `layout:single` specifies this is a single page post; `title` would appear on top of page; `date` keeps time of "latest update", and could be used to sort your post. There are also a bunch of other parameters you can specify: [other parameters](https://mmistakes.github.io/minimal-mistakes/docs/posts/).

Let's create this toy post `toy.md` and put it in `_posts`. 

### Modify page file to include posts
In order to put `top.md` on you Blog page, you need to add commands in `blogs.md` to manually include it.
 
There are many ways to do this. I'll just give one example:   
open the previous `blogs.md` file and add the following lines:

![addToPage](/pics/website_tut/addToPage.png)

This is basically [Liquid language](http://shopify.github.io/liquid/). You can adapt this block of code to get different display: sort by year, month or category etc.
 
Rename `toy.md`  with prefix `YEAR-MONTH-DAY`. Then you can see the it on Blog page:

![new blog](/pics/website_tut/new_blog.png)


## Step 4: use Github for hosting

## Step 5: customize website style (to be updated)
Now the website is up and running, everything's great. However, if you are eager to modify the website style to better fit your taste, it's gonna cost a little more work.  