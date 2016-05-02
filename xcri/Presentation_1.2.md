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







Presentation 1.2 
================













### From Xcri 







Jump to: [navigation](Presentation_1.2.html#column-one),
[search](Presentation_1.2.html#searchInput)





This definition requires an example.



*Versions*: [v1.0, v1.1](Presentation.html "Presentation"), *v1.2*

*URI*: 

*Definition*: A presentation describes a particular presentation of a
course. A presentation is a particular instance of the course offered at
a particular time and place and is the entity to which learners apply.
Alternative names for this type of structure include *course offering*
and *course instance*.

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
| -   [1 Properties](Presentation_1.2.html#Properties) |
|     -   [1.1 At     |
|         Risk](Presentation_1.2.html#At_Risk)                      |
| -   [2 Guidance     |
|     Notes](Presentation_1.2.html#Guidance_Notes)                  |
| -   [3 History](Presentation_1.2.html#History)       |
| -   [4 Usage](Presentation_1.2.html#Usage)           |
+--------------------------------------------------------------------------+


\[[edit](../index.php@title=Presentation_1.2&action=edit&section=1.html "Edit section: Properties")\] Properties
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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

[start\_1.2](Start_1.2.html "Start 1.2") (optional) when the course
presentation starts. See [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}

[end](End.html "End") (optional) when the course presentation ends

[startUntil](StartUntil.html "StartUntil") (optional)

[endFrom](EndFrom.html "EndFrom") (optional)

[duration\_1.2](Duration_1.2.html "Duration 1.2") (optional) how long
the presentation lasts. See [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}

[applyFrom](ApplyFrom.html "ApplyFrom") (optional) the date from which
applications can be made

[applyUntil](ApplyUntil.html "ApplyUntil") (optional) the closing date
for applications

[studyMode](StudyMode.html "StudyMode") (optional) the mode of study

[attendanceMode](AttendanceMode.html "AttendanceMode") (optional) DRAFT.
The primary mode of attendance, for example distance or campus-based

[attendancePattern](AttendancePattern.html "AttendancePattern")
(optional) DRAFT. The pattern of attendance, for example evenings,
daytime, weekends

[languageOfInstruction\_1.2](LanguageOfInstruction_1.2.html "LanguageOfInstruction 1.2")
(optional, multiple) a language the presentation can be taught in. See
[CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}

[languageOfAssessment](LanguageOfAssessment.html "LanguageOfAssessment")
(optional, multiple) a language the presentation can be assessed in

[places](Places.html "Places") (optional) the number of places on the
course presentation. See [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text} *Changed in 1.2*

[cost](Cost.html "Cost") (optional) how much the course presentation
costs (e.g. tuition fees). See [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}

[entryRequirements](EntryRequirements.html "EntryRequirements")
(optional) details of formal and informal requirements for entry to the
course offering

[entryProfile](EntryProfile.html "EntryProfile") (optional) information
that would help applicants match themselves to the course offering.

[venue](Venue_1.2.html "Venue 1.2") (optional, multiple, inheritable) a
place where the presentation is held, or a provider that offers the
presentation. Note that this is equivalent to MLO: OfferedAt - see [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}


### \[[edit](../index.php@title=Presentation_1.2&action=edit&section=2.html "Edit section: At Risk")\] At Risk

The following properties are at risk of being removed or replaced with
vocabularies:

[applyTo](ApplyTo.html "ApplyTo") (optional, inheritable) where to apply

[enquireTo](EnquireTo.html "EnquireTo") (optional, multiple)
instructions for sending enquiries about the presentation


\[[edit](../index.php@title=Presentation_1.2&action=edit&section=3.html "Edit section: Guidance Notes")\] Guidance Notes
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**MLO Compliance**: Presentation is equivalent to Learning Opportunity
Instance in [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}.

**Absence of applyTo organisation:** Where an organisation to apply to
is not specified, aggregators SHOULD interpret this as meaning that the
[provider](Provider.html "Provider") is the organisation to apply to,
and use its contact information for this purpose.

**Absence of Venue:** Where a venue is not specified, aggregators SHOULD
interpret this as meaning that the [provider](Provider.html "Provider")
address is the venue, and use its contact information for this purpose.

**Determining uniqueness:** Where a presentation does not contain an
identifier, aggregators may need to [construct presentation
identifiers](Construct_presentation_identifiers.html "Construct presentation identifiers").
It is recommended that presentations use a URL-formatted identifier
where possible, following the scheme for the provider and course. E.g.
""

**Absence of study mode and attendance**: Aggregators SHOULD assume that
the default for any presentation is: studymode="Full Time",
attendanceMode="Campus", attendancePattern="Daytime"

**Recstatus**: If the [recstatus](Recstatus.html "Recstatus") attribute
is used, it should be used in conjunction with an identifier.


\[[edit](../index.php@title=Presentation_1.2&action=edit&section=4.html "Edit section: History")\] History
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**v1.1**: Note the addition of new metadata fields following the
rationalisation of core metadata across the specification. Also,
[StartUntil](StartUntil.html "StartUntil"),
[EndFrom](EndFrom.html "EndFrom"),
[EnquireTo](EnquireTo.html "EnquireTo"),
[EntryProfile](EntryProfile.html "EntryProfile"),
[AttendanceMode](AttendanceMode.html "AttendanceMode") and
[AttendancePattern](AttendancePattern.html "AttendancePattern") are new
additions.

**v1.2**: Changes to core metadata; renamed placesAvailable to places
for consistency with CEN MLO.


\[[edit](../index.php@title=Presentation_1.2&action=edit&section=5.html "Edit section: Usage")\] Usage
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Presentation is used in [Course](Course.html "Course").



Retrieved from
"[http://localhost/Presentation\_1.2](Presentation_1.2.html)"





[Categories](Special%253ACategories.html "Special:Categories"): [Items needing
examples](Category%253AItems_needing_examples.html "Category:Items needing examples")
| [Resource
Types](Category%253AResource_Types.html "Category:Resource Types")
| [Classes](Category%253AClasses.html "Category:Classes")

















##### Views



-   

    

    [Article](Presentation_1.2.html)
-   

    

    [Discussion](../index.php@title=Talk%253APresentation_1.2&action=edit.html)
-   

    

    [Edit](../index.php@title=Presentation_1.2&action=edit.html)
-   

    

    [History](../index.php@title=Presentation_1.2&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Presentation_1.2.html)











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





??









##### Toolbox



-   

    

    [What links here](Special%253AWhatlinkshere/Presentation_1.2.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Presentation_1.2.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Presentation_1.2&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Presentation_1.2&oldid=1311.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 15:22, 27 October 2009.
-   

    

    This page has been accessed 3,324 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




