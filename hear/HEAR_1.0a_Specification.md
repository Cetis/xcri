---
layout: default
---






HEAR 1.0a Specification 
=======================



### From Xcri 







Jump to: [navigation](HEAR_1.0a_Specification#column-one),
[search](HEAR_1.0a_Specification#searchInput)



+--------------------------------------------------------------------------+
|                                                       |
|                                                                          |
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
|                                                                    |
|                                                                          |
| -   [1 About](HEAR_1.0a_Specification#About)         |
|     -   [1.1 Status](HEAR_1.0a_Specification#Status)   |
|     -   [1.2 Patents](HEAR_1.0a_Specification#Patents) |
|     -   [1.3 Copyright and                                    |
|         License](HEAR_1.0a_Specification#Copyright_and_License)   |
|     -   [1.4 Inspiration and                                  |
|         acknowledgements](HEAR_1.0a_Specification#Inspiration_and |
| _acknowledgements)                                                       |
|     -   [1.5 Introduction](HEAR_1.0a_Specification#Int |
| roduction)                                                               |
| -   [2 Conformance](HEAR_1.0a_Specification#Conforma |
| nce)                                                                     |
| -   [3 HEAR         |
|     Documents](HEAR_1.0a_Specification#HEAR_Documents)            |
|     -   [3.1 The    |
|         HEAR Template](HEAR_1.0a_Specification#The_HEAR_Template) |
|         -   [3.1.1 Contextual                                   |
|             Information](HEAR_1.0a_Specification#Contextual_Infor |
| mation)                                                                  |
|     -   [3.2 XML    |
|         Document                                                         |
|         Structure](HEAR_1.0a_Specification#XML_Document_Structure |
| )                                                                        |
|     -   [3.3 Core   |
|         elements](HEAR_1.0a_Specification#Core_elements)          |
|         -   [3.3.1 the &lt;achievementReport&gt;                |
|             element](HEAR_1.0a_Specification#the_.3CachievementRe |
| port.3E_element)                                                         |
|             -   [3.3.1.1 Definition](HEAR_1.0a_Specificati |
| on#Definition)                                                           |
|             -   [3.3.1.2 Core elements used within the            |
|                 achievementReport                                        |
|                 element](HEAR_1.0a_Specification#Core_elements_us |
| ed_within_the_achievementReport_element)                                 |
|     -   [3.4 Specification of elements below the root         |
|         element](HEAR_1.0a_Specification#Specification_of_element |
| s_below_the_root_element)                                                |
|         -   [3.4.1 the &lt;issuer&gt;                           |
|             element](HEAR_1.0a_Specification#the_.3Cissuer.3E_ele |
| ment)                                                                    |
|             -   [3.4.1.1 Definition](HEAR_1.0a_Specificati |
| on#Definition_2)                                                         |
|             -   [3.4.1.2 Constraints](HEAR_1.0a_Specificat |
| ion#Constraints)                                                         |
|             -   [3.4.1.3 Namespaces](HEAR_1.0a_Specificati |
| on#Namespaces)                                                           |
|             -   [3.4.1.4 Sub-elements used in the &lt;issuer&gt;  |
|                 element](HEAR_1.0a_Specification#Sub-elements_use |
| d_in_the_.3Cissuer.3E_element)                                           |
|         -   [3.4.2 the &lt;learner&gt;                          |
|             element](HEAR_1.0a_Specification#the_.3Clearner.3E_el |
| ement)                                                                   |
|             -   [3.4.2.1 Definition](HEAR_1.0a_Specificati |
| on#Definition_3)                                                         |
|             -   [3.4.2.2 Constraints](HEAR_1.0a_Specificat |
| ion#Constraints_2)                                                       |
|             -   [3.4.2.3 Namespaces](HEAR_1.0a_Specificati |
| on#Namespaces_2)                                                         |
|             -   [3.4.2.4 Sub-elements used in the &lt;learner&gt; |
|                 element](HEAR_1.0a_Specification#Sub-elements_use |
| d_in_the_.3Clearner.3E_element)                                          |
|         -   [3.4.3 the &lt;qualification&gt;                    |
|             element](HEAR_1.0a_Specification#the_.3Cqualification |
| .3E_element)                                                             |
|             -   [3.4.3.1 Definition](HEAR_1.0a_Specificati |
| on#Definition_4)                                                         |
|             -   [3.4.3.2 Constraints](HEAR_1.0a_Specificat |
| ion#Constraints_3)                                                       |
|             -   [3.4.3.3 Namespaces](HEAR_1.0a_Specificati |
| on#Namespaces_3)                                                         |
|             -   [3.4.3.4 Sub-elements used in the                 |
|                 &lt;qualification&gt;                                    |
|                 element](HEAR_1.0a_Specification#Sub-elements_use |
| d_in_the_.3Cqualification.3E_element)                                    |
|             -   [3.4.3.5 Attributes](HEAR_1.0a_Specificati |
| on#Attributes)                                                           |
|         -   [3.4.4 the &lt;provider&gt;                         |
|             element](HEAR_1.0a_Specification#the_.3Cprovider.3E_e |
| lement)                                                                  |
|             -   [3.4.4.1 Definition](HEAR_1.0a_Specificati |
| on#Definition_5)                                                         |
|             -   [3.4.4.2 Constraints](HEAR_1.0a_Specificat |
| ion#Constraints_4)                                                       |
|             -   [3.4.4.3 Namespaces](HEAR_1.0a_Specificati |
| on#Namespaces_4)                                                         |
|             -   [3.4.4.4 Sub-elements used in the                 |
|                 &lt;provider&gt;                                         |
|                 element](HEAR_1.0a_Specification#Sub-elements_use |
| d_in_the_.3Cprovider.3E_element)                                         |
|             -   [3.4.4.5 Attributes](HEAR_1.0a_Specificati |
| on#Attributes_2)                                                         |
|         -   [3.4.5 the &lt;course&gt;                           |
|             element](HEAR_1.0a_Specification#the_.3Ccourse.3E_ele |
| ment)                                                                    |
|             -   [3.4.5.1 Definition](HEAR_1.0a_Specificati |
| on#Definition_6)                                                         |
|             -   [3.4.5.2 Constraints](HEAR_1.0a_Specificat |
| ion#Constraints_5)                                                       |
|             -   [3.4.5.3 Namespaces](HEAR_1.0a_Specificati |
| on#Namespaces_5)                                                         |
|             -   [3.4.5.4 Sub-elements used in the &lt;course&gt;  |
|                 element at Programme                                     |
|                 Level](HEAR_1.0a_Specification#Sub-elements_used_ |
| in_the_.3Ccourse.3E_element_at_Programme_Level)                          |
|             -   [3.4.5.5 Sub-elements used in the &lt;course&gt;  |
|                 element at other                                         |
|                 levels](HEAR_1.0a_Specification#Sub-elements_used |
| _in_the_.3Ccourse.3E_element_at_other_levels)                            |
|             -   [3.4.5.6 Sub-elements used in the                 |
|                 &lt;presentation&gt; element at Programme                |
|                 Level](HEAR_1.0a_Specification#Sub-elements_used_ |
| in_the_.3Cpresentation.3E_element_at_Programme_Level)                    |
|             -   [3.4.5.7 Sub-elements used in the                 |
|                 &lt;presentation&gt; element at other                    |
|                 levels](HEAR_1.0a_Specification#Sub-elements_used |
| _in_the_.3Cpresentation.3E_element_at_other_levels)                      |
|         -   [3.4.6 the &lt;assessment&gt;                       |
|             element](HEAR_1.0a_Specification#the_.3Cassessment.3E |
| _element)                                                                |
|             -   [3.4.6.1 Definition](HEAR_1.0a_Specificati |
| on#Definition_7)                                                         |
|             -   [3.4.6.2 Constraints](HEAR_1.0a_Specificat |
| ion#Constraints_6)                                                       |
|             -   [3.4.6.3 Namespaces](HEAR_1.0a_Specificati |
| on#Namespaces_6)                                                         |
|             -   [3.4.6.4 Sub-elements used in the                 |
|                 &lt;assessment&gt;                                       |
|                 element](HEAR_1.0a_Specification#Sub-elements_use |
| d_in_the_.3Cassessment.3E_element)                                       |
|             -   [3.4.6.5 Attributes](HEAR_1.0a_Specificati |
| on#Attributes_3)                                                         |
|         -   [3.4.7 the &lt;additionalInformation&gt;            |
|             element](HEAR_1.0a_Specification#the_.3CadditionalInf |
| ormation.3E_element)                                                     |
|             -   [3.4.7.1 Definition](HEAR_1.0a_Specificati |
| on#Definition_8)                                                         |
|             -   [3.4.7.2 Constraints](HEAR_1.0a_Specificat |
| ion#Constraints_7)                                                       |
|             -   [3.4.7.3 Namespaces](HEAR_1.0a_Specificati |
| on#Namespaces_7)                                                         |
|             -   [3.4.7.4 Sub-elements used in the                 |
|                 &lt;additionalInformation&gt;                            |
|                 element](HEAR_1.0a_Specification#Sub-elements_use |
| d_in_the_.3CadditionalInformation.3E_element)                            |
|         -   [3.4.8 the &lt;certificationOftheHEAR&gt;           |
|             element](HEAR_1.0a_Specification#the_.3Ccertification |
| OftheHEAR.3E_element)                                                    |
|             -   [3.4.8.1 Definition](HEAR_1.0a_Specificati |
| on#Definition_9)                                                         |
|             -   [3.4.8.2 Constraints](HEAR_1.0a_Specificat |
| ion#Constraints_8)                                                       |
|             -   [3.4.8.3 Sub-elements used in the                 |
|                 &lt;certificationOftheHEAR&gt;                           |
|                 element](HEAR_1.0a_Specification#Sub-elements_use |
| d_in_the_.3CcertificationOftheHEAR.3E_element)                           |
| -   [4 XML Schema   |
|     and                                                                  |
|     Instance](HEAR_1.0a_Specification#XML_Schema_and_Instance)    |
+--------------------------------------------------------------------------+


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=1 "Edit section: About")\] About
================================================================================================================================================================================================

*Back to [HEAR
home](HEAR "http://www.xcri.org/HEAR")*

Editors:

-   Scott Wilson (scott.bradley.wilson@gmail.com)
-   Alan Paull (alan@alanpaull.co.uk)
-   Richard Entwistle (richard.entwistle@igsl.co.uk)

Authors:

-   Scott Wilson (scott.bradley.wilson@gmail.com)
-   Alan Paull (alan@alanpaull.co.uk)
-   Richard Entwistle (richard.entwistle@igsl.co.uk)


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=2 "Edit section: Status")\] Status

This is currently a working draft of version 1.0a.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=3 "Edit section: Patents")\] Patents

This specification is subject to a royalty free patent policy.

There are no known patents covering any of this work. If you think that
part of this work may be subject to an existing or pending patent,
please email the editors.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=4 "Edit section: Copyright and License")\] Copyright and License

TBC


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=5 "Edit section: Inspiration and acknowledgements")\] Inspiration and acknowledgements


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=6 "Edit section: Introduction")\] Introduction
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=7 "Edit section: Conformance")\] Conformance
============================================================================================================================================================================================================

*Back to [HEAR
home](HEAR "http://www.xcri.org/HEAR")*

There are two classes of application that can conform to this
specification:

-   A *producer* is a class of application that produces HEAR XML
    documents
-   An *consumer* is a class of application that consumers HEAR XML
    documents

A product MAY belong to both classes.

A **strictly conforming instance** is a set of structured information
constituted only of elements and attributes defined by this
specification and *fully qualified refinements* of the elements defined
in this specification.

A **fully qualified refinement** is defined for the purpose of
conformance as an element that explicitly extends an element defined by
this specification. A fully qualified refinement must be capable of
being processed according to the semantics of the element it extends.

A **conforming instance** MAY contain additional elements and attributes
not defined by this specification.

A **conforming producer** MUST be capable of generating and sharing
*strictly conforming instances*.

A **conforming consumer** MUST be capable of processing *strictly
conforming instances*.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=8 "Edit section: HEAR Documents")\] HEAR Documents
==================================================================================================================================================================================================================

A producer MUST create HEAR documents that are valid XML documents.

A producer MUST create HEAR documents with one of the following elements
as its top-level element:

-   AchievementReport

A consumer MUST be able to process a valid HEAR XML document.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=9 "Edit section: The HEAR Template")\] The HEAR Template
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*This section is non-normative*

This specification covers the structure of the XML representation of the
HEAR data; it does not define the structure of the HEAR document per se.
The following information is provided to give context to the
specification of the data elements. Readers are asked to refer to the
[HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf"){.external
.text} for more details.

A HEAR must adhere to the prescribed template described in the [HEAR
Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf"){.external
.text}. The Guidance defines the sections of the HEAR and requires that
sections are numbered and follow the sequence and explanatory guidance
given in the Guidance Document.

The structure of the template for a HEAR is as follows:

-   Contextual information
-   Section 1. Information identifying the holder of the qualification
-   Section 2. Information identifying the qualification
-   Section 3. Information on the level of the qualification
-   Section 4. Information on the contents and results gained
-   Section 5. Information on the function of the qualification
-   Section 6. Additional information
-   Section 7. Certification of the HEAR
-   Section 8. Information on the national higher education system

On output for printing or for viewing electronically a HEAR should
contain section numbering and standard statements as described in the
[HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf"){.external
.text}.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=10 "Edit section: Contextual Information")\] Contextual Information

The [HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf"){.external
.text} gives details of statements that should be included in the HEAR
at specified points, for example a standard statement at the start of
the HEAR should be included in order to meet the requirements of the
European Diploma Supplement (DS). Information about these statements is
included in the Guidance sections of this specification.




Guidelines In the Contextual Information of the HEAR,
institutions SHOULD include the following statements:

*This Higher Education Achievement Report follows the model developed by
the European Commission, Council of Europe and UNESCO/CEPES for the
Diploma Supplement.*

*The purpose of the Supplement is to provide sufficient recognition of
qualifications (diplomas, degrees, certificates etc). It is designed to
provide a description of the nature, level, context and status of the
studies that were pursued and successfully completed by the individual
named on the original qualifications to which this Supplement is
appended. It should be free from any value judgements, equivalence
statements or suggestions about recognition. Information in all eight
sections should be provided. Where information is not provided, an
explanation should give the reason why.*




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=11 "Edit section: XML Document Structure")\] XML Document Structure
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This section describes diagrammatically the main information elements of
the HEAR XML document structure and their relationships. Definitions are
included under the Core Elements section.

The HEAR model includes information drawn from Student Records Systems,
Course Information Systems and supporting systems that will be created
and maintained by various different administrative processes and
academic practices within academic institutions. The model builds upon
information about learners, descriptions of programmes and other
learning opportunity structures, information about modules and other
educational components enrolled on by learners, assessment results and
other accredited achievements for each completed learning opportunity,
and information about the awarding and providing organisations
themselves.

[![Image:HEAROutlineInformationModel2011-02-17.png](http://www.xcri.org/wiki/images/4/42/HEAROutlineInformationModel2011-02-17.png){width="449"
height="485"}](./Image:HEAROutlineInformationModel2011-02-17.png "Image:HEAROutlineInformationModel2011-02-17.png")


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=12 "Edit section: Core elements")\] Core elements
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=13 "Edit section: the &lt;achievementReport&gt; element")\] the &lt;achievementReport&gt; element

*URI: \[to be completed\]*


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=14 "Edit section: Definition")\] Definition

The default root element for a HEAR.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=15 "Edit section: Core elements used within the achievementReport element")\] Core elements used within the achievementReport element

-   issuer (required, one only)
-   learner (required, one only)
-   awardedBy (required if different from issuer, one only)
-   qualification (required, one only)
-   provider (required, one or more)
-   course(s) (required, at least one)
-   assessment (required, at least one per presentation)
-   certificationOfTheHEAR (required, one only)
-   additionalInformation (optional, one only)




Guidelines These core elements are listed here, so that the major
components of a HEAR are clearly indicated. Some of these elements are
sub-elements of top level elements, as noted in this guidance.

**awardedBy:** A component of qualification (see
[XCRI-CAP](XCRI_CAP_1.2#the_.3Cqualification.3E_element "http://www.xcri.org/XCRI_CAP_1.2#the_.3Cqualification.3E_element"){.external
.text} specification).

**qualification:** A component of course (see
[XCRI-CAP](XCRI_CAP_1.2#the_.3Cqualification.3E_element "http://www.xcri.org/XCRI_CAP_1.2#the_.3Cqualification.3E_element"){.external
.text} specification).

**course:** A component of provider (see
[XCRI-CAP](XCRI_CAP_1.2#the_.3Ccourse.3E_element "http://www.xcri.org/XCRI_CAP_1.2#the_.3Ccourse.3E_element"){.external
.text} specification).

**assessment:** A component of presentation (see
[XCRI-CAP](XCRI_CAP_1.2#the_.3Cassessment.3E_element "http://www.xcri.org/XCRI_CAP_1.2#the_.3Cassessment.3E_element"){.external
.text} specification)

**Absence of provider:** Where a provider is not specified, consumers
SHOULD interpret this as meaning that the awardingBody is also the
provider.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=16 "Edit section: Specification of elements below the root element")\] Specification of elements below the root element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=17 "Edit section: the &lt;issuer&gt; element")\] the &lt;issuer&gt; element


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=18 "Edit section: Definition")\] Definition

The organisation that is responsible for producing the HEAR.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=19 "Edit section: Constraints")\] Constraints

