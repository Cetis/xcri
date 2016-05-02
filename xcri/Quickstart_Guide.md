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

Quickstart Guide 
================


Getting started with XCRI for education providers
================================================================================================================================================================================================================================================================

To advertise your courses with XCRI:

1\. Check your readiness using the [XCRI Implementation Model (XIM)
report](http://www.jisc.ac.uk/media/documents/programmes/elearningcapital/ximfinalreport.pdf "http://www.jisc.ac.uk/media/documents/programmes/elearningcapital/ximfinalreport.pdf"){.external
.text} and see the [two page guide to implementing
XCRI-CAP](http://www.alanpaull.co.uk/xim/docs/xcritwopageguide.pdf "http://www.alanpaull.co.uk/xim/docs/xcritwopageguide.pdf"){.external
.text}.

2\. Get the XML schema; you can download it from the [tools
page](http://www.xcri.org/Tools.html "http://www.xcri.org/Tools.html"){.external
.text}

3\. Check out what other providers have done by reading their [Project
Reports](Project_Reports.html "Project Reports")

4\. Implement XCRI in whatever fashion makes sense.

-   The simplest method is to write a script that turns your course data
    into XML using the schema (detailed information about the fields is
    available on this wiki) and publishes it on your website. You can
    use a tool such as cron to make this happen reguarly (e.g. every
    week), or trigger it to run based on database changes.
-   There are some [implementation
    patterns](Category%253AImplementation_patterns.html "Category:Implementation patterns")
    described on this wiki that can help.
-   If you need help, post a message on the
    [forum](http://www.xcri.org/forum "http://www.xcri.org/forum")

5\. Check your feed with the online validator (coming soon!)

6\. Submit your URL to the [XCRI
aggregator](http://www.xcri.org/aggregator "http://www.xcri.org/aggregator"){.external
.text} to check it looks how you expect

7\. Tell aggregators such as UCAS, HotCourses, 14-19 prospectus sites and
LLNs about your new course feed. (Not all are ready to use them, but
notifying them lets them know that data is available if they enable XCRI
harvesting)