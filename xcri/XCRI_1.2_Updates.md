---
layout: post
---







XCRI 1.2 Updates 
================













### From Xcri 







Jump to: [navigation](XCRI_1.2_Updates.html#column-one),
[search](XCRI_1.2_Updates.html#searchInput)






Editor's NoteThis is just an initial draft pulling together
various other bits of documentation, and needs more work



+--------------------------------------------------------------------------+
|                                                       |
|                                                                          |
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
|                                                                    |
|                                                                          |
| -   [1 About](XCRI_1.2_Updates.html#About)           |
|     -   [1.1 Status](XCRI_1.2_Updates.html#Status)     |
|     -   [1.2 Patents](XCRI_1.2_Updates.html#Patents)   |
|     -   [1.3 Copyright and                                    |
|         License](XCRI_1.2_Updates.html#Copyright_and_License)     |
|     -   [1.4 Inspiration and                                  |
|         acknowledgements](XCRI_1.2_Updates.html#Inspiration_and_a |
| cknowledgements)                                                         |
| -   [2 Introduction](XCRI_1.2_Updates.html#Introduct |
| ion)                                                                     |
| -   [3 Pull         |
|     model](XCRI_1.2_Updates.html#Pull_model)                      |
|     -   [3.1 Overview of the interaction between data         |
|         collecting organisation and                                      |
|         provider](XCRI_1.2_Updates.html#Overview_of_the_interacti |
| on_between_data_collecting_organisation_and_provider)                    |
|     -   [3.2 Provider updates local                           |
|         system](XCRI_1.2_Updates.html#Provider_updates_local_syst |
| em)                                                                      |
|     -   [3.3 Data   |
|         collecting organisation gets                                     |
|         update](XCRI_1.2_Updates.html#Data_collecting_organisatio |
| n_gets_update)                                                           |
| -   [4 The          |
|     recstatus                                                            |
|     attribute](XCRI_1.2_Updates.html#The_recstatus_attribute)     |
|     -   [4.1 Example](XCRI_1.2_Updates.html#Example)   |
|     -   [4.2 Usage](XCRI_1.2_Updates.html#Usage)       |
+--------------------------------------------------------------------------+


\[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=1.html "Edit section: About")\] About
------------------------------------------------------------------------------------------------------------------------------------------------------------------------




Editor's NoteMaybe move some of the names to the acknowledgements
section, and add in contributors from the forum etc



Editors:

-   Mark Stubbs (m.stubbs@mmu.ac.uk)
-   Scott Wilson (scott.bradley.wilson@gmail.com)
-   Alan Paull (alan@alanpaull.co.uk)

Authors:

-   [Simon
    Grant](http://www.simongrant.org/home.html "http://www.simongrant.org/home.html")
-   Alan Paull (alan@alanpaull.co.uk)
-   Ben Ryan (mail@benryan.co.uk)
-   Mark Stubbs (m.stubbs@mmu.ac.uk)
-   Scott Wilson (scott.bradley.wilson@gmail.com)


### \[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=2.html "Edit section: Status")\] Status

This is currently a working draft of version 1.2.


### \[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=3.html "Edit section: Patents")\] Patents

This specification is subject to a royalty free patent policy.

There are no known patents covering any of this work. If you think that
part of this work may be subject to an existing or pending patent,
please email the editors.


### \[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=4.html "Edit section: Copyright and License")\] Copyright and License

This work is (c) 2005-2010 XCRI.org, and licensed under a Creative
Commons Attribution 3.0 Licence. All contributions MUST be licensed
under the same conditions. This is to ensure that the specification work
can be transferred to an appropriate standardisation body.


### \[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=5.html "Edit section: Inspiration and acknowledgements")\] Inspiration and acknowledgements

We would like to thank the many UK institutions and lifelong learning
networks that have contributed to its development through their work on
implementation. We also thank JISC for supporting the development of
this specification.


\[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=6.html "Edit section: Introduction")\] Introduction
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The delta update or delta harvesting pattern involves a data collector
receiving or taking updated data only, in contrast to whole data sets.
This method can be implemented in a wide variety of ways, including the
use of static files and dynamic system-to-system procedures either by
pushing the updates or pulling them. It relies on the provider
implementing a minimum level of auditing information that can be
referenced by the data aggregator. The main structures in XCRI-CAP
contain a [recstatus](Recstatus.html "Recstatus") attribute that
satisfies the minimum requirement.


\[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=7.html "Edit section: Pull model")\]  Pull model 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

A potential method is shown in the following diagrams. This method pulls
the updates from the provider's system, so that control of timing rests
with the data collector, which is assumed to be a separate organisation
for the purposes of this example.

\


### \[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=8.html "Edit section: Overview of the interaction between data collecting organisation and provider")\]  Overview of the interaction between data collecting organisation and provider 

[![Overview of the interaction between data collecting organisation and
provider](../images/2/29/DraftUpdateProcess.gif){width="974"
height="290"}](Image%253ADraftUpdateProcess.gif.html "Overview of the interaction between data collecting organisation and provider")

\


### \[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=9.html "Edit section: Provider updates local system")\]  Provider updates local system 

[![Provider updates local
system](../images/a/a8/ProviderUpdatesLocalSystem.gif){width="454"
height="309"}](Image%253AProviderUpdatesLocalSystem.gif.html "Provider updates local system")

\


### \[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=10.html "Edit section: Data collecting organisation gets update")\]  Data collecting organisation gets update 

[![Data collector pulls
update](../images/8/8b/GetUpdate.gif){width="643"
height="701"}](Image%253AGetUpdate.gif.html "Data collector pulls update")

\
**For further discussion:** It is likely that more extensive logging,
including date:time might be needed to enable delta harvesting.


\[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=11.html "Edit section: The recstatus attribute")\] The recstatus attribute
=============================================================================================================================================================================================================

*URI: *

The optional recstatus attribute provides a mechanism for indicating
whether the resource to which it refers has changed. The enumerated
value of the attribute indicates the nature of the change:

1.  = Added
2.  = Updated
3.  = Deleted

This attribute MUST contain only one of "1", "2" or "3" with no leading
or trailing whitespace.

An element that has this attribute MUST include an identifier element
that supplies a persistent, unique value so that the recipient of the
xml can maintain state for itself.


\[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=12.html "Edit section: Example")\] Example
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    
         http://xcri.org/example/courses/1
         ...


\[[edit](../index.php@title=XCRI_1.2_Updates&action=edit&section=13.html "Edit section: Usage")\] Usage
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Recstatus may be used in the Course and Provider elements of an XCRI
document.



Retrieved from
"[http://localhost/XCRI\_1.2\_Updates](XCRI_1.2_Updates.html)"

















##### Views



-   

    

    [Article](XCRI_1.2_Updates.html)
-   

    

    [Discussion](Talk%253AXCRI_1.2_Updates.html)
-   

    

    [Edit](../index.php@title=XCRI_1.2_Updates&action=edit.html)
-   

    

    [History](../index.php@title=XCRI_1.2_Updates&action=history.html)







##### Personal tools



-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=XCRI_1.2_Updates.html)











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

    

    [What links here](Special%253AWhatlinkshere/XCRI_1.2_Updates.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/XCRI_1.2_Updates.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=XCRI_1.2_Updates&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=XCRI_1.2_Updates&oldid=4356.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 12:38, 27 March 2012.
-   

    

    This page has been accessed 4,929 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