A valid HEAR MUST contain one and only one issuer instance.

An issuer instance MUST contain the sub-elements defined below and no
other elements.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=20 "Edit section: Namespaces")\] Namespaces

Uses namespace dc: 

Uses namespace dcterms: 


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=21 "Edit section: Sub-elements used in the &lt;issuer&gt; element")\] Sub-elements used in the &lt;issuer&gt; element

-   identifier, dc\#identifier (required, multiple)
-   title, dc\#title (required, multiple)




Guidelines This element identifiers the issuing organisation,
which may be a different organisation from the provider or the awarding
body, for example a broker.

The &lt;issuer&gt; element MUST NOT contain any other elements. Further
elements describing the organisation(s) offering the course or awarding
the qualification MUST be contained in the provider element.




### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=22 "Edit section: the &lt;learner&gt; element")\] the &lt;learner&gt; element


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=23 "Edit section: Definition")\] Definition

Information identifying the holder of the qualification.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=24 "Edit section: Constraints")\] Constraints

A valid HEAR MUST contain one and only one learner instance.

A learner instance MUST contain the sub-elements defined below and no
other elements.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=25 "Edit section: Namespaces")\] Namespaces

Uses namespace elm: European Learner Mobility Achievement Information
(EuroLMAI).

Uses scop: the SEMIC-EU Core Person Specification (not yet published in
machine readable form), which is compatible with EuroLMAI.

