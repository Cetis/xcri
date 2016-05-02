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







Transforming XHTML text into formatted plain text 
=================================================













### From Xcri 







Jump to:
[navigation](Transforming_XHTML_text_into_formatted_plain_text.html#column-one),
[search](Transforming_XHTML_text_into_formatted_plain_text.html#searchInput)



XCRI CAP allows for
[XHTML](http://www.w3.org/MarkUp/ "http://www.w3.org/MarkUp/"){.external
.text} marked-up text within the various description elements. Some
aggregators may not store XHTML text, but instead require plain text,
with some specific formatting rules.

It might be useful to provide a sample XHTML-text-to-plain-text XSLT
stylesheet. I've put together a basic prototype, which is shown below.
The entities are &\#x2022; (bullet), &\#xa; (new line) and &\#x9 (tab).

Please note that some of the element handling, specifically that for
span elements, has been written to handle some awkward (and invalid)
markup produced by Microsoft InfoPath.

The imported copy.xslt is the identity transform stylesheet as described
in [XSLT
Cookbook](http://oreilly.com/catalog/9780596009748/index.html "http://oreilly.com/catalog/9780596009748/index.html"){.external
.text}.

Feel free to update, correct or replace any code here, or point to
another stylesheet which does the job better and can be freely used.

    
    
        
        
        
        
        
        
        
        
        
        
        
        
            
        
        
            
                
                
            
        
        
            
            
            &#xa;
            
            &#xa;
        
        
            
            &#xa;
            
            &#xa;
        
        
            
            
        
        
            
            
            &#xa;
        
        
            
            
        
        
            
            
            &#x9;
            
            &#xa;
        
        
            
            
            &#x9;
            
            &#xa;
        
        
            
            &#xa;
        
        
        
    

And the copy.xslt stylesheet:

    
    
    
        
            
        
    
    



Retrieved from
"[http://localhost/Transforming\_XHTML\_text\_into\_formatted\_plain\_text](Transforming_XHTML_text_into_formatted_plain_text.html)"

















##### Views



-   

    

    [Article](Transforming_XHTML_text_into_formatted_plain_text.html)
-   

    

    [Discussion](Talk%253ATransforming_XHTML_text_into_formatted_plain_text.html)
-   

    

    [Edit](../index.php@title=Transforming_XHTML_text_into_formatted_plain_text&action=edit.html)
-   

    

    [History](../index.php@title=Transforming_XHTML_text_into_formatted_plain_text&action=history.html)







##### Personal tools



-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Transforming_XHTML_text_into_formatted_plain_text.html)











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

    

    [What links
    here](Special%253AWhatlinkshere/Transforming_XHTML_text_into_formatted_plain_text.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Transforming_XHTML_text_into_formatted_plain_text.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Transforming_XHTML_text_into_formatted_plain_text&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Transforming_XHTML_text_into_formatted_plain_text&oldid=4407.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 13:29, 21 November 2012.
-   

    

    This page has been accessed 9,230 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




