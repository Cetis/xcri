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







Sample ASP.NET code to take XCRI CAP 1.2 XML from database and publish it as a web feed 
=======================================================================================













### From Xcri 







Jump to:
[navigation](Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed.html#column-one),
[search](Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed.html#searchInput)



Having got your XCRI CAP 1.2 XML generated from your database (see
[Sample SQL Server 2008 code for extracting XCRI CAP 1.2 XML from a
relational
database](Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html "Sample SQL Server 2008 code for extracting XCRI CAP 1.2 XML from a relational database")),
you will now probably want to publish it on the web. A best practice
could be to set up a scheduled task which extracts the XML, validates
it, and (if passed) writes the XML as a static file to your webserver,
then sends an email notification on the result to your administrators.

However, if you just want to generate a live feed, here is some code
showing a way to do it using a Microsoft ASP.NET web form, using Visual
Basic code.


\[[edit](../index.php@title=Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed&action=edit&section=1.html "Edit section: The ASP.NET page, save as default.aspx")\]  The ASP.NET page, save as default.aspx 
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This is a pretty simple page, which returns a content type of
"application/xml", and holds the XML control that will be filled with
the XCRI CAP 1.2 output.

    
    


\[[edit](../index.php@title=Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed&action=edit&section=2.html "Edit section: The ASP.NET Visual Basic code behind file, save as default.aspx.vb")\]  The ASP.NET Visual Basic code behind file, save as default.aspx.vb 
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

The main work is done in the code behind file, which sits in the same
directory. The connection to your database should be set in your
site/web application's web.config file, and you should replace
"kelpiecollegeConnectionString" with the name of your connection string.
You should also amend the values of the three parameters as necessary
(they will work for the sample set of course data on this wiki).

    Imports System.Configuration
    Imports System.Data
    Imports System.Data.SqlClient
    Imports System.Xml
    Imports System.Xml.XPath

    Partial Class courses_xcri_cap_1p2_default
        Inherits System.Web.UI.Page

        Protected Sub Page_Load(ByVal sender As Object, ByVal e As System.EventArgs) Handles Me.Load
            Dim strSchemaName As String = "XCRI CAP 1.2"
            Dim strProviderIdentifier As String = "0000X00XX0"
            Dim strLanguage As String = "en"

            Try
                'Set up SQL connection and command which returns XCRI XML, using named connection string from web.config file.
                Dim conn As SqlConnection
                conn = New SqlConnection(ConfigurationManager.ConnectionStrings("kelpiecollegeConnectionString").ConnectionString)
                Dim cmd As SqlCommand = New SqlCommand()
                cmd.CommandType = CommandType.StoredProcedure
                cmd.CommandText = "dbo.usp_Course"
                cmd.Connection = conn

                'Add parameters.
                Dim sprSchemaName As SqlParameter = New SqlParameter()
                Dim sprProviderIdentifier As SqlParameter = New SqlParameter()
                Dim sprLanguage As SqlParameter = New SqlParameter()
                sprSchemaName.ParameterName = "@schemaName"
                sprSchemaName.SqlDbType = SqlDbType.NVarChar
                sprSchemaName.Size = 25
                sprSchemaName.Direction = ParameterDirection.Input
                sprSchemaName.Value = strSchemaName
                sprProviderIdentifier.ParameterName = "@providerIdentifier"
                sprProviderIdentifier.SqlDbType = SqlDbType.NVarChar
                sprProviderIdentifier.Size = 25
                sprProviderIdentifier.Direction = ParameterDirection.Input
                sprProviderIdentifier.Value = strProviderIdentifier
                sprLanguage.ParameterName = "@language"
                sprLanguage.SqlDbType = SqlDbType.NVarChar
                sprLanguage.Size = 50
                sprLanguage.Direction = ParameterDirection.Input
                sprLanguage.Value = strLanguage
                cmd.Parameters.Add(sprSchemaName)
                cmd.Parameters.Add(sprProviderIdentifier)
                cmd.Parameters.Add(sprLanguage)

                'Open the connection.
                cmd.Connection.Open()

                'Get the XML from the stored procedure with an XmlReader and put it into the XML control to be passed to the requester.
                Dim xmlr As System.Xml.XmlReader
                xmlr = cmd.ExecuteXmlReader()
                xmlr.Read()
                Dim xpnDoc As New XPathDocument(xmlr)
                xmlCoursesCAP1p2.XPathNavigator = xpnDoc.CreateNavigator()

                'Dispose of command and connection objects.
                cmd.Dispose()
                conn.Dispose()
            Catch ex As Exception
                'Do stuff to handle an exception.
            End Try
        End Sub
    End Class

Now all you need to do is publish these to your website and request the
page. And remember that your webserver account will need EXECUTE
permissions on the stored procedure (dbo.usp\_Course).

You could set up caching on this page to avoid hitting the database
every time.
--[Tavis](../index.php@title=User%253ATavis&action=edit.html "User:Tavis")
22:26, 5 April 2012 (BST)



Retrieved from
"[http://localhost/Sample\_ASP.NET\_code\_to\_take\_XCRI\_CAP\_1.2\_XML\_from\_database\_and\_publish\_it\_as\_a\_web\_feed](Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed.html)"

















##### Views



-   

    

    [Article](Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed.html)
-   

    

    [Discussion](../index.php@title=Talk%253ASample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed&action=edit.html)
-   

    

    [Edit](../index.php@title=Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed&action=edit.html)
-   

    

    [History](../index.php@title=Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed&action=history.html)







##### Personal tools



-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed.html)











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
    here](Special%253AWhatlinkshere/Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Sample_ASP.NET_code_to_take_XCRI_CAP_1.2_XML_from_database_and_publish_it_as_a_web_feed&oldid=4375.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 21:26, 5 April 2012.
-   

    

    This page has been accessed 2,380 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




