---
author: "Aga's IT Space"
date: "2021-02-22" 
linktitle: "Tutorial 1: Create and hosting a HUGO blog using GitHub and Netlify"
title: "Tutorial 1: Create and Host a HUGO blog using GitHub and Netlify"
weight: 10
---


# 0. Introduction - Prerequisite:

Hugo is a great tool to use if you want to start a blog. It is simple , flexible and fast , and the best thing you can create , upload and host your hugo blog for free.


Tools to install before proceeding:

[GitHub Desktop App](https://central.github.com/deployments/desktop/desktop/latest/win32)\
[Git](https://git-scm.com/download/win)

&nbsp;  

# 1. Install and Configure Hugo on Windows:

We are going to install and configure HUGO on Windows 10 - for installing it on other platforms (Linux and MacOS) check [this link.](https://gohugo.io/getting-started/installing/#homebrew-macos)


#### Step 1: Download and extract hugo executable:

[Download HUGO](https://github.com/gohugoio/hugo/releases/download/v0.81.0/hugo_0.81.0_Windows-64bit.zip)


#### Step 2: Add hugo.exe to environment variables so you can access it from anywhere using CMD:


```-Right Click "This PC"
- Properties  
- Advanced System Settings 
- Environment Variables 
- Path  
- Add the location where HUGO is located 
- Save
```

Check [this link](https://www.twilio.com/blog/2017/01/how-to-set-environment-variables.html) for more detailed explanation.

&nbsp;

# 2. Creating your first blog:

To create the website structure , open CMD and type the following command:

```hugo new site <sitename>```

Assuming that everything is configured correctly the command should return the following output:


```Congratulations! Your new Hugo site is created in <YOUR SITE LOCATION>.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/ or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>\<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
```


&nbsp;

# 3. Add a theme to your blog:

In order for your website to be beautiful you have to use a theme. You can download a theme from [HUGO THEMES](https://themes.gohugo.io/) , or you can create a theme by yourself (for advanced users)

Steps to follow after choosing the theme:

- Open CMD
- Navigate to your site: ```cd C:\Users\Aga\Desktop\thebestsite ```
- Navigate to themes folder: ```cd themes```
- Enter the following command to download the theme: ``` git clone <theme-github-repository-url> ``` 
- Ex. ```git clone https://github.com/yoshiharuyamashita/blackburn.git```

&nbsp;

# 4. Modifying the CONFIG.TOML file:

Every theme on their respective GitHub repository provides a demo configuration. Select everything in that configuration and paste it in the Config.toml file:

Steps to follow:

- Open the themes github repository
- Find the config.toml file in the README section
- Select everything and Copy
- Open Config.toml file (which is located in your sites main directory)
- Paste the copied settings and Save

NOTE: ```Various settings can be removed from the config.toml file if you don't want them to show up on your blog. Ex. you can remove categories, comments and social media links```

NOTE:
```You can check how your site looks like before deploying to github using the command "hugo server -D" and then accessing "localhost:1313" through your browser```
&nbsp;

# 5. Configuring GitHub and Uploading your blog:

We are one step closer to having our blog up and running on the internet. In this section you are going to:

#### Step 1: Create a GitHub Free Account

[Create a GitHub Free Account](https://github.com/pricing)


#### Step 2: Create a GitHub Repository

[Create a GitHub Repository](https://docs.github.com/en/github/getting-started-with-github/create-a-repo)

#### Step 3: Clone your newly created repository

[Clone your repository to GitHub Desktop](https://docs.github.com/en/desktop/contributing-and-collaborating-using-github-desktop/cloning-a-repository-from-github-to-github-desktop)

#### Step 4: Copy the contents of your blog (C:\Users\Aga\Desktop\thebestsite) to the GitHub Desktop repository folder (commonly under Documents\Github\<repo-name>)

#### Step 5: Commit and Push the changes

&nbsp;
# 6. Adding .gitmodules file and configuring it:

In order for our site to be able to display the theme correctly , we should provide the theme's repository as a submodule.

Steps to follow:

- Navigate to the sites folder and right click on a blank space
- Choose the ``` Git Bash here``` option , a new terminal will open
- Enter the following command: ``` git submodule add <theme-github-repository-url> themes/<theme-name>```
- Ex. ``` git submodule add https://github.com/yoshiharuyamashita/blackburn.git themes/blackburn```
- Commit and Push the repository to github

&nbsp;
# 7. Configuring Netlify and Using our custom domain:

We are at the last step of our journey:

Steps to follow:

- Join Netlify using GitHub: [Netlify](app.netlify.com/)
- Choose which GitHub repository to use (the one you have uploaded your site to)
- Under ```Basic build settings``` enter: ```hugo``` - under build command , and ```public``` under publish directory
- Press the ```Show advanced``` button and create a new variable with the following values: ```HUGO_VERSION``` - under key and ```<hugo version number which you can get by executing the command "hugo version" on cmd>``` - under value
- Press ```DEPLOY SITE``` button and YOU ARE READY TO ROCK !!!


&nbsp;

#### References:
```
https://www.twilio.com/blog/2017/01/how-to-set-environment-variables.html
https://github.com/pricing
https://docs.github.com
https://www.andrewhoog.com/post/git-submodule-for-hugo-themes/
https://app.netlify.com
```