Uses namespace dc: 

Uses namespace dcterms: 




Note The elm namespace relates to the European Learner Mobility
Achievement Information (EuroLMAI), for which see [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf"){.external
.text}. The elements in hear:learner are fully compatible and strictly
compliant with the elm:Learner profile, which specifies vCard properties
for these elements, including Identifier. These are UK-specific
implementations.




#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=26 "Edit section: Sub-elements used in the &lt;learner&gt; element")\] Sub-elements used in the &lt;learner&gt; element

-   **[identifier](Identifier_(HEAR) "Identifier (HEAR)")** (required,
    at least one), dc\#identifier. Unique identifier for the learner.
-   **identifierDescription** (optional), used to indicate the
    provenance of the identifier. Required text for the HUSID is as
    follows

"HUSID (HESA Unique Student Identifier) is the unique national
identifying number for students registered at a UK university. It is
defined by HESA, the UK's Higher Education Statistics Agency."

-   **familyName** (required, one element only), elm\#familyName. Full
    family or surname, as included on official documents, such as
    a passport.
-   **givenNames** (required, one element only), elm\#givenNames. All
    given or first names in the order specified by the learner, as
    included on official documents, such as a passport.
-   **fullName** (required, one only), elm\#fullName. The complete name
    of the learner; components should be those included on official
    documents, such as a passport.
