---
layout: post
---


Sample SQL Server 2005 code for generating XCRI XML from a simplified relational course database 
================================================================================================

Here is some sample SQL for Microsoft SQL Server 2005 that sets up a
simple relational course database, populates it with two courses, each
of which have two programmes, and creates a stored procedure to return a
course feed in XCRI XML.


Create the tables 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[Course](
        [CourseId] [nvarchar](6) NOT NULL,
        [Title] [nvarchar](50) NOT NULL,
        [QualificationName] [nvarchar](50) NULL,
        [QualificationLevel] [tinyint] NULL,
        [Overview] [xml] NULL,
        [SubjectArea] [nvarchar](50) NOT NULL,
     CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED 
    (
        [CourseId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]

    GO

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[Programme](
        [ProgrammeId] [nvarchar](25) NOT NULL,
        [StartDate] [datetime] NOT NULL,
        [EndDate] [datetime] NULL,
        [Venue] [nvarchar](50) NULL,
        [CourseId] [nvarchar](6) NOT NULL,
        [ModeOfAttendance] [nvarchar](50) NOT NULL,
     CONSTRAINT [PK_Programme] PRIMARY KEY CLUSTERED 
    (
        [ProgrammeId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]

    GO
    EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Unique identifier for a programme (an instance of a course).' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'Programme', @level2type=N'COLUMN',@level2name=N'ProgrammeId'
    GO
    ALTER TABLE [dbo].[Programme]  WITH CHECK ADD  CONSTRAINT [FK_Occurence_Course] FOREIGN KEY([CourseId])
    REFERENCES [dbo].[Course] ([CourseId])
    GO
    ALTER TABLE [dbo].[Programme] CHECK CONSTRAINT [FK_Occurence_Course]


Populate the tables with dummy course and programme data 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    INSERT INTO [dbo].[Course]
               ([CourseId]
               ,[Title]
               ,[QualificationName]
               ,[QualificationLevel]
               ,[Overview]
               ,[SubjectArea])
         VALUES
               ('BSCAN'
               ,'Applied Networking Technologies'
               ,'BSc'
               ,9
               ,'Industry analysts are currently predicting a shortfall of trained networking staff with a Business knowledge.  Building on from our HND this course is designed to equip students with the very latest skills and qualities that they will need to succeed in the vibrant IT orientated world.  You will develop specialist skills in security technologies and techniques and in particular the use of intrusion techniques and penetration testing as methods of determining the robustness of IT security.'
               ,'Information Technology and Information')
    GO

    INSERT INTO [dbo].[Course]
               ([CourseId]
               ,[Title]
               ,[QualificationName]
               ,[QualificationLevel]
               ,[Overview]
               ,[SubjectArea])
         VALUES
               ('UWBKW'
               ,'Underwater Basketweaving'
               ,NULL
               ,NULL
               ,'Learn this traditional craft, using quality local materials, in the comfort of a swimming pool.Full snorkelling kit and reed thimbles are provided.'
               ,'Unreal crafts')
    GO

    INSERT INTO [dbo].[Programme]
               ([ProgrammeId]
               ,[StartDate]
               ,[EndDate]
               ,[Venue]
               ,[CourseId]
               ,[ModeOfAttendance])
         VALUES
               ('2008/2009/BSCAN/F1/BK/08'
               ,'2008-09-01 00:00:00'
               ,'2009-05-20 00:00:00'
               ,NULL
               ,'BSCAN'
               ,'Full Time')
    GO

    INSERT INTO [dbo].[Programme]
               ([ProgrammeId]
               ,[StartDate]
               ,[EndDate]
               ,[Venue]
               ,[CourseId]
               ,[ModeOfAttendance])
         VALUES
               ('2008/2009/BSCAN/I1/BK/08'
               ,'2008-09-01 00:00:00'
               ,'2009-05-20 00:00:00'
               ,NULL
               ,'BSCAN'
               ,'Part Time Day')
    GO

    INSERT INTO [dbo].[Programme]
               ([ProgrammeId]
               ,[StartDate]
               ,[EndDate]
               ,[Venue]
               ,[CourseId]
               ,[ModeOfAttendance])
         VALUES
               ('2008/2009/UWBKW/X1/08'
               ,'2008-04-01 00:00:00'
               ,'2008-04-01 00:00:00'
               ,NULL
               ,'UWBKW'
               ,'Day')
    GO

    INSERT INTO [dbo].[Programme]
               ([ProgrammeId]
               ,[StartDate]
               ,[EndDate]
               ,[Venue]
               ,[CourseId]
               ,[ModeOfAttendance])
         VALUES
               ('2008/2009/UWBKW/Y1/08'
               ,'2008-04-30 00:00:00'
               ,'2008-05-06 00:00:00'
               ,NULL
               ,'UWBKW'
               ,'Part Time Day')
    GO


Create stored procedure 
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    -- =============================================
    -- Author:  Tavis Reddick, Adam Smith College
    -- Create date: 2009-08-03
    -- Modified date: 2010-03-13
    -- Description: Returns XCRI course feeds from a greatly simplified course database.
    -- Licence: This work is licensed under the Creative Commons Attribution 3.0 Unported License.
    -- To view a copy of this license, visit http://creativecommons.org/licenses/by/3.0/ or send a
    -- letter to Creative Commons, 171 Second Street, Suite 300, San Francisco, California, 94105, USA.
    -- =============================================
    CREATE PROCEDURE [dbo].[usp_CourseFeed]
        -- Add the parameters for the stored procedure here
        @schemaName NVARCHAR(25) = 'XCRI CAP 1.1', -- in future, add new feed for 'XCRI CAP 1.2'.
        @providerIdentifier NVARCHAR(25) = '0000X00XX0', -- your organizational identifier
        @providerName NVARCHAR(50) = 'Acme University' -- your organizational name
    AS
        -- SET NOCOUNT ON added to prevent extra result sets from
        -- interfering with SELECT statements.
        SET NOCOUNT ON;
        SET CONCAT_NULL_YIELDS_NULL OFF; -- So null values can be concatenated with strings.


    IF @schemaName = 'XCRI CAP 1.0'
        BEGIN
           -- Build the XCRI CAP 1.0 XML using correlated subqueries with FOR XML PATH.
            WITH XMLNAMESPACES ('http://xcri.org/profiles/catalog' AS xcri, 
                'http://www.w3.org/1999/xhtml' AS xhtml,
                'http://purl.org/dc/elements/1.1/' AS dc,
                DEFAULT 'http://xcri.org/profiles/catalog')
            SELECT GETDATE() AS "@generated",
            CAST ((SELECT @providerIdentifier AS identifier, @providerName AS [name],
            CAST ((SELECT CourseId AS identifier, (LTRIM(QualificationName + ' ') + Title) AS title,
                CONVERT(XML, '' + CAST(Overview AS NVARCHAR(4000)) + '') AS [description], -- wrap the Overview XML fragment in a div with the appropriate HTML namespace.
                COALESCE(QualificationName, '') AS "qualification/title", COALESCE(QualificationLevel, 0) AS "qualification/level", -- qualification can't be empty, so use COALESCE to put empty strings or zeroes in if columns contain null values.
                CAST((SELECT ProgrammeId AS identifier, StartDate AS start, ModeOfAttendance AS studyMode
                FROM dbo.Programme AS programme WHERE course.CourseId = programme.CourseId
                FOR XML PATH('presentation'), ELEMENTS) AS XML)
                , SubjectArea AS "dc:subject"
            FROM dbo.Course AS course
            FOR XML PATH ('course')) AS XML)
            FOR XML PATH ('provider')) AS XML)
            FOR XML PATH ('catalog')
        END

    IF @schemaName = 'XCRI Curriculum 1.0'
        BEGIN
           -- Build the XCRI CAP 1.0 XML using correlated subqueries with FOR XML PATH.
            WITH XMLNAMESPACES ('http://elframework.org/curriculum/elements' AS xcri, 
                'http://www.w3.org/1999/xhtml' AS xhtml,
                'http://purl.org/dc/elements/1.1/' AS dc,
                'http://www.imsglobal.org/services/rli/xsd/imsRLIManDataSchema_v1p0' AS imsRLI,
                DEFAULT 'http://elframework.org/curriculum/elements')
            SELECT 'Date/time of data extract' AS  [calendarEvent/dc:title], GETDATE() AS [calendarEvent/dc:date],
            CAST ((SELECT 'course' AS [@type], CourseId AS identifier, (LTRIM(QualificationName + ' ') + Title) AS [dc:title],
                SubjectArea AS "dc:subject",
                CONVERT(XML, '' + CAST(Overview AS NVARCHAR(4000)) + '') AS [description], -- wrap the Overview XML fragment in a div with the appropriate HTML namespace.
                COALESCE(QualificationName, '') AS [recognitions/recognition/award/awardTitle], COALESCE(QualificationLevel, 0) AS [recognitions/recognition/award/awardLevel], -- qualification can't be empty, so use COALESCE to put empty strings or zeroes in if columns contain null values.
                CAST ((SELECT
                    CAST((SELECT ProgrammeId AS identifier, ModeOfAttendance AS studyMode,
                    StartDate AS start, EndDate AS [end], Venue AS location
                    FROM dbo.Programme AS programme WHERE course.CourseId = programme.CourseId
                    FOR XML PATH('offering'), ELEMENTS, ROOT('offerings')) AS XML)
                FOR XML PATH('offeringPattern')) AS XML)
            FROM dbo.Course AS course
            FOR XML PATH ('spec')) AS XML)
            FOR XML PATH ('curriculum')
        END;

    IF @schemaName = 'XCRI CAP 1.1'
        BEGIN
           -- Build the XCRI CAP 1.1 XML using correlated subqueries with FOR XML PATH.
            WITH XMLNAMESPACES ('http://xcri.org/profiles/catalog/terms' AS xcriTerms, 
                'http://xcri.org/profiles/catalog' AS xcri,
                'http://www.w3.org/1999/xhtml' AS xhtml,
                'http://www.w3.org/2001/XMLSchema-instance' AS xsi,
                DEFAULT 'http://xcri.org/profiles/catalog')
            SELECT GETDATE() AS "@generated", 'http://xcri.org/profiles/catalog/terms http://www.xcri.org/bindings/xcri_cap_terms_1_1.xsd' AS "@xsi:schemaLocation",
            CAST ((SELECT @providerIdentifier AS identifier, @providerName AS title,
                CAST ((SELECT CourseId AS identifier, (LTRIM(QualificationName + ' ') + Title) AS title, SubjectArea AS "subject",
                CAST ((SELECT 'xcriTerms:aim' AS "@xsi:type",
                    CONVERT(XML, '' + CAST(Overview AS NVARCHAR(4000)) + '')-- wrap the Overview XML fragment in a div with the appropriate HTML namespace.           
                    FOR XML PATH ('description'), ELEMENTS) AS XML),
                COALESCE(QualificationName, '') AS "qualification/title", COALESCE(QualificationLevel, 0) AS "qualification/level", -- qualification can't be empty, so use COALESCE to put empty strings or zeroes in if columns contain null values.
                CAST((SELECT ProgrammeId AS identifier, StartDate AS start, ModeOfAttendance AS studyMode
                FROM dbo.Programme AS programme WHERE course.CourseId = programme.CourseId
                FOR XML PATH('presentation'), ELEMENTS) AS XML)
            FROM dbo.Course AS course
            FOR XML PATH ('course')) AS XML)
            FOR XML PATH ('provider')) AS XML)
            FOR XML PATH ('catalog')
        END;


 Execute stored procedure for 'XCRI CAP 1.0' and default parameters 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

    EXEC dbo.usp_CourseFeed @schemaName = 'XCRI CAP 1.0', @providerIdentifier = '0000X00XX0', @providerName = 'Acme University'


Results 1
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

You should get from the stored procedure an XML output which is valid XCRI CAP 1.0, as shown below.

    
      
        0000X00XX0
        Acme University
        
          BSCAN
          BSc Applied Networking Technologies
          
            
              Industry analysts are currently predicting a shortfall of trained networking staff with a Business knowledge.  Building on from our HND this course is designed to equip students with the very latest skills and qualities that they will need to succeed in the vibrant IT orientated world.  You will develop specialist skills in security technologies and techniques and in particular the use of intrusion techniques and penetration testing as methods of determining the robustness of IT security.
            
          
          
            BSc
            9
          
          
            2008/2009/BSCAN/F1/BK/08
            2008-09-01T00:00:00
            Full Time
          
          
            2008/2009/BSCAN/I1/BK/08
            2008-09-01T00:00:00
            Part Time Day
          
          Information Technology and Information
        
        
          UWBKW
          Underwater Basketweaving
          
            
              Learn this traditional craft, using quality local materials, in the comfort of a swimming pool.
              Full snorkelling kit and reed thimbles are provided.
            
          
          
            
            0
          
          
            2008/2009/UWBKW/X1/08
            2008-04-01T00:00:00
            Day
          
          
            2008/2009/UWBKW/Y1/08
            2008-04-30T00:00:00
            Part Time Day
          
          Unreal crafts
        
      
    


 Execute stored procedure for XCRI Curriculum 1.0 with other default parameters 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Now, try generating an XCRI Curriculum 1.0 feed.

    EXEC dbo.usp_CourseFeed @schemaName = 'XCRI Curriculum 1.0'


Results 2 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

You should get a valid XCRI Curriculum 1.0 result like:

    
      
        Date/time of data extract
        2009-08-11T00:42:10.067
      
      
        BSCAN
        BSc Applied Networking Technologies
        Information Technology and Information
        
          
            Industry analysts are currently predicting a shortfall of trained networking staff with a Business knowledge.  Building on from our HND this course is designed to equip students with the very latest skills and qualities that they will need to succeed in the vibrant IT orientated world.  You will develop specialist skills in security technologies and techniques and in particular the use of intrusion techniques and penetration testing as methods of determining the robustness of IT security.
          
        
        
          
            
              BSc
              9
            
          
        
        
          
            
              2008/2009/BSCAN/F1/BK/08
              Full Time
              2008-09-01T00:00:00
              2009-05-20T00:00:00
            
            
              2008/2009/BSCAN/I1/BK/08
              Part Time Day
              2008-09-01T00:00:00
              2009-05-20T00:00:00
            
          
        
      
      
        UWBKW
        Underwater Basketweaving
        Unreal crafts
        
          
            Learn this traditional craft, using quality local materials, in the comfort of a swimming pool.
            Full snorkelling kit and reed thimbles are provided.
          
        
        
          
            
              
              0
            
          
        
        
          
            
              2008/2009/UWBKW/X1/08
              Day
              2008-04-01T00:00:00
              2008-04-01T00:00:00
            
            
              2008/2009/UWBKW/Y1/08
              Part Time Day
              2008-04-30T00:00:00
              2008-05-06T00:00:00
            
          
        
      
    


Execute stored procedure for XCRI CAP 1.1 and default parameters 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Now, try generating an XCRI CAP 1.1 feed.

    EXEC dbo.usp_CourseFeed @schemaName = 'XCRI CAP 1.1'


Results 3 
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

You should get a valid XCRI CAP 1.1 result like:

    
      
        0000X00XX0
        Acme University
        
          BSCAN
          BSc Applied Networking Technologies
          Information Technology and Information
          
            
              Industry analysts are currently predicting a shortfall of trained networking staff with a Business knowledge.  Building on from our HND this course is designed to equip students with the very latest skills and qualities that they will need to succeed in the vibrant IT orientated world.  You will develop specialist skills in security technologies and techniques and in particular the use of intrusion techniques and penetration testing as methods of determining the robustness of IT security.
            
          
          
            BSc
            9
          
          
            2008/2009/BSCAN/F1/BK/08
            2008-09-01T00:00:00
            Full Time
          
          
            2008/2009/BSCAN/I1/BK/08
            2008-09-01T00:00:00
            Part Time Day
          
        
        
          UWBKW
          Underwater Basketweaving
          Unreal crafts
          
            
              Learn this traditional craft, using quality local materials, in the comfort of a swimming pool.
              Full snorkelling kit and reed thimbles are provided.
            
          
          
            
            0
          
          
            2008/2009/UWBKW/X1/08
            2008-04-01T00:00:00
            Day
          
          
            2008/2009/UWBKW/Y1/08
            2008-04-30T00:00:00
            Part Time Day
          
        
      
    


Notes 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

This method of XML extraction:

-   doesn't work in SQL Server 2000, and hasn't been tested in SQL
    Server 2008 or other database engines. The variant of SQL used is
    Microsoft's T-SQL and the XML parts may not be very portable.
    However, it does work with the free [SQL Server 2005
    Express](http://www.microsoft.com/sqlserver/2005/en/us/express.aspx "http://www.microsoft.com/sqlserver/2005/en/us/express.aspx"), so it should easy enough to try it out.
-   is simpler, more direct and easier to maintain than our previous
    method, which relied on an ASP.NET web page and various stored
    procedures and XSLT transformations.
-   does not yet have full functionality. I haven't worked out the
    validation yet; the obvious thing is to get SQL Server Integration
    Services to run the stored procedure, validate the XML and write the
    file to a webserver if it passes, but this hasn't proved as easy as
    saying it, and if anyone can help, that would be a valuable addition
    to this page. The code for the CAP validator on [the XCRI tools
    page](http://www.xcri.org/Tools.html "http://www.xcri.org/Tools.html") could be used here, but it might be more convenient to use a
    validating web service with parameterized schema, which Integration
    Services should be able to connect with.
-   can easily be extended to produce different flavours of XCRI, and
    any forthcoming European standard.
