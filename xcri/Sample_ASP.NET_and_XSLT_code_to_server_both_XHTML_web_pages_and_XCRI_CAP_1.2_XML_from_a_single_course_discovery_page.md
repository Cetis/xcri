---
layout: post
---







Sample ASP.NET and XSLT code to server both XHTML web pages and XCRI CAP 1.2 XML from a single course discovery page 
====================================================================================================================













### From Xcri 







Jump to:
[navigation](Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.html#column-one),
[search](Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.html#searchInput)



We can expand the functionality of the ASP.NET and XSLT course discovery
page from [Sample XSLT and ASP.NET code to create web pages from your
course
feed](Sample_XSLT_and_ASP.NET_code_to_create_web_pages_from_your_course_feed.html "Sample XSLT and ASP.NET code to create web pages from your course feed")
to serve subsets of your XCRI CAP 1.2 feed as well as HTML pages. This
will mean adding a new XSLT stylesheet to produce a subset of the feed
using the same parameters as before (filtered by qualification, study
mode and subject) and optionally restricting the amount of course
information passed through using a new profile parameter. The Visual
Basic.NET code is updated to support the two paths.

+--------------------------------------------------------------------------+
|                                                       |
|                                                                          |
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
|                                                                    |
|                                                                          |
| -   [1 Directory    |
|     structure](Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_ |
| web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.html# |
| Directory_structure)                                                     |
| -   [2 The ASP.NET  |
|     page, save as                                                        |
|     default2.aspx](Sample_ASP.NET_and_XSLT_code_to_server_both_XH |
| TML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.h |
| tml#The_ASP.NET_page.2C_save_as_default2.aspx)                           |
| -   [3 The ASP.NET  |
|     Visual Basic code behind file, save as                               |
|     default2.aspx.vb](Sample_ASP.NET_and_XSLT_code_to_server_both |
| _XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_pag |
| e.html#The_ASP.NET_Visual_Basic_code_behind_file.2C_save_as_default2.asp |
| x.vb)                                                                    |
| -   [4 The XCRI CAP |
|     subsetting XSLT stylesheet, save as                                  |
|     xcricap1p2subset.xslt](Sample_ASP.NET_and_XSLT_code_to_server |
| _both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discover |
| y_page.html#The_XCRI_CAP_subsetting_XSLT_stylesheet.2C_save_as_xcricap1p |
| 2subset.xslt)                                                            |
| -   [5 Sample XCRI  |
|     CAP 1.2                                                              |
|     output](Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web |
| _pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.html#Sam |
| ple_XCRI_CAP_1.2_output)                                                 |
| -   [6 Notes](Sample_ASP.NET_and_XSLT_code_to_server |
| _both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discover |
| y_page.html#Notes)                                                       |
+--------------------------------------------------------------------------+


\[[edit](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&action=edit&section=1.html "Edit section: Directory structure")\]  Directory structure 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The sample website has this structure. The enhanced course discovery
page lives in the /courses directory, and the course details page lives
in the /courses/course subdirectory. The XSLT stylesheets are in
/xml/xsl/t/courses.

-   courses
    -   default2.aspx
    -   default2.aspx.vb
-   xml
    -   xsl
        -   t
            -   courses
                -   xcricap1p2toxhtmlcoursediscovery.xslt
                -   xcricap1p2subset.xslt


\[[edit](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&action=edit&section=2.html "Edit section: The ASP.NET page, save as default2.aspx")\]  The ASP.NET page, save as default2.aspx 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This page is virtually the same as before, although note that the code
behind file is now default2.aspx.vb, it inherits "courses\_default2, and
there is an ASP.NET Label control to write useful feedback to for
testing.

    
    
    
    
        
    
    
      
    


\[[edit](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&action=edit&section=3.html "Edit section: The ASP.NET Visual Basic code behind file, save as default2.aspx.vb")\]  The ASP.NET Visual Basic code behind file, save as default2.aspx.vb 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The code now has conditional branching for two sets of HTTP ACCEPT
values, one requesting a HTML web page, another requesting an XCRI CAP
document.

    Imports System.IO
    Imports System.Xml
    Imports System.Xml.XPath
    Imports System.Xml.Xsl

    Partial Class courses_default2
        Inherits System.Web.UI.Page
        
        Protected Sub Page_Load(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Load
            Const chrSemiColon As Char = ";"c
            Const chrComma As Char = ","c
            Dim strRequestAccepts As String = Request.ServerVariables("HTTP_ACCEPT")
            If Not strRequestAccepts.IndexOf(chrSemiColon) = -1 Then
                strRequestAccepts = strRequestAccepts.Substring(0, strRequestAccepts.IndexOf(chrSemiColon))
            End If
            Dim chrDelimiters() As Char = 
            lblRequest.Text = "Request accepts"
            Dim strRequestAcceptArray As String() = strRequestAccepts.Split(chrDelimiters)
            Dim strRequestAccept
            For Each strRequestAccept In strRequestAcceptArray
                lblRequest.Text &= "" & strRequestAccept
            Next strRequestAccept
            ' Get parameters from query string.
            Dim strQualification As String = Request.QueryString("qualification")
            Dim strStudyMode As String = Request.QueryString("studymode")
            Dim strSubject As String = Request.QueryString("subject")
            Dim strPage As String = Request.QueryString("page")
            Dim strPageSize As String = Request.QueryString("pagesize")
            ' Compile the style sheet.
            Dim xctTransform1 As New XslCompiledTransform()
            ' Choose the transform stylesheet
            Dim strStylesheetUri1 As String
            If strRequestAcceptArray.Contains("text/html") Or strRequestAcceptArray.Contains("application/xhtml+xml") Then
                strStylesheetUri1 = "http://www.kelpiecollege.org.uk/xml/xsl/t/courses/xcricap1p2toxhtmlcoursediscovery.xslt"
            Else If strRequestAcceptArray.Contains("application/xcri-cap+xml")
                strStylesheetUri1 = "http://www.kelpiecollege.org.uk/xml/xsl/t/courses/xcricap1p2subset.xslt"
            End If
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
            ' Transform the XCRI CAP 1.2
            xctTransform1.Transform(strDocumentUri1, argList1, ms1) 
            ' Load the results into an XPathDocument object.
            ms1.Seek(0, SeekOrigin.Begin)
            If strRequestAcceptArray.Contains("text/html") Or strRequestAcceptArray.Contains("application/xhtml+xml") Then 'add the course XHTML to the web page.
                Dim xpnDoc1 As XPathNavigator
                Dim xpdDoc1 As XPathDocument = New XPathDocument(ms1)
                xpnDoc1 = xpdDoc1.CreateNavigator
                xmlCourseList.XPathNavigator = xpnDoc1
            Else If strRequestAcceptArray.Contains("application/xcri-cap+xml") 'replace the web page with an XCRI CAP 1.2 document.
                Dim data As Byte()
                data = ms1.ToArray()
                ms1.Flush()
                ms1.Close()
                HttpContext.Current.Response.Clear()
                HttpContext.Current.Response.ContentType = "application/xcri-cap+xml" 'For testing purposes, you can use "application/xml" below, it will render in web browsers.
                'HttpContext.Current.Response.ContentType = "application/xml"
                HttpContext.Current.Response.AddHeader("Content-Length", data.Length.ToString())
                HttpContext.Current.Response.BinaryWrite(data)
                HttpContext.Current.Response.[End]()
            End If
        End Sub
    End Class

\


\[[edit](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&action=edit&section=4.html "Edit section: The XCRI CAP subsetting XSLT stylesheet, save as xcricap1p2subset.xslt")\]  The XCRI CAP subsetting XSLT stylesheet, save as xcricap1p2subset.xslt 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This XSLT stylesheet uses a similar approach to the
xcricap1p2toxhtmlcoursediscovery.xslt one listed in a previous example.
This time, though, it returns a subset of your XCRI CAP 1.2 course feed.

    
    
        
        
            
                Created on: 2012-04-17
                Author: Tavis Reddick
                Takes an XCRI CAP 1.2 document and filters it on parameters, and returns either a full course profile or some
                    subset like title, URL and abstract only.
            
        
        
        
        
        
        
        
        
        
            
                
                
                
            
        
        
            
                
                
                    
                    
                        
                            
                        
                        
                            
                                
                                
                                
                            
                        
                    
                
            
        
    


\[[edit](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&action=edit&section=5.html "Edit section: Sample XCRI CAP 1.2 output")\]  Sample XCRI CAP 1.2 output 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

If you request the URL with a web browser, you will see a web page,
because the browser tells the page it will accept "text/html" or
"application/xhtml+xml" content types.

For example,

will list all the Full time courses as before. However, if you request a
special "application/xcri-cap+xml" content type (from a custom web
application that is designed to consume XCRI CAP, or a REST-aware
debugging tool) using the same URL, you will get something like this:

    
    
      
        Kelpie College
        
          Conversational Cetacean Harbour Dolphin Dialect
          http://www.kelpiecollege.org.uk/courses(HDLANG)
          Learn to speak the Harbour Dolphin dialect of Cetacean and converse, question and barter with these friendly and helpful creatures.
        
        
          Hive Mind Speak level 1
          http://www.kelpiecollege.org.uk/courses(HLANG1)
          Learn the telepathic Mind Speak of the Hive, and commune humbly with our near-neighbours from the Tenth Planet!
        
      
    

Note that we are using the xcricap1p2subset.xslt style sheet's default
'abstract' profile here, which only returns course title, URL and
abstract (although it is a valid XCRI CAP 1.2 document, and your
application should check this). This would make a nice linked list on a
remote site, for example.


\[[edit](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&action=edit&section=6.html "Edit section: Notes")\]  Notes 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This sample should be treated with the same kind of caution as the other
samples here:

-   Important! In all this code, replace any references to
    "" with your own site domain name,
    or better still fix the code to use a relative address.
-   This is not optimized, production-ready code. In fact, I think
    Microsoft are bringing out a \[[Web API
    framework](http://www.asp.net/web-api "http://www.asp.net/web-api")\] which should make this kind of requirement easier to code.
-   There is no error handling.

--[Tavis](../index.php@title=User%253ATavis&action=edit.html "User:Tavis")
01:18, 18 April 2012 (BST)



Retrieved from
"[http://localhost/Sample\_ASP.NET\_and\_XSLT\_code\_to\_server\_both\_XHTML\_web\_pages\_and\_XCRI\_CAP\_1.2\_XML\_from\_a\_single\_course\_discovery\_page](Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.html)"

















##### Views



-   

    

    [Article](Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.html)
-   

    

    [Discussion](../index.php@title=Talk%253ASample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&action=edit.html)
-   

    

    [Edit](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&action=edit.html)
-   

    

    [History](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&action=history.html)







##### Personal tools



-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.html)











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

    

    [What links
    here](Special%253AWhatlinkshere/Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Sample_ASP.NET_and_XSLT_code_to_server_both_XHTML_web_pages_and_XCRI_CAP_1.2_XML_from_a_single_course_discovery_page&oldid=4383.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 00:18, 18 April 2012.
-   

    

    This page has been accessed 2,795 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




