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
Sample XSLT code for transforming XCRI CAP 1.1 into HTML web pages 
==================================================================


These code samples take an XCRI CAP 1.1 source document and transform it
into two separate sections of HTML, which could be included in a course
listings page (with links); and a course details page, with a table of
presentations on offer. The
[XSLT](http://www.w3.org/standards/xml/transformation "http://www.w3.org/standards/xml/transformation")(extensible style language transform) code is not intended to
show best practice, but rather to give an indication of what is
possible, and to work on a low-specification XML processor. You should
check that the HTML output is valid, and suppress the XML declaration
and namespaces if possible.

The idea would be to populate your website by automatically generating
the CAP XML as a feed from your database and saving it to your web
server, say on an overnight schedule. This static XML file could then be
transformed by XSLT stylesheets like the samples below.


XCRI CAP 1.1 input
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

We will start with the sample CAP 1.1 output from [Sample SQL Server
2005 code for generating XCRI XML from a simplified relational course
database](Sample_SQL_Server_2005_code_for_generating_XCRI_XML_from_a_simplified_relational_course_database.html "Sample SQL Server 2005 code for generating XCRI XML from a simplified relational course database").

    
    
	<?xml version="1.0" encoding="UTF-8"?>
	<catalog xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms" generated="2010-03-13T00:35:48.240" xsi:schemaLocation="http://xcri.org/profiles/catalog/terms http://www.xcri.org/bindings/xcri_cap_terms_1_1.xsd">
	<provider xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms">
		<identifier>0000X00XX0</identifier>
		<title>Acme University</title>
		<course xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms">
			<identifier>BSCAN</identifier>
			<title>BSc Applied Networking Technologies</title>
			<subject>Information Technology and Information</subject>
			<description xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms" xsi:type="xcriTerms:aim">
				<div xmlns="http://www.w3.org/1999/xhtml">
					<p>Industry analysts are currently predicting a shortfall of trained networking staff with a Business knowledge.  Building on from our HND this course is designed to equip students with the very latest skills and qualities that they will need to succeed in the vibrant IT orientated world.  You will develop specialist skills in security technologies and techniques and in particular the use of intrusion techniques and penetration testing as methods of determining the robustness of IT security.</p>
				</div>
			</description>
			<qualification>
				<title>BSc</title>
				<level>9</level>
			</qualification>
			<presentation xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms">
				<identifier>2008/2009/BSCAN/F1/BK/08</identifier>
				<start>2008-09-01T00:00:00</start>
				<studyMode>Full Time</studyMode>
			</presentation>
			<presentation xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms">
				<identifier>2008/2009/BSCAN/I1/BK/08</identifier>
				<start>2008-09-01T00:00:00</start>
				<studyMode>Part Time Day</studyMode>
			</presentation>
		</course>
		<course xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms">
			<identifier>UWBKW</identifier>
			<title>Underwater Basketweaving</title>
			<subject>Unreal crafts</subject>
			<description xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms" xsi:type="xcriTerms:aim">
				<div xmlns="http://www.w3.org/1999/xhtml">
					<p>Learn this traditional craft, using quality local materials, in the comfort of a swimming pool.</p>
					<p>Full snorkelling kit and reed thimbles are provided.</p>
				</div>
			</description>
			<qualification>
				<title />
				<level>0</level>
			</qualification>
			<presentation xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms">
				<identifier>2008/2009/UWBKW/X1/08</identifier>
				<start>2008-04-01T00:00:00</start>
				<studyMode>Day</studyMode>
			</presentation>
			<presentation xmlns="http://xcri.org/profiles/catalog" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms">
				<identifier>2008/2009/UWBKW/Y1/08</identifier>
				<start>2008-04-30T00:00:00</start>
				<studyMode>Part Time Day</studyMode>
			</presentation>
		</course>
	</provider>
	</catalog>

        
    


XSLT for course listings
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This XSLT stylesheet finds all subjects, sorts them alphabetically, and
outputs a section of HTML with course titles, wrapped in hyperlinks,
grouped by subject. It is a fairly simple method, and not necessarily
the most efficient (the preceding axis can be processor-intensive).

HTML heading levels are optionally passed in as parameters, or you can
just keep the defaults.

You would likely have to change the URL generated in the hyperlink to
match your site's pattern.

	<?xml version="1.0" encoding="UTF-8"?>
	<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns="http://www.w3.org/1999/xhtml"
	xmlns:dc="http://purl.org/dc/elements/1.1/" xmlns:xhtml="http://www.w3.org/1999/xhtml"
	xmlns:xcri="http://xcri.org/profiles/catalog">
	<xsl:output method="xml" version="1.0" encoding="UTF-8" omit-xml-declaration="yes" indent="yes"/>
	<xsl:param name="headingLevel" select="'h1'"/>
	<xsl:param name="subjectHeadingLevel" select="'h2'"/>
	<xsl:variable name="subjects"
		select="/xcri:catalog/xcri:provider/xcri:course/xcri:subject[not(. = preceding::xcri:subject)]"/>
	<xsl:template match="/">
		<xsl:element name="div">
			<xsl:element name="{$headingLevel}">
				<xsl:text>Courses from </xsl:text>
				<xsl:value-of select="xcri:catalog/xcri:provider/xcri:title"/>
			</xsl:element>
			<xsl:for-each select="$subjects">
				<xsl:sort select="."/>
				<xsl:variable name="thisSubject" select="."/>
				<xsl:element name="{$subjectHeadingLevel}">
					<xsl:value-of select="$thisSubject"/>
				</xsl:element>
				<xsl:element name="ul">
					<xsl:for-each select="/xcri:catalog/xcri:provider/xcri:course[xcri:subject = $thisSubject]">
						<xsl:sort select="title"/>
						<xsl:element name="li">
							<xsl:element name="a">
								<xsl:attribute name="href">
									<xsl:value-of select="concat('/courses(', xcri:identifier, ')')"/>
								</xsl:attribute>
								<xsl:value-of select="xcri:title"/>
							</xsl:element>
						</xsl:element>
					</xsl:for-each>
				</xsl:element>
			</xsl:for-each>
		</xsl:element>
	</xsl:template>
	</xsl:stylesheet>


XSLT for course details page
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This XSLT stylesheet expects to be passed one course identifier as a
parameter.

	<div xmlns="http://www.w3.org/1999/xhtml">
   <h1>BSc Applied Networking Technologies</h1>
   <h2>Aim</h2>
   <div xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms">
      <p>Industry analysts are currently predicting a shortfall of trained networking staff with a Business knowledge.  Building on
         from our HND this course is designed to equip students with the very latest skills and qualities that they will need to succeed
         in the vibrant IT orientated world.  You will develop specialist skills in security technologies and techniques and in particular
         the use of intrusion techniques and penetration testing as methods of determining the robustness of IT security.
      </p>
   </div>
   <table xmlns:xhtml="http://www.w3.org/1999/xhtml" summary="Course offerings by start date and study mode.">
      <caption>List of course presentations</caption>
      <tr>
         <th scope="col">Identifer</th>
         <th scope="col">Start date</th>
         <th scope="col">Study mode</th>
      </tr>
      <tr>
         <td>2008/2009/BSCAN/F1/BK/08</td>
         <td>2008-09-01T00:00:00</td>
         <td>Full Time</td>
      </tr>
      <tr>
         <td>2008/2009/BSCAN/I1/BK/08</td>
         <td>2008-09-01T00:00:00</td>
         <td>Part Time Day</td>
      </tr>
   </table>
	</div>

        
    

This sample HTML output shows the transformation for the parameter
\$course equal to 'BSCAN'.

    
       BSc Applied Networking Technologies
      <div xmlns="http://www.w3.org/1999/xhtml">
   <h1>BSc Applied Networking Technologies</h1>
   <h2>Aim</h2>
   <div xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xhtml="http://www.w3.org/1999/xhtml" xmlns:xcri="http://xcri.org/profiles/catalog" xmlns:xcriTerms="http://xcri.org/profiles/catalog/terms">
      <p>Industry analysts are currently predicting a shortfall of trained networking staff with a Business knowledge.  Building on
         from our HND this course is designed to equip students with the very latest skills and qualities that they will need to succeed
         in the vibrant IT orientated world.  You will develop specialist skills in security technologies and techniques and in particular
         the use of intrusion techniques and penetration testing as methods of determining the robustness of IT security.
      </p>
   </div>
   <table xmlns:xhtml="http://www.w3.org/1999/xhtml" summary="Course offerings by start date and study mode.">
      <caption>List of course presentations</caption>
      <tr>
         <th scope="col">Identifer</th>
         <th scope="col">Start date</th>
         <th scope="col">Study mode</th>
      </tr>
      <tr>
         <td>2008/2009/BSCAN/F1/BK/08</td>
         <td>2008-09-01T00:00:00</td>
         <td>Full Time</td>
      </tr>
      <tr>
         <td>2008/2009/BSCAN/I1/BK/08</td>
         <td>2008-09-01T00:00:00</td>
         <td>Part Time Day</td>
      </tr>
   </table>
	</div>

    


XSLT for course discovery page 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This style sheet produces a section of course listing HTML markup with
paged results and groups of links which refine (filter) the result set.
Note: this sample uses XSLT 2.0 and XPath 2.0 (for efficiency, otherwise
workarounds would make the code more verbose) and is not suitable for
frameworks/XSLT processors which only support XSLT 1.0 or XPath 1.0. The
code was tested with Saxon-HE 9.3.0.4.

The idea is to show the first 20 (or so) courses on a web page,
generating links to further pages and to values of qualifications, study
modes and subjects to allow the user to narrow down their search. It is
expected that the web page server code handles the parameters being
passed back and forth. As a link (say, a specific qualification) is
clicked on, the course subset is regenerated to only return courses with
that qualification. This is a simpler version of the type of search
refinement used by sites such as Amazon.

In practice, the desired course properties used will vary, and depend on
the quality of the data, and whether controlled vocabularies or free
text is used. This approach may be combined with a free text or
controlled vocabulary keyword search.

To keep the number of choices in a property group manageable, a higher
level of grouping may be desirable. This could be provided by a separate
XML document, say grouping subjects hierarchically (to drill down
through them), or by relying on data already in the CAP document, such
as grouping several qualifications together based on level.

    
    
        
        
            
                Created on: 2011-05-22
                Author: Tavis Reddick
                Takes an XCRI CAP 1.1 document and outputs an XHTML section containing results and filtering links.
            
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
            
                
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
                                
                                    
                                        
                                            
                                                
                                                
                                            
                                            
                                        
                                    
                                    
                                    
                                    
                                
                            
                        
                    
                
            
        
    


\[[edit](../index.php@title=Sample_XSLT_code_for_transforming_XCRI_CAP_1.1_into_HTML_web_pages&action=edit&section=5.html "Edit section: Further types of web page")\]  Further types of web page 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

You might also look at populating course subject or department pages
from your XCRI CAP feed. You could also use your feed for course search
purposes.


\[[edit](../index.php@title=Sample_XSLT_code_for_transforming_XCRI_CAP_1.1_into_HTML_web_pages&action=edit&section=6.html "Edit section: Working example")\]  Working example 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

You can see a basic working example (using a feed generated from a SQL
Server 2005 database, with the XSLT transformations handled by ASP.NET)
at [Courses from Kelpie
College](http://www.kelpiecollege.org.uk/courses "http://www.kelpiecollege.org.uk/courses"){.external
.text}, a test site which also introduces a URL Rewriting rule to make
passing the course identifier parameter in a bit friendlier:

> `RewriteRule ^courses\(([A-Za-z0-9]+)\) courses/course/?courseid=$1 [QSA]`

