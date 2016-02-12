---
layout: post
---

XCRI CAP 1.1 
============

### Status

This is currently a working draft of version 1.1.

There is a [proposal available for version
1.2](XCRI_CAP_1.2.html "XCRI CAP 1.2").


### Patents

This specification is subject to a royalty free patent policy.

There are no known patents covering any of this work. If you think that
part of this work may be subject to an existing or pending patent,
please email the editors.


### Copyright and License

This work is (c) 2005-2009 XCRI.org, and licensed under a Creative
Commons Attribution 3.0 Licence. All contributions MUST be licensed
under the same conditions. This is to ensure that the specification work
can be transferred to an appropriate standardisation body.


###  Inspiration and acknowledgements


Introduction
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The XCRI Course Advertising Profile (XCRI-CAP) is a specification to
enable the interoperability of descriptions of courses, or any other
kind of learning opportunity, between the course provider and any number
of aggregators and brokers, by supplying an XML description.

There are two implementation patterns for XCRI-CAP, one following the
general model of simple XML syndication (rather like RSS or Atom) called
the [simple aggregation
pattern](Simple_aggregation_pattern.html "Simple aggregation pattern"),
and another following the model of metadata harvesting by checking for
differences between the current catalog and a previously harvested copy
(the [delta update
pattern](Delta_update_pattern.html "Delta update pattern")). Whichever
pattern is used, the XML format used for the course description is
largely identical.

An XCRI-CAP document typically consists of a top-level
[catalog](Catalog.html "Catalog") element, encapsulating a single
[provider](Provider.html "Provider"), and a collection of
[course](Course.html "Course") descriptions for the courses offered by
the provider. Each course has various descriptive information available
such as syllabus, the qualification you can obtain, career options and
so on. The course is also divided into any number of
[presentations](Presentation.html "Presentation"), which are the
'instances' or 'offerings' of the course that a prospective student will
apply for, and which have specific start and end dates, locations and so
on, and can vary in aspects such as the location and mode of study (e.g.
a full-time and part-time presentation, with different duration and end
date).


###  Design Goals

XCRI-CAP is being designed with the following goals in mind. XCRI-CAP
should:

-   Be simple to implement by providers using existing course databases
    and publishing systems or as a single static XML file
-   Be simple to implement by aggregators using existing metadata
    harvesting and syndication techniques
-   Be capable of being parsed by widely used XML parsing modules in a
    range of languages, including PHP, Java, Ruby, C\#
-   Enable the development of added-value services using aggregated data
    as a starting point
-   Reduce the amount of data transformation and re-keying needed to
    advertise courses
-   Provide immediate and identifiable benefits for both provider and
    aggregators/brokers
-   Support a wide range of potential business models


### Basic Concepts

The basic mode of operation for XCRI is for organisations to create a
feed of course information, consisting of an XML document that contains
their [provider](Provider.html "Provider") details, including the
[courses](Course.html "Course") they offer. Each of these objects (or
*resources* as we call them) is described using a number of
*properties*.

An *aggregator* or a *broker* can then download a number of feeds and
collate them to enable cross-searching or other capabilities.

[![Image:Model.png](../images/7/79/Model.png)](Image%253AModel.png "Image:Model.png")


### Implementation Patterns

XCRI-CAP supports two main implementation patterns:

-   In the [simple aggregation
    pattern](Simple_aggregation_pattern.html "Simple aggregation pattern"),
    each [provider](Provider.html "Provider") offers its feed as an XML
    file that can be periodically downloaded by an aggregator. The
    aggregator replaces any previous information about the
    [provider](Provider.html "Provider") and their
    [courses](Course.html "Course") with the latest data.
-   the [delta update
    pattern](Delta_update_pattern.html "Delta update pattern") follows
    the same pattern as the Open Archives Protocol for Metadata
    Harvesting (OAI-PMH). In this pattern, each provider offers an API
    where aggregators can obtain an XML catalog file containing
    information about changes since a specified date.

For aggregators, there are also patterns for discovering XCRI feeds:

-   the [feed
    autodiscovery](Feed_autodiscovery.html "Feed autodiscovery") pattern
    uses the Link tag in HTML pages on the provider's site
-   the [reliable feed
    location](Reliable_feed_location.html "Reliable feed location")
    pattern uses a convention for deploying XCRI feeds in consistent
    ways

See also [Category:Implementation
patterns](Category%253AImplementation_patterns.html "Category:Implementation patterns")
for more patterns.


Format
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------


### XCRI Documents

An XCRI-CAP XML document MUST have one of the following
[resources](Category%253AResource_Types.html "Category:Resource Types")
as its *root element*:

-   [Catalog](Catalog.html "Catalog")
-   [Provider](Provider.html "Provider")
-   [Course](Course.html "Course")

