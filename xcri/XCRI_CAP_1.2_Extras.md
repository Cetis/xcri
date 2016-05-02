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

XCRI CAP 1.2 Extras 
===================

This document contains various "bits n pieces" that aren't included in
the final specification document

### Design Goals and Requirements

*This section is non-normative*

The design goals and requirements for this specification are documented
in the [XCRI 1.2
Requirements](XCRI_1.2_Requirements.html "XCRI 1.2 Requirements")
document.

The specification meets the following requirements as identified in
[XCRI 1.2
Requirements](XCRI_1.2_Requirements.html "XCRI 1.2 Requirements"):

R1 Conform to the European Norm for Metadata for Learning Opportunities
:   See section on MLO Conformance

R2 Support Online Application Links
:   This is implemented using the &lt;applyTo&gt; element

R3 Support Higher Ambitions
:   TBC

R4 Flexible date handling
:   See notes on *temporal elements*

R5 Different provider types
:   This is implemented using the &lt;type&gt; element

R6 Link to Ofsted
:   This is implemented using the &lt;ofstedUrl&gt; refinement in [XCRI
    Terms 1.2](XCRI_Terms_1.2.html "XCRI Terms 1.2")

R7 Short description for list views
:   This is implemented using the &lt;abstract&gt; refinement in [XCRI
    Terms 1.2](XCRI_Terms_1.2.html "XCRI Terms 1.2")

R8 Age range
:   This is implemented using the &lt;age&gt; element.


### Implementation Patterns

*This section is non-normative*

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

The basic mode of operation for XCRI is for organisations to create a
feed of course information, consisting of an XML document that contains
their provider details, including the courses they offer.

An Aggregator or a broker can then download a number of feeds and
collate them to enable cross-searching or other capabilities.

[![Image:Model.png](../images/7/79/Model.png){width="259"
height="279"}](Image%253AModel.png "Image:Model.png")

XCRI-CAP supports two main implementation patterns:

-   In the [simple aggregation
    pattern](Simple_aggregation_pattern.html "Simple aggregation pattern"),
    each provider offers its feed as an XML file that can be
    periodically downloaded by an Aggregator. The Aggregator replaces
    any previous information about the
    [provider](Provider.html "Provider") and their courses with the
    latest data.
-   the [delta update
    pattern](Delta_update_pattern.html "Delta update pattern") follows
    the same pattern as the Open Archives Protocol for Metadata
    Harvesting (OAI-PMH). In this pattern, each provider offers an API
    where Aggregators can obtain an XML catalog file containing
    information about changes since a specified date.

For Aggregators, there are also patterns for discovering XCRI feeds:

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


Extensions
=====================================================================================================================================================================================

*This section is non-normative*

You can extend XCRI-CAP in a number of ways; check out the [Extending
XCRI-CAP](Extending_XCRI-CAP.html "Extending XCRI-CAP") guidelines.


Vocabularies
=========================================================================================================================================================================================

*This section is non-normative*

Use of the [XCRI\_Terms\_1.2](XCRI_Terms_1.2.html "XCRI Terms 1.2")
vocabulary encoding scheme is recommended.



Changes from V1.1
===================================================================================================================================================================================================

*This section is non-normative*

The following changes have been made in v1.2 of XCRI-CAP

1.  Added Contributor, Date, and Type properties to Catalog, Provider,
    Course and Presentation
2.  Replaced Relation with HasPart
3.  RelationDType redefined as supporting association both by reference
    and inclusion
4.  Modified Venue property of a Presentation to contain a Provider
    instance for the venue Location
5.  Added Location property to Provider, containing the information
    previously supplied in OrganisationDType
6.  Replaced Credit with a very similar model taken from CEN
7.  Added Objective to XCRI Terms
8.  Added level to course
9.  Added engagement to replace studyMode etc
10. Removed @recstatus (now a separate spec)
11. Removed entryProfile and entryRequirements: now uses Prerequisite,
    plus parked separate spec for structured entry requirements
12. Added age
13. Added Abstract to XCRI Terms
14. Added url to location




Editor's NoteThis image is now out of date:



The changes are summarised in the following information model:

[![Image:XCRI CAP 1 2.png](../images/4/44/XCRI_CAP_1_2.png)](Image%253AXCRI_CAP_1_2.png "Image:XCRI CAP 1 2.png")

