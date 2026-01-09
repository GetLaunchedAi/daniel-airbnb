# Starter Kit v4 - Eleventy

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [File Structure](#file-structure)
- [How it Works](#how-it-works)
- [Using the Kit](#using-the-kit)
- [Converting a Static Site](#converting-a-static-site)
- [Things to do before deployment](#pre-deployment-things)

# Overview
<a name="#overview" />

### Introduction
This kit aims to get any project off the ground in as little time as possible. It mimics a premade website, so you can make modifications where needed to get a fully functioning, mostly optimised website in hours. It comes with a fully responsive design by default, and has a few bells and whistles to make for a nicer dev experience.

# Features
<a name="#features" />

Some of those additional features include:
- **Eleventy** - Eleventy gives you access templating languages within your project. This allows you to supercharge your HTML to allow for reusable components and layouts to keep your code as DRY as possible. The templating language used in this kit is Nunjucks, but eleventy allows you to use multiple at the same time. It also comes with a range of plugins too...
- **Eleventy Images**. With this plugin, you no longer need to spend hours optimising and reformatting your images. Just use the image shortcode, and eleventy will optimise, compress and convert your image to next-gen formats. Provided you write good code, you can get straight 90+ scores on Lighthouse out-the-box
- **Eleventy Navigation** - This simplifies the way you do navigations to just 3 lines within the frontmatter of your HTML. All the rest has been done for you.
- **Centralised Data** - To make it quicker and easier to get started and scale your project, there is a folder containing key information about the client. Should you then later want to change a phone number, address or name, it's all contained in one place.
- **Dark Mode** - With dark mode catching on nowadays, having it on your websites is a nice extra touch you can add. This kit gives you an easy way to add dark styles. What's better, is the users system preferences are taken on first visit, so those who have opted-in to dark mode have that served to them on their first visit.

# File Structure
<a name="#file-structure" />
Before diving into the nitty gritty parts of using the kit, it is useful to understand how the project is structured, so you can expand on it in the right way.

### root
At the project root, you will find a couple of folders, .eleventy.js, .gitignore and some package.json files.

Out of all of the files, the .eleventy.js is the only one you need to worry about. Here, you will find the config files for the eleventy SSG. It is in this config file we can tell eleventy how to optimise our images, define where our components, data and layouts live, as well as determine what files make it into our production build.

The gitignore keeps the node_modules and public folders out of the repo, as these are huge folders which serve no purpose to others. Speaking of, what are those other folders for?

### public vs src vs node_modules
Out of these three folders, you only need to worry about one. The node_modules one contains all the dependencies and extra code needed for the website. The public folder contains the production-ready code for your website.

Both of these **should not be modified**. That only leaves the src folder for you to work in. There are folders in there for you, as we'll explain below.

### Source Folders
You'll be working in the src folder with this project. In here is an organised system with everything you'll need to make an awesome website.

- **_data** - This is a global store for data that can be accessed from anywhere in the project. The kit ships with a client file, containing information about a potential client that you may be making a website for. This data can be accessed by using the filename as an object, then accessing the key/value pairs within. So in this case, if you wanted to inject the client name somewhere, you use `{{ client.name }}`.
- **_includes and _layouts** - These two folders allow for some of the templating features within eleventy. Full page layout templates are stored in _layouts, and can be used in the 'layout' field within the frontmatter of your files. _includes contain the smaller, reusable components, such as the header or footer
- **admin** - Configuration for the CMS. You can ignore the index.html file, but the config.yml file may be of interest for you. You can read more about this with the [Netlify Docs]()
- **assets** - For all non-HTML/CSS related assets, such as SVGs, JavaScript and images you don't want to be optimised.
- **CSS** - For this project, we use the LESS preprocessor. All LESS and CSS files are stored in here.
- **images** - Images to be optimised are stored here, before getting transformed and spat out in the /public folder
- **pages** - All non-home pages are kept here

#### src/images vs assets/images
You may be wondering why there are two places to store images. This is to do with the eleventy image plugin. Images stored in src/images will be optimised and saved to the /public build folder, which includes a name change. assets/images contains images you don't want to be optimised by eleventy.

Because of how the build process works, and how the names of the image files change when being optimised, images from the CMS cannot be optimised with eleventy. On top of that, some images, like the logo, don't need to be resized or optimised, and thus can live here.

# How it works under the hood:
<a name="#how-it-works" />

We have a base.html file that has all the code that will be repeated on every page, like the head tag and its meta data, navigation, footer, etc and we use template blocks (like little variables) to insert the content for each page's info into that base file. It loads the content, meta tag info, inserts any extra link tags or other tags that are unique to that page needed to display it properly (like individual page css files), and basically fills in the blanks on the base.html page template.

# Using the Kit
<a name="#using-the-kit" />

### Getting Started
<a name="#getting-started" />
1. Clone the repository and save it to your computer and open it up in your code editor. We recommend Visual Studio.
2. Once you open the project in your code editor, open up the terminal in your editor. On PC it's (CTRL + ~). Then on the line in the terminal window, type "npm install" to install all the node modules needed for it to work.
3. once npm finished installing, type "npm start" to "turn on" the project and run the local server. A lot of text will show up and at the bottom there will be "Local: http://localhost:8080". Hold CTRL (on PC at least) and click on the "http://localhost:8080" to open the project in your browser. Any changes saved will update live on that link.
4. Now you're ready to start editing the kit to your needs. You can use the prebuilt template or add your own files to it, or delete them all and start fresh inside the kit.

If you close the project and open it back up at a later date, you will need to open the terminal and run "npm start" again to start the server and compile your code for you. Then click the localhost link to open it in a new tab again like before. You have to do this every time you close and reopen a project built with this kit. If there's any errors, it will show up here too and point you in the direction to fix.

### Setting up Eleventy
<a name="#setting-up-eleventy" />
Before you get stuck into the HTML and CSS, it's best to make the changes to the SSG config now. If you go into /.eleventy.js, you'll see a long, slightly scary looking config file. There are a couple of things you need to change here, as hinted by the comment at the top.

The first thing to change is the default media queries in the imageShortcode function. On line 9, you should see a line that looks like this

`async function imageShortcode(src, alt, className, loading, sizes = '(max-width: 600px) 400px, 850px')`

The part which says `sizes = '(max-width: 600px) 400px, 850px` is the part you have to change. This is saying "on devices up to a width of 600px, render the 400px version of the image, while on larger devices, use the 850px image".

On this website, most images on mobile widths are 400px wide, while the desktop images are around 850px wide. Based on your design, this may change. If so, change the media query to reflect this. This can be overwritten when using the shortcode, but to save yourself time, it's worth setting the default up.

The second thing to change is the array of widths you want the SSG to produce, on line 17. By default, this is set up to 200px, 400px, 850px, 1920px and 2500px. Note that the image widths in the media query all appear here. When you call the media query, you need to make sure that the width of the image you want is listed in the image widths.

If you would to read more about the eleventy image plugin, you can do so using the [eleventy image docs](https://www.11ty.dev/docs/plugins/image/)

### Setting up data
The next step is to go into /src/_data/client.json, and replace the default values with the applicable ones for your project. The changes will instantly be reflected across the site.

If there are any sets of related or repeated data during the development of the website, consider making a new file in the _data folder, to keep data centralised. This keeps your code easy to maintain. A good example would be a menu - you could have menu data in a menu.json folder, then use a [nunjucks for loop](https://mozilla.github.io/nunjucks/templating.html#for) to iterate over the menu items. Then if the client requests a price update, you know exactly where to look.

### Layouts and Components
As mentioned in the File Structure section, there are folders to keep your layouts and components in order. All pages pull from the base.html file in _layouts. This contains the head, header, footer and a main tag where the page content is inserted. The header and footer themselves are componenets found in _includes.

Most of the <head> will be completed for you by filling out the frontmatter of each page (next section), but some things, like favicons and font preloads, will need to be manually adjusted.

The title tag is also preconfigured, giving an SEO optimised title for each page. Home page and interior page titles are treated differently, but this can all be changed in base.html

### Adding a new page

All new pages need to be added to the /pages folder. If you are moving an existing website to this kit, all your website's old pages need to be added to this folder. All of them!

In the \pages folder there’s a .txt document labeled "_new-page-template". It has the following code inside of it:

```
---
layout: 'base.html' 
description: "Meta description for the page"
metaTitle: 'Title that shows up on social OG tags'
tagTitle: 'Title that shows up on google, and is concatenated with | {{ client.name }}'
preloadImg: '/images/imageName.format'
preloadCSS: '/css/fileName.css'
permalink: 'page/'
eleventyNavigation:
    key: Navigation Name
    order: 1000
---

<!-- Enter html code below -->
```

We laid out all the front matter and its variables with labels for you, so you know what goes where and what to edit. Below the "Enter html code here" comment is where you start writing the html for that page. We don't need to include the header or footer, just the unique html for this page. Fill out the frontmatter with the appropriate information, making sure to keep the same format of paths as the .txt file says

If you are adding an existing page to this kit, all you do is create a new html file and paste the content of the new-page-template.txt to the top of that file, and copy all the content between the `<main></main>` tags of your site below the line that says "<!-- Enter html code below -->". If for some reason you didn't use a `<main></main>` tag in your site, just copy and paste everything of that page between the navigation and the footer and paste it below the comment line.

The permalink is the actual slug name of the page that will show up in the URL. This will be www.website/page for example.

Also, DON'T include the `<main></main>` tags on the page. They are already on the base.html file in the /includes folder. The system will insert the contents of the page inside the `<main></main>` tags on that page. So they are not needed on your new page files.

### How to use Navigation
With the eleventy navigation plugin, you have access to an easy, scalable way to design a navigation. In the frontmatter, you can the data under eleventyNavigation is what controls the nav. The key is what name will be rendered on the navigation, while the order determines, well, what order the pages will appear, from smallest to largest.

If you don't want a page to be linked on the navigation, just leave the eleventyNavigation part of the frontmatter out.

### Optimising Images
Whenever you want to use an image, don't do it how you normally would, when using the template. Instead, use the below shortcode. Replace the capital letters with what you want, keeping the quotations

`{% image 'DIRECT IMAGE PATH', 'ALT TEXT', 'PICTURE ELEMENT CLASS', 'LAZY/EAGER LOADING', 'IMG MEDIA QUERY'%}`

An example of this shortcode in use would be this
`{% image './src/images/portfolio/port1.jpg', 'new hallway', 'cs-picture cs-picture-1', 'lazy', '(max-width: 600px) 200px, 400px'%}`

A couple things to note:
1. The image path need to be in the given format above, prefixing with ./src.
2. You need to include all information, except for the image media query. If you leave the media query, it will default to the one set in your .eleventy.js

#### Linking to images elsewhere
There may be a case where you need to use an image or image source without using the shortcode. For example, as a CSS background-image or in the preload section of the frontmatter. For this, it's important to know what happens when you call a shortcode.

The image gets moved into /public/images, and is renamed. In the .eleventy.js file, the name structure is given as `{name}-{width}w.{format}`. So a 400px wide jpg originally called picture.jpg will be returned as picture-400w.jpg. It is that which you use in your URLs. So, when linking to an image as a CSS background image, you should use `background-image: url(/images/picture-400w.jpg)`.

# How to convert a static HTML and CSS site into the new system:
<a name="#converting-a-static-site" />

### Move over all assets

Move images you would like to be optimised into the /images folder. The other assets belong in /assets, including unoptimised images. Then, you will have to go through and replace all images with the {% image ... %} shortcode. This is still quicker than manually optimising the images, however!

### Separating the header and footer sections

If you're trying to move over a current website to this kit, go in the \_includes folder and there is a header.html and a footer.html, and all you have to do is copy and paste all the html needed for your header into the header.html file and add all the footer code to the footer.html file.

However, how do we set dynamic active states to show which page you're on? Here's the code

```
<!--Main Nav-->
<nav id="navbar-menu">
    <ul>
        <li><a class="{{ 'active' if '' == page.url }}" href="/">Home</a></li>
        <li><a class="{{ 'active' if 'about' == page.url }}" href="/about">About Us</a></li>
        <li><a class="{{ 'active' if 'projects' == page.url }}" href="/projects">Projects</a></li>
        <li><a class="{{ 'active' if 'reviews' == page.url }}" href="/reviews">Reviews</a></li>
        <li><a class="{{ 'active' if 'contact' == page.url }}" href="/contact">Contact</a></li>
    </ul>
</nav>
```

We add this code `{{ 'active' if '' == page.url }}` to each link tag and fill in the empty quotes after the "if" with the page slug. For example, on the about page link, it's saying "add a class of "active" to this a tag if the text between these quotes is an exact match for the page slug name." In this case the slugs name is /about. So when you're on the about page, page.fileSlug = about, which matches exactly with the "about" string it's being matched to. This evaluates to true, so a class of .active gets added to the a tag and the styles associated with that tag having that class will be rendered. When you copy and paste your header into this file to override the default one we have in there, copy and paste that code in a seperate file and grab it once you added your header file and paste it inside the class="" quotes where you want the active class to be added when we're on that page.

On the home page we leave the string empty. Because when we're on the home page, there is no /fileSlug. It's just /. There's nothing. So on that home link, we're saying "if there's no file slug, add the active class to this tag".

Once you do this, you never have to touch them again unless you need to make an edit. They will be rendered on all pages. So on your about.html document, you don't need to add them in there. Just write your html for that page under the line that says "`<!-- Enter html code below -->`". Eleventy will handle everything else. It will build the page for you with the header and footer.

### Converting old file paths to the new ones, remove .html extension from all links

If you copy and pasted a previous site's html over to a new page in the kit, do a CTRL + F and find all instances of your image file path and replace it with /assets/images/. For example, when I moved over an old site to the kit, all my image tag source paths were /images/image.jpg. In this new kit, all images are inside the /assets/images file path. So I copy and paste "/images and replace it with "/assets/images - and yes that quote is supposed to be there. It makes sure I'm grabbing only the file paths that start with /images because all file path that start with /images happen to be right next to the open quote of the source quotes. like src="/images/image.jpg". If I only did a find a replace for /images I could potentially grab a file path I don't want to replace. Like if I already had a /assets/images/image.jpg on the page, if I did a find a replace for /images and replace it with /assets/images, it'd replace the /images in the middle of that path and it'd turn into /assets/assets/images/image.jpg - not what I wanted. So it's a little more strategic find and replace method.

You may ask - what is the reason why we use "/assets/images" when referencing images? Well, remember at the top of the README it's mentioned that /public is where your code is built to, and is where Netlify loads the website from. The leading / at the start tells Netlify to ALWAYS look from the root of the project. Not using that first / will cause Netlify to look at the folder the page is in, and not the root.

Then make sure ALL the links in the html have the .html extension removed. Eleventy doesn't recognize it. /contact.html should be changed to /contact. I also do a find and replace for .html, but make sure you check the top of your page front matter and double check the base.html still has its extension. If it got removed from the find and replace, put it back!

If you're ever unsure about file paths, it won't hurt to look in the public folder, and work your way through the folder tree in there (just don't accidently change anything in there - you'll lose all changes on the next build!). 11ty works on a folder-based file system. /contact points to the contact folder, and Netlify will load the index.html in there when you go to www.website.com/contact. This is why we don't use .html in the folders.

### Keeping the same file paths:

If you have file paths you don't want to change to maintain SEO, for example /pearland/pearland-piano-lessons, simply change the permalink for that page to that file path in the front matter of that page.

```
---
layout: 'base.html'
description: "Meta description for the page"
metaTitle: 'True Heating and Cooling'
tagTitle: 'About'
preloadImg: '/images/cabinets2-1920w.webp'
preloadCSS: '/css/about.css'
permalink: 'folder/page'
eleventyNavigation:
    key: About Us
    order: 200
---
<!-- Enter html code below -->
```

Normally, we set our permalink to be the page slug (pearland-piano-lessons/) but if they have a unique file path all you have to do is include it in the permalink. No slashes before the slug name, only 1 slash after as seen in the example above.

# Things to do before deployment
<a name="#pre-deployment-things" />
### Adding the sitemap

If you need to create a sitemap, use this tool to do so and download the file: https://www.xml-sitemaps.com/

To add this sitemap to the Eleventy system, you need to create a sitemap.njk file in the /src directory.  At the top of the file, add the permalink front matter to tell it the URL for this page:

```
---
permalink: /sitemap.xml
eleventyExcludeFromCollections: true
---
```

Then copy and paste the sitemap code below the front matter. NO SPACE BETWEEN THE FRONT MATTER AND STEMAP CODE. This will throw up an error "errors: error on line 2 at column 6: XML declaration allowed only at the start of the document". There can be no spaces at the top of a sitemap.xml file.  The front matter is removed when compiled and the sitemap code moves up to the top where it's supposed to be.  So when you copy and paste your sitemap code below the front matter, make sure there's no gap between it and the "---" bottom line. Like so:

```
---
permalink: '/sitemap.xml'
eleventyExcludeFromCollections: true
---
<?xml version="1.0" encoding="UTF-8"?>
<urlset
      xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9
            http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd">
<url>
```

### Adding robots.txt

We added a passthrough in the eleventy.js file that makes the robots.txt file usable inside the /src folder.  So when you need to create a new one or move an old one over, place it in the /src folder and it will work.

Make sure you add ```Disallow: /admin/``` in your robots.txt just below the ```User-agent: *``` at the top.  This will keep the /admin folder from being indexed on google. We don't want it indexed, it has no SEO value and will probably hurt your sites ranking because of it.  We've included a robots.txt file with this anyway as default. So all you have to do is add any other data that needs to be added. 

Also **Add your sitemap URL to the robots.txt file**.  In the robots.txt file, theres a line that says ```Sitemap: https://www.yourwebsite/sitemap.xml```. Change the "https://www.yourwebsite" to the URL of your client's site and save and you're done. 

### Adding a _redirects file with Netlify

If you need to add a redirects file, the way it works for Netlify is you create a _redirects file with no file extension.  When you save it, you have the option to select the file type, just scroll all the way down and "no extension" will be at the bottom usually.  Save it to your /src directory. We included a blank _redirects file in the kit for you.  We also added a passthough in the eleventy.js file so it gets picked up by the system.  

To add a redirect, add the file slug of the old domain on the left and the file slug of the new one to the right of that. Like this:

```
/old-page /new-page
```

And now that /old-page link will redirect to the /new-page.

### Adding the github to Netlify **IMPORTANT**

Normally, this is pretty straightforward. But there's a slight difference when using this kit. Once you get to step 3 of "Import an existing project from a Git repository", at the bottom there’s a box for "publish directory". Sometimes it populates with "_site", sometimes it has nothing. Make sure you change it to "public". If you don't do this it won't work.
