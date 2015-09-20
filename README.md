####There are certain criteria for making a template for Blogger Blog :

1. There must be skin (```<b:skin></b:skin>```) in the template
2. A template must have at least one b:section tag
3. Every section should have a unique id.
4. Correct Syntax

####If the above criterias are met, Blogger won't produce any errors when saving the template. For creating a blank HTML Template, we will make sure these criterias are met.

###Contents Of Blogger Blank Template

As we said before, Blogger Templates should meet the criterias of Blogger. A Blank Blogger Template should contain the following :


1. Basic HTML Page Tags (html, head, body) and their closings
2. Only one ```<b:skin></b:skin>``` tag
3. Need At least a ```<b:section></b:section>``` tag.

###Create Template

Make sure your blog is using **Simple Template**. If not, apply Simple Template to your blog.

Go to your **Blogger Blog -> Template** and click on **Edit HTML** button. Remove the contents of Template.

We will now add the Basic HTML page to the Template :

```<?xml version="1.0" encoding="UTF-8" ?>
<html xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
 <head>
 </head>
 <body>
 </body>
</html>```

##HEAD

The contents of the ```<head></head>``` tag are the title, skin and other elements. We should add the normal codes that are seen on Blogger Templates first :

```<meta content='IE=EmulateIE7' http-equiv='X-UA-Compatible'/> 
 <b:if cond='data:blog.isMobile'> 
  <meta content='width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0' name='viewport'/> 
 <b:else/> 
  <meta content='width=1100' name='viewport'/> 
 </b:if> 
<b:include data='blog' name='all-head-content'/>```

####Add the title :

<b:skin>
 <![CDATA[/* 
  body { 
   font: $(body.font); 
   color: $(body.text.color); 
   background: $(body.background); 
   padding: 0 $(content.shadow.spread) $(content.shadow.spread) $(content.shadow.spread); 
   $(body.background.override) margin: 0; 
   padding: 0; 
  }
 ]]>
</b:skin>

There are additional CSS files that are loaded by Blogger before <b:skin>. If you want to disable that

###Body

Blogger needs a <b:section> element in template. So, we should add it inside body.

<b:section id='main' showaddelement='yes'/>

This section is the main section of the blog where we can add gadgets to it.

###The Whole Code

And the whole Template code would be :

```<pre> <?xml version="1.0" encoding="UTF-8" ?>
    <html xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
     <head>
      <meta content='IE=EmulateIE7' http-equiv='X-UA-Compatible'/> 
      <b:if cond='data:blog.isMobile'> 
       <meta content='width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0' name='viewport'/> 
      <b:else/> 
       <meta content='width=1100' name='viewport'/> 
      </b:if> 
      <b:include data='blog' name='all-head-content'/>
      <title><data:blog.pageTitle/></title>
      <b:skin>
       <![CDATA[/* 
        body { 
         font: $(body.font); 
         color: $(body.text.color); 
         background: $(body.background); 
         padding: 0 $(content.shadow.spread) $(content.shadow.spread) $(content.shadow.spread); 
         $(body.background.override) margin: 0; 
         padding: 0; 
        }
       ]]>
      </b:skin>
     </head>
     <body>
      <b:section class='main' id='main' showaddelement='yes'/>
    <!-- Please Keep The Credits -->
      <center><a href="http://subinsb.com/make-a-blank-blogger-template">Blank Template By subinsb.com</a></center>
    </body>
    </data:blog.pageTitle>
    </html>
    </pre>```

####Additional Code adding

* Add additional CSS codes inside ```<b:skin></b:skin>```
* Add JavaScript codes before ```</head>``` or after ```<head>```
* Add HTML codes (widgets, code) inside ```<body>```.
* You can do all the stuff in this template just like you do it a HTML page.

If you want to display the Posts, add the following code inside ```<b:section></b:section>``` in body :

<b:widget id='Blog1' locked='true' title='Blog Posts' type='Blog'/>

####Example

    <b:section class='main' id='main' showaddelement='yes'>
      <b:widget id='Blog1' locked='true' title='Blog Posts' type='Blog'/>
    </b:section>

####Save Your template