-   **birthday** (required, one only), scop\#dateOfBirth. Date of birth
    of the learner.




Guidelines **dateOfBirth**: This value MUST be in ISO 8601 date
format, yyyy-mm-dd (example: "1985-05-16"). Note that this specification
does not prescribe the final form output for date (for example in a PDF
or paper document); implementers may wish to present the date in an
alternative format to end users. Additionally there may be applications,
such as outputs for employers, in which the inclusion of the learner's
dateOfBirth is not required.

**identifier**: Where the HESA Unique Student Identifier (HUSID) is
known, for example stored in the Student Record System, this value MUST
be the learner's HUSID. In other cases a different authoritative
identifier MUST be used. Alternatives recommended in this specification
include the Unique Learner Number (ULN) and the Scottish Candidate
Number (SCN). Namespace refinements for these identifiers are included
in the HEAR XML schema. For identifiers other than the HUSID, ULN or SCN
implementers MUST either extend the identifier element to include
another namespace or indicate the provenance of the identifier in the
comment attribute. An internal issuer or awardingBody identifier can
also be included.




### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=27 "Edit section: the &lt;qualification&gt; element")\] the &lt;qualification&gt; element


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=28 "Edit section: Definition")\] Definition

A status awarded to or conferred on a learner by an awarding body.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=29 "Edit section: Constraints")\] Constraints

