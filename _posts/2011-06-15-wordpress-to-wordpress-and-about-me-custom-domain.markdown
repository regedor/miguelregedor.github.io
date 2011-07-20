---
layout: post
title: From Wordpress to GitHub and About.me with Custom Domain
---

Recently, I moved my writings from Worpress to GitHub.
In addition, I created a profile on "about.me" and I wanted to have everything under the same domain (www.regedor.com).

The plan was to have the about.me profile as the landing page,
but about.me does not provide a custom domain service. 
In fact, they were planing to add it. 
Although, because they were acquired by AOL, it isn't sure if that is going to happen anytime soon.

I could have used a rewrite rule in the htaccess, but either get the redirect without the URL or get the URL with broken links. 
Furthermore, I wanted to have the blog posts under the same domain, so this would never work.

My solution was to host the blog in GitHub 
(All GitHub accounts include web hosting and you can add custom domains to it.)
and use the old style framesets to embed the about.me profile, 
the only issue with this solution is that it will mess the about.me link source statistics,
obvious the source link will always be your own web site.

Lots of people asked how I did.
Next, I'll explain the whole process (you should consider www.regedor.com as an example, replace it with your domain):


## Embeding about.me

After creating the repository, in my case regedor.github.com.
Create an index.html file like the one bellow. This is the magic for embedding about.me or any other site into any webpage under any domain. 
However, when you're using frames with pages not from the same domain, you will have some limitation, that happens for security reasons.

{% highlight html linenos %}
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN"
  "http://www.w3.org/TR/html4/frameset.dtd">
<html>
<head>
  <meta http-equiv="content-type" content="text/html; charset=utf-8"/>
  <title>Personal Web Site</title>
  <meta name="Description" content="Personal Web Site"> 
</head>
<frameset>
  <frame src="http://about.me/regedor" />
</frameset> 
</html>	
{% endhighlight %}

    
Then, create a file called CNAME containing your domain, so that GitHub will accept the custom domain, this can be done in the shell:

    echo "www.regedor.com" > CNAME

You need to add the CNAME record to your DNS (it should redirect www.regedor.com to regedor.github.com).  		

		
## Exporting posts from wordpress:


The first step is to download the xml file containing the posts (replace miguelregedor with your wordpress username):

     https://miguelregedor.wordpress.com/wp-admin/export.php

At this point I tried to use Jekyll::WordpressDotCom to create the posts. 
However, it was a litle bit buggy at the time.
I created a script (based on Jekyll code). After downloading the script, 
[here](https://raw.github.com/regedor/regedor.github.com/master/assets/wordpress_xml.rb), 
you can use it to generate the posts with something like this: 

    $ ruby -r 'wordpress_xml.rb' -e 'WordpressXML.to_posts("wordpress.xml")'

Now you have a folder with all your posts.
You just need to add a file that will list the posts:

{% highlight html linenos %}
---
layout: default
title: Miguel Regedor
---
<div id="home">
  <h1>Writings</h1>
  <ul class="posts">
    { % for post in site.posts %}
    <li>
      <a href="{ { post.url }}">{ { post.title }}</a>,
      <span>{ { post.date | date_to_long_string }}</span>
    </li>
    { % endfor %}
  </ul> 
</div>
{% endhighlight %}

To have a better understanding of how to organize your files, you can look at my repository.






