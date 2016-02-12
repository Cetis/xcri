---
layout: default
---

HEAR 1.0 Requirements 
=====================




Design Goals
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


*This section is non-normative*

Accessibility:   The specification needs to support relevant accessibility
    guidelines, such as WCAG 2.0.

Compatibility with other standards:   The specification needs to maintain compatibility with, or directly
    make use of, other standards where possible.

Current development practice or industry best-practice:   The specification needs to consider the development practices
    currently used by developers and promote relevant
    industry best-practice.

Internationalization and localization:   The specification needs to implement relevant internationalization
    and localization guidelines, such as i18n-XML and BCP 47, as well as
    consider current practical internationalization solutions used by
    the development community.

Interoperability:   The specification needs to attempt to be as interoperable as
    possible with existing systems.

Longevity:   The specification needs to be specified in such a way that it
    ensures that a feed can still be processed well into the future.

Security:   The specification needs to address the security concerns of
    end-users, authors, distributors and device manufacturers by
    recommending appropriate security policies and programming behavior.

Wider community benefit:   Any new technologies or processes defined by the specification need
    to designed in such a way that they are beneficial to the wider
    community at large. In other words, the specification should try not
    to be insular to its problem domain, but should also consider the
    needs of the wider community.

XML interoperability:   The specification must be capable of being parsed by widely used XML
    parsing modules in a range of languages, including PHP, Java, Ruby,
    C\#

Enable new opportunities:   The specification must not preclude the development of added-value
    services using HEAR data in a wide range of potential
    business models.

Flexibility:   The specification should allow achievement information to be
    rendered, reordered, transformed and matched in a wide range
    of ways.


Requirements
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### R1: Conform to the emerging European Norm for European Learner Mobility (EuroLM)

The specification must conform to the European Norm for European Learner
Mobility (EuroLM) (See [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf"){.external
.text}.)

**Motivation**: *compatibility with other standards, longevity,
interoperability*

**Rationale**: The EuroLM European Norm is very likely to be the agreed
data model for the expression and exchange of European Learner Mobility
information, as defined by the European transparency instruments.
Conforming to it enables wider interoperability between HEAR
implementations and Europass related information in systems in other EU
countries conforming to other specifications based on EuroLM.


###  R2: Support interoperability between systems in UK Higher Education Institutions (HEIs)

The specification must support XML-based interoperability of achievement
information between systems in UK Higher Education Institutions (HEIs),
including Universities and other UK institutions offering UK HE courses
and awarding UK HE qualifications.

**Motivation**: *compatibility with other standards, current development
practice or industry best-practice, XML interoperability*

**Rationale**: The specification uses other existing XML specifications,
for example XCRI-CAP, and is designed to interoperate with other
XML-based systems.


### R3: Adhere to the HEAR guidance template produced by the Burgess Implementation Group

The final specification must adhere to the final version of the HEAR
guidance template produced by the Burgess Implementation Group. The
final version has not yet been produced, so the initial version of the
specification will adhere to the latest version of the template.

**Motivation**: *wider community benefit, immediate benefits,
flexibility*

**Rationale**: The HEAR implementation process in institutions is driven
by the guidance notes and templates produced by the Burgess
Implementation Group. This requirement is vital, so that developers do
not diverge from the institutional process.


###  R4: Incorporate the dataset of the Diploma Supplement (DS)

**Motivation**: *compatibility with other standards, interoperability,
longevity, immediate benefits*

**Rationale**: HEIs have already implemented the DS and this will
continue to be a European standard requirement.


###  R5: Incorporate the dataset of the HE Transcript

**Motivation**: *compatibility with other standards, interoperability,
longevity, immediate benefits*

**Rationale**: HE policy requires the implementation of a transcript and
HEIs have already implemented it; the HEAR builds on this work.


### R6:  Link to external information from persistent URIs")\] R6: Link to external information from persistent URIs

The specification must support links to the following nationally
established and maintained information (where persistent URIs exist):

-   Nationally devised ‚Äòlevel indicators‚Äô (see guidance notes)
-   Preamble to the Diploma Supplement (standard text \[where is
    this held?\]).
-   Statement about HESA and HESA number (standard text \[where is
    this held?\]).
-   Information related to PSRB involvement, in the form of a statement
    agreed with relevant PSRBs at national level.
-   Information on national HE Systems (see guidance notes)

**Motivation**: *interoperability, longevity, efficiency, flexibility*

**Rationale**: The HEAR is required to include pre-determined statements
from regulatory authorities.

Note This requirement was written when it was believed that there
were or were going to be persistent URIs for these items of information.
This is not the case. Therefore this requirement is subject to revision.
It is likely that the responsibility for this information will rest with
individual HEIs.

### R7: Support usage as a formative document

To be used as a formative document from the point of a student‚Äôs entry
to HE onwards throughout their HE experience:

-   as a basis for reviewing progress and planning future activities;
-   to support student engagement in opportunities beyond the
    curriculum;