A valid HEAR MUST contain one and only one qualification instance.
Instances of associate qualifications or other achievements not forming
part of the learner's academic achievements as a result of following the
indicated programme of study MAY be recorded in the Additional
Information element.

A qualification instance MUST contain the required sub-elements defined
below and MAY contain the optional sub-elements.

Producers MUST ensure that the qualification element of the HEAR relates
directly to the top level course element in a one-to-one relationship.
Each HEAR contains information about one and only one qualification,
achieved by a learner as a result of completion of one and only one top
level course.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=30 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Uses namespace elm: European Learner Mobility Achievement Information
(EuroLMAI), for which see [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf"){.external
.text}.

Uses namespace eds: [European Diploma
Supplement](http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp "http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp"){.external
.text}

Uses namespace dc: 

Uses namespace dcterms: 




Note XCRI refers to the [eXchanging Course Related Information -
Course Advertising Profile (XCRI-CAP v1.1) eProspectus
standard](http://www.xcri.org/wiki/ "http://www.xcri.org/wiki/"){.external
.text}.

There are currently no elements declared within the namespaces qm, elm,
eds.

\




#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=31 "Edit section: Sub-elements used in the &lt;qualification&gt; element")\] Sub-elements used in the &lt;qualification&gt; element

-   **identifier** (required, one only), dc\#identifier. Unique
    identifier for the qualification.
-   **title** (required, one only), dc\#title. Full official name of
    the award.
-   **regulations** (required, one only). This description SHOULD
    include reference to the regulations concerning degree-awarding
    powers in the UK. The recommended text is: "The power to award
    degrees is regulated by law in the UK."
-   **dualAward** (optional, zero or one). If the qualification is a
    dual award, for example between two UK institutions or between a UK
    and European institution, give details here.
-   **professionalStatus** (optional, zero or one). Details of any
    rights to practise or other professional standing accorded to
    holders of the award.
-   **furtherStudy** (optional, zero or one). Indicate if, within the
    country of origin, the qualification normally provides access
    (not admission) to further academic and/or professional study,
    especially leading to any specific qualifications, or levels
    of study.
-   **terminalAward** (optional, zero or one). Specify if the
    qualification is a terminal (end) award or part of a hierarchy
    of awards.
-   **subject** (required, at least one), dc\#subject. Main field(s) of
    study for the qualification.
-   **level** (required, one only). Numerical position of the
    qualification in the relevant national qualifications framework.
-   **qualificationHolderTitle** (optional, zero or
    one), eds\#qualificationHolderTitle. Nationally accepted title
    conferred by the award, for example *Bachelor of Science (Honours)*.
-   **issueDate** (required, one only), elm\#issueDate. Date on which
    the qualification was awarded.
-   **awardedBy** (required, one only). This element identifies and
    names the recognised organisation (Awarding Body) that confers the
    qualification upon the learner.




Guidelines **regulations:** The recommended text is: "The power
to award degrees is regulated by law in the UK."

**professionalStatus :** The institution MAY use a generic statement
from a professional body or one of its own devising (see HEAR Guidance
Document).

**furtherStudy:** Include the grades or standards normally necessary to
allow progression within the EHEA.

For example:

*Access to postgraduate study: Bologna FQ-EHEA 3rd cycle PhD or MD.*

*Access to postgraduate study: Bologna FQ-EHEA 2nd cycle degree or
diploma.*

**subject:** Put each main field of study in a separate element. On
output, the elements should be concatenated to form one string. There is
no nationally approved vocabulary for the subject in a HEAR. Use the
institution's own terminology. If subjects or fields of study are not
held in respect of qualifications, use the subjects in respect of the
top level course (programme) element.

**level:** The level element MUST contain both the numerical position of
the qualification in the relevant national qualifications framework and
a cross-reference to section 8: Information on the national Higher
Education System. See guidance on Education Levels and Frameworks at
[http://www.xcri.org/XCRI\_1.2\_Qualifications](XCRI_1.2_Qualifications "http://www.xcri.org/XCRI_1.2_Qualifications"){.external
.free}.

\




#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=32 "Edit section: Attributes")\] Attributes

-   idRef, attribute of awardedBy.




