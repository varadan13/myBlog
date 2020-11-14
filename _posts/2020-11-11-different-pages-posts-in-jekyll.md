---
title: "How to add pages where posts are listed according to theme or topic in Jekyll?"
layout: post
---

I was trying to create a blog using Jekyll and GitHub and choose to create my blog using the default minima  
theme of Jekyll but one of the many things that I couldn't do and took a great deal of searching  
for a solution was how to have a posts page (by default) and also some other page say blog,  
both of which shows some posts in the appropriate category in the website.

### The solution I found for my problem.

lets say I create a collection called 'XYZ' and this can be done by adding the following code to the config.yml file  

		collections:
			- xyz	
            

In the root directory lets create xyz.md file and add the following font matter to it.

		---
		title: xyz
		layout: page
		permalink: /xyz/
		---
        

lets say I have a post titled 'ABC' and I want it to be displayed under the collection 'xyz'  

To do this. First, the font matter of the 'ABC' must be as follows

		---
		title: ABC
		layout: post
		permalink: /xyz/ABC/
		---
        

Secondly, add the following code to the file 'xyz.md'

				
		{% for item in site.xyz %}
		  <h2>{{ item.title }}</h2>
		  <p>{{ item.description }}</p>
		  <p><a href = "{{ item.url }}" >{{ item.title }}</a></p>
		{% endfor %}

Now Run 

		jekyll serve --open-url
