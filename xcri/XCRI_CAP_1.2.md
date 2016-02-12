---
layout: post
---

XCRI CAP 1.2
============


### Status

This is the final version of XCRI CAP 1.2. This specification supersedes
XCRI CAP 1.1.

Please provide bug reports and issues on the [XCRI
Issue Tracker](https://github.com/xcri/xcri.github.io/issues "https://github.com/xcri/xcri.github.io/issues").

This specification has been reviewed by members of the XCRI community
and has been endorsed by the XCRI Project Team. It is a stable document
and may be used as reference material or cited from another document. If
there are any significant issues with this document other than minor
typographical or grammatical corrections, it will not be modified, but
instead a new version issued with a new version number.


### Patents

This specification is subject to a royalty free patent policy.

There are no known patents covering any of this work. If you think that
part of this work may be subject to an existing or pending patent,
please email the editors.


### Copyright and License

This work is (c) 2005-2011 the University of Bolton, and licensed under
a Creative Commons Attribution 3.0 Licence. All contributions MUST be
licensed under the same conditions. This is to ensure that the
specification work can be transferred to an appropriate standardisation
body.


### Inspiration and acknowledgements

The development of this specification has benefited from close
co-operation with the CEN Workshop on Learning Technologies and the Rome
Student Systems and Standards Group (RS3G). We would also like to thank
the many UK institutions and lifelong learning networks that have
contributed to its development through their work on implementation. We
also thank JISC for supporting the development of this specification. In
particular we would like to acknowledge the contributions of Simon
Grant, Tavis Reddick, Ben Ryan, Stuart Feltham, Liam Green-Hughes,
Martin Edney, Richard Hyett and all the others who have contributed to
the specification through the XCRI community.


Introduction
---------------------------------------------

The XCRI Course Advertising Profile (XCRI-CAP) is a specification to
enable the interoperability of descriptions of courses, or any other
kind of learning opportunity, between the course provider and any number
of Aggregators and brokers, by supplying an XML description.

XCRI-CAP 1.2 provides an XML format based on the CEN Metadata for
Learning Opportunities standard (see \[EN 15982\]), which means
documents that conform to this specification have the same underlying
semantics as those produced to other bindings of the same standard.

An XCRI-CAP document typically consists of a top-level &lt;catalog&gt;
element, encapsulating a single &lt;provider&gt;, and a collection of
&lt;course&gt; descriptions for the courses offered by the provider.
Each course has various descriptive information available such as
syllabus, the qualification you can obtain, career options and so on.
The course is also divided into any number of &lt;presentation&gt;s,
which are the 'instances' or 'offerings' of the course that a
prospective student will apply for, and which have specific start and
end dates, locations and so on, and can vary in aspects such as the
location and mode of study (e.g. a full-time and part-time presentation,
with different duration and start date).

The following diagram illustrates the main elements of the
specification.

[![Image:Xcri 1 2 uml.png](../images/e/e0/Xcri_1_2_uml.png)](Image%253AXcri_1_2_uml.png "Image:Xcri 1 2 uml.png")


Normative References
=====================================================

\[EN 15982\] EN 15982: Metadata For Learning Opportunities (Advertising)

\[ISO 15836\] ISO 15836: Dublin Core Element Set

\[ISO 8601\] ISO 8601:Data elements and interchange formats ‚Äî
Information interchange ‚Äî Representation of dates and times

\[W3C DTF\] W3C Date and Time Formats. See


\[W3C XML Schema\] W3C XML Schema. See 

\[DCTERMS\] Dublin Core Metadata Terms. See


\[CWA 16077\] CWA 16077: Educational Credit Information Model

{BCP-47\] IETF BCP47: Tags for Identifying Languages


Conformance
============================================

There are two classes of application that can conform to this
specification:

-   A *Producer* is a class of application that produces XCRI-CAP
    documents
-   An *Aggregator* is a class of application that aggregates XCRI-CAP
    documents

A product MAY belong to both classes.

A **strictly conforming instance** is a set of structured information
constituted only of elements and attributes defined by this standard and
*fully qualified refinements* of the elements defined in this standard.

A **fully qualified refinement** is defined for the purpose of
conformance as an element that explicitly extends an element defined by
this standard. A fully qualified refinement MUST be capable of being
processed according to the semantics of the element it extends.

A **conforming instance** MAY contain additional elements and attributes
not defined by this standard.

A **conforming Producer** MUST be capable of generating and sharing
*strictly conforming instances*.

A **conforming Aggregator** MUST be capable of processing *strictly
conforming instances*.


XCRI Documents
===============================================

A Producer MUST create XCRI-CAP documents that are valid XML documents.

A Producer MUST create XCRI-CAP documents with one of the following
elements as its top-level element:

-   catalog
-   provider
-   course

An Aggregator MUST be able to process a valid XCRI-CAP document.




GuidelinesA Producer SHOULD use the catalog element as the
top-level element for general purpose use. The specification allows both
provider and course as alternative top-level elements to enable
REST-style operations to be supported.




Namespace
------------------------------------------

XCRI-CAP elements and attributes are identified using the namespace:


This specification also includes elements defined in other standards,
specifically \[EN 15982\], \[ISO 15836\] and \[DCTERMS\].

Elements defined by \[EN 15982\] MUST use the Namespace


Elements defined by \[ISO 15836\] MUST use the Namespace


Elements defined by \[DCTERMS\] MUST use the Namespace





Note Information on namespaces can also be found at





Core Elements
----------------------------------------------


### the &lt;catalog&gt; element

*URI: *

The default root element for an XCRI-CAP feed




NoteThe catalog element does not imply a relationship between the
XCRI-CAP document and a course catalog. A catalog does not necessarily
relate to a concept of a catalog in an originating or consuming system,
but rather provides the context for the content of the XCRI-CAP
document.



Attributes:

-   @generated (required) The date and time at which the catalog was
    generated, in \[ISO 8601\] format.

Elements:

-   all *Common Elements*
-   [provider](XCRI_CAP_1.2.html#the_.3Cprovider.3E_element)
    (optional, multiple) The provider whose *courses* are included in
    the *catalog*.

Producers MUST include a @generated attribute, and the value of the
attribute MUST be a valid date/time according to \[ISO 8601\].




Guidelines

**generated**: Producers SHOULD use both date and time in the @generated
attribute. Example: '2010-08-02T06:14:37Z'.

**generated attribute is missing**: If a &lt;catalog&gt; does not
contain an @generated attribute, then an Aggregator MAY process the
document treating the document as if it was generated at the time the
catalog was obtained by the Aggregator.

**generated attribute is invalid**: if the value of the @generated
attribute is not a valid date/time according to ISO 8601, then an
Aggregator SHOULD treat the XCRI document as being in error.




### the &lt;provider&gt; element

*URI: *

Providers are organisations that offer one or more courses.




Note Provider is equivalent to Learning Opportunity Provider in
\[EN 15982\].

A provider MAY be an organisational component of another provider, for
example a Faculty of a University.



Elements:

-   all *Common Elements*
-   [location](XCRI_CAP_1.2.html#the_.3Clocation.3E_element) (optional)
-   [course](XCRI_CAP_1.2.html#the_.3Ccourse.3E_element)
    (optional, multiple)




Guidelines

**Identifiers**: Producers SHOULD create Provider elements with a
default unique identifier formatted as a URL (e.g.
""). Producers MAY include additional
identifiers in other formats, but these SHOULD be qualified using
xsi:type to a specific identifier namespace. An example would include
the UK provider reference number (UKPRN) within the UKRLP:UKPRN
namespace. See the identifier element definition for more details.

**Title**: Producers SHOULD include at least one title element for a
provider, which SHOULD be the trading name of the organisation

**Type**: Where a Producer uses the Type element for a provider, this
SHOULD use a sector-specific controlled list of terms for this element.
These SHOULD be qualified using xsi:type to a specific vocabulary
namespace.

**Url**: Producers SHOULD include one Url element for each provider,
which SHOULD include a URL for its homepage, or its applications
microsite, in addition to its primary domain identifier (see above).

**Course**: In almost all cases Producers SHOULD include at least one
course for a provider. The capability for supporting zero courses is
offered for cases where XCRI CAP is used to format course search
results.




### the &lt;course&gt; element

*URI: *

A course provides details of a learning opportunity offered by a
learning [provider](XCRI_CAP_1.2.html#the_provider_element).




Note Course is equivalent to Learning Opportunity Specification
in [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf"){.external
.text}.



Elements:

-   all *Common Elements*
-   all *Common Descriptive Elements*
-   [level](XCRI_CAP_1.2.html#the_.3Clevel.3E_element) (optional)
-   [qualification](XCRI_CAP_1.2.html#the_.3Cqualification.3E_element)
    (optional, multiple)
-   [presentation](XCRI_CAP_1.2.html#the_.3Cpresentation.3E_element)
    (optional, multiple)
-   [credit](XCRI_CAP_1.2.html#the_.3Ccredit.3E_element)
    (optional, multiple)




Guidelines

**Identifier**: A Course SHOULD have a unique identifier formatted as a
URI (e.g. ""). Additional identifiers
in other formats may be used, but SHOULD be qualified using xsi:type to
a specific identifier namespace. See the guidance on the identifier
element for more details.

**Title**: Producers SHOULD include at least one title element for each
course.

**Subject**: Producer SHOULD include at least one subject element for
each course. See the guidance on the subject element for more
information.

**Level**: This is included for compatibility with \[EN 15982\].
Producers SHOULD NOT use this element, and Aggregators SHOULD make use
of the Qualification and Credit elements to assist users to discover
courses by level.

**Credit**: Producers SHOULD use separate credit elements for describing
the credits available under each scheme, for example CATS or ECTS.

**Absence of Image**: Where a course does not contain an image, but its
containing provider does, an Aggregator MAY use the image of the
provider when displaying the course.




### the &lt;presentation&gt; element

*URI: *

A presentation is a particular instance of the course offered at a
specific time and place or through specified media. It is the entity to
which learners apply. Alternative names for this type of structure
include *course offering* and *course instance*.




Note Presentation is equivalent to Learning Opportunity Instance
in \[EN 15982\].



Elements:

-   all *Common Elements*
-   all *Common Descriptive Elements*
-   [start](XCRI_CAP_1.2.html#the_.3Cstart.3E_element)(optional)
-   [end](XCRI_CAP_1.2.html#the_.3Cend.3E_element) (optional)
-   [duration](XCRI_CAP_1.2.html#the_.3Cduration.3E_element) (optional)
-   [applyFrom](XCRI_CAP_1.2.html#the_.3CapplyFrom.3E_element) (optional)
-   [applyUntil](XCRI_CAP_1.2.html#the_.3CapplyUntil.3E_element) (optional)
-   [applyTo](XCRI_CAP_1.2.html#the_.3CapplyTo.3E_element) (optional)
-   [engagement](XCRI_CAP_1.2.html#the_.3Cengagement.3E_element)
    (optional, multiple)
-   [studymode](XCRI_CAP_1.2.html#the_.3Cstudymode.3E_element) (optional)
-   [attendancemode](XCRI_CAP_1.2.html#the_.3Cattendancemode.3E_element) (optional)
-   [attendancepattern](XCRI_CAP_1.2.html#the_.3Cattendancepattern.3E_element) (optional)
-   [languageOfInstruction](XCRI_CAP_1.2.html#the_.3ClanguageOfInstruction.3E_element)
    (optional, multiple)
-   [languageOfAssessment](XCRI_CAP_1.2.html#the_.3ClanguageOfAssessment.3E_element)
    (optional, multiple)
-   [places](XCRI_CAP_1.2.html#the_.3Cplaces.3E_element) (optional)
-   [cost](XCRI_CAP_1.2.html#the_.3Ccost.3E_element) (optional)
-   [age](XCRI_CAP_1.2.html#the_.3Cage.3E_element) (optional)
-   [venue](XCRI_CAP_1.2.html#the_.3Cvenue.3E_element)
    (optional, multiple)




Guidelines

**Absence of Venue:** Where a venue is not specified, Aggregators SHOULD
interpret this as meaning that the provider address is the venue, and
use its contact information for this purpose.

**Determining uniqueness:** Where a presentation does not contain an
identifier, Aggregators may need to [construct presentation
identifiers](Construct_presentation_identifiers.html "Construct presentation identifiers").
It is recommended that presentations use a URL-formatted identifier
where possible, following the scheme for the provider and course. E.g.
""

**Absence of study mode and attendance:** Aggregators SHOULD assume that
the default value for studyMode is "Full Time", the default for
attendanceMode is "Campus", and the default for attendancePattern is
"Daytime"

**Start dates** : A Producer SHOULD include a start element even if
there is no specific start date as this can still be used to describe
the start details- see the section on Temporal Elements.

**Duration**: A Producer SHOULD include a duration element or start and
end dates, or both.

**Absence of Image**: Where a presentation does not contain an image,
but its containing course does, an Aggregator MAY use the image of the
course when displaying the presentation.

**Absence of Title**: Where a presentation does not contain a title, but
its containing course does, an Aggregator MAY use the title of the
course when displaying the presentation.

**Absence of Description**: Where a presentation does not contain a
description, but its containing course does, an Aggregator MAY use the
description of the course when displaying the presentation.

\




Common Elements
------------------------------------------------

Each of the core elements of XCRI use the following set of common
elements:

-   hasPart (optional, multiple)
-   isPartOf (optional, multiple)
-   [contributor](XCRI_CAP_1.2.html#the_.3Ccontributor.3E_element)
    (optional, multiple)
-   date (optional, multiple)
-   [description](XCRI_CAP_1.2.html#the_.3Cdescription.3E_element)
    (optional, multiple, inheritable)
-   [identifier](XCRI_CAP_1.2.html#the_.3Cidentifier.3E_element)
    (optional, multiple)
-   [image](XCRI_CAP_1.2.html#the_.3Cimage.3E_element)
    (optional, inheritable)
-   [subject](XCRI_CAP_1.2.html#the_.3Csubject.3E_element) (optional,
    multiple, inheritable)
-   [title](XCRI_CAP_1.2.html#the_.3Ctitle.3E_element)
    (optional, multiple)
-   [type](XCRI_CAP_1.2.html#the_.3Ctype.3E_element)
    (optional, multiple)
-   [url](XCRI_CAP_1.2.html#the_.3Curl.3E_element) (optional)

An Aggregator MUST be able to process the description, identifier,
image, subject, title and url elements.




Guidelines See Core Elements for guidelines on usage in each
specific context.

**date**: Producers SHOULD NOT use the &lt;date&gt; element, but instead
where possible use the &lt;start&gt; element and the temporal elements
defined in this document: &lt;end&gt;, &lt;applyFrom&gt;, and
&lt;applyUntil&gt;

**hasPart/isPartOf**: these elements are included for compatibility with
the \[EN 15982\] standard. Producers SHOULD NOT use these elements. For
more information on these elements see \[EN 15982\]

**type**: Producers MAY use this element to classify providers, courses
and presentations; additional guidance may be found under the sections
on the Provider, Course and Presentation elements.




### the &lt;contributor&gt; element

*URI:*

An entity responsible for making contributions to the resource. See \[EN
15982\] and \[ISO 15836\].

This element MUST use the Dublin Core Namespace:





Guidelines **Refinements** Producers SHOULD use refinements of
this element, for example for "presenter" or "lecturer" or other
contributor types relevant to the type of course or presentation.

**Contact Information** Producers SHOULD NOT use this element for
general contact information; Producers SHOULD use the &lt;location&gt;
element for this purpose.




### the &lt;description&gt; element

*URI:*

An account of the resource. See \[EN 15982\] and \[ISO 15836\].

This is a *Descriptive Text Element*. For more information on the syntax
of this element, see the section on Descriptive Text Element elements.

This element MUST use the Dublin Core Namespace:



### the &lt;identifier&gt; element

*URI:*

An unambiguous reference to the resource within a given context. See
\[EN 15982\] and \[ISO 15836\].

Structures MUST NOT contain more than one identifier without an
explicitly-defined encoding scheme, and this MUST be A Uniform Resource
Identifier (URI) conforming to the URL scheme as specified by [IETF RFC
3986](http://tools.ietf.org/html/rfc3986 "http://tools.ietf.org/html/rfc3986"){.external
.text}.

Example:

     http://www.bolton.ac.uk
     23424341414

This element MUST use the Dublin Core Namespace:





Guidelines

**Resolvable URLs** Producers SHOULD use URLs for identifiers that also
resolve to human-readable content.

**Third-party identifiers:** Producers SHOULD use *identifier* with an
encoding scheme to represent third-party identifiers; Producers SHOULD
use dc:subject to represent third-party codes that refer to multiple
objects (e.g. subject classification codes, provider type codes)




### the &lt;title&gt; element

*URI:*

The title of the resource. See \[EN 15982\] and \[ISO 15836\].

Examples:

    Physics For Dogs

    The Stars Of The Night Sky
    Las Estrellas del Cielo de la Noche

This element MUST use the Dublin Core Namespace:





Guidelines

**Localisation:** Producers SHOULD use the xml:lang attribute to provide
alternative language versions of a title; there SHOULD NOT be more than
one occurrence of title per language tag.

**Qualifications:** In the qualification element, Producers SHOULD use
title for the name of the qualification, preferably as given by its
Awarding Body.




### the &lt;subject&gt; element

*URI:*

The topic of the resource. See \[EN 15982\] and \[ISO 15836\].

Attributes:

@identifier (optional)

Each subject element MUST contain one and only one keyword, phrase, or
classification.




NoteFor example, do not use multiple keywords separated by spaces
or other conventions; use separate subject elements instead.



If this element does not contain any text content, Aggregators MUST
treat this element as in error, and ignore this element.

Examples:

    Political Theory 
    mental health
    addiction nursing
    development
    bildung

This element MUST use the Dublin Core Namespace:





Guidelines **Identifier:**: Where a subject has both a
human-readable label and an identifier, Producers SHOULD use an
@identifier attribute of the subject element for the identifier, and the
text content of the subject element for the label.

**Localisation:** Producers SHOULD use an xml:lang attribute to provide
alternative language versions of a subject element.

**Vocabularies:** Producers SHOULD use vocabulary encoding schemes to
include classification terms using the subject element.

**Inheritance:** This element and any refinements of it is inheritable.
See the section on inheritance for more guidance.




### the &lt;type&gt; element

*URI:*

The type of resource. See \[EN 15982\] and \[ISO 15836\].




Guidelines Producers MAY use this element to classify providers,
courses, qualifications and presentations; additional guidance may be
found under the sections on the Provider, Course, Qualification and
Presentation elements.




### the &lt;url&gt; element

*URI:*

A link to a web resource that provides an alternate representation of
the resource. See \[EN 15982\].

Example:

     
       http://www.example.org/courses/1
       ...
       http://www.example.org/prospectus.jsp?course=1
       ...
     

This element MUST use the \[EN 15982\] namespace:





Guidelines

**When to use Url versus Identifier:** Producers SHOULD Use identifier
with the default encoding type in addition to the url element wherever
possible. Also, Producers SHOULD use this element when the resource
cannot be given a dereferencable URL as an identifier (for example, a
course description generated from within a CMS, or where the identifier
is a URN or HDL) to indicate a place on the provider's website where
further information can be obtained, even if it is just general
information about the department offering the course.




### the &lt;image&gt; element

*URI: *

An image element is used to enable images to be displayed by an
Aggregator.

A Producer MUST NOT create image elements that contain any text content
or child elements.

An Aggregator MUST ignore any text content or child elements of the
image element.

Attributes:

-   @**src** (required) A Uniform Resource Identifier (URI) conforming
    to the URL scheme as specified by [IETF RFC
    3986](http://tools.ietf.org/html/rfc3986 "http://tools.ietf.org/html/rfc3986"). This is used for the image location.
-   @**title** (optional) a title for the image, such as could be used
    as a caption.
-   @**alt** (optional) alternative text to display if the image cannot
    be rendered.

Example:

      




Guidelines

**Image size:** An Aggregator MAY choose to re-scale images.

**Image format:** A Producer SHOULD offer images in standard formats,
such as PNG and JPEG.

**Accessibility:** While @alt is optional, following the structure of
XHTML, a Producer SHOULD provide meaningful alternative text.

**Inheritance:** This element and any refinements of it is inheritable.
See the section on inheritance for more guidance.




Common Descriptive Elements
------------------------------------------------------------

-   abstract (optional, multiple, inheritable)
-   applicationProcedure (optional, multiple, inheritable)
-   assessment (optional, multiple, inheritable)
-   learningOutcome (optional, multiple, inheritable)
-   objective (optional, multiple, inheritable)
-   prerequisite (optional, multiple, inheritable)
-   regulations (optional, multiple, inheritable)




Guidelines The &lt;course&gt; and &lt;presentation&gt; elements
MAY use any of the Common Descriptive Elements. See the course and
presentation element definitions for guidelines on usage in each
specific context.




### the &lt;abstract&gt; element

*URI: *

A short one-sentence description for use in a course list.

This is a *Descriptive Text Element*. For more information on the syntax
of this element, see the section on Descriptive Text Element elements.

Producers MUST NOT create a value of this element that exceeds 140
characters.




Guidelines **Length**: A Aggregator MAY choose to truncate the
value of this element if it exceeds 140 characters.




### the &lt;applicationProcedure&gt; element

*URI: *

The procedure for applying to a course of study.

This is a *Descriptive Text Element*. For more information on the syntax
of this element, see the section on Descriptive Text Element elements.


### the &lt;assessment&gt; element

*URI: *

Assessment strategy: a description of the broad approach to assessment
used in the Learning Opportunity.




Note Examples include types of assessments and evaluations of
learning and competency development such as exams, mostly by coursework,
etc.



This is a *Descriptive Text Element*. For more information on the syntax
of this element, see the section on Descriptive Text Element elements.

This element MUST use the \[EN 15982\] namespace:



### the &lt;learningOutcome&gt; element

*URI: *

Learning outcomes for a course of study

This is a *Descriptive Text Element*. For more information on the syntax
of this element, see the section on Descriptive Text Element elements.




Guidelines **Learning Outcome:** This SHOULD be used for
specific, individual, measurable learning outcomes. For more general
course aims, use the "objective" element.




### the &lt;objective&gt; element

*URI: *

An aim or learning objective. See \[EN 15982\].

This is a *Descriptive Text Element*. For more information on the syntax
of this element, see the section on Descriptive Text Element elements.

This element MUST use the \[EN 15982\] namespace:





Guidelines **Objective**: This SHOULD be used for the general
aims of the course or presentation, and give a general overview of the
purpose of the course.




### the &lt;prerequisite&gt; element

*URI: *

A prerequisite or entry requirement for accessing a course or
presentation. See \[EN 15982\].

This is a *Descriptive Text Element*. For more information on the syntax
of this element, see the section on Descriptive Text Element elements.

This element MUST use the \[EN 15982\] namespace:





Guidelines **Prerequisite**: Use this for general entry
requirements for the course or presentation, e.g. details of formal and
informal requirements for entry to the course offering




### the &lt;regulations&gt; element

*URI: *

Regulations relevant to a course of study.

This is a *Descriptive Text Element*. For more information on the syntax
of this element, see the section on Descriptive Text Element elements.


Elements used in the provider element
----------------------------------------------------------------------


### the &lt;location&gt; element

*URI:*

The spatial location of the provider

Elements:

-   street (optional) Street address
-   town (optional) Postal town
-   postcode (optional) Postcode for the address
-   address (optional, multiple) Additional address information.
-   phone (optional) A phone number as it would be dialled from the UK
-   fax (optional) A fax number as it would be dialled from the UK
-   email (optional) An email address
-   url (optional) A link to information about the location

Producers MUST NOT use a PO Box or other 'virtual' address in street,
town or postcode.

Producers MUST create &lt;email&gt; elements containing content that
conforms to the "addr-spec" production in
[RFC2822](http://www.ietf.org/rfc/rfc2822.txt?number=2822 "http://www.ietf.org/rfc/rfc2822.txt?number=2822"){.external
.text}

Producers MUST create &lt;url&gt; elements containing a valid URL as
defined by
[RFC1738](http://www.ietf.org/rfc/rfc1738.txt "http://www.ietf.org/rfc/rfc1738.txt"){.external
.text}

This element MUST use the \[EN 15982\] namespace:


Example:

     
           The College of Art, Bolton
           
               Deane Road
               Bolton
           BL3 1EX
               -123.7
               54
          
      
      




Guidelines **Refinements**: Producers MAY refine the address
element using other schemes to create specific address components. If
using an alternative or additional encoding scheme, the scheme SHOULD be
indicated using an xsi:type attribute.

**Document order**: Aggregators SHOULD interpret any untyped address
elements in document order by default.

**PO Boxes** Producers MAY use an address element for PO Box
information.






Note Attention is drawn to UPU-S42, EN14142-1 and GEO-RSS for
alternative content for this element




Elements used in the course element
--------------------------------------------------------------------


### the &lt;qualification&gt; element

*URI: *

A formal recognition of achievement or competence certificated by its
awarding body that can result from studying a course. See \[EN 15982\]

Elements:

-   [identifier](XCRI_CAP_1.2.html#the_.3Cidentifier.3E_element)
    (optional, multiple)
-   [title](XCRI_CAP_1.2.html#the_.3Ctitle.3E_element)
    (required, multiple)
-   [abbr](XCRI_CAP_1.2.html#the_.3Cabbr.3E_element) (optional)
-   [description](XCRI_CAP_1.2.html#the_.3Cdescription.3E_element)
    (optional, multiple)
-   [educationLevel](XCRI_CAP_1.2.html#the_.3CeducationLevel.3E_element) (optional)
-   [type](XCRI_CAP_1.2.html#the_.3Ctype.3E_element) (optional)
-   [url](XCRI_CAP_1.2.html#the_.3Curl.3E_element) (optional)
-   [awardedBy](XCRI_CAP_1.2.html#the_.3CawardedBy.3E_element) (optional)
-   [accreditedBy](XCRI_CAP_1.2.html#the_.3CaccreditedBy.3E_element) (optional)

This element MUST use the \[EN 15982\] namespace:





Guidelines

**identifier**: It is possible that Awarding Bodies will have permanent
URLs for the qualifications they award; these would be preferable
identifiers, but it is accepted that they may be difficult to collect,
so internal identifiers are a practical alternative. Producers SHOULD
also include an identifier that refines this property where possible to
refer to an entry in a specific qualification framework, e.g. QAN.

**educationLevel**: Producers SHOULD where possible use a URI to refer
to a level within a relevant framework, e.g.
"" would refer to EQF level 4.
Attention is drawn to
[\[1\]](http://ec.europa.eu/education/lifelong-learning-policy/doc/eqf/ukreport_en.pdf "http://ec.europa.eu/education/lifelong-learning-policy/doc/eqf/ukreport_en.pdf"){.external
.autonumber}

**awardedBy and accreditedBy**: A Producer SHOULD use the common name of
the organisation for the content of these elements.

**absence of awardedBy or accreditedBy**: Where a qualification does not
contain an awardedBy and/or accreditedBy property, an Aggregator SHOULD
interpret this as meaning the capability is provided by the Provider.

\



\




Note

In earlier versions of XCRI the AwardedBy and AccreditedBy elements were
organisation structures. However in XCRI-CAP 1.2 we define these purely
as literal values, based on actual usage by implementations.



Example:

     
       Higher National Certificate
       HNC
       QCF Level 4
       BTEC
     


### the &lt;credit&gt; element

*URI: *

An account of the credits that can be obtained from completion of a
course. See \[EN 15982\]




Note Attention is drawn to \[CWA16077\] for the definition of the
following elements and for additional guidance on their use



Elements:

-   scheme (optional, but see Guidelines) The scheme under which credits
    are obtained. See \[CWA16077\]
-   level (required) The level at which credits are obtained. See
    \[CWA16077\]
-   value (required) The number of credits that can be obtained. See
    \[CWA16077\]

If the &lt;credit&gt; element does not contain a &lt;level&gt; or
&lt;value&gt; child element, Aggregators MUST treat the &lt;credit&gt;
element as being in error.

If the &lt;credit&gt; element does not contain a &lt;scheme&gt; child
element, then any Aggregator MUST treat the &lt;credit&gt; element as
being in error.

If the &lt;credit&gt; element contains more than one &lt;scheme&gt;
child element, Aggregators MUST treat the &lt;credit&gt; element as
being in error.

Example:

    
      http://purl.org/net/cm/terms/ECTS
      http://purl.org/net/cm/terms/ECTS#1
      20
    
    
      CATS
      2
      40
    

This element MUST use the \[EN 15982\] namespace:
. The &lt;scheme&gt;, &lt;level&gt; and
&lt;value&gt; elements MUST use the Educational Credit Namespace:
.




Guidelines

**multiple credit schemes**: Producers SHOULD use a separate credit
element to represent the credits for each scheme.

**scheme:** While scheme is optional, the scheme SHOULD be stated unless
a default has been agreed between the Producer and the Aggregator.

\




Elements used in the qualification element
---------------------------------------------------------------------------




Note The other elements used in the qualification element are
defined elsewhere in this specification




### the &lt;abbr&gt; element

*URI:*

An abbreviated form of the title of the qualification


### the &lt;educationLevel&gt; element

*URI:*

The level of award. See \[DCTERMS\].

This element MUST use the DCMI Metadata Terms namespace:



### the &lt;awardedBy&gt; element

*URI:*

The organisation that awards the qualification.




Guidelines Producers SHOULD use the common name of the
organisation for the content of this element.




### the &lt;accreditedBy&gt; element

*URI:*

The organisation that accredits the qualification.




Guidelines Producers SHOULD use the common name of the
organisation for the content of this element.




Elements used in the presentation element
--------------------------------------------------------------------------


### the &lt;start&gt; element

*URI: *

The date at which a presentation begins. See \[EN 15982\].

This is a *temporal element*. For more information on the syntax of this
element, see the section on temporal elements.

This element MUST use the \[EN 15982\] namespace:



### the &lt;end&gt; element

*URI:*

The date or time at which the presentation of a course finishes.

This is a *temporal element*. For more information on the syntax of this
element, see the section on temporal elements.


### the &lt;duration&gt; element

*URI: *

A duration of a presentation. See \[EN 15982\].

Attributes:

@**interval** (optional). A machine-readable interval formatted as an
\[ISO 8601\] duration-only time interval.

If the &lt;duration&gt; element has no text content, the
&lt;duration&gt; element is in error and an Aggregator MUST ignore this
element.

If the &lt;duration&gt; element contains both text content and an
@interval attribute, and the value of the @interval attribute is NOT a
duration-only time interval as specified by \[ISO 8601\], then an
Aggregator MUST process the text content and ignore the interval
attribute.

Example:

    Three years

This element MUST use the \[EN 15982\] namespace:





Guidelines **Use of the interval attribute** While the text
content of the duration element is intended to contain a human-readable
description of the duration of the learning opportunity, the interval
attribute can be used to provide a machine-readable equivalent. If there
is no direct machine-equivalent value (e.g., the duration is flexible),
then Producers SHOULD NOT include the interval attribute.




### the &lt;applyFrom&gt; element

*URI:*

The date from which applications can be accepted for the presentation of
a course.

This is a *temporal element*. For more information on the syntax of this
element, see the section on temporal elements.


### the &lt;applyUntil&gt; element

*URI:*

The date after which applications cannot be accepted for the
presentation of a course.

This is a *temporal element*. For more information on the syntax of this
element, see the section on temporal elements.


### the &lt;applyTo&gt; element

*URI:*

A URL to a resource for further information about, or an online
application system for, the presentation.


### the &lt;engagement&gt; element

*URI:*

The logistical means by which individuals engage in a Presentation,
encompassing temporal, modal and spatial patterns of engagement and
attendance. See \[EN 15982\].

This element MUST use the \[EN 15982\] namespace:





Guidelines **Refinements** Producers SHOULD use the refinements
defined for this element with their predefined vocabularies in
preference to this element.




### the &lt;studyMode&gt; element

*URI::*

A general expression of the overall amount of the student's time that is
devoted to the learning opportunity, as defined by the provider.




Note This element is a refinement of the Engagement element



Attributes:

@identifier (optional)

Example:

    Full time




Guidelines

*Recommended Values*: Producers SHOULD use the following values for this
element, with the two-letter code used in the @identifier attribute, and
the label in the element content:

 NK Not known \[DEFAULT\] 
:   The provider has not supplied the information.

 FL Flexible 
:   Could be full time or part time dependent on the learner.

 FT Full time 
:   The learning opportunity is the learner's main activity.

 PF Part of a full time programme
:   The learning opportunity is a component of a set of learning
    opportunities that form the learner's main activity.

 PT Part time
:   The learning opportunity is not the learner's main activity

*Note*: These are mutually exclusive terms, so 'Full time' does not
include 'Part of a full time programme'.

-   This vocabulary is also available in VDEX format:
    

\




### the &lt;attendanceMode&gt; element

*URI::*

The type of location at which the student will undertake the learning
opportunity, for example distance learning, campus-based, work-based, or
online.




Note This element is a refinement of the Engagement element



Attributes:

@identifier (optional)

Example:

    Campus

\




Guidelines

*Recommended Values:* Producers SHOULD use the following values for this
element, with the two-letter code used in the @identifier attribute, and
the label in the element content:

The value of this element MUST be one of:

CM Campus
DA Distance with attendance
DS Distance without attendance
NC Face-to-face non-campus
MM Mixed mode
ON Online (no attendance)
WB Work-based
-   This vocabulary is also available in VDEX format:
    




### the &lt;attendancePattern&gt; element

*URI::*

The period in the day and/or frequency during which attendance at a
venue is required (if any), for example evenings, daytime, weekends.




Note This element is a refinement of the Engagement element



\
Attributes:

@identifier (optional)

Example:

    Daytime

\




Guidelines *Recommended Values:* Producers SHOULD use the
following values for this element, with the two-letter code used in the
@identifier attribute, and the label in the element content:

DT Daytime
EV Evening
TW Twilight
DR Day/Block release
WE Weekend
CS Customised
-   This vocabulary is also available in VDEX format:
    

\




### the &lt;languageOfInstruction&gt; element

*URI:mlo:languageOfInstruction*

A language in which the presentation is available to be taught. See \[EN
15982\].

If the content of this element is not a valid language tag according to
the \[BCP-47\] specification, then Aggregators MUST treat this element
as being in error and ignore this element.

This element MUST use the \[EN 15982\] namespace:


The codes available for use in this element are also available in VDEX
format: 


### the &lt;languageOfAssessment&gt; element

*URI:*

A language in which a presentation of a course can be assessed.

If the content of this element is not a valid language tag according to
the \[BCP-47\] specification, then Aggregators MUST treat this element
as being in error and ignore this element.

The codes available for use in this element are also available in VDEX
format: 


### the &lt;places&gt; element

*URI: *

Number of places available for participants in the presentation . See
\[EN 15982\].

This element MUST use the \[EN 15982\] namespace:





Guidelines The default, unqualified value of this property is a
simple textual description. Producers MAY use specific encoding schemes
that refine the use of this property.




### the &lt;cost&gt; element

*URI: *

A cost associated with obtaining access to the presentation. See \[EN
15982\].

Example:

     The course fees are ¬£800 per semester, payable either in advance or monthly by direct debit.

This element MUST use the \[EN 15982\] namespace:





Guidelines The default, unqualified value of this property is a
simple textual description. Producers MAY use specific encoding schemes
that refine the use of this property.




### the &lt;age&gt; element

*URI: *

The intended age range for which the presentation is suitable. This is a
refinement of: 

The value of this element MUST be one of:

-   any
-   not known
-   *x*-*y*
-   *x*+

Where *x* and *y* MUST be non-negative integers.

If the value of *x* is greater than the value of *y*, Aggregators MUST
treat this element as in error and ignore this element.

If the content of this element is not one of the values or patterns
defined above, Aggregators MUST treat this element as in error and
ignore this element.

Examples:

    14+
    14-16
    14-19
    any




Guidelines

If the value of *y* is greater than or equal to 99, Aggregator MAY treat
the value of this element as being equivalent to *x*+.

If the value of *x* or *y* is greater than 120, Aggregators MAY either
truncate the value from the right to a more realistic number, for
example changing "124" to "12", or they MAY treat this element as in
error and ignore this element.

\




### the &lt;venue&gt; element

*URI: *

A location where a course is presented.




Note Venue is equivalent to offeredAt in \[EN 15982\].



Elements:

-   provider (required)

Producers MUST include a &lt;provider&gt; element as the only child
element of &lt;venue&gt;.

If a &lt;venue&gt; element does not contain one and only one
&lt;provider&gt; element, Aggregators MUST treat the &lt;venue&gt;
element as being in error.

If a &lt;venue&gt; element contains any child elements other than
&lt;provider&gt;, Aggregators MUST treat the &lt;venue&gt; element as
being in error.

If a &lt;venue&gt; element contains any text content, Aggregators MUST
treat the &lt;venue&gt; element as being in error.

Example:

    
     
       
          asc:Priory Campus
          Priory Campus
           
               Victoria Road
               Kirkcaldy
               KY1 2QT
           
      
     
    




Guidelines **Provider**: Producers SHOULD use the provider
element to describe the organisation which acts as the provider of the
venue. This MAY be a sub-organisation of the provider of the
presentation (such as a department or school), or it MAY be a third
party or external organisation.

**Provider Properties**: When a provider element is used in a venue
element, Producers SHOULD include only basic information about an
organisation, such as identifier, title, description, url, image and
location.

**Location**: When a provider element is used in a venue element,
Producers SHOULD include a location element.




Processing XCRI CAP XML Documents
==================================================================


Temporal Elements
--------------------------------------------------

A *Temporal Element* contains information about dates and times, and
this can include both the "human readable" and the "machine processable"
aspects of information.

A *Temporal Element* is defined as having the following attributes:

-   **@dtf** (optional) A machine-processable date or time

A *Temporal Element* MUST contain temporal information suitable for
presentation as text content.




Note For example "September, 2012" or "Early Summer, 2011".



If a *Temporal Element* contains a @dtf attribute, this attribute MUST
contain a date or time formatted in accordance with \[W3C-DTF\], as used
in the definition of the \[W3C XML Schema\] specification's "DateTime"
type OR "Date" types, at any level of precision.




Note For example, the year only, or year-month-day



If a *Temporal Element* does not contain text content, an Aggregator
MUST treat the element as in error and ignore the element.

If a *Temporal Element* has a @dtf attribute, and the value of the
attribute does not contain a valid date or time according to
\[W3C-DTF\], an Aggregator MUST treat the element as in error and ignore
the element.

Examples:

     September 2011
     May 2012

     As soon as enough students have enrolled, usually once every four weeks




Guidelines If a *Temporal Element* has both a valid @dtf
attribute and text content, an Aggregator MAY use either or both of the
values.




Descriptive Text Elements
----------------------------------------------------------

A *Descriptive Text Element* contains or refers to descriptive text
content.

A *Descriptive Text Element* is defined as having the following
attributes:

-   **@lang** (optional) The language used for the description
-   **@href** (optional) A link to supporting information

The content of a *Descriptive Text Element* MUST be one of either:

-   Empty
-   Plain unescaped text content
-   Valid XHTML 1.0 content

If a *Descriptive Text Element* has an @href attribute, the Producer
MUST NOT include any text content or child elements.

If a *Descriptive Text Element* has an @href attribute and the
&lt;description&gt; element contains either text content or child
elements, an Aggregator MUST treat the element as in error and ignore
the element.

Example

        
            
                This module shows how to take an existing presentation and modify it and how to create 
                 your own presentations. No knowledge of PowerPoint is assumed.
                The topics covered are:
                    
                        Using and modifying an existing PowerPoint presentation 
                        Creating a simple presentation 
                        Making use of themes and schemes supplied with PowerPoint 
                        The PowerPoint views 
                        Printing and saving your presentation
                    
                 
                    
        




Guidelines

**Encoding schemes:** Use of vocabularies for types of *Descriptive Text
Elements* is encouraged.

**Use of images:** Images SHOULD NOT be referenced from within the
*Descriptive Text Element* element by Producers as these are unlikely to
be presented by Aggregators; potentially an image tag can be used to
execute cross-site scripting (XSS) attacks. Instead, any image SHOULD be
provided separately using the XCRI [image](Image.html "Image") element.

**Length:** Aggregators MAY choose to truncate long *Descriptive Text
Element* content; a suggested maximum length is 4000 characters.

**Safe use of XHTML:** See the section on Security Considerations for
guidance.

**Inheritance:** *Descriptive Text Elements* and any refinements are
*inheritable*. See the section on inheritance for more guidance.




Inheritable Elements
-----------------------------------------------------

Inheritable Elements are elements whose content can be inferred within
child elements from a parent element. This enables documents to be less
verbose by not repeating basic information.




Note For example, an Aggregator may infer that a
&lt;presentation&gt; has a subject of "technology" because its parent
&lt;course&gt; element contains
&lt;dc:subject&gt;technology&lt;/dc:subject&gt;



Inheritable elements are indicated in the specification text using the
'**inheritable'** keyword.




Note

Inheritability also applies to refinements of elements

For example:

    
        ...
       This course is aimed at providing a basic competence in electrical engineering
        
           1
            ...
         
         
            2
            This course is aimed at providing a basic competence in electrical engineering with the specific aim of progressing to a professional qualification
          
    

Here an Aggregator would interpret this as meaning:

Presentation 1: objective: This course is aimed at providing a basic
competence in electrical engineering

Presentation 2: objective: This course is aimed at providing a basic
competence in electrical engineering with the specific aim of
progressing to a professional qualification

\






Guidelines Aggregators SHOULD make use of inheritance when
interpreting XCRI-CAP documents.




XML Schema
===========================================

*This section is not normative*

Example schemas are available from [Google
code](http://code.google.com/p/xcri-schemas/source/browse/#svn%2Fbranches%2F1.2%2Fxsd "http://code.google.com/p/xcri-schemas/source/browse/#svn%2Fbranches%2F1.2%2Fxsd"){.external
.text} or as a zipped file from the [XCRI Knowledge
Base](http://www.xcri.co.uk/bindings/xcri_cap_1_2.zip "http://www.xcri.co.uk/bindings/xcri_cap_1_2.zip"){.external
.text}.


Security Considerations
========================================================


XHTML Content
----------------------------------------------

*This section is not normative*

Descriptive Text Elements allow the delivery of XHTML. Many elements in
these languages are considered 'unsafe' in that they open clients to one
or more types of attack. Aggregators should carefully consider their
handling of every type of element when processing incoming XHTML in XCRI
CAP 1.2 Documents. Attention is drawn to the security section of
[RFC2854](http://tools.ietf.org/html/rfc2854 "http://tools.ietf.org/html/rfc2854"){.external
.text} for guidance.

Aggregators SHOULD pay particular attention to the security of the IMG,
SCRIPT, EMBED, OBJECT, FRAME, FRAMESET, IFRAME, META, and LINK elements,
but other elements might also have negative security properties.

XHTML can either directly contain or indirectly reference executable
content.


Conformance to \[EN 15982\]
============================================================

*This section is not normative*

XCRI CAP 1.2 is a *conforming binding* for \[EN 15982\]. This means that
XCRI CAP 1.2 provides a binding for all the classes and properties
defined in \[EN 15982\] but also adds extensions. This means that any
XCRI CAP 1.2 XML document is also a *conforming instance* of \[EN
15982\].

The tables below show how \[EN 15982\] classes and properties are
related to XCRI CAP 1.2 elements.

*Equivalent* indicates that XCRI defines an element in its own namespace
that is semantically equivalent to the \[EN 15982\] class or property,
and can be considered a fully qualified refinement of the \[EN 15982\]
class or property. (In most cases, the only difference is the label).

*Implemented By* indicates that the XCRI element is a direct
implementation of the \[EN 15982\] class or property using the \[EN
15982\] namespace.

*Extension* indicates that the XCRI element is an extension of \[EN
15982\] and does not directly map onto an existing \[EN 15982\] property
or class.

*Refined By* indicates that the XCRI element is a fully qualified
refinement of an \[EN 15982\] class or property.

  \[EN 15982\] class                   Relationship   XCRI element   Conformance Level
  ------------------------------------ -------------- -------------- ---------------------
  Learning Opportunity Specification   Equivalent     Course         Strictly Conforming
  Learning Opportunity Instance        Equivalent     Presentation   Strictly Conforming
  Learning Opportunity Provider        Equivalent     Provider       Strictly Conforming

  :  Mapping \[EN 15982\] classes to XCRI elements

  \[EN 15982\] property     Relationship     XCRI element                                                                                                Conformance Level
  ------------------------- ---------------- ----------------------------------------------------------------------------------------------------------- ---------------------
  contributor               Implemented By   contributor                                                                                                 Strictly Conforming
  date                      Implemented By   date                                                                                                        Strictly Conforming
  date                      Refined By       end                                                                                                         Strictly Conforming
  date                      Refined By       applyFrom                                                                                                   Strictly Conforming
  date                      Refined By       applyUntil                                                                                                  Strictly Conforming
  description               Implemented By   description                                                                                                 Strictly Conforming
  identifier                Implemented By   identifier                                                                                                  Strictly Conforming
  subject                   Implemented By   subject                                                                                                     Strictly Conforming
  title                     Implemented By   title                                                                                                       Strictly Conforming
  type                      Implemented By   type                                                                                                        Strictly Conforming
  url                       Implemented By   url                                                                                                         Strictly Conforming
  hasPart                   Implemented By   hasPart                                                                                                     Strictly Conforming
  location                  Implemented By   location                                                                                                    Strictly Conforming
  offers                    Equivalent       Elided by the containment of Course elements in Provider elements rather than by explicit association       Strictly Conforming
  specifies                 Equivalent       Elided by the containment of Presentation elements in Course elements rather than by explicit association   Strictly Conforming
  qualification             Implemented By   qualification                                                                                               Strictly Conforming
  credit                    Implemented By   credit                                                                                                      Strictly Conforming
  level                     Implemented By   level                                                                                                       Strictly Conforming
  offeredAt                 Equivalent       venue                                                                                                       Strictly Conforming
  start                     Implemented By   start                                                                                                       Strictly Conforming
  duration                  Implemented By   duration                                                                                                    Strictly Conforming
  cost                      Implemented By   cost                                                                                                        Strictly Conforming
  language of instruction   Implemented By   languageOfInstruction                                                                                       Strictly Conforming
  prerequisite              Implemented By   prerequisite                                                                                                Strictly Conforming
  places                    Implemented By   places                                                                                                      Strictly Conforming
  engagement                Implemented By   engagement                                                                                                  Strictly Conforming
  engagement                Refined By       studyMode                                                                                                   Strictly Conforming
  engagement                Refined By       attendanceMode                                                                                              Strictly Conforming
  engagement                Refined By       attendancePattern                                                                                           Strictly Conforming
  objective                 Implemented By   objective                                                                                                   Strictly Conforming
  assessment                Implemented By   assessment                                                                                                  Strictly Conforming
  N/A                       Extension        languageOfAssessment                                                                                        Conforming
  N/A                       Extension        applyTo                                                                                                     Conforming
  N/A                       Extension        image                                                                                                       Conforming
  N/A                       Extension        age                                                                                                         Conforming
  N/A                       Extension        abstract                                                                                                    Conforming
  N/A                       Extension        applicationProcedure                                                                                        Conforming
  N/A                       Extension        learningOutcome                                                                                             Conforming
  N/A                       Extension        regulations                                                                                                 Conforming

  :  Mapping \[EN 15982\] properties to XCRI elements


Mapping from XCRI CAP 1.2 to \[EN 15982\]
--------------------------------------------------------------------------

*This section is not normative*

An XCRI document is already a *conforming instance* of \[EN 15982\]. The
following guidelines are intended to assist implementers in converting
XCRI CAP 1.2 documents to *strictly conforming instances* of \[EN
15982\].


### Equivalents

Elements identified as "equivalent" should be converted directly into
their equivalent element in \[EN 15982\]; for example,
&lt;xcri:venue&gt; should be converted to &lt;mlo:offeredAt&gt;


### Refinements of &lt;engagement&gt;

The &lt;studyMode&gt;, &lt;attendanceMode&gt; and
&lt;attendancePattern&gt; elements should be treated refinements of
mlo:engagement when converting an document from XCRI CAP 1.2 to a
*strictly conforming instance* of \[EN 15982\].


### Refinements of &lt;date&gt;

The following elements should be treated as refinements of dc:date when
converting from XCRI CAP 1.2 to a *strictly conforming instance* of \[EN
15982\]:

-   end
-   applyFrom
-   applyUntil


### Temporal Elements

In general \[EN 15982\] instances would expect to have temporal elements
to contain data in \[W3C DTF\] format; therefore when converting from
XCRI CAP 1.2, you should first map the value of any @dtf attribute of
these elements to the content of the dc:date element. If there is no
@dtf attribute, then the text content of the XCRI element should be
used.


### Extensions

To convert an XCRI CAP 1.2 XML document so that it is a *strictly
conforming instance* of \[EN 15982\], the following extensions should be
omitted:

-   languageOfAssessment
-   applyTo
-   image
-   age
-   abstract
-   applicationProcedure
-   learningOutcome
-   regulations


### Location details

While \[EN 15982\] does not define a detailed structure for the
mlo:location element, XCRI CAP 1.2 defines a structure of address and
contact information. This is still strictly conformant, but may need to
be converted to make sense in other systems, either by mapping the
elements to another contact information schema (e.g. PortableContacts or
VCard) or downgrading to plain text content.


### Descriptive Text Elements

XCRI CAP 1.2 uses a richer structure for describing resources than \[EN
15982\]; the Descriptive Text Elements can contain XHTML content.

To convert to \[EN 15982\] it may be necessary to "mark down" the
content of these elements, for example by extracting the child text
nodes and stripping out any XHTML tags.