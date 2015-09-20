####There are certain criteria for making a template for Blogger Blog :

1. There must be skin (```<b:skin></b:skin>```) in the template
2. A template must have at least one b:section tag
3. Every section should have a unique id.
4. Correct Syntax

*If the above criterias are met, Blogger won't produce any errors when saving the template. For creating a blank HTML Template, we will make sure these criterias are met.*

###Contents Of Blogger Blank Template

As we said before, Blogger Templates should meet the criterias of Blogger. A Blank Blogger Template should contain the following :


1. Basic HTML Page Tags (html, head, body) and their closings
2. Only one ```<b:skin></b:skin>``` tag
3. Need At least a ```<b:section></b:section>``` tag.

###Create Template

Make sure your blog is using **Simple Template**. If not, apply Simple Template to your blog.

Go to your **Blogger Blog -> Template** and click on **Edit HTML** button. Remove the contents of Template.

We will now add the Basic HTML page to the Template :

```
    <?xml version="1.0" encoding="UTF-8" ?>
    <html xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
     <head>
     </head>
     <body>
     </body>
    </html>
```

##HEAD

The contents of the ```<head></head>``` tag are the title, skin and other elements. We should add the normal codes that are seen on Blogger Templates first :

```
    <meta content='IE=EmulateIE7' http-equiv='X-UA-Compatible'/> 
     <b:if cond='data:blog.isMobile'> 
      <meta content='width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0' name='viewport'/> 
     <b:else/> 
      <meta content='width=1100' name='viewport'/> 
     </b:if> 
    <b:include data='blog' name='all-head-content'/>
```

####Add the title :

```
    <title><data:blog.pageTitle/></title>
```

####Add the Skin with basic CSS that can be changed using Blogger's Template Designer :

```
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
```

There are additional CSS files that are loaded by Blogger before ```<b:skin>```. If you want to disable that:

    http://subinsb.com/disable-blogger-official-css-loading

###Body

Blogger needs a ```<b:section>``` element in template. So, we should add it inside body.

```
    <b:section id='main' showaddelement='yes'/>
```

This section is the main section of the blog where we can add gadgets to it.

###The Whole Code

And the whole Template code would be:

```
    <?xml version="1.0" encoding="UTF-8" ?>
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
```

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

######Save Your template

#Disable Blogger Official CSS From Loading In Template

Blogger adds their CSS styles to every templates. These files' load time will make your site slow. So for a better user experience, Blogger CSS files should be removed. But there isn't any Settings page for this. Blogger automatically add it's style sheets. But you can disable the loading with a simple hack.

####Blogger Style Sheets

The Blogger CSS files are these :

```
    https://www.blogger.com/static/v1/widgets/4219271310-widget_css_2_bundle.css
    https://www.blogger.com/static/v1/widgets/1937454905-widget_css_bundle.css
    https://www.blogger.com/static/v1/widgets/3160349130-widget_css_2_bundle.css
```

When Blogger updates, the above URL's will also change. Thus page load increases.

#####Warning

The Blogger CSS files contain the styles of Blogger Native Widgets. If you are using a Blogger Made Template and disable the Style Sheet loading, your site will look ugly. Use this hack only if your blog is using a custom template.

#####How ?

The CSS loading ```"<link>"``` tags will appear on the source code of your blog, but won't be loaded by browsers, because it is wrapped in HTML Comment tag. Browsers ignore the HTML markup inside the comments. So, the Blogger CSS files won't be loaded.

#####Disable Loading In Template

Go to your **Blogger Blog -> Template -> Edit HTML**

Search for ```"<b:skin>"``` in the Template Code using your browser Find Tool (CTRL + F). Move the contents of the ```"<b:skin>" to "</b:skin>"``` element to a file. Now, replace the``` "<b:skin></b:skin>"``` code with the following :

```
    &lt;style&gt;&lt;!--/*<b:skin><![CDATA[*/]]></b:skin>
```

After replacing search for the "</head>" element. Before it add the following code :

```
    <style></style>
```

Copy the code that we moved to a file and paste it after ```"<style>" ```in the above code.

Save the Template.

#####Did It Work ?

Now, we should check if it worked on your blog. So, go to your blog address, right click on an empty space and choose the "View Page Source" option from the right click context menu Or use the CTRL + U keyboard shortcut.

Search for the following code :

```
    <style><!---/*
```

If you found the code above and it is highlighted in black/gray color, then you have successfully disabled the Blogger CSS loading.