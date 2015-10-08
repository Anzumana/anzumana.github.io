#Blog Automation

-----
##My Setup:
[Two Site on one Server](http://www.anzumana.com/blog/2014_06_25_virtualhost.html) 
[Github](http://www.github.com) 
[LAMP](http://en.wikipedia.org/wiki/LAMP_(software_bundle) 

-------
#Before
Most of my post start out in [nvalt](http://brettterpstra.com/projects/nvalt/) written in [Markdown](http://daringfireball.net/projects/markdown/).
If you don't know what Markdown is shame on you :).
No but seriously its awesome go check it out.
To see what my post will look like on the web i use [Marked 2](http://marked2app.com).
When i am done i commit the resulting html file to github. 
Then i ssh into my webserver and i make a pull request to github to get the most current version of my repository.
This workflow is  obviously not efficient at all :)
However i wanted full control over my blog and the server back end.( specifically the  software used).
One does learn so much by testing and fixing things wouldn't you agree ?


#Simplification Number 1
Whenever i commit to the website repositories the web server issues a pull request to get the latest updates to the repository. 
Luckily Github offers web hooks and i found a php script that looks and works pretty well.

[Deploy your site with git](https://gist.github.com/oodavid/1809044)
To get the script presented there working i had to chmod the folders for my two websites.

	chmod www-data:www-data var/www/anzumana
	chmod www-data:www-data var/www/theprojectcast 
	
then the script worked perfectly.
A bit of reading up on permissions along the way never hurts:
[Git pull from a php script , not so simple](http://jondavidjohn.com/git-pull-from-a-php-script-not-so-simple/)
[User and Group permissions,with chmod , and Apache](http://fideloper.com/user-group-permissions-chmod-apache)

#Simplification Number 2
When the post is done, run a script that adds all the html elements and  commits the file to the repository and pushes to Github.
This is my little script:

	#!/bin/bash -e
	TOP="cat ../public_html/blog/template_top.html"
	BOT="cat ../public_html/blog/template_bot.html"
	BODY="perl Markdown.pl --html4tags ../notesy/$1"
	$TOP >> ~/Dropbox/public_html/blog/$2
	$BODY >> ~/Dropbox/public_html/blog/$2
	$BOT >> ~/Dropbox/public_html/blog/$2
	commit_message="added post $2"
	cd ~/Dropbox/public_html
	git add blog/$2
	git commit -m "$commit_message"
	git push

  [shelidorado](http://shelldorado.com/goodcoding/cmdargs.html)

##Now
When i finished a post i run the script and i am done.

###Sidenote
I think its rly important to ensure that your blogging workflow is as efficient as possible so that when you make a post technology is not in your way.
That way we get more helpful blog posts onto the internet.

	


