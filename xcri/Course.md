---
layout: post
---







Course 
======













### From Xcri 







Jump to: [navigation](Course.html#column-one),
[search](Course.html#searchInput)



*Versions*: *v1.0*, *v1.1*, [v1.2](Course_1.2.html "Course 1.2")

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
| -   [1 Properties](Course.html#Properties)           |
| -   [2 Guidance     |
|     Notes](Course.html#Guidance_Notes)                            |
| -   [3 History](Course.html#History)                 |
| -   [4 Usage](Course.html#Usage)                     |
+--------------------------------------------------------------------------+


\[[edit](../index.php@title=Course&action=edit&section=1.html "Edit section: Properties")\] Properties
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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

[qualification](Qualification.html "Qualification") (optional, multiple)
defines a qualification that can be achieved from completing the course
and its various option pathways

[presentation](Presentation.html "Presentation") (optional, multiple) a
presentation of the course to which students might apply and enrol

[credit](Credit.html "Credit") (optional) Provides details about the
quantified value of the learning awarded in recognition of the verified
achievement of designated learning outcomes at a specified level.

\


\[[edit](../index.php@title=Course&action=edit&section=2.html "Edit section: Guidance Notes")\] Guidance Notes
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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
use of the [XCRI Terms 1.1](XCRI_Terms_1.1.html "XCRI Terms 1.1")
encoding scheme to provide detailed information about the course in
different information categories. See the encoding scheme for more
details.


\[[edit](../index.php@title=Course&action=edit&section=3.html "Edit section: History")\] History
------------------------------------------------------------------------------------------------------------------------------------------------------------------

**v1.1**: As well as various changes in metadata since v1.0, note the
addition of [credit](Credit.html "Credit"), and that
[qualification](Qualification.html "Qualification") is now optional.


\[[edit](../index.php@title=Course&action=edit&section=4.html "Edit section: Usage")\] Usage
--------------------------------------------------------------------------------------------------------------------------------------------------------------

Course is available as a root element, or as part of
[provider](Provider.html "Provider")



Retrieved from "[http://localhost/Course](Course.html)"





[Category](Special%253ACategories.html "Special:Categories"): [Classes](Category%253AClasses.html "Category:Classes")

















##### Views



-   

    

    [Article](Course.html)
-   

    

    [Discussion](Talk%253ACourse.html)
-   

    

    [Edit](../index.php@title=Course&action=edit.html)
-   

    

    [History](../index.php@title=Course&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Course.html)











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

    

    [What links here](Special%253AWhatlinkshere/Course.html)
-   

    

    [Related changes](Special%253ARecentchangeslinked/Course.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable version](../index.php@title=Course&printable=yes.html)
-   

    

    [Permanent link](../index.php@title=Course&oldid=1305.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 15:19, 27 October 2009.
-   

    

    This page has been accessed 22,699 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




