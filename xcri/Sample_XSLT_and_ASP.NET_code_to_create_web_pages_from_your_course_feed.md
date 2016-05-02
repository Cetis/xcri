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







Sample XSLT and ASP.NET code to create web pages from your course feed 
======================================================================













### From Xcri 







Jump to:
[navigation](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed.html#column-one),
[search](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed.html#searchInput)



Once you have your XCRI CAP 1.2 course feed, you may well want to
populate your website with pages generated from the XML.

Here is a set of ASP.NET web form and VB.NET program code, and XSLT
stylesheets which create:

1 a course details page, with a formatted URL; 2 a course discovery
page, with refinement links and paging.

The version of ASP.NET tested was 4.0, although most of the code should
work in other versions. I am using the [Sample ASP.NET code to take XCRI
CAP 1.2 XML from database and publish it as a web
feed](Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed.html "Sample ASP.NET code to take XCRI CAP 1.2 XML from database and publish it as a web feed")
example.

+--------------------------------------------------------------------------+
|                                                       |
|                                                                          |
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
|                                                                    |
|                                                                          |
| -   [1 Directory    |
|     structure](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_f |
| rom_your_course_feed.html#Directory_structure)                           |
| -   [2 Site master  |
|     page](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_y |
| our_course_feed.html#Site_master_page)                                   |
| -   [3 Course       |
|     details                                                              |
|     page](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_y |
| our_course_feed.html#Course_details_page)                                |
| -   [4 Course       |
|     details                                                              |
|     XSLT](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_y |
| our_course_feed.html#Course_details_XSLT)                                |
| -   [5 URL routing  |
|     with                                                                 |
|     Global.asax](Sample_XSLT_and_ASP.NET_code_to_create_web_pages |
| _from_your_course_feed.html#URL_routing_with_Global.asax)                |
| -   [6 Course       |
|     discovery                                                            |
|     page](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_y |
| our_course_feed.html#Course_discovery_page)                              |
| -   [7 Course       |
|     discovery                                                            |
|     XSLT](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_y |
| our_course_feed.html#Course_discovery_XSLT)                              |
| -   [8 Notes](Sample_XSLT_and_ASP.NET_code_to_create |
| _web_pages_from_your_course_feed.html#Notes)                             |
| -   [9 Summary](Sample_XSLT_and_ASP.NET_code_to_crea |
| te_web_pages_from_your_course_feed.html#Summary)                         |
+--------------------------------------------------------------------------+


\[[edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit&section=1.html "Edit section: Directory structure")\]  Directory structure 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The sample website has three files in the root directory: the master
file, its code behind VB.NET file, and Global.asax. The course discovery
page lives in the /courses directory, and the course details page lives
in the /courses/course subdirectory. The XSLT stylesheets for each page
are safely tucked away in /xml/xsl/t/courses.

-   courses
    -   course
        -   default.aspx
        -   default.aspx.vb
    -   default.aspx
    -   default.aspx.vb
-   kelpiecollege.master
-   kelpiecollege.master.vb
-   Global.asax
-   xml
    -   xsl
        -   t
            -   courses
                -   xcricap1p2toxhtmlcoursediscovery.xslt
                -   xcricap1p2toxhtmldetails.xslt


\[[edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit&section=2.html "Edit section: Site master page")\]  Site master page 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

You can use whatever site master page you want. The important thing for
this demonstration is that it has the following placeholders, the first
in the head and the following two in the body:

        
        
        
        
        
        
        


\[[edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit&section=3.html "Edit section: Course details page")\]  Course details page 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The course details page will be an ASP.NET web form located in this test
website at /courses/course/default.aspx (if "default.aspx" is set as one
of your directory document file names, you can access the page simply by
/courses/course). Here's the ASP.NET markup:

    
    
    
    
    
    
      
    

The common page elements and links to CSS files and so on are created by
the master page (see above, saved in the site root as
kelpiecollege.master). The distinctive content, taken from your XCRI CAP
1.2 feed, will replace the asp.Xml control. This is done using the
VisualBasic.NET code behind file, located in the same directory at
/courses/course/default.aspx.vb, here's its code:

    Imports System
    Imports System.IO
    Imports System.Xml
    Imports System.Xml.XPath
    Imports System.Xml.Xsl
    Partial Class courses_course_default
        Inherits System.Web.UI.Page
        
        Protected Sub Page_Load(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Load
            Dim strPageTitle As String
            'Construct the course identifier from the query string parameter.
            Dim strCourse As String = "http://kelpiecollege.org.uk/courses(" & Convert.ToString(Page.RouteData.Values("courseid")) & ")"
            ' Compile the style sheet.
            Dim xctTransform1 As New XslCompiledTransform()
            ' Choose the transform stylesheet
            Dim strStylesheetUri1 As String = "http://www.kelpiecollege.org.uk/xml/xsl/t/courses/xcricap1p2toxhtmldetails.xslt"
            ' Choose the source XML document.
            Dim strDocumentUri1 As String = "http://www.kelpiecollege.org.uk/courses/xcri/cap/1.2"
            xctTransform1.Load(strStylesheetUri1)
            ' Create the XsltArgumentList.
            Dim argList1 As XsltArgumentList = New XsltArgumentList()
            ' Add parameters
            argList1.AddParam("course", "", strCourse)
            ' Create a memory stream to carry the output of the transformation.
            Dim ms1 As MemoryStream = New MemoryStream()
            ' Transform the RDF to QTI Lite
            xctTransform1.Transform(strDocumentUri1, argList1, ms1)
            ' Load the results into an XPathDocument object.
            ms1.Seek(0, SeekOrigin.Begin)
            Dim xpdDoc1 As XPathDocument = New XPathDocument(ms1)
            Dim xpnDoc1 As XPathNavigator
            xpnDoc1 = xpdDoc1.CreateNavigator
            xmlCourseDetails.XPathNavigator = xpnDoc1
            ' Set the page title to the course title.
            ' Add the namespace.
            Dim nsmgr As New XmlNamespaceManager(xpnDoc1.NameTable)
            nsmgr.AddNamespace("xhtml", "http://www.w3.org/1999/xhtml")
            strPageTitle = xpnDoc1.SelectSingleNode("/xhtml:div/xhtml:h1", nsmgr).Value
            Page.Title = strPageTitle
        End Sub
    End Class

What this code does (after the usual stuff) when the page loads is:

1 gets the all-important course identifier from the URL, using routing
as explained below; 2 transforms the XCRI CAP 1.2 feed into a section of
XHTML using an XSLT stylesheet, to which is passed a course identifier
parameter; 3 puts this XHTML into the page, replacing the asp:Xml
control; 4 gets the course title and puts it into the web page title.


\[[edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit&section=4.html "Edit section: Course details XSLT")\]  Course details XSLT 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The transformation above uses an XSLT stylesheet, and here's its code:

    
    
        
        
            
                Created on: 2012-04-08
                Author: Tavis Reddick
                Takes an XCRI CAP 1.2 document and outputs an XHTML course details section, selected by course identifier
                    parameter.
                This work is licensed under the Creative Commons Attribution 3.0 Unported License. To view a copy of this license, visit http://creativecommons.org/licenses/by/3.0/ or send a letter to Creative Commons, 444 Castro Street, Suite 900, Mountain View, California, 94041, USA.
            
        
        
        
            
                
            
        
        
            
                
                    
                     
                    
                
                
                    Topic
                
                
                
                    Career outcome
                
                
                
                    
                        List of course presentations
                        
                            Start date
                            End date
                            Study mode
                        
                        
                            
                                
                                
                                
                            
                        
                    
                
            
        
        
        
            
    

The result should look something like this:

[![Image:Kelpiecollegecourses03.png](http://localhost/wiki/images/a/a4/Kelpiecollegecourses03.png){width="626"
height="451"}](Image%253AKelpiecollegecourses03.png "Image:Kelpiecollegecourses03.png")


\[[edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit&section=5.html "Edit section: URL routing with Global.asax")\]  URL routing with Global.asax 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

We would like the URLs of our course details page to follow the format:

     /courses(XYZ)

where "XYZ" is an internal database identifier (actually in our sample
database our id is a URI, but the "XYZ" part is the only part that
changes).

There are a number of ways of achieving this, but a fairly simple one in
ASP.NET 4.0 is to use URL routing in the Global.asax file, like so (only
the relevant sections of code are shown):

    
    
    
      Sub Application_Start(ByVal sender As Object, ByVal e As EventArgs)
        RegisterRoutes(RouteTable.Routes)
      End Sub
      Shared Sub RegisterRoutes(routes As RouteCollection)
          routes.MapPageRoute("",
              "courses()",
              "~/courses/course/default.aspx")
      End Sub
    


\[[edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit&section=6.html "Edit section: Course discovery page")\]  Course discovery page 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The course discovery page (located here at /courses/default.aspx) first
lists all courses in a table with a list of refinement or filtering
links beside it. These links when clicked pass parameters through the
page into the XSLT stylesheet, and filter the results accordingly.
Here's the ASP.NET markup, it's very similar to the course details page
(you will want to set debug to false in a live website, of course):

    
    
    
    
    
    
      
    

and here is the VB.NET code behind that does more work and calls the
XSLT with parameters:

    Imports System.IO
    Imports System.Xml
    Imports System.Xml.XPath
    Imports System.Xml.Xsl

    Partial Class courses_default
        Inherits System.Web.UI.Page
        
        Protected Sub Page_Load(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Load
            ' Get parameters from query string.
            Dim strQualification As String = Request.QueryString("qualification")
            Dim strStudyMode As String = Request.QueryString("studymode")
            Dim strSubject As String = Request.QueryString("subject")
            Dim strPage As String = Request.QueryString("page")
            Dim strPageSize As String = Request.QueryString("pagesize")
            ' Compile the style sheet.
            Dim xctTransform1 As New XslCompiledTransform()
            ' Choose the transform stylesheet
            Dim strStylesheetUri1 As String = "http://www.kelpiecollege.org.uk/xml/xsl/t/courses/xcricap1p2toxhtmlcoursediscovery.xslt"
            ' Choose the source XML document.
            Dim strDocumentUri1 As String = "http://www.kelpiecollege.org.uk/courses/xcri/cap/1.2"
            xctTransform1.Load(strStylesheetUri1)
            
            ' Create the XsltArgumentList.
            Dim argList1 As XsltArgumentList = New XsltArgumentList()
            ' Add parameters
            If Not strQualification = "" Then
                argList1.AddParam("qualification", "", strQualification)
            End if
            If Not strStudyMode = "" Then
                argList1.AddParam("studyMode", "", strStudyMode)
            End if
            If Not strSubject = "" Then
                argList1.AddParam("subject", "", strSubject)
            End if
            If Not strPage = "" Then
                argList1.AddParam("page", "", strPage)
            End if
            If Not strPageSize = "" Then
                argList1.AddParam("pageSize", "", strPageSize)
            End if

            ' Create a memory stream to carry the output of the transformation.
            Dim ms1 As MemoryStream = New MemoryStream()
            ' Transform the XCRI CAP 1.2 to XHTML
            xctTransform1.Transform(strDocumentUri1, argList1, ms1)
            
            ' Load the results into an XPathDocument object.
            ms1.Seek(0, SeekOrigin.Begin)
            Dim xpdDoc1 As XPathDocument = New XPathDocument(ms1)
            
            Dim xpnDoc1 As XPathNavigator
            xpnDoc1 = xpdDoc1.CreateNavigator
            xmlCourseList.XPathNavigator = xpnDoc1
        End Sub
    End Class


\[[edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit&section=7.html "Edit section: Course discovery XSLT")\]  Course discovery XSLT 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This stylesheet renders a table of courses, the columns taken from XCRI
CAP 1.2 course and presentation elements; and a list of refinement
links. Here's the code:

    
    
        
        
            
                Created on: 2012-04-08
                Author: Tavis Reddick
                Takes an XCRI CAP 1.2 document and outputs an XHTML section containing results and filtering links.
                Based on an earlier (2011-05-22) XCRI CAP 1.1 version, but moved from XPath 2.0 to 1.0 for greater
                    compatibility with older frameworks.
                This work is licensed under the Creative Commons Attribution 3.0 Unported License. To view a copy of this license, visit http://creativecommons.org/licenses/by/3.0/ or send a letter to Creative Commons, 444 Castro Street, Suite 900, Mountain View, California, 94041, USA.
            
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
            
                
                    Courses from 
                    
                
                
                
                    
                    Qualifications
                    
                        
                            
                                All qualifications
                            
                            
                                
                                
                                
                                
                            
                        
                    
                    
                    Study Modes
                    
                        
                            
                                All study modes
                            
                            
                                
                                
                                
                                
                            
                        
                    
                    
                    Subjects
                    
                        
                            
                                All subjects
                            
                            
                                
                                
                                
                                
                            
                        
                    
                
                
                
                Page: 
                
                    
                        
                            
                                
                            
                            
                                
                            
                        
                    
                
                
                
                    
                        Course
                        Qualification
                        Subject
                        Study modes
                    
                    
                        
                            
                             $pageSize * ($page - 1) and position() 
                                
                                    
                                        
                                            
                                                
                                                
                                            
                                            
                                        
                                    
                                    
                                    
                                    
                                
                            
                        
                    
                
            
        
    

When you first visit the web page, it will look something like this:

[![Image:Kelpiecollegecourses01.png](http://localhost/wiki/images/e/ec/Kelpiecollegecourses01.png){width="780"
height="454"}](Image%253AKelpiecollegecourses01.png "Image:Kelpiecollegecourses01.png")

and then when you click on a link (here, the subject link "interspecies
linguistics") to filter your selection (hardly needed in this example
with 5 courses, but helpful when you have hundreds), you get a subset,
like so:

[![Image:Kelpiecollegecourses02.png](http://localhost/wiki/images/c/cc/Kelpiecollegecourses02.png){width="738"
height="392"}](Image%253AKelpiecollegecourses02.png "Image:Kelpiecollegecourses02.png")


\[[edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit&section=8.html "Edit section: Notes")\]  Notes 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   Important! In all this code, replace any references to
    "" with your own site domain name,
    or better still fix the code to use a relative address.
-   This is not optimized, production-ready code.
-   There is no error handling.
-   This method leaves an unwanted XML declaration stuck in middle of
    web page.
-   This example uses some titles instead of identifiers for parameters.
    One great thing about XCRI CAP vocabularies is that you will be able
    to pass short tokens like 'FT' in URLs instead of long,
    URL-encoded labels.
-   CSS styles are not included. You could really improve the display by
    adding design flair, colour, icons and so on.
-   Text search is not included. You might want to incorporate search
    into your discovery solution, by providing a text input and passing
    that as a parameter too.


\[[edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit&section=9.html "Edit section: Summary")\]  Summary 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This sample set of working code builds a small, test website using
ASP.NET 4.0 and XSLT, and an XCRI CAP 1.2 XML feed, to create a course
discovery web page on which users can read and filter a list of courses,
and then click through to a course details page, also created here in
code.

If you have any comments, please use the [XCRI
forum](http://www.xcri.org/forum/ "http://www.xcri.org/forum/"){.external
.text}.
--[Tavis](../index.php@title=User%253ATavis&action=edit.html "User:Tavis")
22:10, 11 April 2012 (BST)



Retrieved from
"[http://localhost/Sample\_XSLT\_and\_ASP.NET\_code\_to\_create\_web\_pages\_from\_your\_course\_feed](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed.html)"

















##### Views



-   

    

    [Article](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed.html)
-   

    

    [Discussion](../index.php@title=Talk%253ASample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit.html)
-   

    

    [Edit](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=edit.html)
-   

    

    [History](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&action=history.html)







##### Personal tools



-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed.html)











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

    

    [What links
    here](Special%253AWhatlinkshere/Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed&oldid=4381.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 23:52, 11 April 2012.
-   

    

    This page has been accessed 7,596 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




