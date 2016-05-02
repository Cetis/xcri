---
layout: post
---

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

  ga('create', 'UA-73710929-3', 'auto');
  ga('send', 'pageview');

</script>







Description 1.2 
===============













### From Xcri 







Jump to: [navigation](Description_1.2.html#column-one),
[search](Description_1.2.html#searchInput)



This property is defined in \[EN 15982\].

+--------------------------------------------------------------------------+
|                                                       |
|                                                                          |
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
|                                                                    |
|                                                                          |
| -   [1 Attributes](Description_1.2.html#Attributes)  |
| -   [2 Content](Description_1.2.html#Content)        |
| -   [3 Example](Description_1.2.html#Example)        |
| -   [4 Guidance     |
|     Notes](Description_1.2.html#Guidance_Notes)                   |
+--------------------------------------------------------------------------+


### \[[edit](../index.php@title=Description_1.2&action=edit&section=1.html "Edit section: Attributes")\] Attributes

**@lang** (optional) The language used for the description

**@href** (optional) A link to supporting information


### \[[edit](../index.php@title=Description_1.2&action=edit&section=2.html "Edit section: Content")\] Content

The content of the element MUST be one of either:

-   Empty (@href MUST NOT be empty or missing)
-   Plain unescaped text
-   Valid XHTML 1.0 content


\[[edit](../index.php@title=Description_1.2&action=edit&section=3.html "Edit section: Example")\] Example
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

        
            
                This module shows how to take an existing presentation and modify it and how to create 
                 your own presentations. No knowledge of PowerPoint is assumed.
                The topics covered are:
                    
                        Using and modifying an existing PowerPoint presentation 
                        Creating a simple presentation 
                        Making use of themes and schemes supplied with PowerPoint 
                        The PowerPoint views 
                        Printing and saving your presentation
                    
                 
                    
        


\[[edit](../index.php@title=Description_1.2&action=edit&section=4.html "Edit section: Guidance Notes")\] Guidance Notes
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Encoding schemes:** Use of vocabularies is encouraged for
descriptions. See
[XCRI\_Terms\_1.2](XCRI_Terms_1.2.html "XCRI Terms 1.2").

**Use of images:** In general images should not be referenced from
within the description element by [providers](Provider.html "Provider")
as these are unlikely to be presented by Aggregators; potentially an
image tag can be used to execute cross-site scripting (XSS) attacks.
Instead, any image should be provided separately using the XCRI
[image](Image.html "Image") element.

**Long descriptions:** Aggregators may choose to truncate long
descriptions.

**Safe use of XHTML:** XCRI Description elements allow the delivery of
XHTML. Many elements in these languages are considered 'unsafe' in that
they open clients to one or more types of attack. Implementers of
software which processes XCRI should carefully consider their handling
of every type of element when processing incoming XHTML in XCRI XML
documents. See the security sections of IETF RFC2854 and W3C XHTML for
guidance. XCRI Aggregators should pay particular attention to the
security of the IMG, SCRIPT, EMBED, OBJECT, FRAME, FRAMESET, IFRAME,
META, and LINK elements, but other elements might also have negative
security properties. XHTML can either directly contain or indirectly
reference executable content.



Retrieved from
"[http://localhost/Description\_1.2](Description_1.2.html)"





[Category](Special%253ACategories.html "Special:Categories"): [Properties
1.2](Category%253AProperties_1.2.html "Category:Properties 1.2")

















##### Views



-   

    

    [Article](Description_1.2.html)
-   

    

    [Discussion](../index.php@title=Talk%253ADescription_1.2&action=edit.html)
-   

    

    [Edit](../index.php@title=Description_1.2&action=edit.html)
-   

    

    [History](../index.php@title=Description_1.2&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Description_1.2.html)











[](../../wiki.1.html "XCRI Wiki")





##### Navigation



-   

    

    [XCRI Wiki](../../wiki.1.html)
-   

    

    [XCRI website](http://www.xcri.org/)
-   

    

    [Current events](Current_events.html)
-   

    

    [Recent changes](Special%253ARecentchanges.html)
-   

    

    [Help](Help%253AContents.html)







##### Search





 









##### Toolbox



-   

    

    [What links here](Special%253AWhatlinkshere/Description_1.2.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Description_1.2.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Description_1.2&printable=yes.html)
-   

    

    [Permanent link](../index.php@title=Description_1.2&oldid=1270.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 15:00, 27 October 2009.
-   

    

    This page has been accessed 655 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




