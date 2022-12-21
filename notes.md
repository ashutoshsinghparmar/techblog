---
layout: page
title: Notes
permalink: /notes/
---

#### Running Jekyll locally  
- `jekyll new folder-name` a new website inside folder "folder-name"  
- `bundle exec jekyll serve` process the content of the folder and generates the site and starts serving it  
  - Need to do only first time  
  - If there is any change in `Gemfile` then only we need to rebuild the website  
- `jekyll server` for subsequent serve commands  

#### Front Matters  
- Very first section on each page or blog post or any other type of custom layouts  
- It provides configuration values for that page  
- **Default** values can be defined in _config.yaml, that will apply to all of our pages which uses them by default  
- eg: `author: Ashutosh`, this can be placed in one place and will be applied in all pages  

#### Creating new Posts(https://youtu.be/gsYqPL9EFwQ)  
- created inside `_posts` folder  
- Naming convention: date-postname.extension  
  - Starts with date any date(YYYY-MM-DD format)  
  - This date is used for folder strucutre(yyyy/mm/dd/title-of-post.html) in generated site  
  - Title of the post  
  - extension(markdown or html)  
- Always Add front matter in the beginning  
  - `layout`: this front matter variable will give a design to the page while rendering(page, post or custom layouts)  
  - `title`: this variable is used to override the default title value from file name  
  - `date`: this variable is used to override the default date value from file name, it also modifies the path in which it has kept the corresponding html file in the resultant directory  
- Page starts appearing on the website as soon as it it added in the structure, no additional work required  
- sub-directories inside `_posts` can be used to organise posts, but it do not impact the path of the post  

#### Draft Posts  
- Should be placed inside "_drafts" folder  
- `jekyll serve --draft` this will serve the draft folder content too(used for testing)  

#### Permanent links for pages, blog posts etc  
- `parmalink` variable is used for this  
- `parmalink:"/some-value/:my-var-name/:year"` Value for this variable can make use of other front matter variables  
- `parmalink:"/some-value/:my-var-name/:year.html"` Custom extention can be used too  

#### Themes  
- rubygems.org : Search for themes here  
- Themes are ruby gems, hence add them as dependency in Gemfile  
- use `bundle install` command to install all the new gems added in the Gemfile  

#### Modifying Layouts  
- https://youtu.be/bDQsGdCWv4I  

#### Variables  
- Variables are defined inside front matter  
- it can be used using interpolation syntax `{{ variable-name }}`  
- `{{ layout.variable-name }}` to access variable defined in a layout  
- `{{ page.variable-name }}` to access variable defined in a page from layout  
- `{{ site.variable-name }}` to access variable defined in config  
- `content` is one comman variable  

#### Includes  
- Content such as header and footer can be separated into include files  
- include files are kept inside `_includes` folder at root level  
- include files are html markup to design that particular section  
- `{% include header.html %}` in layout, this will include header.html in the layout  
- `{% include header.html variable-name="blue" %}` passing variables to include files  
- `{{ include.variable-name }}` can be used to access the value of variable  

#### Looping through pages/posts  
- `{% for post in site.posts %}`  
- `{{ post.title }}` <br/>
- `{% endfor %}`  

#### Datafiles  
- kept inside `_data` folder at root  
- format: json, yaml or csv  
- `{{ site.data.name-of-data-file }}` from inside a page  

#### Statifiles  

#### Hosting @GithubPages  
- Free hosting  
- integrates smoothly with GHPages  
- `baseurl` varible inside _config.yml should be modified with **name of repository** or domain name if you have one  
- keep all the content to "gh-pages" branch of the repo  
