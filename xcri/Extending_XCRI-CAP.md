---
layout: post
---







Extending XCRI-CAP 
==================













### From Xcri 







Jump to: [navigation](Extending_XCRI-CAP.html#column-one),
[search](Extending_XCRI-CAP.html#searchInput)



+--------------------------------------------------------------------------+
|                                                       |
|                                                                          |
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
|                                                                    |
|                                                                          |
| -   [1 Overview](Extending_XCRI-CAP.html#Overview)   |
| -   [2 Inclusion of |
|     additional                                                           |
|     properties](Extending_XCRI-CAP.html#Inclusion_of_additional_p |
| roperties)                                                               |
| -   [3 Encoding     |
|     schemes](Extending_XCRI-CAP.html#Encoding_schemes)            |
|     -   [3.1 Syntax |
|         encoding                                                         |
|         schemes](Extending_XCRI-CAP.html#Syntax_encoding_schemes) |
|     -   [3.2 Vocabulary encoding                              |
|         schemes](Extending_XCRI-CAP.html#Vocabulary_encoding_sche |
| mes)                                                                     |
+--------------------------------------------------------------------------+


\[[edit](../index.php@title=Extending_XCRI-CAP&action=edit&section=1.html "Edit section: Overview")\] Overview
================================================================================================================================================================================

There are a number of extension mechanisms that you can use in XCRI-CAP:

-   Adding a property from another namespace
-   Constraining the structure of a property using a syntax encoding
    scheme
-   Constraining the values of a property using a vocabulary encoding
    scheme

Information on the different methods is given below.

If you make an extension, please add it to the [XCRI-CAP Extensions
Registry](XCRI-CAP_Extensions_Registry.html "XCRI-CAP Extensions Registry").


\[[edit](../index.php@title=Extending_XCRI-CAP&action=edit&section=2.html "Edit section: Inclusion of additional properties")\] Inclusion of additional properties
====================================================================================================================================================================================================================================

XCRI-CAP already makes use of some external schemas, such as XHTML.
Implementers are free to include additional elements where the XCRI-CAP
schema permits, provided this is done (1) using an explicitly referenced
namespace, and (2) the resource or property permits extension in the
XCRI-CAP XSD. There are no particular limits on the type or structure of
additional properties.


\[[edit](../index.php@title=Extending_XCRI-CAP&action=edit&section=3.html "Edit section: Encoding schemes")\] Encoding schemes
================================================================================================================================================================================================

XCRI-CAP makes extensive use of encoding schemes to handle a range of
diverse value-spaces, both for structured values (syntax encoding
schemes) and controlled vocabularies (vocabulary encoding schemes). For
example, properties such as [identifier](Identifier.html "Identifier")
are designed to be used in conjunction with encoding schemes to enable
the representation of third-party identification mechanisms, so that a
[course](Course.html "Course") can be identified using the identifier
issued by the institution, the identifier expected by a major broker
such as UCAS, and with the identifier issued by other agencies.
Aggregators and brokers should check the values of elements for encoding
schemes so that they make use of the correct value for their business
rules.


\[[edit](../index.php@title=Extending_XCRI-CAP&action=edit&section=4.html "Edit section: Syntax encoding schemes")\] Syntax encoding schemes
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The general pattern of usage for syntax encoding schemes follows that of
Dublin Core, with the use of the xsi:type attribute to identify the
encoding scheme used for the enclosed value by a URI consisting of a
namespace prefix and the encoding scheme name. For example:

    12345

The following encoding schemes are known for use with XCRI-CAP within
the context of the [identifier](Identifier.html "Identifier") element:

-   **ukrlp:ukprn** The UK [Unique Provider Reference
    Number](http://www.ukrlp.co.uk/ "http://www.ukrlp.co.uk/")
-    ???:??? UCAS course ID

The following encoding schemes are known for use with XCRI-CAP within
the context of use of dc:subject for [courses](Course.html "Course"):

-    ???:??? UCAS JACS code
    --[scottwilson](../index.php@title=User%253AScottwilson&action=edit.html "User:Scottwilson")
    23:25, 20 March 2007 (UTC)
-   Lots of subject codes as used in DC?
    --[scottwilson](../index.php@title=User%253AScottwilson&action=edit.html "User:Scottwilson")
    23:25, 20 March 2007 (UTC)


\[[edit](../index.php@title=Extending_XCRI-CAP&action=edit&section=5.html "Edit section: Vocabulary encoding schemes")\] Vocabulary encoding schemes
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The following vocabulary encoding schemes are defined within XCRI-CAP
for use with the [description](Description.html "Description") element:

-   [XCRI Terms 1.1](XCRI_Terms_1.1.html "XCRI Terms 1.1")

These are used differently from the syntax encoding schemes above. Check
the documentation of the [description](Description.html "Description")
element for usage.

Implementers are of course free to add other vocabularies. To use these
it is suggested that the xsi:type attribute is used to qualify the
element that the vocabulary is being applied to as being of a qualified
type. The type itself should be defined in a referenced schema using an
XML Schema enumeration.



Retrieved from
"[http://localhost/Extending\_XCRI-CAP](Extending_XCRI-CAP.html)"

















##### Views



-   

    

    [Article](Extending_XCRI-CAP.html)
-   

    

    [Discussion](../index.php@title=Talk%253AExtending_XCRI-CAP&action=edit.html)
-   

    

    [Edit](../index.php@title=Extending_XCRI-CAP&action=edit.html)
-   

    

    [History](../index.php@title=Extending_XCRI-CAP&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Extending_XCRI-CAP.html)











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

    

    [What links here](Special%253AWhatlinkshere/Extending_XCRI-CAP.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Extending_XCRI-CAP.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Extending_XCRI-CAP&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Extending_XCRI-CAP&oldid=746.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 16:33, 23 January 2008.
-   

    

    This page has been accessed 2,884 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




