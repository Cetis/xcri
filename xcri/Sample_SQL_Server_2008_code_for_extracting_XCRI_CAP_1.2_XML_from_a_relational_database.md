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







Sample SQL Server 2008 code for extracting XCRI CAP 1.2 XML from a relational database 
======================================================================================













### From Xcri 







Jump to:
[navigation](Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html#column-one),
[search](Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html#searchInput)



Modern relational databases tend to have good XML support, so it should
be possible to extract XCRI CAP 1.2 from them using SQL. This is true
for Microsoft SQL Server 2008, and here is some code that will do just
that.

This example uses the sample database built in [Sample SQL Server 2008
code for building an XCRI-CAP-1.2-compatible relational
database](Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database.html "Sample SQL Server 2008 code for building an XCRI-CAP-1.2-compatible relational database")
and populated in [Populating the sample SQL Server 2008
XCRI-CAP-1.2-compatible relational
database](Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database.html "Populating the sample SQL Server 2008 XCRI-CAP-1.2-compatible relational database"),
so if you want to run the code, follow those steps first.

\


\[[edit](../index.php@title=Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database&action=edit&section=1.html "Edit section: A function to build course description elements")\]  A function to build course description elements 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

To save on some repetitive and slightly tricky code, here is a function
which is used to build the description elements which are described in
[XCRI Terms
1.2](http://www.xcri.org/XCRI_Terms_1.2 "http://www.xcri.org/XCRI_Terms_1.2"){.external
.text}.

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    -- =============================================
    -- Author:      Tavis Reddick
    -- Create date: 2012-03-28
    -- Modified:    2012-03-31
    -- Description: For an instance of a course, a particular type of description in a specified language, returns an XCRI CAP description element.
    -- =============================================
    CREATE FUNCTION [dbo].[udf_XcriCapDescription] 
    (
        -- Add the parameters for the function here
        @CourseId dbo.URI,
        @LanguageId NVARCHAR(50),
        @TermId dbo.URI,
        @VocabularyId dbo.URI
    )
    RETURNS XML
    AS
    BEGIN
        -- The return variable is XML
        DECLARE @Result XML;
        WITH XMLNAMESPACES (
            'http://xcri.org/profiles/1.2/catalog/terms' AS xcriTerms,
            'http://purl.org/dc/terms/' AS dcterms,
            'http://www.w3.org/1999/xhtml' AS xhtml, 
            'http://www.w3.org/2001/XMLSchema-instance' AS xsi,
            DEFAULT 'http://xcri.org/profiles/1.2/catalog')

        -- Add the T-SQL statements to compute the return value here
        SELECT @Result = 
            (
                SELECT 'xcriTerms:' + @TermId AS 'dcterms:description/@xsi:type'
                    ,Text AS 'dcterms:description'
                FROM dbo.Course
                    INNER JOIN
                        dbo.CourseDescription
                            ON Course.CourseId = CourseDescription.CourseId
                WHERE Course.CourseId = @CourseId
                    AND CourseDescription.LanguageId = @LanguageId
                    AND CourseDescription.TermId = @TermId
                    AND CourseDescription.VocabularyId = @VocabularyId
                FOR XML PATH(''), TYPE
            )
        -- Return the result of the function
        RETURN @Result
    /*
    --Test
    SELECT dbo.udf_XcriCapDescription('http://kelpiecollege.org.uk/courses(HDLANG)',
        'en',
        'careerOutcome',
        'http://xcri.org/profiles/catalog/terms')
    */
    /*
    --Expected result
    
      
        After picking up a smattering of Cetacean: Harbour Dolphin dialect, you could be on your way to a career as:
        
          dolphin gopher;
          harbourmaster's assistant.
        
      
    
    */
    END
    GO


\[[edit](../index.php@title=Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database&action=edit&section=2.html "Edit section: A stored procedure to return XCRI CAP 1.2 XML")\]  A stored procedure to return XCRI CAP 1.2 XML 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This stored procedure builds a fairly comprehensive XCRI CAP 1.2
document from the sample database. It validates against the schema, but
it does not (yet) pass all the tests at Craig Hawker's [XCRI-CAP 1.2
Online
Validator](http://validator.xcri.co.uk/ "http://validator.xcri.co.uk/"){.external
.text}, so more work will be need for that.

The procedure calls on the function (above); apart from that, it relies
on FOR XML PATH for the main structure building.

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    -- =============================================
    -- Author:      Tavis Reddick
    -- Create date: 2012-03-25 to 2012-03-31
    -- Description: Extracts course data in XCRI CAP 1.2 XML format.
    -- Licence: This work is licensed under the Creative Commons Attribution 3.0 Unported License.
    -- To view a copy of this license, visit http://creativecommons.org/licenses/by/3.0/ or send a
    -- letter to Creative Commons, 171 Second Street, Suite 300, San Francisco, California, 94105, USA.
    -- =============================================
    CREATE PROCEDURE [dbo].[usp_Course] -- CREATE not ALTER as was the error in original published code, sorry
        -- Add the parameters for the stored procedure here
        @schemaName NVARCHAR(25) = 'XCRI CAP 1.2', -- only 'XCRI CAP 1.2' supported here
        @providerIdentifier NVARCHAR(25) = '0000X00XX0', -- your organizational identifier
        --@providerName NVARCHAR(50) = 'Acme University', -- your organizational name
        @language NVARCHAR(50) = 'en' -- language of text
    AS
    BEGIN
        -- SET NOCOUNT ON added to prevent extra result sets from
        -- interfering with SELECT statements.
        SET NOCOUNT ON;

        -- Insert statements for procedure here
        IF @schemaName = 'XCRI CAP 1.2'
        BEGIN
           -- Build the XCRI CAP 1.2 XML using correlated subqueries with FOR XML PATH.
            WITH XMLNAMESPACES (
                'http://xcri.org/profiles/1.2/catalog/terms' AS xcriTerms,
                'http://purl.org/net/cm' AS credit,
                'http://purl.org/dc/elements/1.1/' AS dc,
                'http://purl.org/dc/terms/' AS dcterms,
                'http://purl.org/net/mlo' AS mlo,
                'http://www.w3.org/1999/xhtml' AS xhtml, 
                'http://www.w3.org/2001/XMLSchema-instance' AS xsi,
                DEFAULT 'http://xcri.org/profiles/1.2/catalog')
                -- Attributes for root catalog element.
                SELECT GETDATE() AS "@generated", 'http://xcri.org/profiles/1.2/catalog http://www.xcri.co.uk/bindings/xcri_cap_1_2.xsd http://xcri.org/profiles/1.2/catalog/terms http://www.xcri.co.uk/bindings/xcri_cap_terms_1_2.xsd' AS "@xsi:schemaLocation",
                    (
                    -- Attributes for child provider element.
                    SELECT @providerIdentifier AS 'dcterms:identifier',
                        Provider.CommonName AS 'dcterms:title',
                        ProviderLocation.Street AS 'mlo:location/mlo:street',
                        ProviderLocation.Town AS 'mlo:location/mlo:town',
                        ProviderLocation.Postcode AS 'mlo:location/mlo:postcode',
                        ProviderLocation.Address AS 'mlo:location/mlo:address',
                        (
                        -- Multiple course elements.
                        SELECT
                            -- Use a function to return each descriptive element.
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'careerOutcome', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'contactHours', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'contactPattern', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'events', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'indicativeResource', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'leadsTo', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'policy', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'providedResource', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'requiredResource', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'specialFeature', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'structure', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'studyHours', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'support', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'teaching Strategy', 'http://xcri.org/profiles/catalog/terms'),
                            dbo.udf_XcriCapDescription(Course.CourseId, @language, 'topic', 'http://xcri.org/profiles/catalog/terms'),
                            Course.CourseId AS 'dc:identifier',
                            -- Multiple subject elements.
                            (
                            SELECT [Subject].TermId AS '@identifier'
                                ,[Subject].Label AS 'text()'
                                FROM dbo.Term AS [Subject]
                                    INNER JOIN
                                        dbo.CourseAttribute
                                            ON CourseAttribute.TermId = [Subject].TermId
                                                AND CourseAttribute.VocabularyId = [Subject].VocabularyId
                            WHERE CourseAttribute.CourseId = Course.CourseId
                                AND CourseAttribute.VocabularyId = 'http://kelpiecollege.org.uk/courses/subjects'
                            FOR XML PATH('dc:subject'), TYPE
                            ),
                            COALESCE(CourseTitle.Prefix + ' ', '') + CourseTitle.MainSort + COALESCE(' ' + CourseTitle.Suffix, '') AS 'dcterms:title',
                            Course.Url AS 'mlo:url',
                            CourseAbstract.Text AS abstract,
                            -- Multiple qualification elements.
                            (
                            SELECT Qualification.Title AS 'mlo:qualification/dc:title',
                                Qualification.EducationLevel AS 'mlo:qualification/dcterms:educationLevel',
                                AwardingBody.CommonName AS 'mlo:qualification/awardedBy',
                                AccreditingBody.CommonName AS 'mlo:qualification/accreditedBy'
                            FROM dbo.Qualification
                                INNER JOIN dbo.CourseQualification
                                    ON Qualification.QualificationId = CourseQualification.QualificationId
                                LEFT OUTER JOIN
                                    dbo.Organization AS AwardingBody ON
                                        AwardingBody.OrganizationId = Qualification.AwardedBy
                                LEFT OUTER JOIN
                                    dbo.Organization AS AccreditingBody ON
                                        AccreditingBody.OrganizationId = Qualification.AccreditedBy
                            WHERE Course.CourseId = CourseQualification.CourseId
                            FOR XML PATH(''), TYPE
                            ),
                            -- Multiple credit elements.
                            (
                            SELECT CourseCredit.CreditSchemeId AS 'mlo:credit/credit:scheme',
                                CourseCredit.CreditId AS 'mlo:credit/credit:level',
                                CourseCredit.Value AS 'mlo:credit/credit:value'
                            FROM dbo.CourseCredit
                            WHERE Course.CourseId = CourseCredit.CourseId
                            FOR XML PATH(''), TYPE
                            ),
                            -- Multiple presentation elements.
                            (
                            SELECT
                                Presentation.PresentationId AS 'dcterms:identifier',
                                Presentation.Start AS 'mlo:start',
                                Presentation.[End] AS 'end',
                                -- Multiple studyMode elements.
                                (
                                SELECT StudyMode.TermId AS '@identifier',
                                    StudyMode.Label AS 'text()'
                                    FROM dbo.Term AS StudyMode
                                        INNER JOIN
                                            dbo.PresentationAttribute
                                                ON PresentationAttribute.TermId = StudyMode.TermId
                                                    AND PresentationAttribute.VocabularyId = StudyMode.VocabularyId
                                WHERE PresentationAttribute.PresentationId = Presentation.PresentationId
                                    AND PresentationAttribute.VocabularyId = 'http://xcri.org/profiles/catalog/1.2/studyMode'
                                FOR XML PATH('studyMode'), TYPE
                                ),
                                -- Multiple attendanceMode elements.
                                (
                                SELECT AttendanceMode.TermId AS '@identifier',
                                    AttendanceMode.Label AS 'text()'
                                    FROM dbo.Term AS AttendanceMode
                                        INNER JOIN
                                            dbo.PresentationAttribute
                                                ON PresentationAttribute.TermId = AttendanceMode.TermId
                                                    AND PresentationAttribute.VocabularyId = AttendanceMode.VocabularyId
                                WHERE PresentationAttribute.PresentationId = Presentation.PresentationId
                                    AND PresentationAttribute.VocabularyId = 'http://xcri.org/profiles/catalog/1.2/attendanceMode'
                                FOR XML PATH('attendanceMode'), TYPE
                                ),
                                -- Multiple attendancePattern elements.
                                (
                                SELECT AttendancePattern.TermId AS '@identifier',
                                    AttendancePattern.Label AS 'text()'
                                    FROM dbo.Term AS AttendancePattern
                                        INNER JOIN
                                            dbo.PresentationAttribute
                                                ON PresentationAttribute.TermId = AttendancePattern.TermId
                                                    AND PresentationAttribute.VocabularyId = AttendancePattern.VocabularyId
                                WHERE PresentationAttribute.PresentationId = Presentation.PresentationId
                                    AND PresentationAttribute.VocabularyId = 'http://xcri.org/profiles/catalog/1.2/attendancePattern'
                                FOR XML PATH('attendancePattern'), TYPE
                                ),
                                Organization.IndustrialId AS 'venue/provider/dc:identifier',
                                Organization.CommonName AS 'venue/provider/dc:title',
                                Location.Street AS 'venue/provider/mlo:location/mlo:street',
                                Location.Town AS 'venue/provider/mlo:location/mlo:town',
                                Location.Postcode AS 'venue/provider/mlo:location/mlo:postcode',
                                Location.Address AS 'venue/provider/mlo:location/mlo:address'
                            FROM dbo.Presentation
                                INNER JOIN
                                    dbo.Course AS PresentationCourse
                                        ON PresentationCourse.CourseId = Presentation.CourseId
                                LEFT OUTER JOIN
                                    dbo.ProviderVenue
                                        ON ProviderVenue.ProviderId = Presentation.ProviderId
                                            AND ProviderVenue.LocationId = Presentation.LocationId
                                LEFT OUTER JOIN
                                    dbo.Location
                                        ON ProviderVenue.LocationId = Location.LocationId
                                LEFT OUTER JOIN
                                    dbo.Organization
                                        ON ProviderVenue.ProviderId = Organization.OrganizationId
                            WHERE PresentationCourse.CourseId = Course.CourseId
                            FOR XML PATH('presentation'), TYPE
                            )
                        FROM dbo.Course
                            LEFT OUTER JOIN
                                dbo.CourseTitle
                                    ON Course.CourseId = CourseTitle.CourseId
                                        AND CourseTitle.LanguageId = @language
                            LEFT OUTER JOIN
                                dbo.CourseAbstract
                                    ON Course.CourseId = CourseAbstract.CourseId
                                        AND CourseAbstract.LanguageId = @language
                        FOR XML PATH('course'), TYPE 
                        )
                    FOR XML PATH('provider'), TYPE
                    )
                FROM dbo.Organization AS Provider
                    LEFT OUTER JOIN
                        dbo.ProviderVenue
                            ON Provider.OrganizationId = ProviderVenue.ProviderId
                    LEFT OUTER JOIN
                        dbo.Location AS ProviderLocation
                            ON ProviderLocation.LocationId = ProviderVenue.LocationId
                WHERE Provider.IndustrialId = @providerIdentifier
                FOR XML PATH('catalog')
        END;
    /*
    --Test
    EXEC dbo.usp_Course
    EXEC dbo.usp_Course @schemaName = 'XCRI CAP 1.2', @providerIdentifier = '0000X00XX0', @language = 'en' 
    */
    END;