-   as an aide memoire for students in making applications which may be
    required before the final award is made, e.g. for sandwich
    placements and internships; permanent employment; further study or
    training opportunities;
-   subject to the appropriate permissions, for verification by
    employers and postgraduate tutors of statements made by the student.

**Motivation**: *interoperability, wider community benefit*

**Rationale**: This is a central function of the HEAR.


### R8: Support output of the information as a formal, final format, exit document

The HEAR is needed as an authoritative final format document for use by
students, employers and others as its central function.

**Motivation**: *security, wider community benefit, immediate benefits*

**Rationale**: This is a central function of the HEAR.


### R9: Contain a clear and consistent core element for all institutions

Based on the transcript which has a Minimum Data Set, the HEAR should
contain a clear and consistent core element.

**Motivation**: *interoperability, wider community benefit, enable new
opportunities, efficiency*

**Rationale**: Needed in order to enable both automatic processing and
comparability between students.


###  R10: Support interoperability between different institutions

Information for HEARs must be exchangeable between different
institutions.

**Motivation**: *interoperability, enable new opportunities*

**Rationale**: Information for single HEARs may be contained within
systems of different institutions, as a student may take components of
courses from different institutions.


###  R11: Support the usage of institutional and other standardised vocabularies

The HEAR should use well-defined and controlled standardised
vocabularies where possible.

**Motivation**: *Compatibility with other standards, interoperability,
flexibility*

**Rationale**: Interoperability is enhanced by detailed definition and
consistency of content; consistent vocabulary usage will enable content
to be mapped across different standards.


### R12: Incorporate the use of the HESA number and the Unique Learner Number

Students should be identified by the use of industry standard
identifiers.

**Motivation**: *compatibility with other standards, current development
practice or industry best-practice, interoperability, enable new
opportunities*

**Rationale**: Use of the HESA number and later, the Unique Learner
Number, solves the problem of identification of the student.


### R13: Include an explanatory statement if the HEAR is available only in electronic format

**Motivation**: *Current development practice or industry best-practice,
efficiency*

**Rationale**: The guidance notes require a clear statement if there is
a restriction on availability of the information.


### R14: Include standard statements about the name and status of the institution awarding the qualification

Institutions that have been granted legal powers by the Privy Council to
award UK degrees are designated as 'recognised bodies'. Other
institutions, which do not have the power to award their own degrees,
but may through partnership arrangements deliver full programmes that
lead to a degree that is awarded by a 'recognised body', are designated
as 'listed bodies'.

**Motivation**: *wider community benefit,*

**Rationale**: Required for European standardisation.




Note See note on R6.




### R15: Support authentication of the HEAR by the institution

The HEAR is authenticated and verified as accurate by the institution
that produced it.

**Motivation**: *security, immediate benefits*

**Rationale**: As the official record of the student's achievement, the
HEAR must be verified by the producing institution as an authenticated
document.


### R16: Support the usage of assessment data from the institution's official Student Record System

The HEAR document is generated from data within the University‚Äôs
central Student Record System, in which format it is regulated by the
University.

**Motivation**: *current development practice or industry best-practice,
interoperability, security, efficiency*

**Rationale**: Information for the HEAR must be obtained from an
authoritative source


### R17:  Support authorised amendment to the content of the HEAR")\] R17: Support authorised amendment to the content of the HEAR

Only authorised personnel should be able to amend the content of the
HEAR, but students should be able to challenge the contents in cases of
inaccuracy.

**Motivation**: *current development practice or industry best-practice,
longevity, security*

**Rationale**: All data should be verifiable institutionally, factually
based and non-evaluative except in cases of recorded grades where the
grade records an explicit judgement in respect of academic standards.
Students should be made aware of their rights to remove, challenge or
amend items in cases of proven inaccuracy.


###  R18: Support the use of electronic search tools

The digitised HEAR should support electronic search mechanisms.

**Motivation**: *interoperability, wider community benefit, enable new
opportunities*

**Rationale**: End users may be expected to access records in by the use
of electronic search tools, of the kinds used by graduate recruiters to
scan electronic applications.


###  R19: Format and Schema

The specification MUST specify the document language using a common data
interchange format, as well as the rules for processing the
configuration document language and any micro-syntaxes represented as
character data. The specification SHOULD specify a formal schema for the
language, as well as define any defaults. The schema SHOULD NOT be a
normative part of the specification, but MUST be suitable for use by
conformance checkers. The specification MUST recommend that
configuration documents be encoded in UTF-8.

**Motivation**: Compatibility with other standards, current development
practice or industry best-practice, ease of use, internationalization
and localization, longevity, XML interoperability, and accessibility.

**Rationale**: To have a language in a format that is relatively easy
for authors to read and write, and provides effective
internationalization support. An example of such a language is XML. XML
is generally accepted and understood by widget authors and parsed by all
market-leading widget user agents, and XML parsers generally have
reasonable support for Unicode, which allows for effective
internationalization and localization.