Guidelines **idRef:** The idRef attribute MUST identify the
Awarding Body specified in the awardedBy element. It MUST be A Uniform
Resource Identifier (URI) conforming to the URL scheme as specified by
[IETF RFC
3986](http://tools.ietf.org/html/rfc3986 "http://tools.ietf.org/html/rfc3986"){.external
.text}.




### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=33 "Edit section: the &lt;provider&gt; element")\] the &lt;provider&gt; element

*URI: *


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=34 "Edit section: Definition")\] Definition

An organisation that offers one or more courses.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=35 "Edit section: Constraints")\] Constraints

A valid HEAR MUST contain one or more provider instances.

A provider instance MUST contain the required sub-elements defined
below.

Producers MUST ensure that provider instances contain information only
about providers of courses undertaken by the learner in the context of
the qualification awarded.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=36 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: 




Note XCRI refers to the [eXchanging Course Related Information -
Course Advertising Profile (XCRI-CAP v1.1) eProspectus
standard](http://www.xcri.org/wiki/ "http://www.xcri.org/wiki/"){.external
.text}.




#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=37 "Edit section: Sub-elements used in the &lt;provider&gt; element")\] Sub-elements used in the &lt;provider&gt; element

-   **identifier** (required, at least one), dc\#identifier. Unique
    identifier for the provider.
-   **title** (required, at least one), dc\#title. Full official name of
    the provider.
-   **providerStatus** (required, one only). Describes the legal status
    of the provider, for example as either a 'recognised body' or a
    'listed body'.
-   **course** (required, at least one). Details of the course(s)
    through which the learner achieved the award of the qualification.

Examples:

         http://www.universityoftest.ac.uk/
         12345678
         1234


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=38 "Edit section: Attributes")\] Attributes

-   idRef, attribute of provider.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=39 "Edit section: the &lt;course&gt; element")\] the &lt;course&gt; element

*URI: *


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=40 "Edit section: Definition")\] Definition

A course provides details of a learning opportunity offered by a
learning provider.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=41 "Edit section: Constraints")\] Constraints

A valid HEAR MUST contain one and only one top level course element.
Further course elements MAY be included to reflect the institution's
programme component structures.

The top level course element SHOULD define the Programme Level learning
opportunity undertaken by the learner.

Producers MUST ensure that the top level course element of the HEAR
relates directly to the qualification element in a one-to-one
relationship. Each HEAR contains information about one and only one
qualification, achieved by a learner as a result of completion of one
and only one top level course.

Course elements at levels lower than programme level SHOULD be related
to the top level course element using the isPartOf element, either
directly through inclusion of the identifier of the top level course, or
indirectly through inclusion of the identifier of another course
element.

Example

        
            
            1234
            Information and Communications Undergraduate Programme
        
        
            
            1234-01
            Digital Media and Communications - Stage 1
            1234
        
        
            
            M223
            Information Literacies for the Digital Age
            1234-01
        


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=42 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri:  and
xcriTerms: 

Uses namespace credit: .

Uses namespace dc: 


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=43 "Edit section: Sub-elements used in the &lt;course&gt; element at Programme Level")\] Sub-elements used in the &lt;course&gt; element at Programme Level

-   **identifier** (required, one only), dc\#identifier.



-   **title** (required, one only), dc\#title. Full official name of
    the programme.



-   **type** (required, one only), dc\#type
    (mlo:LearningOpportunitySpecification, type). Indicates that this is
    a programme (cf. use in other course elements).



-   **aim** (required, one only), mlo:objective. Describes the aim(s) of
    the programme.



-   **learningOutcome** (required, one or more). Describes the overall
    learning outcome(s) of the programme.



-   **specialFeature** (optional, zero, one or many). Any particular
    features that help define the programme that are not
    covered elsewhere.



-   **credit** (optional, multiple), cm\#credit. Details of the credit
    values and levels earned on successful completion of the programme.



-   **qualification** (required, one only). Details of the
    qualification achieved.



-   **presentation** (required, one only). Details of the instance or
    version of the course enrolled on.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=44 "Edit section: Sub-elements used in the &lt;course&gt; element at other levels")\] Sub-elements used in the &lt;course&gt; element at other levels 

-   **identifier** (required, one only), dc\#identifier.



-   **title** (required, one only), dc\#title. Full official name of the
    module or other component.



-   **type** (required, one only), mlo\#type
    (mlo:LearningOpportunitySpecification, type). Indicates the type of
    component, such as a module-level component or a grouping component
    such as semester, programme year, level or subject of a programme.



-   **credit** (optional, one only), cm\#credit. Details of the credit
    values and levels earned on successful completion of the modules
    or components.



-   **isPartOf** (required, one only). Indicates the parent
    course element.



-   **presentation** (required, one only). Details of the instance or
    version of the course enrolled on.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=45 "Edit section: Sub-elements used in the &lt;presentation&gt; element at Programme Level")\] Sub-elements used in the &lt;presentation&gt; element at Programme Level

-   **identifier** (required, one only), dc\#identifier.



-   **start** (required, one only), mlo\#start. The date at which the
    programme begins. See \[EN 15982\].



-   **end** (required, one only), xcri\#end. The date at which the
    programme ends.



-   **accessRequirements** (required, one only). Details of the nature
    and length of qualifications or periods of study required before
    starting the programme.



