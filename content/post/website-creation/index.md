---
authors:
- admin
# categories:
# - Demo
# - 教程
# date: "2023-05-22T00:00:00Z"
draft: false
featured: false
image:
  caption: 'Image credit: [**TeePublic**](https://www.teepublic.com/pin/33125939-table-flip-angry-rage-quit-desk-flip-mad-angry-mem)'
  focal_point: ""
  placement: 2
  preview_only: false
lastmod: "2023-06-03T00:00:00Z"
projects: []
subtitle: "A step-by-step tutorial of how I created this website using R."
summary: "A step-by-step tutorial of how I created this website using R."
# tags:
# - Academic
# - 开源
title: How I Created This Website
---

This is a walkthrough of how I created this website using R in combination with several other tools. This post is mostly a note-to-self in case I ever need to recreate this effort, but it may also assist you in creating your own website. 

{{% callout note %}}

**A NOTE OF CAUTION**

It is worth noting that this post is straightforward and simplistic, therefore it is not comprehensive and does not cover bugs you may encounter along the way. If you do encounter issues, as with most coding issues, I recommend Googling or using generative AI platforms (such as ChatGPT) to search for possible solutions.

{{% /callout %}}

---

**WHAT YOU'LL NEED**
- [x] R
- [x] RStudio
- [x] GitHub
- [x] Netlify
- [ ] Optional: Knowledge of other programming languages (Python, HTML)
- [ ] Optional: Jupyter Notebooks
- [ ] Optional: A web domain

---

**STEP BY STEP**

This breakdown is heavily influenced by Alison Hill's [magnificent tutorial](https://www.apreshill.com/blog/2020-12-new-year-new-blogdown/) which I highly recommend you read regardless of this walkthrough.
1. Download the latest version of R and RStudio.

    * R is a programming language and RStudio is an integrated development environment or user interface to code in R. Both are free and open-source, so you can easily download them on RStudio's official website (it changes names time from time so I will not add a URL, but as of the time of this post, you can find it on posit.co)
    * This step can be nuanced and complex depending on the operating system you are using or if you are a complete newcomer to these programs - if so, I would recommend searching on Google or YouTube for further tutorials on this step.

2. Go to GitHub and login to your account or create a new one. 

    * GitHub is an online platform that allows you to save changes online - that way, any changes made to your website using R and RStudio will live not only in your computer (plus we need this platform to download and update the website template). 
    * If this is your first time using the software, some common terms you'll want to become acquainted with are **repository, push, pull, fork, commit, and version control.** 

