In this hands on, we will create a custom tag that will handle the display of the header and footer.

**Tags Used**: [\<cfif>](http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7fe8.html), [\<cfelse>](http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7fe6.html), [\<cfset>](http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7ffd.html), [\<cfimport>](http://help.adobe.com/en_US/ColdFusion/10.0/CFMLRef/WSc3ff6d0ea77859461172e0811cbec22c24-7ea1.html)

1. Create a folder called `customTags` in the `/www/` folder.
1. Create a file called `page.cfm` in the `/www/customTags/` folder.
1. Open the `/www/customTags/page.cfm` file in your code editor.
1. Create a `<cfif>` tag that checks if `thisTag.executionMode` is equal to `"Start"`.
1. Create a `<cfelse>` tag after the `<cfif>` tag.
1. Create a closing `</cfif>` tag after the `<cfelse>` tag.
1. Your code should look similar to this:

        <cfif thisTag.executionMode eq "start">

        <cfelse>

        </cfif>

1. Open up the `/www/includes/header.cfm` file in your code editor.
1. Copy the contents of `header.cfm` and paste them into the first part of the `<cfif>` tag block in `page.cfm`.
1. Open up the `/www/includes/footer.cfm` file in your code editor.
1. Copy the contents of `footer.cfm` and paste them into the `<cfelse>` part of the `<cfif>` statement in `page.cfm`.
1. Open up the `/www/about.cfm` file in your code editor and navigate to the `<cfset>` tag located on or around line 4.
1. Replace the `<cfset>` tag with a `<cfimport>` tag with the following attributes:
    * **taglib**: customTags/
    * **prefix**: layout
1. Your code should look similar to this:

        <cfimport taglib="customTags/" prefix="layout" />

1. Replace the `<cfinclude>` tag, which includes the `header.cfm` file, with a call to your custom tag. The code should look similar to this:

        <layout:page>

1. Replace the `<cfinclude>` tag, which includes the `footer.cfm` file, with a closing tag to your custom tag. Your code should look similar to this:

        </layout:page>

1. Open up your browser and navigate to the `/www/about.cfm` page. Notice that the page loads as it did before. The page is now using your custom tag rather than the include files. The only exception is that the 'Home' navigation item is being selected rather than the 'About' navigation item.
1. Open up the `/www/customtags/page.cfm` file in your code editor.
1. Find the `<cfparam>` tag that should be on or around line 2.
1. Change the name attribute from `section` to `attributes.section`.
1. Locate the Navigation `<ul>` block on or around line 51. For each reference to section in the `<cfif>` tags in the `<li>` tags, update them to read `attributes.section` rather than `section`. Your code should look similar to this:

        <ul class="arrowunderline" id="nav">
        <li class="home" <cfif attributes.section eq "home">id="selected"</cfif>><a href="index.cfm">Home</a></li>
        <li class="about" <cfif attributes.section eq "about">id="selected"</cfif>><a href="about.cfm">About</a></li>
        <li class="resume" <cfif attributes.section eq "resume">id="selected"</cfif>><a href="resume.cfm">Resume</a></li>
        <li class="blog" <cfif attributes.section eq "blog">id="selected"</cfif>><a href="blog.cfm">Blog</a></li>
        <li class="portfolio" <cfif attributes.section eq "portfolio">id="selected"</cfif>><a href="portfolio.cfm">Portfolio</a></li>
        <li class="contact" <cfif attributes.section eq "contact">id="selected"</cfif>><a href="contact.cfm">Contact</a></li>
        </ul>

1. Refresh the `about.cfm` page in your browser notice the home nav item is highlighted.
1. Open up the `/www/about.cfm` file in your code editor.
1. Locate the `<layout:page>` tag and add an attribute called `section` with a value of "about". Your code should look similar to this:

        <layout:page section="about">

1. Refresh the `about.cfm` page in your browser and confirm that the 'About' navigation item is now highlighted.

Homework
--------

Convert all other pages to use the page custom tag