-   **minimumStandards** (required, one only). Details of the
    regulations covering the minimum standards required to secure the
    qualification; therefore applies to the Programme only.



-   **duration** (required, one only), xcri\#duration. The length of
    the programme.



-   **studyMode** (required, one only), xcri\#engagement (studyMode). A
    general expression of the overall amount of the student's time that
    is devoted to the learning opportunity, as defined by the provider.



-   **languageOfInstruction** (required, at least
    one), xcri\#languageOfInstruction. A language in which the
    presentation was taught.



-   **languageOfAssessment** (required, at least
    one), xcri\#languageOfAssessment. A language in which the
    presentation was assessed.



-   assessment (optional). Information about the assessment of
    the presentation.




Guidelines **identifier:** Where presentation does not have its
own identifier, producers SHOULD use and repeat the host course
identifier.

**title:** Producers SHOULD draw the title from the course element, not
the presentation element.

**start**: This is a *temporal element*. For more information on the
syntax of this element, see the section on temporal elements.

**end:** This is a *temporal element*. For more information on the
syntax of this element, see the section on temporal elements.

**accessRequirements**: Producers MAY implement this content using
'boilerplate' text and a hyperlink to specific documents held elsewhere;
in this case, implementers SHOULD have regard to the persistence of the
hyperlinks and the associated content, for example: "Detailed
information regarding admission to the programme is available in the
University‚Äôs on-line Prospectus at:
www.easthampton.ac.uk/admissions/ugprospectus/06." See Guidance
Document, section 3.3.

**minimumStandards**: See Guidance Document, section 4.2.

**description**: Use the recommended encoding scheme to provide detailed
information about the qualification in different information categories.
See the encoding scheme for more details.

**duration:** The content of this element MUST be human readable text of
the form 'value' followed by 'unit of time', for example 'Three years'.
The duration SHOULD be expressed in years, unless the course is shorter
than two years, in which case an expression in months or weeks is
acceptable. Producers MAY include a machine-readable attribute
'interval' that follows the ISO 8601 standard.

Example

        Three years

**studyMode:** See
[http://www.xcri.org/XCRI\_Terms\_1.2\#studyMode](XCRI_Terms_1.2#studyMode "http://www.xcri.org/XCRI_Terms_1.2#studyMode"){.external
.free}

**languageOfInstruction:** The content of this element MUST be a valid
[BCP-47 language
tag](http://tools.ietf.org/rfc/bcp/bcp47.txt "http://tools.ietf.org/rfc/bcp/bcp47.txt"){.external
.text}. Default value: EN.

**languageOfAssessment:** The content of this element MUST be a valid
[BCP-47 language
tag](http://tools.ietf.org/rfc/bcp/bcp47.txt "http://tools.ietf.org/rfc/bcp/bcp47.txt"){.external
.text}. Default value: EN.

**assessment :** In an exit HEAR this element MUST be present for each
presentation, otherwise it is optional.

**Output of languageOfInstruction and languageOfAssessment:** Consumers
SHOULD present final form output of these elements as human readable
text.

**Absence of languageOfInstruction and languageOfAssessment:** Where
these elements are missing, consumers SHOULD interpret this as meaning
that the language of instruction and assessment was English (en-GB).

\




#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=46 "Edit section: Sub-elements used in the &lt;presentation&gt; element at other levels")\]  Sub-elements used in the &lt;presentation&gt; element at other levels

-   **identifier** (required, one only), dc\#identifier.



-   **assessment** (optional). Information about the assessment of
    the presentation.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=47 "Edit section: the &lt;assessment&gt; element")\] the &lt;assessment&gt; element


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=48 "Edit section: Definition")\] Definition

The details of the way in which the learner's performance in the
presentation was judged.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=49 "Edit section: Constraints")\] Constraints

A valid exit HEAR must contain an &lt;assessment&gt; element for the
programme and for each module or course component that is part of the
programme or that is an additional academic credit-bearing student
achievement detailed in the HEAR.

Each &lt;assessment&gt; element must relate only to the learner and the
specific version of the presentation on which the learner was assessed.

NOTE: decision on retakes and numbers of attempts is still outstanding -
[Alan Paull](Alan_Paull "Alan Paull")


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=50 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Uses namespace elm: European Learner Mobility Achievement Information
(EuroLMAI), for which see [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf"){.external
.text}.

Uses namespace eds: [European Diploma
Supplement](http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp "http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp"){.external
.text}




Note XCRI refers to the [eXchanging Course Related Information -
Course Advertising Profile (XCRI-CAP v1.1) eProspectus
standard](http://www.xcri.org/wiki/ "http://www.xcri.org/wiki/"){.external
.text}.




#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=51 "Edit section: Sub-elements used in the &lt;assessment&gt; element")\] Sub-elements used in the &lt;assessment&gt; element

-   **identifier** (required, one only), dc:identifier. Unique
    identifier for the &lt;assessment&gt; element.



-   **assessmentType** (required, one only). Description of the style of
    the assessment.



-   **assessmentWeight** (optional, zero or one). Weighting of the
    assessment result as a proportion of the overall assessment for
    the presentation.



-   **attempts** (optional, zero or one). Number of times the learner
    has made at the assessment.



