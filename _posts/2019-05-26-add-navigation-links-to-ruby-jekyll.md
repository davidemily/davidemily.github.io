# Adding Navigation Links

While the Ruby Jekyll websites templates are really useful and include functionality and custom options, sometimes you may want more. I found that instead of wanting to use the existing options to add my Twitter, I was more interested in linking my LinkedIn and GitHub. Luckily these are easy to add as links in the Navigation section.  

First follow the file structure from base folder > _includes > nav.html. In here you should find a list, noted by: 
```
    <ul class="navbar">
      <li><a href="{{ '/about' | prepend: site.baseurl | prepend: site.url }}">About Me</a></li>
      <li><a href="{{ "/feed.xml" | prepend: site.baseurl | prepend: site.url }}" target="_blank">RSS</a></li>
    </ul>
```  
This is the code that projects the About Me and RSS links in the Navigation Bar. The way you add additional navigation links depends if the website you are linking is stored in the same folder or if it is a website hosted somewhere else.  

If the link is local the folder, you will want to mirror what is already provided. For example, the RSS feed link is set up by linking the "/feed.xml" route to the name RSS. If you wanted to create something like a 
"Projects" link to link to a markdown file stored inside this file, you would do something like:  
```
<li><a href="{{ "/projects" | prepend: site.baseurl | prepend: site.url }}" target="_blank">Projects</a></li>
```
This tells the website when it is creating the display that inside the home folder there is a file called projects and it needs to try and load it and link it to the navigation bar with the name "Projects".  

But maybe you're interested in linking a pre-existing website or something like a LinkedIn profile, in which case you'll just want to include the link to the site like so:
```
<li><a href="{{ 'https://www.linkedin.com/' }}">LinkedIn</a></li>
```
Adding in your personal profile link instead of the base address. This tells your website that the link is not part of it's folder path and to instead send users that click "LinkedIn" to this existing website.
