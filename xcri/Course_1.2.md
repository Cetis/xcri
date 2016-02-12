---
layout: post
---







Course 1.2 
==========













### From Xcri 







Jump to: [navigation](Course_1.2.html#column-one),
[search](Course_1.2.html#searchInput)



*Versions*: [v1.0, v1.1](Course.html "Course"), *v1.2*

*URI*: 

*Definition*: A course provides details of a course of study offered by
a learning [provider](Provider.html "Provider").

*Type*: Class

*Namespace*: This is defined within the namespace:


+--------------------------------------------------------------------------+
|                                                       |
|                                                                          |
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
|                                                                    |
|                                                                          |
| -   [1 Properties](Course_1.2.html#Properties)       |
| -   [2 Guidance     |
|     Notes](Course_1.2.html#Guidance_Notes)                        |
| -   [3 History](Course_1.2.html#History)             |
| -   [4 Usage](Course_1.2.html#Usage)                 |
+--------------------------------------------------------------------------+


\[[edit](../index.php@title=Course_1.2&action=edit&section=1.html "Edit section: Properties")\] Properties
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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

[qualification](Qualification_1.2.html "Qualification 1.2") (optional,
multiple) defines a qualification that can be achieved from completing
the course and its various option pathways

[presentation](Presentation_1.2.html "Presentation 1.2") (optional,
multiple) a presentation of the course to which students might apply and
enrol

[credit](Credit_1.2.html "Credit 1.2") (optional) Provides details about
the quantified value of the learning awarded in recognition of the
verified achievement of designated learning outcomes at a specified
level.


\[[edit](../index.php@title=Course_1.2&action=edit&section=2.html "Edit section: Guidance Notes")\] Guidance Notes
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**MLO Compliance**: Course is equivalent to Learning Opportunity
Specification in [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}.

**Recstatus**: If the [recstatus](Recstatus.html "Recstatus") attribute
is used, it should be used in conjunction with an identifier.

**Identifier**: A Course SHOULD have a default unique identifier
formatted as a URL (e.g. "").
Additional identifiers in other formats may be used, but SHOULD be
qualified using xsi:type to a specific identifier namespace. See the
[identifier](Identifier.html "Identifier") definition for more details.

**Title**: At least one is recommended.

**Subject**: At least one is recommended. Each subject element MUST
contain a single keyword or phrase. Use multiple elements for multiple
keywords. Use of controlled vocabularies is encouraged, using vocabulary
encoding schemes.

**Description**: In addition to the general specification of
[description](Description.html "Description"), courses should also make
use of the [XCRI Terms 1.2](XCRI_Terms_1.2.html "XCRI Terms 1.2")
encoding scheme to provide detailed information about the course in
different information categories. See the encoding scheme for more
details.


\[[edit](../index.php@title=Course_1.2&action=edit&section=3.html "Edit section: History")\] History
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

**v1.1**: As well as various changes in metadata since v1.0, note the
addition of [credit](Credit.html "Credit"), and that
[qualification](Qualification.html "Qualification") is now optional.

**v1.2**: Credit model was replaced by a CEN standard model.


\[[edit](../index.php@title=Course_1.2&action=edit&section=4.html "Edit section: Usage")\] Usage
------------------------------------------------------------------------------------------------------------------------------------------------------------------

Course is available as a root element, or as part of
[provider](Provider_1.2.html "Provider 1.2")



Retrieved from
"[http://localhost/Course\_1.2](Course_1.2.html)"





[Category](Special%253ACategories.html "Special:Categories"): [Classes](Category%253AClasses.html "Category:Classes")

















##### Views



-   

    

    [Article](Course_1.2.html)
-   

    

    [Discussion](../index.php@title=Talk%253ACourse_1.2&action=edit.html)
-   

    

    [Edit](../index.php@title=Course_1.2&action=edit.html)
-   

    

    [History](../index.php@title=Course_1.2&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Course_1.2.html)











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

    

    [What links here](Special%253AWhatlinkshere/Course_1.2.html)
-   

    

    [Related changes](Special%253ARecentchangeslinked/Course_1.2.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Course_1.2&printable=yes.html)
-   

    

    [Permanent link](../index.php@title=Course_1.2&oldid=1307.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 15:20, 27 October 2009.
-   

    

    This page has been accessed 2,851 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