-   **result** (optional, multiple), elm\#result. The actual outcome of
    a presentation for a learner as stated by a provider or issuer.



-   **gradingScheme** (required, one or more). Information about the
    grading scheme used for the assessment of a presentation.




Guidelines **assessmentType:** It is recommended that producers
use an encoding scheme or controlled vocabulary for this item.

**result:** Required in an exit HEAR, one only per assessment.




#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=52 "Edit section: Attributes")\] Attributes

-   resultType: used with **result**. Indicates whether the result is a
    mark, grade or similar. It is recommended that producers use an
    encoding scheme or controlled vocabulary for this item.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=53 "Edit section: the &lt;additionalInformation&gt; element")\] the &lt;additionalInformation&gt; element

*URI: This will relate to elm:additionalInformation; URI not yet
available.*


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=54 "Edit section: Definition")\] Definition

Details of the richer picture of verified student achievement, including
additional awards (with or without academic credit), additional
recognised activities, and university, professional and departmental
prizes.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=55 "Edit section: Constraints")\] Constraints

A valid HEAR MUST contain one and only one additionalInformation
element. Guidance on its contents is given in the 'Guidance to Inform
Institutional Implementation'


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=56 "Edit section: Namespaces")\] Namespaces

Uses namespace elm: European Learner Mobility Achievement Information
(EuroLMAI), for which see CWA 16132.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=57 "Edit section: Sub-elements used in the &lt;additionalInformation&gt; element")\] Sub-elements used in the &lt;additionalInformation&gt; element

-   **prizes** (optional, zero, one or many). Information about
    university, professional and departmental prizes awarded to
    the learner.



-   **additionalAwards** (optional, zero, one or many). Information
    about academic (credit-based) and non-academic awards made to
    the learner.



-   **recognisedActivities** (optional, zero, one or many). Information
    about other recognised non-credit-bearing activities undertaken by
    the learner.



-   **informationSources** (optional, zero, one or many). Further
    information sources and references where more details on the
    qualification could be sought.



-   **ePortfolioUrl** (optional, zero or one), xcri\#url. A hypertext
    link to the learner's ePortfolio.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=58 "Edit section: the &lt;certificationOftheHEAR&gt; element")\] the &lt;certificationOftheHEAR&gt; element


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=59 "Edit section: Definition")\] Definition

Provides evidence that the HEAR is a genuine document produced by the
authorised organisation.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=60 "Edit section: Constraints")\] Constraints

A valid HEAR must contain one and only one
&lt;certificationOftheHEAR&gt; element.


#### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=61 "Edit section: Sub-elements used in the &lt;certificationOftheHEAR&gt; element")\] Sub-elements used in the &lt;certificationOftheHEAR&gt; element

-   **identifier** (required, one only), dc\#identifier. Uniquely
    identifies this version of the HEAR data set for this learner.



-   **date** (required, one only). Date and time of the production of
    this HEAR.



-   **fullName** (required, one only). Full name of the official
    certifying the HEAR.



-   **capacity** (required, one only). The official post of the
    certifying individual.



-   **signature** (required, one only).


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit&section=62 "Edit section: XML Schema and Instance")\] XML Schema and Instance
=====================================================================================================================================================================================================================================

*This section is not normative*

A draft XML Schema is available at
.

A draft XML instance file is available at
.



Retrieved from
"[http://www.xcri.org/HEAR\_1.0a\_Specification](HEAR_1.0a_Specification)"

















##### Views



-   

    

    [Article](HEAR_1.0a_Specification)
-   

    

    [Discussion](http://www.xcri.org/wiki/index.php?title=Talk:HEAR_1.0a_Specification&action=edit)
-   

    

    [Edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=edit)
-   

    

    [History](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&action=history)







##### Personal tools



-   

    

    [Log in / create
    account](http://www.xcri.org/wiki/index.php?title=Special:Userlogin&returnto=HEAR_1.0a_Specification)











[](XCRI_Wiki "XCRI Wiki")





##### Navigation



-   

    

    [XCRI Wiki](XCRI_Wiki)
-   

    

    [XCRI website](http://www.xcri.org/)
-   

    

    [Current events](Current_events)
-   

    

    [Recent changes](./Special:Recentchanges)
-   

    

    [Help](./Help:Contents)







##### Search





 









##### Toolbox



-   

    

    [What links here](./Special:Whatlinkshere/HEAR_1.0a_Specification)
-   

    

    [Related
    changes](./Special:Recentchangeslinked/HEAR_1.0a_Specification)
-   

    

    [Upload file](./Special:Upload)
-   

    

    [Special pages](./Special:Specialpages)
-   

    

    [Printable
    version](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&printable=yes)
-   

    

    [Permanent
    link](http://www.xcri.org/wiki/index.php?title=HEAR_1.0a_Specification&oldid=3142)















[![Powered by
MediaWiki](http://www.xcri.org/wiki/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 18:16, 7 March 2011.
-   

    

    This page has been accessed 13,577 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](./Xcri:Privacy_policy "Xcri:Privacy policy")
-   

    

    [About Xcri](./Xcri:About "Xcri:About")
-   

    

    [Disclaimers](./Xcri:General_disclaimer "Xcri:General disclaimer")




