---
layout: post
---







Using a static XML file 
=======================













### From Xcri 







Jump to: [navigation](Using_a_static_XML_file.html#column-one),
[search](Using_a_static_XML_file.html#searchInput)



A simple and efficient way to implement an XCRI producer is to generate
a static XML file served from a particular URL using a regular
webserver. This has the advantages of better performance as it can
leverage the static file handling capabilities of the webserver. The
process of generating the XML file from source data can be automated
using cron to schedule the generation script.

This method is only really suitable for the [Simple aggregation
pattern](Simple_aggregation_pattern.html "Simple aggregation pattern")
and doesn't enable support for [Filtering courses by
subject](Filtering_courses_by_subject.html "Filtering courses by subject")
or [Supporting XQuery](Supporting_XQuery.html "Supporting XQuery"), but
is probably quite sufficient for many providers.

**External links**

This was the approach used by the [OCCAM
Project](http://www.open.ac.uk/online/p8_2.shtml "http://www.open.ac.uk/online/p8_2.shtml"){.external
.text} for courses information from The Open University.



Retrieved from
"[http://localhost/Using\_a\_static\_XML\_file](Using_a_static_XML_file.html)"





[Category](Special%253ACategories.html "Special:Categories"): [Implementation
patterns](Category%253AImplementation_patterns.html "Category:Implementation patterns")

















##### Views



-   

    

    [Article](Using_a_static_XML_file.html)
-   

    

    [Discussion](../index.php@title=Talk%253AUsing_a_static_XML_file&action=edit.html)
-   

    

    [Edit](../index.php@title=Using_a_static_XML_file&action=edit.html)
-   

    

    [History](../index.php@title=Using_a_static_XML_file&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Using_a_static_XML_file.html)











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
    here](Special%253AWhatlinkshere/Using_a_static_XML_file.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Using_a_static_XML_file.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Using_a_static_XML_file&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Using_a_static_XML_file&oldid=2217.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 15:47, 6 October 2010.
-   

    

    This page has been accessed 2,792 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




