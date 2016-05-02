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







Recstatus 
=========













### From Xcri 







Jump to: [navigation](Recstatus.html#column-one),
[search](Recstatus.html#searchInput)



*URI*: 

*Definition*: The optional recstatus attribute provides a mechanism for
indicating whether the resource to which it refers has changed.

*Type*: Enumeration

The enumerated value of the attribute indicates the nature of the
change:

1.  = Added
2.  = Updated
3.  = Deleted

A resource that has this attribute MUST include an identifier element
that supplies a persistent, unique value so that the recipient of the
xml can maintain state for itself.

*Namespace*: This is defined within the namespace:



\[[edit](../index.php@title=Recstatus&action=edit&section=1.html "Edit section: Example")\] Example
---------------------------------------------------------------------------------------------------------------------------------------------------------------------

    


\[[edit](../index.php@title=Recstatus&action=edit&section=2.html "Edit section: Guidance Notes")\] Guidance Notes
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Recstatus is only used with the [delta update
pattern](Delta_update_pattern.html "Delta update pattern"). The [simple
aggregation
pattern](Simple_aggregation_pattern.html "Simple aggregation pattern")
does not use this attribute.


\[[edit](../index.php@title=Recstatus&action=edit&section=3.html "Edit section: Usage")\] Usage
-----------------------------------------------------------------------------------------------------------------------------------------------------------------

Recstatus is used in:

1.  [catalog](Catalog.html "Catalog")
2.  [course](Course.html "Course")
3.  [provider](Provider.html "Provider")
4.  [qualification](Qualification.html "Qualification")
5.  [presentation](Presentation.html "Presentation")
6.  [entryProfile](EntryProfile.html "EntryProfile")
7.  [entryRequirements](EntryRequirements.html "EntryRequirements")
8.  [venue](Venue.html "Venue")



Retrieved from
"[http://localhost/Recstatus](Recstatus.html)"





[Categories](Special%253ACategories.html "Special:Categories"): [Properties](Category%253AProperties.html "Category:Properties")
| [Properties
1.2](Category%253AProperties_1.2.html "Category:Properties 1.2")

















##### Views



-   

    

    [Article](Recstatus.html)
-   

    

    [Discussion](../index.php@title=Talk%253ARecstatus&action=edit.html)
-   

    

    [Edit](../index.php@title=Recstatus&action=edit.html)
-   

    

    [History](../index.php@title=Recstatus&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Recstatus.html)











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

    

    [What links here](Special%253AWhatlinkshere/Recstatus.html)
-   

    

    [Related changes](Special%253ARecentchangeslinked/Recstatus.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable version](../index.php@title=Recstatus&printable=yes.html)
-   

    

    [Permanent link](../index.php@title=Recstatus&oldid=2830.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 20:01, 6 February 2011.
-   

    

    This page has been accessed 5,266 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




