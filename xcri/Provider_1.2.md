---
layout: post
---







Provider 1.2 
============













### From Xcri 







Jump to: [navigation](Provider_1.2.html#column-one),
[search](Provider_1.2.html#searchInput)



*URI*: 

*Definition*: Providers are organisations that offer one or more
[courses](Course.html "Course").

*Type*: Class

*Namespace*: This is defined within the namespace:



### \[[edit](../index.php@title=Provider_1.2&action=edit&section=1.html "Edit section: Properties")\] Properties

@[recstatus](Recstatus.html "Recstatus") (optional) if the [delta update
pattern](Delta_update_pattern.html "Delta update pattern") is in use,
this attribute MAY be used to indicate the status of the resource.

-   has\_part (optional, multiple)
-   contributor (optional, multiple)
-   date (optional, multiple)
-   description (optional, multiple)
-   identifier (optional, multiple)
-   image (optional)
-   subject (optional, multiple)
-   title (optional, multiple)
-   type (optional, multiple)
-   url (optional)

[location](Location.html "Location") (optional) the location of the
provider. See [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}. *New in 1.2*

[course](Course_1.2.html "Course 1.2") (optional, multiple) a course
offered by the Provider.


\[[edit](../index.php@title=Provider_1.2&action=edit&section=2.html "Edit section: Guidance Notes")\] Guidance Notes
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**MLO Compliance**: Provider is equivalent to Learning Opportunity
Provider in [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}.

**Identifiers**: A Provider SHOULD have a default unique identifier
formatted as a URL (e.g. ""). Additional
identifiers in other formats may be used, but SHOULD be qualified using
xsi:type to a specific identifier namespace. An example would include
the UK provider reference number (UKPRN) within the UKRLP:UKPRN
namespace. See the [identifier](Identifier.html "Identifier") definition
for more details.

**Title**: a Provider SHOULD have a title.

**Description**: A Provider SHOULD have a description, generally a small
amount of generic information about the provider.

If a delta update pattern is being used, the
[recstatus](Recstatus.html "Recstatus") attribute can alert an
aggregator to a change in provider details. Whenever
[recstatus](Recstatus.html "Recstatus") is used, provider.identifier
must contain a persistent, unique identifier, so that an aggregator can
identify what has changed, as well as how it has changed (addition,
modification or deletion).

**Street**, **Town** and **Postcode**: It is recommended that these are
included in the provider information.

**Url**: A Provider SHOULD have a URL for its homepage, or its
applications microsite, in addition to its primary domain identifier
(see above).

**Course**: In almost all cases there SHOULD be at least one course for
a provider. The capability for supporting zero courses is offered for
cases where XCRI CAP is used to format course search results.


\[[edit](../index.php@title=Provider_1.2&action=edit&section=3.html "Edit section: History")\] History
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**v1.1**: Since v1.0 the common metadata for providers, courses, and
other resources was rationalized. This means quite a few minor changes.
In particular, elements that were mandatory or single in v1.0 are now
mostly optional and multiple.

**v1.2**: Since v1.2 the location data has been encapsulated in its own
location element; core properties have also been updated with some new
additions.



Retrieved from
"[http://localhost/Provider\_1.2](Provider_1.2.html)"





[Categories](Special%253ACategories.html "Special:Categories"): [Classes](Category%253AClasses.html "Category:Classes")
| [Organisation
Types](Category%253AOrganisation_Types.html "Category:Organisation Types")

















##### Views



-   

    

    [Article](Provider_1.2.html)
-   

    

    [Discussion](../index.php@title=Talk%253AProvider_1.2&action=edit.html)
-   

    

    [Edit](../index.php@title=Provider_1.2&action=edit.html)
-   

    

    [History](../index.php@title=Provider_1.2&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Provider_1.2.html)











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

    

    [What links here](Special%253AWhatlinkshere/Provider_1.2.html)
-   

    

    [Related changes](Special%253ARecentchangeslinked/Provider_1.2.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Provider_1.2&printable=yes.html)
-   

    

    [Permanent link](../index.php@title=Provider_1.2&oldid=1161.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 15:57, 26 October 2009.
-   

    

    This page has been accessed 2,150 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




