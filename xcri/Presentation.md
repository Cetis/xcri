---
layout: post
---







Presentation 
============













### From Xcri 







Jump to: [navigation](Presentation.html#column-one),
[search](Presentation.html#searchInput)





This definition requires an example.



*Versions*: *v1.0*, *v1.1*,
[v1.2](Presentation_1.2.html "Presentation 1.2")

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
| -   [1 Properties](Presentation.html#Properties)     |
| -   [2 Guidance     |
|     Notes](Presentation.html#Guidance_Notes)                      |
| -   [3 History](Presentation.html#History)           |
| -   [4 Usage](Presentation.html#Usage)               |
+--------------------------------------------------------------------------+


\[[edit](../index.php@title=Presentation&action=edit&section=1.html "Edit section: Properties")\] Properties
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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

[start](Start.html "Start") (optional) when the course presentation
starts

[startUntil](StartUntil.html "StartUntil") (optional)

[endFrom](EndFrom.html "EndFrom") (optional)

[end](End.html "End") (optional) when the course presentation ends

[duration](Duration.html "Duration") (optional) how long the
presentation lasts

[studyMode](StudyMode.html "StudyMode") (optional) the mode of study.

[attendanceMode](AttendanceMode.html "AttendanceMode") (optional) DRAFT.
The primary mode of attendance, for example distance or campus-based

[attendancePattern](AttendancePattern.html "AttendancePattern")
(optional) DRAFT. The pattern of attendance, for example evenings,
daytime, weekends

[languageOfInstruction](LanguageOfInstruction.html "LanguageOfInstruction")
(optional, multiple) a language the presentation can be taught in

[languageOfAssessment](LanguageOfAssessment.html "LanguageOfAssessment")
(optional, multiple) a language the presentation can be assessed in

[venue](Venue.html "Venue") (optional, multiple, inheritable) a place
where the presentation is held

[placesAvailable](PlacesAvailable.html "PlacesAvailable") (optional) the
number of places on the course presentation

[cost](Cost.html "Cost") (optional) how much the course presentation
costs (e.g. tuition fees)

[entryProfile](EntryProfile.html "EntryProfile") (optional) information
that would help applicants match themselves to the course offering.

[entryRequirements](EntryRequirements.html "EntryRequirements")
(optional) details of formal and informal requirements for entry to the
course offering

[applyFrom](ApplyFrom.html "ApplyFrom") (optional) the date from which
applications can be made

[applyUntil](ApplyUntil.html "ApplyUntil") (optional) the closing date
for applications

[applyTo](ApplyTo.html "ApplyTo") (optional, inheritable) where to apply

[enquireTo](EnquireTo.html "EnquireTo") (optional, multiple)
instructions for sending enquiries about the presentation


\[[edit](../index.php@title=Presentation&action=edit&section=2.html "Edit section: Guidance Notes")\] Guidance Notes
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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


\[[edit](../index.php@title=Presentation&action=edit&section=3.html "Edit section: History")\] History
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**v1.1**: Note the addition of new metadata fields following the
rationalisation of core metadata across the specification. Also,
[StartUntil](StartUntil.html "StartUntil"),
[EndFrom](EndFrom.html "EndFrom"),
[EnquireTo](EnquireTo.html "EnquireTo"),
[EntryProfile](EntryProfile.html "EntryProfile"),
[AttendanceMode](AttendanceMode.html "AttendanceMode") and
[AttendancePattern](AttendancePattern.html "AttendancePattern") are new
additions.


\[[edit](../index.php@title=Presentation&action=edit&section=4.html "Edit section: Usage")\] Usage
--------------------------------------------------------------------------------------------------------------------------------------------------------------------

Presentation is used in [Course](Course.html "Course").



Retrieved from
"[http://localhost/Presentation](Presentation.html)"





[Categories](Special%253ACategories.html "Special:Categories"): [Items needing
examples](Category%253AItems_needing_examples.html "Category:Items needing examples")
| [Resource
Types](Category%253AResource_Types.html "Category:Resource Types")
| [Classes](Category%253AClasses.html "Category:Classes")

















##### Views



-   

    

    [Article](Presentation.html)
-   

    

    [Discussion](Talk%253APresentation.html)
-   

    

    [Edit](../index.php@title=Presentation&action=edit.html)
-   

    

    [History](../index.php@title=Presentation&action=history.html)







##### Personal tools



-   

    

    [127.0.0.1](User%253A127.0.0.1.html)
-   

    

    [Talk for this IP](User_talk%253A127.0.0.1.html)
-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Presentation.html)











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

    

    [What links here](Special%253AWhatlinkshere/Presentation.html)
-   

    

    [Related changes](Special%253ARecentchangeslinked/Presentation.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Presentation&printable=yes.html)
-   

    

    [Permanent link](../index.php@title=Presentation&oldid=1854.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 12:38, 19 May 2010.
-   

    

    This page has been accessed 12,986 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




