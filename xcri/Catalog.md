---
layout: post
---







Catalog 
=======













### From Xcri 







Jump to: [navigation](Catalog.html#column-one),
[search](Catalog.html#searchInput)



*URI*: 

*Definition*: Catalog is the default root element for XCRI's Course
Advertising schema and provides a generic container element for an XCRI
feed. It prescribes one or more [providers](Provider.html "Provider")
and a mandatory attribute that timestamps generation of the XML feed. A
Catalog does not necessarily relate to a concept of a "Catalog" in an
originating or consuming system, but rather provides the context for the
content of the feed.

*Type*: Class

*Namespace*: This is defined within the namespace:



\[[edit](../index.php@title=Catalog&action=edit&section=1.html "Edit section: Properties")\] Properties
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

@[generated](Generated.html "Generated") The date and time at which the
catalog was generated, in ISO format. Both date and time should be used.

@[recstatus](Recstatus.html "Recstatus") (optional) if the [delta update
pattern](Delta_update_pattern.html "Delta update pattern") is in use,
this attribute MAY be used to indicate the status of the resource.

[identifier](Identifier.html "Identifier") (optional, multiple) An
identifier

[title](Title.html "Title") (optional, multiple) The title of the
resource

[subject](Subject.html "Subject") (optional, multiple) A tag describing
the resource

[description](Description.html "Description") (optional, multiple)
Descriptive information

[relation](Relation.html "Relation") (optional, multiple) A relationship
to another resource

[url](Url.html "Url") (optional) A URL for further information

[image](Image.html "Image") (optional) An image that represents the
resource, such as a photo or logo

[provider](Provider.html "Provider") (optional, multiple)


\[[edit](../index.php@title=Catalog&action=edit&section=2.html "Edit section: Guidance Notes")\] Guidance Notes
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**provider**: In almost all cases there SHOULD be one and only one
provider in a feed, and this should be the provider that offers the
feed. The capability for supporting zero providers is offered for cases
where XCRI CAP is used to format course search results. The capability
for supporting multiple providers is offered to assist cases where
aggregators wish to combine several feeds for processing, or for sharing
feeds between aggregators.


\[[edit](../index.php@title=Catalog&action=edit&section=3.html "Edit section: History")\] History
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

**v1.1 changes**: Note that in v1.0 the catalog resource only contained
its generated attribute and the provider; additional metadata was added
in v1.1.



Retrieved from "[http://localhost/Catalog](Catalog.html)"





[Category](Special%253ACategories.html "Special:Categories"): [Classes](Category%253AClasses.html "Category:Classes")

















##### Views



-   

    

    [Article](Catalog.html)
-   

    

    [Discussion](../index.php@title=Talk%253ACatalog&action=edit.html)
-   

    

    [Edit](../index.php@title=Catalog&action=edit.html)
-   

    

    [History](../index.php@title=Catalog&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Catalog.html)











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

    

    [What links here](Special%253AWhatlinkshere/Catalog.html)
-   

    

    [Related changes](Special%253ARecentchangeslinked/Catalog.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable version](../index.php@title=Catalog&printable=yes.html)
-   

    

    [Permanent link](../index.php@title=Catalog&oldid=4344.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 08:42, 19 March 2012.
-   

    

    This page has been accessed 11,961 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




