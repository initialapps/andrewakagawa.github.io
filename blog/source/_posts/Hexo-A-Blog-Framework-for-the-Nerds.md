---
title: 'Hexo, A Blog Framework for the Nerds'
date: 2016-08-06 02:36:35
tags: Intermediate, Hexo, 
---
by Andrew Akagawa

![](http://biosparkinnovation.org/blog/images/hexo.png)

# Why we like Hexo

You're an entrepreneurial nerd.  You just finished your minimum viable million dollar app and launched.  Now time to sit back and watch the viral onslaught of users roll in.  One problem... nobody knows you exist.  

Ya, you've heard it all before, the spiel about *_content, content, content_*, but never took it seriously.  Who has time for that when you're developing a product?  But now you finally get it... You need a blog.

## So, what are your options?

There are several mainstream options that we've all heard of.  Yes, Wordpress is the industry standard, with a huge open source community and loads of features, but you're a lean, MEAN, coding machine!  You don't want a bulky PHP/MySQL addition, especially to your Pulitzer Prize of javascript.  So what do you do?

## Enter Hexo!

Hexo is quite an awesome little piece of javascripted blog action.  I recently hit the proverbial content marketing wall not too long ago when launching and pivoting [SubmitHealth](https://submithealth.com) (an app aimed at providing a little help to doctors and patients).  In my search and discovery of Hexo, I was inspired to start a blog here on BioSpark as well, to further our goals in sharing the knowledge on healthcare and technology.  What better place to start than a mini tutorial of getting started with Hexo!

# Getting Up and Running with Hexo

Good news is that the [documentation](https://hexo.io/docs/) is pretty clear and easy to follow, and there are many great themes to checkout, so [take a look](https://hexo.io/themes/) to see if anything interests you.  

## What you need?

We'll be launching this as a static site on github pages so that you'll be able to get your blog going for free.  The following are what we will use.  If these look foreign to you, then you may want to try Wordpress, or I'll also plan to write tutorials on these, so stay tuned and [subscribe](http://eepurl.com/caKlxr).

- A GitHub account
- A linux style operating system 

## Step 1: Install Hexo

Let's get started by making your blog directory.  I'm calling it *_blog_*, but name it whatever you like.

```
mkdir blog
```

Open your blog directory and install Hexo.

```
cd blog
npm install hexo-cli -g
```

If you get a permission error, try:

```
sudo npm install hexo-cli -g
```

Now let's get hexo started by running the following command:

```
hexo init
```

Great! Now you have all the hexo files to get started.  Next, let's get GitHub setup to host your site.

## Step 2: Get Github Going

Go to GitHub.com, and login or signup.

After, you should see a screen like this:

![](http://biosparkinnovation.org/blog/images/github-start.png)

Click "Start a project".

Github will allow you to host your site for free.  In order to do that, you must name you repo the same as your username followed by *_.github.io_*.  See example below for submithealth but replace with your username:

![](http://biosparkinnovation.org/blog/images/github-repo.png)

Click "Create repository"

Make note of your git url.  Mine is as follows, but yours will look a bit different:

```
https://github.com/submithealth/submithealth.github.io.git
```

Now head back to the blog directory you created.  Initialize git and add your url as a remote origin.  Be sure to swap the example git url below with your git url.

```
git init
git remote add origin https://github.com/(git username)/(git username).github.io.git
```

Next, you'll need a text editor.  If you already have one fell free to use it.  If not, I like using nano, which you can install by running the following command:


```
sudo apt-get install nano
```

You should have a file in your directory named **_ _config.yml _**.  This file is the sort of backbone of your blog, and holds a lot of config settings.  Open with nano or your favorite text editor.
```
nano _config.yml
```

You can play around with this file, but we'll skip right down to the deployment section so we can get ready to publish to our github hosted page.  Find the *_deploy_* section in this file and edit it to reflect git as type and your git url as repo. (Note, be sure to swap the example url below with your actual git url):

```
deploy:
  type: git
  repo: https://github.com/(git username)/(git username).github.io.git
```

Save your file.  

## Step 3: Deploying Hexo

Now you're ready to make your first deploy.  Hexo has built in commands to make your blog framework.  The *_generate_* command gets all your files ready, and the *_deploy_* command will publish them to github.  The files published will not be the same as the files in your git repo, so no need to run a git push to github.

Run the following commands:

```
hexo generate
hexo deploy
```

Navigate to your new website.  Your site should be hosted at a url that is **_your username_** followed by **_.github.io_**.  For me it is *_submithealth.github.io_*. 

## Step 4: Blogging Out

Great! You have a framework up and running.  Now you'll want to make your blog really yours.  I won't get into the details with this as there are several helpful resources out there already, but I will give a quick overview and thoughts on where to go from here.

### Setting up a Theme

There are lot's of great themes that exist for Hexo.  [You can browse them here](https://hexo.io/themes/).  They generally have great documentation covering installation and customization.  A few quick things I'll note about how the infrastructure works.  After installing a theme, you will specify the theme you are using in your **_ _config.yml _** file.  The associated theme's files and folders will be installed in your **_ /themes _** directory.  Each theme will have its own separate **_ _config.yml _** file, with its own set of options for how to customize and add features to your site.

### Writing Posts

You can create new posts by entering the following:

```
hexo new post "Your Post Title Here"
```

Your posts will be in markdown format.  If you've never worked with that, it's basically a super easy, shorthand way of writing html.  Here's a great [cheat sheet to help you get started, thanks to Adam-P](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

Your posts will be  in your **_ /source/_posts _** directory, which you can open and edit with nano or your preferred text editor.  When you are ready to deploy, run the *_generate_* and *_deploy_* commands again:

```
hexo generate
hexo deploy
```

Remember, this is not a typical git push, which kind of confused me at first as I was trying to push my repo and was wondering why my site wasn't working.  You have to run the *_ generate _* and *_ deploy _* commands, and Hexo runs a script to put your posts and files in the right directories and automatically pushes to your hosted website.

### Adding a Domain or Subdomain

Work with your DNS provider to have your domain or subdomain CNAME record point to your github url (**_your username_** followed by **_.github.io_**).  If what I just wrote looks confusing, you can also always just call or message your domain provider and say "Hey DNS provider... update my CNAME to point to this github url."

Finally, setting up the domain on github was not entirely straightforward to me.  Don't set this up on your repo settings on the Github website as hexo will just overwrite this with every deploy.  Here's what I think is the easiest way to do this.  From your blog directory, move into your public directory and create a file named *_ CNAME _*:

```
cd public
nano CNAME
```

Now, simply enter your desired domain or subdomain on the first line and save.  For me, it's as follows:

```
blog.submithealth.com
```

Now deploy your site, and you should be up and running on your domain:

```
hexo generate
hexo deploy
```

# Closing Notes

Thanks for reading, and hoped this helped in getting your blog setup!  Thank you to [Hexo](https://hexo.io) for making an awesome framework, and to [Github](https://github.com/) for hosting it, and check out the documentation [here](https://hexo.io/docs/) to keep you running.


Happy Blogging!
 
<h3><a href="http://eepurl.com/caKlxr" target="_blank" rel="external"><span class="fa fa-envelope-o"></span> Subscribe to Email Updates </a></h3>