In general any provider SHOULD use [Catalog](Catalog.html "Catalog") as
the root element. (Note that the "[Catalog](Catalog.html "Catalog")"
element is just a container for the information - it doesn't imply a
relationshop between the feed and a real course catalog)

The specification allows both [Provider](Provider.html "Provider") and
[Course](Course.html "Course") as alternative root elements to enable
REST-style operations to be provided by aggregators (much in the same
way that the IETF Atom specification enables both feed and entry
elements to be document roots).


###  Information Model

Click the image to see a schematic of the XCRI-CAP v1.1 information
model.





[![](../images/thumb/e/e3/Xcri_cap_1_4_r4.png/200px-Xcri_cap_1_4_r4.png)](Image%253AXcri_cap_1_4_r4.png)




[![](../skins/common/images/magnify-clip.png)](Image%253AXcri_cap_1_4_r4.png "Enlarge")




### Namespace

XCRI-CAP elements and attributes are identified using the namespace:

### Resources

A *resource* is something that can be uniquely identified
[\[1\]](http://dublincore.org/documents/abstract-model/ "http://dublincore.org/documents/abstract-model/"){.external
.autonumber}. In XCRI, we identify resources using a *Uniform Resource
Identifier* (URI). A resource can possess a number of *properties*,
which may be simple value-strings or can be structured.

XCRI-CAP specifies the following resource *classes*:

-   [catalogs](Catalog.html "Catalog") advertise
    [providers](Provider.html "Provider")
-   [providers](Provider.html "Provider") advertise
    [courses](Course.html "Course")
-   [courses](Course.html "Course") are presented for enrolment any
    number of times through
    [presentations](Presentation.html "Presentation")
-   [presentations](Presentation.html "Presentation") instantiate
    [courses](Course.html "Course")


###  Properties

Properties contain information about *resources*. While many of the
properties of the resources defined by XCRI-CAP are simple values such
as strings and dates, properties can also be structured objects.
Typically in an implementation structured properties become resources in
their own right, however as they are not addressed directly from outside
the implementation they are usually not given universal identifiers.

[View a complete index of properties defined within the XCRI-CAP
namespace.](Category%253AProperties.html "Category:Properties")


#### Vocabularies

Use of the [XCRI\_Terms\_1.1](XCRI_Terms_1.1.html "XCRI Terms 1.1")
vocabulary encoding scheme is recommended.


#### Inheritable property values

Some elements may be inferred from their presence in a containing
resource when not present in child objects. Specifically:

1.  Where a [presentation](Presentation.html "Presentation") does not
    contain a [venue](Venue.html "Venue"), an Aggregator SHOULD assume
    that the venue details ([name](Name.html "Name"),
    [address](Address.html "Address"), [email](Email.html "Email"),
    [fax](Fax.html "Fax"), [phone](Phone.html "Phone"),
    [url](Url.html "Url"), [image](Image.html "Image")) are exactly the
    same as the properties of the [provider](Provider.html "Provider").
    An Aggregator MAY assume that the
    [description](Description.html "Description") is the same as that of
    the [provider](Provider.html "Provider").
2.  Where a [course](Course.html "Course") does not contain an
    [image](Image.html "Image"), but its containing
    [provider](Provider.html "Provider") does, an Aggregator MAY use the
    image of the [provider](Provider.html "Provider") when displaying
    the [course](Course.html "Course").
3.  Where a [presentation](Presentation.html "Presentation") does not
    contain an [applyTo](ApplyTo.html "ApplyTo") property, or a
    [qualification](Qualification.html "Qualification") does not contain
    an [awardedBy](AwardedBy.html "AwardedBy") and/or
    [accreditedBy](AccreditedBy.html "AccreditedBy") property, an
    aggregator SHOULD interpret this as meaning the capability is
    provided by the [provider](Provider.html "Provider") and use its
    contact information.

This enables XCRI documents to be less verbose by not repeating basic
information.


### Extensions

You can extend XCRI-CAP in a number of ways; check out the [Extending
XCRI-CAP](Extending_XCRI-CAP.html "Extending XCRI-CAP") guidelines.


### XML Binding

The following schemas are available:

-   [XCRI-CAP XML
    Schema](XCRI-CAP_XML_Schema.html "XCRI-CAP XML Schema")


Examples
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------


Similar work
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The following have a similar scope:

-   The Course Description Metadata (CDM) proposal of Norway LINK
-   The Internet2 MACE work LINK
-   [The Course-Catalog
    microformat](http://microformats.org/wiki/course-catalog "http://microformats.org/wiki/course-catalog")

The following have inspired the specification approach:

-   The Atom Syndication Format LINK
-   The [Dublin Core Abstract
    Model](http://www.dublincore.org/documents/abstract-model/ "http://www.dublincore.org/documents/abstract-model/")