3. Create new repository in GitHub.

    * Once in GitHub, you will need to create a folder (or repository, often abbreviated as repo). This is where the code underlying your website will live online.
    * Once you have created your repository, go to the main page of this newly created repo, click on the green **clone or download** button and copy either the **SSH or HTTPS**. If you are a newbie, choose HTTPS - it is slighltly less secure, whereas SSH allows for enhanced encryption but requires additional steps to set up (if you're interested, I also recommend Googling or YouTubing this solution)

4. Create new project in RStudio.

    * Once we have the online folder, we will want to create its equivalent on your local computer. To do so, you will open RStudio > click File > New Project > Version Control > Git.
    * Paste the URL you copied from GitHub (SSH or HTTPS), be intentional with the name you want to assign (it can be either the name you have online, or a different name for you to locate the folder easier on your local computer), and click on create project.

5. Use the blogdown package in RStudio to download website template.

    * Packages are a compilation of R codes and functions, and can be stored in the form of libraries in RStudio. Developers build these to accomplish specific tasks and, ultimately, save them - and by extension, anyone who downloads them - time.
    * There are a couple of ways you can download and set up blogdown - either by using code or by going directly into RStudio's Packages tab and searching for it (I personally prefer the latter). Once you have done so, run the lines of code below in your RStudio Console tab.

{{% callout note %}}

**PLEASE READ BEFORE MOVING ON**

It is important to note that this website is possible thanks to Wowchemy. They are a group of developers who strive to empower creators by offering free, open-source website templates, which are essentially building blocks that you can rearrange and edit at will. This website is built using their [Academic template](https://academic-demo.netlify.app/), but you can explore many more on [their website](https://wowchemy.com/templates/). 

{{% /callout %}}

```r
## COPY AND PASTE THE TWO LINES BELOW IN YOUR R/RSTUDIO CONSOLE
## CHANGE starter-academic ACCORDINGLY IF YOU WANT TO USE ANOTHER TEMPLATE
## WAIT FOR THEM TO RUN BEFORE MOVING ON
library(blogdown)
new_site(theme = "wowchemy/starter-academic")

## ONCE THE LINES ABOVE HAVE RAN, COPY AND PASTE THE CODE BELOW
## THIS WILL RENDER A PREVIEW OF YOUR WEBSITE!
blogdown::serve_site()
```

6. Publish the website using Netlify.

    * If you have done everything so far without issues, you may have seen a preview of your website in RStudio or your predetermined web browser. Now comes my personal favorite part - deploying it to an actual website that people can visit! To do so, simply go to netlify.com, **sign up or log in using your GitHub account**, select New Site from Git > Continuous Deployment: Github > pick the repo where you have your website files > click on Deploy Site > Et Voila, you have your own website!
    * Even though you can implement this step later on, I recommend doing it first with the template so that you can see all of your hard work published online. This will allow you to browse what you created based on other developer's works, get a sense of the website's current layout, and begin the possibilities of your content (if you haven't already done so).
    
7. Update or create content.

    * Even though all of the work is based off of templates, I advise **extreme caution** with your first updates - take it from me, who had to scrape two websites because the updates yielded undesired results and I was not able to revert them (and the whole point of using GitHub is to have version control so you can easily go back to previous versions of your work, but at the time of my first attempts, using this feature was beyond my knowledge).
    * At this point, the world is your oyster - and by that, I mean you can mix and match the content within the realm of possibilites offered by your Hugo template. **Any time you add, edit, or delete ANY file in your local website folder, you must select your changes on the Git tab in RStudio, click on commit, ideally add a message that summarizes the updates, click on commit again and push.** This will add the changes to your online repository (GitHub) and are pushed into your actual website (Netlify) shortly after that.

{{< spoiler text="*Click to view some (poorly written) shortcuts to edit your website*" >}}
* To modify favicon: assets > media > icon.jpeg
* To update website name AND tagline in web browser tab: config > _default > params.yml
* To update website description and sharing license: config > _default > params.yml
* To edit landing page: content > _index.md
* To edit first block with bio, interests and education: content > authors > admin > index.md
* To update profile pic: content > authors > admin > avatar.jpeg
* To add an image to a project: Go to Canva’s Text to Image feature > file size 1125 x 1125
* To add a Tableau project: Go to Tableau viz you want to add (on Tableau), click on share, copy code (under “Embed Code”), paste that into the .md file, and you’re all set!
* To edit main menu:
    * Main menu stuff lives in: config > _default > menus
    * To make it so that buttons lead to new page, change hash (e.g., #posts) in url section for slash (e.g., /post/). 
    
* To add a Jupyter Notebook post:

    * Convert the ipynb file to md file by going to the terminal, changing the work directory to wherever the ipynb file is (e.g., if it’s in a folder in downloads: cd Downloads/jupyter) then run this code: jupyter nbconvert --to markdown YourNotebook.ipynb
    * This should have created a new md file, and also very likely a new folder with all of the images.
    * Created a new folder in content > post with the desired name of the blog post which will show up in the URL. Each word should be separated with hyphens instead of spaces (e.g., predict-depression-with-music).
    * Drag or copy the md file and the new folder with images (if applicable) to the folder you just created in content > post > new-folder.
    
{{< /spoiler >}}


8. Optional: Link your website to your own domain.

    * You may have noticed that your website name has an extravagant name. Netlify automatically assigns these names, but within Netlify you can either purchase a domain of your choosing or link your website to a domain you already had.
    * For example, in my case I had previously purchased my domain - macuriels.com - via WordPress. As of the time of this writing, the domain is still managed through WordPress, but I made it so that whenever someone types my domain, it redirects to my Netlify website. The nuances of this are beyond my knowledge, but I do know that any host - including Netlify - provides instructions on doing any of the above actions.
    
---

**ADDITIONAL REFERENCES**

Creating my own website was a highly iterative process that took watching and reading ton of tutorials, as well as taking inspiration from other colleague's works. These are some of the sources I used:

- A special shoutout to professor Weiai Wayne Xu and his [website](https://curiositybits.cc/). I had the pleasure of taking a class with him (Digital Behavioral Data) during my master's program, I was inspired by his website and he provided the first reference to using R (specifically, the blogdown library) and the Hugo Academic theme (one of the many open-source themes provided by Wowchemy) to build a website.
- Alison Hill's [tutorial](https://www.apreshill.com/blog/2020-12-new-year-new-blogdown/) to set up your own website from scratch using R (blogdown) and Hugo website templates. This was the most accurate and straightforward tutorial I could find.
- Kyle Chan's [tutorial](https://www.kyleichan.com/post/hugo-academic/) to set up your own website from scratch using R (blogdown) and Hugo website templates. In contrast to Alison's tutorial (mentioned above), I found Kyle's to be more comprehensive - but because of that, also harder to follow.
- Yihui Xie's [book](https://bookdown.org/yihui/blogdown/) to set up your own website from scratch using R (blogdown). Unlike the previous blog posts (Alison and Kyle's), the book is even more extensive and focuses heavily on the ins and outs of of blogdown - which makes sense as Yihui is the developer behind blogdown!
- Wowchemy's [official documentation](https://wowchemy.com/docs/) which includes tips and tricks to use your Hugo themed website proficiently.
- Wowchemy's [sample website](https://academic-demo.netlify.app/) template which is the base I used for this website.
- Philip Daniel's [Hugo cheatsheet](https://www.philipdaniels.com/blog/2016/hugo-blogging-cheatsheet/), which is extremely helpful when you're personalizing your Hugo website.
- John Sorrentino's side-project called favicon.io, which is a [free icon generator](https://favicon.io/) and which I used to generate my website's icon (a letter "m" in cursive writing with a blue backgroun)
- Other options I know exist to create, update, and host websites, but I did not explore thoroughly: GitHub websites, WordPress, GoDaddy, Wix, and Squarespace. I ultimately chose to use RStudio and Hugo templates because I wanted to create a relatively straightforward website where I can showcase my R/RStudio, Jupyter Notebooks/Python and Tableau projects; but it seems to me that the alternatives offer greater flexibility and are more apt for complex visualizations, blogging, and e-commerce.