Now, when you EXECUTE the stored procedure (try running the
commented-out test statements at the end of the above code), you should
get XCRI-CAP 1.2 output such as below:

    
      
        0000X00XX0
        Kelpie College
        
          
            
              After picking up a smattering of Cetacean: Harbour Dolphin dialect, you could be on your way to a career as:
              
                dolphin gopher;
                harbourmaster's assistant.
              
            
          
          
            
              Harbour dolphins are friendly creatures, excellent guides and reliable marine navigators. They are also very chatty.
              This introductory course will let you confidently:
              
                exchange pleasantries;
                ask for directions;
                barter in the local currency (the all-important commercial fish vocabulary).
              
            
          
          http://kelpiecollege.org.uk/courses(HDLANG)
          interspecies linguistics
          Conversational Cetacean Harbour Dolphin Dialect
          http://www.kelpiecollege.org.uk/courses(HDLANG)
          Learn to speak the Harbour Dolphin dialect of Cetacean and converse, question and barter with these friendly and helpful creatures.
          
            C0918328-1979-E111-99C1-02F3E9FFDFEB
            2012-09-01T00:00:00+01:00
            2013-05-20T00:00:00+01:00
            Flexible
            Campus
            Daytime
            
              
                0000X00XX0/1
                Pict Harbour College
                
                  Port Street
                  Picton
                  PCT1
                
              
            
          
          
            004DA3F4-E579-E111-99C1-02F3E9FFDFEB
            2013-09-01T00:00:00+01:00
            2014-05-20T00:00:00+01:00
            Full time
            Campus
            Daytime
            
              
                0000X00XX0/1
                Pict Harbour College
                
                  Port Street
                  Picton
                  PCT1
                
              
            
          
        
        
          
            
              Even brief contact with the Hive mind may produce mental burnout or enslavement, leading to opportunities as:
              
                a vegetable (crispy);
                a slave (creepy).
              
            
          
          
            
              The Hive are the only sentient species of the Tenth Planet. They have amazing mindsharing abilities, which they use to form one colossal, connected mind.
              They can telepathically communicate with other species as well, and this course will introduce you to Hive Mind Speak. Delivered by our guest Hive lecturer, you will learn:
              
                telepathic communication protocols;
                the lesser and greater obsequies;
                Mind Speak knock-knock jokes.
              
            
          
          http://kelpiecollege.org.uk/courses(HLANG1)
          interspecies linguistics
          Hive Mind Speak level 1
          http://www.kelpiecollege.org.uk/courses(HLANG1)
          Learn the telepathic Mind Speak of the Hive, and commune humbly with our near-neighbours from the Tenth Planet!
          
            20867645-E679-E111-99C1-02F3E9FFDFEB
            2012-09-01T00:00:00+01:00
            2013-05-20T00:00:00+01:00
            Full time
            Campus
            Daytime
            
              
                0000X00XX0/1
                Pict Harbour College
                
                  Port Street
                  Picton
                  PCT1
                
              
            
          
          
            21867645-E679-E111-99C1-02F3E9FFDFEB
            2013-09-01T00:00:00+01:00
            2014-05-20T00:00:00+01:00
            Part of a full time programme
            Campus
            Customised
            
              
                0000X00XX0/1
                Pict Harbour College
                
                  Port Street
                  Picton
                  PCT1
                
              
            
          
        
        
          
            
              On finishing this course the sky is the limit, as you can launch into careers such as:
              
                shuttlesmith;
                shield welder;
                solar panel beater.
              
            
          
          
            
              Traditional metalworking methods come together with cutting edge space technology in this practical course.
              By the end of your studies, you should have launched a working space probe in wrought iron, cast bronze or sheet-hammered tin.
            
          
          http://kelpiecollege.org.uk/courses(HNCMS)
          future industries
          Metalwork and Spacecraft
          http://www.kelpiecollege.org.uk/courses(HNCMS)
          Traditional metalworking methods come together with cutting edge space technology in this practical course.
          
            Highly Notional Certificate
            Kelpie College
            Swampland Qualifications Agency
          
          
            http://example.org/sqa/credit
            3
            60
          
          
            00862458-F87B-E111-8C49-02F3E9FFDFEB
            2012-08-20T00:00:00+01:00
            2013-05-25T00:00:00+01:00
            Campus
            Daytime
            
              
                0000X00XX0/2
                Celt Harbour College
                
                  Harbour Lane
                  Celtville
                  CLT2
                
              
            
          
        
        
          
            
              A career in the shipping lanes of our solar system awaits successful apprentices from this course, such as:
              
                assistant navigator;
                first contact hero/alien food animal.
              
            
          
          
            
              This made-up apprenticeship teaches the basics of navigating between the various bodies of the solar system, using a variety of instruments you will build yourself. Plot your course to make best use of gravity, take parallax readings, and avoid that big shiny thing in the middle.
            
          
          http://kelpiecollege.org.uk/courses(ISN1)
          notional navigation
          Intra-System Navigation level 1
          http://www.kelpiecollege.org.uk/courses(ISN1)
          Learn the art of navigating around the solar system at apprentice level. In a spaceship. Obviously.
          
            Mock Apprenticeship
            Kelpie College
            Swampland Qualifications Agency
          
          
            http://example.org/sqa/credit
            2
            40
          
          
            B0173B78-F87B-E111-8C49-02F3E9FFDFEB
            2012-08-20T00:00:00+01:00
            2014-05-25T00:00:00+01:00
            Campus
            Day/Block release
            
              
                0000X00XX0/3
                The Schooner "Privateering and Slavedriving"
                
                  Celtville
                  CLT2
                  Offshore anchorage, Celt Harbour
                
              
            
          
          
            C03D9D80-F87B-E111-8C49-02F3E9FFDFEB
            2013-08-21T00:00:00+01:00
            2015-05-26T00:00:00+01:00
            Campus
            Daytime
            
              
                0000X00XX0/3
                The Schooner "Privateering and Slavedriving"
                
                  Celtville
                  CLT2
                  Offshore anchorage, Celt Harbour
                
              
            
          
        
        
          
            
              Underwater basketweaver, what else?
            
          
          
            
              Learn this traditional craft, using quality local materials, in the comfort of a swimming pool.
              Full snorkelling kit and reed thimbles are provided.
            
          
          http://kelpiecollege.org.uk/courses(UWBKW)
          unreal crafts
          Underwater Basketweaving
          http://www.kelpiecollege.org.uk/courses(UWBKW)
          Learn the traditional craft of underwater basketweaving, using quality local materials, in the comfort of a swimming pool.
          
            C09780AC-F87B-E111-8C49-02F3E9FFDFEB
            2012-09-01T00:00:00+01:00
            2012-12-15T00:00:00Z
            Campus
            Day/Block release
            
              
                0000X00XX0/4
                The Barque "Acquired Tacking"
                
                  Picton
                  PCT1
                  Berth 4, Pict Harbour
                
              
            
          
          
            90E902B8-F87B-E111-8C49-02F3E9FFDFEB
            2012-09-01T00:00:00+01:00
            2012-12-15T00:00:00Z
            Campus
            Customised
            
              
                0000X00XX0/1
                Pict Harbour College
                
                  Port Street
                  Picton
                  PCT1
                
              
            
          
          
            2061C3D6-F87B-E111-8C49-02F3E9FFDFEB
            2013-01-12T00:00:00Z
            2013-03-26T00:00:00+01:00
            Campus
            Daytime
            
              
                0000X00XX0/2
                Celt Harbour College
                
                  Harbour Lane
                  Celtville
                  CLT2
                
              
            
          
        
      
    

There are still some issues with the design and code, but it is not far
off a complete working solution. The procedure should run quickly, but
has not been tested on a large sample database.

If you have any comments on this, please use the [XCRI
Forum](http://www.xcri.org/forum "http://www.xcri.org/forum"){.external
.text}.
--[Tavis](../index.php@title=User%253ATavis&action=edit.html "User:Tavis")
21:45, 1 April 2012 (BST)



Retrieved from
"[http://localhost/Sample\_SQL\_Server\_2008\_code\_for\_extracting\_XCRI\_CAP\_1.2\_XML\_from\_a\_relational\_database](Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html)"

















##### Views



-   

    

    [Article](Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html)
-   

    

    [Discussion](../index.php@title=Talk%253ASample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database&action=edit.html)
-   

    

    [Edit](../index.php@title=Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database&action=edit.html)
-   

    

    [History](../index.php@title=Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database&action=history.html)







##### Personal tools



-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html)











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
    here](Special%253AWhatlinkshere/Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database&oldid=4369.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 11:57, 2 April 2012.
-   

    

    This page has been accessed 2,063 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




