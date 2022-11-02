---
layout: page
title: Notes
permalink: /notes/
---


#### Front Matters  
- Very first section on each page or blog post or any other type of custom layouts  
- It provides configuration values for that page  
- **Default** values can be defined in _config.yaml, that will apply to all of our pages which uses them by default  
- eg: `author: Ashutosh`, this can be placed in one place and will be applied in all pages  

#### Draft Posts  
- Should be placed inside "_drafts" folder  
- `jekyll serve --draft` this will serve the draft folder content too(used for testing)  

#### New Pages  
- Need front matter with layout  
- Such pages starts appearing on the site  

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
- 