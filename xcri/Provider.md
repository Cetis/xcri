---
layout: post
---







Provider 
========













### From Xcri 







Jump to: [navigation](Provider.html#column-one),
[search](Provider.html#searchInput)



*URI*: 

*Definition*: Providers are organisations that offer one or more
[courses](Course.html "Course").

*Type*: Class

*Namespace*: This is defined within the namespace:



### \[[edit](../index.php@title=Provider&action=edit&section=1.html "Edit section: Properties")\] Properties

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

[street](../index.php@title=Street&action=edit.html "Street")
(optional) Street address

[town](../index.php@title=Town&action=edit.html "Town") (optional)
Postal town

[postcode](../index.php@title=Postcode&action=edit.html "Postcode")
(optional) PostCode for the address. This MUST NOT be a POBox or other
'virtual' address as aggregators should be able to use this for
geocoding. Use a typed address line entry for POBox.

[address](Address.html "Address") (optional, multiple) Additional
address information, expressed as a String with an optional @type
attribute describing the type of address information. May occur zero or
more times to hold address line information that benefits from being
broken down for display purposes.

[phone](Phone.html "Phone") (optional) A phone number as it would be
dialled from the UK

[fax](Fax.html "Fax") (optional) A fax number as it would be dialled
from the UK

[email](Email.html "Email") (optional) An email address

[course](Course.html "Course") (optional, multiple) a course offered by
the Provider.


\[[edit](../index.php@title=Provider&action=edit&section=2.html "Edit section: Guidance Notes")\] Guidance Notes
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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


\[[edit](../index.php@title=Provider&action=edit&section=3.html "Edit section: History")\] History
--------------------------------------------------------------------------------------------------------------------------------------------------------------------

**v1.1**: Since v1.0 the common metadata for providers, courses, and
other resources was rationalized. This means quite a few minor changes.
In particular, elements that were mandatory or single in v1.0 are now
mostly optional and multiple.



Retrieved from
"[http://localhost/Provider](Provider.html)"





[Categories](Special%253ACategories.html "Special:Categories"): [Classes](Category%253AClasses.html "Category:Classes")
| [Organisation
Types](Category%253AOrganisation_Types.html "Category:Organisation Types")

















##### Views



-   

    

    [Article](Provider.html)
-   

    

    [Discussion](Talk%253AProvider.html)
-   

    

    [Edit](../index.php@title=Provider&action=edit.html)
-   

    

    [History](../index.php@title=Provider&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Provider.html)











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

    

    [What links here](Special%253AWhatlinkshere/Provider.html)
-   

    

    [Related changes](Special%253ARecentchangeslinked/Provider.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable version](../index.php@title=Provider&printable=yes.html)
-   

    

    [Permanent link](../index.php@title=Provider&oldid=912.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 21:21, 8 February 2008.
-   

    

    This page has been accessed 13,300 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




