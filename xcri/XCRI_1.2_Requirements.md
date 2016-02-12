---
layout: post
---







XCRI 1.2 Requirements 
=====================

Design Goals
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

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


Simplicity:   The specification must be simple to implement by providers using
    existing course databases and publishing systems or as a single
    static XML file


Implementation-readiness:   The specification must be simple to implement by aggregators using
    existing metadata harvesting and syndication techniques


XML interoperability:   The specification must be capable of being parsed by widely used XML
    parsing modules in a range of languages, including PHP, Java, Ruby,
    C\#


Enable new opportunities:   The specification must enable the development of added-value
    services using aggregated data as a starting point, and must support
    a wide range of potential business models


Efficiency:   The specification must reduce the amount of data transformation and
    re-keying needed to advertise courses


Immediate Benefits:   The specification must provide immediate and identifiable benefits
    for both provider and aggregators/brokers


Flexibility:   The specification should allow course information to be rendered,
    reordered, transformed and matched in a wide range of ways with
    precise selection of strongly-typed but elastic data elements.



Requirements
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


###  R1: Conform to the European Norm for Metadata for Learning Opportunities

The specification must conform to the European Norm for Metadata for
Learning Opportunities (See [CWA
15903](ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf "ftp://ftp.cenorm.be/PUBLIC/CWAs/e-Europe/WS-LT/CWA15903-00-2008-Dec.pdf").)

**Motivation**: *compatibility with other standards, longevity,
interoperability*

**Rationale**: The MLO standard represent the core agreement on course
information across Europe, and supporting this standard enables wider
interoperability between XCRI implementations and systems in other EU
countries conforming to other specifications based on MLO.


###  R2: Support Online Application Links

Support links to online application process where supported

**Motivation**: Current development practice or industry best-practice,
Enable new opportunities, Immediate Benefits

**Rationale**: See discussion at



### R3:Support Higher Ambitions

Provide more details for applicants based on the Higher Ambitions
recommendations. The areas of weakness in XCRi-CAP 1.1 from this
perspective \*might\* be opportunities for international experience and
access to external expertise or experience.

**Motivation**: Enable new opportunities, Immediate Benefits

**Rationale**: See discussion at





Editor's Note Should we instead be looking at the HEI key
Information sheet requirements now?




###  R4:Flexible date handling

Support dates in a way which enables flexible behaviour with regard to
dates; for example specifiying only a year or month name, or a complete
datetime, without worrying too much about the ability of an aggregator
to be able to intelligently process the information.

**Motivation**: Simplicity, Interoperability, Flexibility

**Rationale**: See discussion at



###  R5:Different provider types

Support identifying the type of provider offering a course, e.g. school,
university, college, training company.

**Motivation**: Implementation-readiness, Enable new opportunities,
Efficiency, Immediate Benefits

**Rationale**: See discussion at



###  R6:Link to Ofsted

Support linking providers to Ofsted information.

**Motivation**: Efficiency, Immediate Benefits

**Rationale**: See discussion at



###  R7:Short description for list views

Provide space for a short text-only description of a course suitable for
appearing in lists.

**Motivation**: Simplicity, Interoperability, Efficiency, Immediate
Benefits, Flexibility

**Rationale**: See discussion at



### R8:Age range

Provide space for an intended age range for a course or presentation.

**Motivation**: Simplicity, Interoperability, Efficiency, Immediate
Benefits

**Rationale**: See discussion at



###  R9:Vocabularies

Support the use of encoding schemes, controlled text and other types of
taxonomy by providing explicit structures for machine readable coded
values and human readable terms.

**Motivation**: Compatibility with other standards, Current development
practice or industry best-practice, Internationalization and
localization, Interoperability, Implementation-readiness, Flexibility

**Rationale**: Enables efficient parsing of instances by systems
requiring RSS-type feeds and / or well-defined, highly structured data.
