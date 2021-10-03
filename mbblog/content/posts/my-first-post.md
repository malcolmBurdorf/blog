---
title: "My First Post: Hosting Hugo generated static files with GitHub Pages"
date: 2021-10-02T01:40:07+01:00
---

Hello.  This is my first post. 
I would like to provide some information on how I created this website with Hugo, 
and deployed it with GitHub Pages. 
Hopefully, this will be helpful for people like me, or my future self, 
since I just went through the process. 
This will be specifically for Windows, since that is the OS that I used.

Firstly, this will basically be a summary of both the [Hugo Quick Start page](https://gohugo.io/getting-started/quick-start/) and 
[The Simple Engineer's video](https://www.youtube.com/watch?v=LIFvgrRxdt4), so please look at those, if you would like more information.

(btw markdown shortcode {_{_< youtube LIFvgrRxdt4 >}} would embed the video into this webpage)  
&nbsp; 

### Prerequisites:

- Install [Git](https://git-scm.com/download/win)

- Setup a [GitHub account](https://github.com/join)

- Preferably, have [Vim](https://neovim.io/) to edit files, otherwise Notepad  
&nbsp;
 

### Step 1: Install Hugo

I didn't have any of the package management tools listed, so I tried Chocolatey, which didn't work.


I then tried Scoop, which did work, so install [Scoop](https://scoop.sh/).


Make sure the execution policy is correct (to enable Powershell), 
by running this in the Powershell:
```
Set-ExecutionPolicy RemoteSigned -scope CurrentUser
```

Then, run this expression to install Scoop:
```
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh') 
```

Now, we can install Hugo (the extended version) with Scoop:
```
scoop install hugo-extended
```

To verify it's installed, run: 
```
hugo version
```
&nbsp; 
 
### Step 2: Create website repositories

In order for our website to be hosted for others to see, we can use GitHub Pages.
We will use one repository for storing our website content, 
and another repository to deploy our website. 

Go to your [GitHub homepage](https://github.com/), 
and create two new public repositories with README documents.
The first one will be our storage repository, which I named 'blog'.
The second one will be our deployment repository, which will I named 'malcolmBurdorf.github.io'.  
It is important, that your deployment repository ends with '.github.io', since that will be the website domain ending.  
[With additional work, GitHub Pages allows you to change your domain.](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
&nbsp; 
 

 

### Step 3: Create the Website

Git clone the storage repo and cd into it.  Then, run:

```
hugo new site mBblog
```

to create the skeleton files for the site in the folder 'mBblog'. 
(Name this folder whatever you like.)
&nbsp;
 

### Step 4: Pick a Theme

The theme will dictate the look and flexibility of the website. 
You can choose one [here](https://themes.gohugo.io/).
I ended up choosing PaperMod. 

Go to the theme's GitHub page, which you can get to by clicking Download on the Themes page.
Cd into blog/mBblog and git clone the theme into the theme folder.  In my case, I used:

```
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

You then need to set 'theme = PaperMod' in your config file. 
You can do this manually (in Notepad or Vim) or run:

```
echo theme = "PaperMod" >> config.toml
```
&nbsp;


### Step 5: Add the deployment repo as submodule
 
You also need to change the baseURL. 
For Github Pages, this would be the name of the deployment repo. 
So in my case, ' baseURL = "https://malcolmBurdorf.github.io/" '

Now, we want to use our deployment repo to house the static assets that our storage repo generates. 
So, add the deployment repo as a submodule of the storage repo using from blog/mBblog:

```
git submodule add -b main https://github.com/malcolmBurdorf/malcolmBurdorf.github.io.git public
```

This will git clone our deployment repo into the new folder 'public'.  
&nbsp; 

### Step 6: Generate static files

Now also in blog/mBblog, generate the static files using the name of your theme. In my case:

```
hugo -t PaperMod
```

This should automatically generate static files into the 'public' folder.
&nbsp; 

### Step 7: Push

We can now push everything to their respective repos.
In blog and blog/mBblog/public, run:

```
git add .
git commit -m "init commit"
git push origin main
```

Once in the storage repo (blog), and once for the deployment submodule (blog/mBblog/public), since it is pointing to our second repo.

And we're done! Just go to Settings->Pages, switch the Source to main, click Save, and your website url should pop up.

This has just been the bare minimum to get a website created and hosted with Hugo and Github Pages.
If you would like the other accoutrements, the [previously](https://gohugo.io/getting-started/quick-start/) [mentioned](https://www.youtube.com/watch?v=LIFvgrRxdt4) resources are good places to start.

[Here](https://support.atlassian.com/jira-software-cloud/docs/markdown-and-keyboard-shortcuts/), [are](https://www.markdownguide.org/basic-syntax/) some Markdown tables and [this](https://gohugo.io/content-management/shortcodes/) explains Hugo shortcodes.

