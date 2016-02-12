---
layout: post
---







Populating the sample SQL Server 2008 XCRI-CAP-1.2-compatible relational database 
=================================================================================













### From Xcri 







Jump to:
[navigation](Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database.html#column-one),
[search](Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database.html#searchInput)



This article discusses some methods of importing data into the database
built in [Sample SQL Server 2008 code for building an
XCRI-CAP-1.2-compatible relational
database](Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database.html "Sample SQL Server 2008 code for building an XCRI-CAP-1.2-compatible relational database"),
which is intended for illustrative purposes, not as a production model.

You may already have your own tables which you can use instead, or copy
data across from, or build views. Here are some suggested approaches.

The first tables to populate are your lookup tables (probably starting
with the Language table in this model). If the data for these exists in
an XML format such as VDEX, then SQL Server 2008 can 'shred' the XML
into tables using the T-SQL OPENROWSET command by loading the files from
disc. However, you can also just paste the
[XML](http://www.xcri.co.uk/vocabularies/attendancePattern2_1.xml "http://www.xcri.co.uk/vocabularies/attendancePattern2_1.xml"){.external
.text} (omitting the declaration; watching for and escaping single
quotes) into a SQL variable and import it like this:

    DECLARE @VocabularyXml AS XML
    SET @VocabularyXml = '
    
        Attendance Pattern for Course Data Programme
        Licence: Open Government Licence (OGL), v1.0. A general attribution statement is sufficient, of the form: "Contains public sector information licensed under the Open Government Licence v1.0." Owner: APS Ltd
    
    http://xcri.org/profiles/catalog/1.2/attendancePattern
    
        DT
        Daytime
        
            The opportunity takes place at some time roughly in the hours 9am to 5pm.
        
    
    
        EV
        Evening
        
            The opportunity takes place at 8pm or later.
        
    
    
        TW
        Twilight
        
            The opportunity takes place between 5pm and 8pm.
        
    
    
        DR
        Day/Block release
        
            The opportunity takes place over the course of a day or more of intensive study.
        
    
    
        WE
        Weekend
        
            The opportunity takes place on Saturday or Sunday.
        
    
    
        CS
        Customised
        
            The timetable for the learning opportunity is agreed with the learner.
        
    
        http://www.xcri.co.uk/vocabularies/attendancePattern2_1.xml
        Jennifer Paull, APS Ltd
        Attendance Pattern, v2.1
        2012-03-05
        attendance pattern
        vocabulary
    '
    -- We need to commit the vocabulary insertion before its terms, otherwise it will violate the foreign key constraint.
    BEGIN TRY;
        BEGIN TRANSACTION;
            ;WITH XMLNAMESPACES(
                'http://www.w3.org/2001/XMLSchema-instance' AS xsi,
                'http://purl.org/dc/elements/1.1/' AS dc,
                DEFAULT 'http://www.imsglobal.org/xsd/imsvdex_v1p0'
                 )
                -- Insert the vocabulary
                INSERT INTO dbo.Vocabulary (VocabularyId, Source, Creator, Title, [Date], [Description])
                SELECT @VocabularyXml.value('(/vdex/vocabIdentifier)[1]', 'dbo.URI') AS VocabularyId,
                    @VocabularyXml.value('(/vdex/metadata/dc:source)[1]', 'dbo.URI') AS Source,
                    @VocabularyXml.value('(/vdex/metadata/dc:creator)[1]', 'NVARCHAR(255)') AS Creator,
                    @VocabularyXml.value('(/vdex/metadata/dc:title)[1]', 'NVARCHAR(255)') AS Title,
                    @VocabularyXml.value('(/vdex/metadata/dc:date)[1]', 'DATE') AS [Date],
                    @VocabularyXml.value('(/vdex/vocabName)[1]', 'NVARCHAR(255)') AS [Description];
        COMMIT TRANSACTION;
    END TRY
    BEGIN CATCH;
        ROLLBACK TRANSACTION;
    END CATCH;
    BEGIN TRY;
        BEGIN TRANSACTION;
            ;WITH XMLNAMESPACES(
                'http://www.w3.org/2001/XMLSchema-instance' AS xsi,
                'http://purl.org/dc/elements/1.1/' AS dc,
                DEFAULT 'http://www.imsglobal.org/xsd/imsvdex_v1p0'
                 )
            --Insert each term belonging to the vocabulary
            INSERT INTO dbo.Term(TermId, VocabularyId, Label, [Description])
            SELECT
                Term.value('termIdentifier[1]', 'dbo.URI') AS TermId,
                @VocabularyXml.value('(/vdex/vocabIdentifier)[1]', 'dbo.URI') AS VocabularyId,
                Term.value('caption[1]', 'NVARCHAR(100)') AS Label,
                Term.value('description[1]', 'NVARCHAR(255)') AS [Description]
            FROM @VocabularyXml.nodes('/vdex/term') AS VocabularyTable(Term);
        COMMIT TRANSACTION;
    END TRY
    BEGIN CATCH;
        ROLLBACK TRANSACTION;
    END CATCH;
    /*
    -- Test
    SELECT *
    FROM dbo.Term
    WHERE VocabularyId = @VocabularyXml.value('(/vdex/vocabIdentifier)[1]', 'dbo.URI')
    */
    GO

For more information on 'shredding' XML into relational tables, see
[nodes() Method (xml Data
Type)](http://msdn.microsoft.com/en-us/library/ms188282(SQL.105).aspx "http://msdn.microsoft.com/en-us/library/ms188282(SQL.105).aspx"){.external
.text}.

You could write this into a stored procedure, upload your vocabulary XML
into an XML column in a dedicated SQL table, and import their contents
into your relational tables.


\[[edit](../index.php@title=Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database&action=edit&section=1.html "Edit section: SQL code for populating sample tables")\]  SQL code for populating sample tables 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

However, for the purposes of moving on to data extraction, we need a
reasonably comprehensive set of sample data, so here is a SQL script
that will populate the sample tables:

(Note: bug in ProviderVenue INSERT SQL below was fixed,
--[Tavis](../index.php@title=User%253ATavis&action=edit.html "User:Tavis")
23:53, 4 April 2012 (BST)).

    /****** Object:  Table [dbo].[Organization]    Script Date: 04/01/2012 18:57:33 ******/
    SET IDENTITY_INSERT [dbo].[Organization] ON
    INSERT [dbo].[Organization] ([OrganizationId], [CommonName], [IndustryCode], [IndustrialId], [OrganizationalUnitOf]) VALUES (1, N'Kelpie College', N'8530', N'0000X00XX0', NULL)
    INSERT [dbo].[Organization] ([OrganizationId], [CommonName], [IndustryCode], [IndustrialId], [OrganizationalUnitOf]) VALUES (2, N'Caledonian Swampland Federation', N'8550', NULL, NULL)
    INSERT [dbo].[Organization] ([OrganizationId], [CommonName], [IndustryCode], [IndustrialId], [OrganizationalUnitOf]) VALUES (3, N'Pict Harbour College', N'8530', N'0000X00XX0/1', 1)
    INSERT [dbo].[Organization] ([OrganizationId], [CommonName], [IndustryCode], [IndustrialId], [OrganizationalUnitOf]) VALUES (4, N'Celt Harbour College', N'8530', N'0000X00XX0/2', 1)
    INSERT [dbo].[Organization] ([OrganizationId], [CommonName], [IndustryCode], [IndustrialId], [OrganizationalUnitOf]) VALUES (5, N'The Schooner "Privateering and Slavedriving"', N'8530', N'0000X00XX0/3', 1)
    INSERT [dbo].[Organization] ([OrganizationId], [CommonName], [IndustryCode], [IndustrialId], [OrganizationalUnitOf]) VALUES (6, N'The Barque "Acquired Tacking"', N'8530', N'0000X00XX0/4', 1)
    INSERT [dbo].[Organization] ([OrganizationId], [CommonName], [IndustryCode], [IndustrialId], [OrganizationalUnitOf]) VALUES (7, N'Swampland Qualifications Agency', N'8550', NULL, NULL)
    SET IDENTITY_INSERT [dbo].[Organization] OFF
    /****** Object:  Table [dbo].[Language]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[Language] ([LanguageId], [ExtensionOf], [ScriptOf], [RegionOf], [VariantOf], [Description], [Comments]) VALUES (N'cy', NULL, NULL, NULL, NULL, N'Welsh', NULL)
    INSERT [dbo].[Language] ([LanguageId], [ExtensionOf], [ScriptOf], [RegionOf], [VariantOf], [Description], [Comments]) VALUES (N'de', NULL, NULL, NULL, NULL, N'German', NULL)
    INSERT [dbo].[Language] ([LanguageId], [ExtensionOf], [ScriptOf], [RegionOf], [VariantOf], [Description], [Comments]) VALUES (N'en', NULL, NULL, NULL, NULL, N'English', NULL)
    INSERT [dbo].[Language] ([LanguageId], [ExtensionOf], [ScriptOf], [RegionOf], [VariantOf], [Description], [Comments]) VALUES (N'en-scotland', NULL, NULL, NULL, N'en', N'Scottish Standard English', NULL)
    INSERT [dbo].[Language] ([LanguageId], [ExtensionOf], [ScriptOf], [RegionOf], [VariantOf], [Description], [Comments]) VALUES (N'fr', NULL, NULL, NULL, NULL, N'French', NULL)
    /****** Object:  Table [dbo].[Course]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[Course] ([CourseId], [Url]) VALUES (N'http://kelpiecollege.org.uk/courses(HDLANG)', N'http://www.kelpiecollege.org.uk/courses(HDLANG)')
    INSERT [dbo].[Course] ([CourseId], [Url]) VALUES (N'http://kelpiecollege.org.uk/courses(HLANG1)', N'http://www.kelpiecollege.org.uk/courses(HLANG1)')
    INSERT [dbo].[Course] ([CourseId], [Url]) VALUES (N'http://kelpiecollege.org.uk/courses(HNCMS)', N'http://www.kelpiecollege.org.uk/courses(HNCMS)')
    INSERT [dbo].[Course] ([CourseId], [Url]) VALUES (N'http://kelpiecollege.org.uk/courses(ISN1)', N'http://www.kelpiecollege.org.uk/courses(ISN1)')
    INSERT [dbo].[Course] ([CourseId], [Url]) VALUES (N'http://kelpiecollege.org.uk/courses(UWBKW)', N'http://www.kelpiecollege.org.uk/courses(UWBKW)')
    /****** Object:  Table [dbo].[Vocabulary]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[Vocabulary] ([VocabularyId], [Title], [Description], [Creator], [Source], [Date]) VALUES (N'http://example.org/sqa/credit', N'Swampland Qualifications Agency Credit Framework', N'Fictional credit scheme.', NULL, NULL, CAST(0x81350B00 AS Date))
    INSERT [dbo].[Vocabulary] ([VocabularyId], [Title], [Description], [Creator], [Source], [Date]) VALUES (N'http://kelpiecollege.org.uk/courses/subjects', N'Kelpie College course subject vocabulary', N'Test, in-house vocabulary from the fictitious college.', NULL, NULL, NULL)
    INSERT [dbo].[Vocabulary] ([VocabularyId], [Title], [Description], [Creator], [Source], [Date]) VALUES (N'http://xcri.org/profiles/catalog/1.2/age', N'Age', N'The intended age range for which the presentation is suitable. This is a refinement of: http://purl.org/dc/terms/audience', NULL, NULL, NULL)
    INSERT [dbo].[Vocabulary] ([VocabularyId], [Title], [Description], [Creator], [Source], [Date]) VALUES (N'http://xcri.org/profiles/catalog/1.2/attendanceMode', N'Attendance Mode, v2.1', N'Attendance Mode for Course Data ProgrammeLicence: Open Government Licence (OGL), v1.0. A general attribution statement is sufficient, of the form: "Contains public sector information licensed under the Open Government Licence v1.0." Owner: APS Ltd', N'Jennifer Paull, APS Ltd', N'http://www.xcri.co.uk/vocabularies/attendanceMode2_1.xml', CAST(0x66350B00 AS Date))
    INSERT [dbo].[Vocabulary] ([VocabularyId], [Title], [Description], [Creator], [Source], [Date]) VALUES (N'http://xcri.org/profiles/catalog/1.2/attendancePattern', N'Attendance Pattern, v2.1', N'Attendance Pattern for Course Data ProgrammeLicence: Open Government Licence (OGL), v1.0. A general attribution statement is sufficient, of the form: "Contains public sector information licensed under the Open Government Licence v1.0." Owner: APS Ltd', N'Jennifer Paull, APS Ltd', N'http://www.xcri.co.uk/vocabularies/attendancePattern2_1.xml', CAST(0x66350B00 AS Date))
    INSERT [dbo].[Vocabulary] ([VocabularyId], [Title], [Description], [Creator], [Source], [Date]) VALUES (N'http://xcri.org/profiles/catalog/1.2/studyMode', N'Study Mode, v2.1', N'Study Mode for Course Data Programme.Licence: Open Government Licence (OGL), v1.0. A general attribution statement is sufficient, of the form: "Contains public sector information licensed under the Open Government Licence v1.0." Owner: APS Ltd', N'Alan Paull, APS Ltd', N'http://www.xcri.co.uk/vocabularies/studyMode2_1.xml', CAST(0x66350B00 AS Date))
    INSERT [dbo].[Vocabulary] ([VocabularyId], [Title], [Description], [Creator], [Source], [Date]) VALUES (N'http://xcri.org/profiles/catalog/terms', N'XCRI Terms 1.2', N'http://www.xcri.org/XCRI_Terms_1.2', NULL, NULL, NULL)
    /****** Object:  Table [dbo].[Location]    Script Date: 04/01/2012 18:57:33 ******/
    SET ANSI_PADDING ON
    GO
    SET IDENTITY_INSERT [dbo].[Location] ON
    INSERT [dbo].[Location] ([LocationId], [UriBase], [Address], [Street], [Town], [Postcode], [Phone], [Fax], [Email], [Url]) VALUES (1, N'http://kelpiecollege.org.uk/venue/', NULL, N'Port Street', N'Picton', N'PCT1', NULL, NULL, NULL, NULL)
    INSERT [dbo].[Location] ([LocationId], [UriBase], [Address], [Street], [Town], [Postcode], [Phone], [Fax], [Email], [Url]) VALUES (2, N'http://kelpiecollege.org.uk/venue/', NULL, N'Harbour Lane', N'Celtville', N'CLT2', NULL, NULL, NULL, NULL)
    INSERT [dbo].[Location] ([LocationId], [UriBase], [Address], [Street], [Town], [Postcode], [Phone], [Fax], [Email], [Url]) VALUES (3, N'http://kelpiecollege.org.uk/venue/', N'Berth 4, Pict Harbour', NULL, N'Picton', N'PCT1', NULL, NULL, NULL, NULL)
    INSERT [dbo].[Location] ([LocationId], [UriBase], [Address], [Street], [Town], [Postcode], [Phone], [Fax], [Email], [Url]) VALUES (4, N'http://kelpiecollege.org.uk/venue/', N'Offshore anchorage, Celt Harbour', NULL, N'Celtville', N'CLT2', NULL, NULL, NULL, NULL)
    SET IDENTITY_INSERT [dbo].[Location] OFF
    SET ANSI_PADDING OFF
    /****** Object:  Table [dbo].[Qualification]    Script Date: 04/01/2012 18:57:33 ******/
    SET IDENTITY_INSERT [dbo].[Qualification] ON
    INSERT [dbo].[Qualification] ([QualificationId], [Title], [Abbr], [Description], [EducationLevel], [Type], [Url], [AwardedBy], [AccreditedBy]) VALUES (1, N'Highly Notional Certificate', N'HNC', NULL, NULL, NULL, NULL, 1, 7)
    INSERT [dbo].[Qualification] ([QualificationId], [Title], [Abbr], [Description], [EducationLevel], [Type], [Url], [AwardedBy], [AccreditedBy]) VALUES (2, N'Mock Apprenticeship', N'MA', NULL, NULL, NULL, NULL, 1, 7)
    SET IDENTITY_INSERT [dbo].[Qualification] OFF
    /****** Object:  Table [dbo].[ProviderVenue]    Script Date: 04/01/2012 18:57:33 ******/
    --INSERT [dbo].[ProviderVenue] ([ProviderId], [LocationId]) VALUES (3, 1)
    --INSERT [dbo].[ProviderVenue] ([ProviderId], [LocationId]) VALUES (4, 2)
    --INSERT [dbo].[ProviderVenue] ([ProviderId], [LocationId]) VALUES (5, 4)
    --INSERT [dbo].[ProviderVenue] ([ProviderId], [LocationId]) VALUES (6, 3)
    /****** Object:  Table [dbo].[CourseAbstract]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[CourseAbstract] ([CourseId], [LanguageId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HDLANG)', N'en', N'Learn to speak the Harbour Dolphin dialect of Cetacean and converse, question and barter with these friendly and helpful creatures.')
    INSERT [dbo].[CourseAbstract] ([CourseId], [LanguageId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HLANG1)', N'en', N'Learn the telepathic Mind Speak of the Hive, and commune humbly with our near-neighbours from the Tenth Planet!')
    INSERT [dbo].[CourseAbstract] ([CourseId], [LanguageId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HNCMS)', N'en', N'Traditional metalworking methods come together with cutting edge space technology in this practical course.')
    INSERT [dbo].[CourseAbstract] ([CourseId], [LanguageId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(ISN1)', N'en', N'Learn the art of navigating around the solar system at apprentice level. In a spaceship. Obviously.')
    INSERT [dbo].[CourseAbstract] ([CourseId], [LanguageId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(UWBKW)', N'en', N'Learn the traditional craft of underwater basketweaving, using quality local materials, in the comfort of a swimming pool.')
    /****** Object:  Table [dbo].[Term]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'1', N'http://example.org/sqa/credit', N'en', N'Level 1', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'16+', N'http://xcri.org/profiles/catalog/1.2/age', N'en', N'16+', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'16‚Äì18', N'http://xcri.org/profiles/catalog/1.2/age', N'en', N'16‚Äì18', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'16‚Äì20', N'http://xcri.org/profiles/catalog/1.2/age', N'en', N'16‚Äì20', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'2', N'http://example.org/sqa/credit', N'en', N'Level 2', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'3', N'http://example.org/sqa/credit', N'en', N'Level 3', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'any', N'http://xcri.org/profiles/catalog/1.2/age', N'en', N'any', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'careerOutcome', N'http://xcri.org/profiles/catalog/terms', N'en', N'career outcome', N'Career outcomes for a course of study.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', N'en', N'Campus', N'Learner will be expected to attend at the venue for the bulk of their teaching time.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'contactHours', N'http://xcri.org/profiles/catalog/terms', N'en', N'contact hours', N'The number and style of contact hours that a learner should expect on a course of study.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'contactPattern', N'http://xcri.org/profiles/catalog/terms', N'en', N'contact pattern', N'The style of contact that a learner would receive on a course of study.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'CS', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', N'en', N'Customised', N'The timetable for the learning opportunity is agreed with the learner.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'DA', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', N'en', N'Distance with attendance', N'Primarily distance learning however the learner will be required to attend at the venue as necessary.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'DR', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', N'en', N'Day/Block release', N'The opportunity takes place over the course of a day or more of intensive study.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'DS', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', N'en', N'Distance without attendance', N'The learning opportunity does not require any attendance at the venue.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'DT', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', N'en', N'Daytime', N'The opportunity takes place at some time roughly in the hours 9am to 5pm.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'EV', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', N'en', N'Evening', N'The opportunity takes place at 8pm or later.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'events', N'http://xcri.org/profiles/catalog/terms', N'en', N'events', N'Events relevant to a course of study, such as open days.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'FL', N'http://xcri.org/profiles/catalog/1.2/studyMode', N'en', N'Flexible', N'Could be full time or part time dependent on the learner. ')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'FT', N'http://xcri.org/profiles/catalog/1.2/studyMode', N'en', N'Full time', N'The learning opportunity is the learner''s main activity.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'http://kelpiecollege.org.uk/courses/subjects(S01)', N'http://kelpiecollege.org.uk/courses/subjects', N'en', N'interspecies linguistics', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'http://kelpiecollege.org.uk/courses/subjects(S02)', N'http://kelpiecollege.org.uk/courses/subjects', N'en', N'future industries', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'http://kelpiecollege.org.uk/courses/subjects(S03)', N'http://kelpiecollege.org.uk/courses/subjects', N'en', N'notional navigation', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'http://kelpiecollege.org.uk/courses/subjects(S04)', N'http://kelpiecollege.org.uk/courses/subjects', N'en', N'unreal crafts', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'indicativeResource', N'http://xcri.org/profiles/catalog/terms', N'en', N'indicative resource', N'Examples of the kind of resources that would be used on a course of study, such as IT facilities and reading lists.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'leadsTo', N'http://xcri.org/profiles/catalog/terms', N'en', N'leads to', N'Opportunities likely to flow from a course of study, such as opportunities for further study (course articulations).')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'MM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', N'en', N'Mixed mode', N'')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'NC', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', N'en', N'Face-to-face non-campus', N'The learner undertakes the course off campus.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'NK', N'http://xcri.org/profiles/catalog/1.2/studyMode', N'en', N'Not known', N'The study mode is not known.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'not known', N'http://xcri.org/profiles/catalog/1.2/age', N'en', N'not known', NULL)
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'ON', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', N'en', N'Online (no attendance)', N'The learner undertakes the course over the internet only.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'PF', N'http://xcri.org/profiles/catalog/1.2/studyMode', N'en', N'Part of a full time programme', N'The learning opportunity is a component of a set of learning opportunities that form the learner''s main activity. ')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'policy', N'http://xcri.org/profiles/catalog/terms', N'en', N'policy', N'Policies relevant to a course of study, such as diversity of adjustments for disability.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'providedResource', N'http://xcri.org/profiles/catalog/terms', N'en', N'provided resource', N'Resources that would be provided to learners by the institution.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'PT', N'http://xcri.org/profiles/catalog/1.2/studyMode', N'en', N'Part time', N'The learning opportunity is not the learner''s main activity')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'requiredResource', N'http://xcri.org/profiles/catalog/terms', N'en', N'required resource', N'Resources that the learner must provide in order to engage in a course of study.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'specialFeature', N'http://xcri.org/profiles/catalog/terms', N'en', N'special feature', N'Used to highlight special features of a course of study.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'structure', N'http://xcri.org/profiles/catalog/terms', N'en', N'structure', N'An overview of the module composition of a course of study.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'studyHours', N'http://xcri.org/profiles/catalog/terms', N'en', N'study hours', N'Hours of study expected of a learner for successful completion.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'support', N'http://xcri.org/profiles/catalog/terms', N'en', N'support', N'Support facilities available to learners.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'teaching Strategy', N'http://xcri.org/profiles/catalog/terms', N'en', N'teaching strategy', N'The teaching strategies that will be employed on a course of study.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'topic', N'http://xcri.org/profiles/catalog/terms', N'en', N'topic', N'A syllabus of topics that would be covered in a course of study.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'TW', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', N'en', N'Twilight', N'The opportunity takes place between 5pm and 8pm.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'WB', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', N'en', N'Work-based', N'The learner undertakes the course at their workplace.')
    INSERT [dbo].[Term] ([TermId], [VocabularyId], [Language], [Label], [Description]) VALUES (N'WE', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', N'en', N'Weekend', N'The opportunity takes place on Saturday or Sunday.')
    /****** Object:  Table [dbo].[CourseTitle]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[CourseTitle] ([CourseId], [LanguageId], [Prefix], [MainSort], [Suffix]) VALUES (N'http://kelpiecollege.org.uk/courses(HDLANG)', N'en', N'Conversational', N'Cetacean', N'Harbour Dolphin Dialect')
    INSERT [dbo].[CourseTitle] ([CourseId], [LanguageId], [Prefix], [MainSort], [Suffix]) VALUES (N'http://kelpiecollege.org.uk/courses(HLANG1)', N'en', N'Hive', N'Mind Speak', N'level 1')
    INSERT [dbo].[CourseTitle] ([CourseId], [LanguageId], [Prefix], [MainSort], [Suffix]) VALUES (N'http://kelpiecollege.org.uk/courses(HNCMS)', N'en', NULL, N'Metalwork and Spacecraft', NULL)
    INSERT [dbo].[CourseTitle] ([CourseId], [LanguageId], [Prefix], [MainSort], [Suffix]) VALUES (N'http://kelpiecollege.org.uk/courses(ISN1)', N'en', N'Intra-System', N'Navigation', N'level 1')
    INSERT [dbo].[CourseTitle] ([CourseId], [LanguageId], [Prefix], [MainSort], [Suffix]) VALUES (N'http://kelpiecollege.org.uk/courses(UWBKW)', N'en', N'Underwater', N'Basketweaving', NULL)
    /****** Object:  Table [dbo].[CourseQualification]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[CourseQualification] ([CourseId], [QualificationId]) VALUES (N'http://kelpiecollege.org.uk/courses(HNCMS)', 1)
    INSERT [dbo].[CourseQualification] ([CourseId], [QualificationId]) VALUES (N'http://kelpiecollege.org.uk/courses(ISN1)', 2)
    /****** Object:  Table [dbo].[CourseDescription]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HDLANG)', N'en', N'careerOutcome', N'http://xcri.org/profiles/catalog/terms', N'After picking up a smattering of Cetacean: Harbour Dolphin dialect, you could be on your way to a career as:dolphin gopher;harbourmaster''s assistant.')
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HDLANG)', N'en', N'topic', N'http://xcri.org/profiles/catalog/terms', N'Harbour dolphins are friendly creatures, excellent guides and reliable marine navigators. They are also very chatty.This introductory course will let you confidently:exchange pleasantries;ask for directions;barter in the local currency (the all-important commercial fish vocabulary).')
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HLANG1)', N'en', N'careerOutcome', N'http://xcri.org/profiles/catalog/terms', N'Even brief contact with the Hive mind may produce mental burnout or enslavement, leading to opportunities as:a vegetable (crispy);a slave (creepy).')
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HLANG1)', N'en', N'topic', N'http://xcri.org/profiles/catalog/terms', N'The Hive are the only sentient species of the Tenth Planet. They have amazing mindsharing abilities, which they use to form one colossal, connected mind.They can telepathically communicate with other species as well, and this course will introduce you to Hive Mind Speak. Delivered by our guest Hive lecturer, you will learn:telepathic communication protocols;the lesser and greater obsequies;Mind Speak knock-knock jokes.')
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HNCMS)', N'en', N'careerOutcome', N'http://xcri.org/profiles/catalog/terms', N'On finishing this course the sky is the limit, as you can launch into careers such as:shuttlesmith;shield welder;solar panel beater.')
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HNCMS)', N'en', N'topic', N'http://xcri.org/profiles/catalog/terms', N'Traditional metalworking methods come together with cutting edge space technology in this practical course.By the end of your studies, you should have launched a working space probe in wrought iron, cast bronze or sheet-hammered tin.')
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(ISN1)', N'en', N'careerOutcome', N'http://xcri.org/profiles/catalog/terms', N'A career in the shipping lanes of our solar system awaits successful apprentices from this course, such as:assistant navigator;first contact hero/alien food animal.')
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(ISN1)', N'en', N'topic', N'http://xcri.org/profiles/catalog/terms', N'This made-up apprenticeship teaches the basics of navigating between the various bodies of the solar system, using a variety of instruments you will build yourself. Plot your course to make best use of gravity, take parallax readings, and avoid that big shiny thing in the middle.')
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(UWBKW)', N'en', N'careerOutcome', N'http://xcri.org/profiles/catalog/terms', N'Underwater basketweaver, what else?')
    INSERT [dbo].[CourseDescription] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(UWBKW)', N'en', N'topic', N'http://xcri.org/profiles/catalog/terms', N'Learn this traditional craft, using quality local materials, in the comfort of a swimming pool.Full snorkelling kit and reed thimbles are provided.')
    /****** Object:  Table [dbo].[CourseCredit]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[CourseCredit] ([CourseId], [CreditSchemeId], [CreditId], [Value]) VALUES (N'http://kelpiecollege.org.uk/courses(HNCMS)', N'http://example.org/sqa/credit', N'3', 60)
    INSERT [dbo].[CourseCredit] ([CourseId], [CreditSchemeId], [CreditId], [Value]) VALUES (N'http://kelpiecollege.org.uk/courses(ISN1)', N'http://example.org/sqa/credit', N'2', 40)
    /****** Object:  Table [dbo].[CourseAttribute]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[CourseAttribute] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HDLANG)', N'en', N'http://kelpiecollege.org.uk/courses/subjects(S01)', N'http://kelpiecollege.org.uk/courses/subjects', NULL)
    INSERT [dbo].[CourseAttribute] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HLANG1)', N'en', N'http://kelpiecollege.org.uk/courses/subjects(S01)', N'http://kelpiecollege.org.uk/courses/subjects', NULL)
    INSERT [dbo].[CourseAttribute] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(HNCMS)', N'en', N'http://kelpiecollege.org.uk/courses/subjects(S02)', N'http://kelpiecollege.org.uk/courses/subjects', NULL)
    INSERT [dbo].[CourseAttribute] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(ISN1)', N'en', N'http://kelpiecollege.org.uk/courses/subjects(S03)', N'http://kelpiecollege.org.uk/courses/subjects', NULL)
    INSERT [dbo].[CourseAttribute] ([CourseId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'http://kelpiecollege.org.uk/courses(UWBKW)', N'en', N'http://kelpiecollege.org.uk/courses/subjects(S04)', N'http://kelpiecollege.org.uk/courses/subjects', NULL)
    /****** Object:  Table [dbo].[Presentation]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'00862458-f87b-e111-8c49-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(HNCMS)', CAST(0x007043010D360B3C000000 AS DateTimeOffset), CAST(0x0070430123370B3C000000 AS DateTimeOffset), NULL, NULL, NULL, N'en', N'en', NULL, NULL)--4, 2)
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'b0173b78-f87b-e111-8c49-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(ISN1)', CAST(0x007043010D360B3C000000 AS DateTimeOffset), CAST(0x0070430190380B3C000000 AS DateTimeOffset), NULL, NULL, NULL, N'en', N'en', NULL, NULL)--5, 4)
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'c03d9d80-f87b-e111-8c49-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(ISN1)', CAST(0x007043017B370B3C000000 AS DateTimeOffset), CAST(0x00704301FE390B3C000000 AS DateTimeOffset), NULL, NULL, NULL, N'en', N'en', NULL, NULL)--5, 4)
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'c09780ac-f87b-e111-8c49-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(UWBKW)', CAST(0x0070430119360B3C000000 AS DateTimeOffset), CAST(0x0000000083360B00000000 AS DateTimeOffset), NULL, NULL, NULL, N'en', N'en', NULL, NULL)--6, 3)
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'90e902b8-f87b-e111-8c49-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(UWBKW)', CAST(0x0070430119360B3C000000 AS DateTimeOffset), CAST(0x0000000083360B00000000 AS DateTimeOffset), NULL, NULL, NULL, N'en', N'en', NULL, NULL)--3, 1)
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'2061c3d6-f87b-e111-8c49-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(UWBKW)', CAST(0x000000009F360B00000000 AS DateTimeOffset), CAST(0x00704301E7360B3C000000 AS DateTimeOffset), NULL, NULL, NULL, N'en', N'en', NULL, NULL)--4, 2)
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'c0918328-1979-e111-99c1-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(HDLANG)', CAST(0x0070430119360B3C000000 AS DateTimeOffset), CAST(0x007043011E370B3C000000 AS DateTimeOffset), NULL, NULL, NULL, NULL, NULL, NULL, NULL)--3, 1)
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'004da3f4-e579-e111-99c1-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(HDLANG)', CAST(0x0070430186370B3C000000 AS DateTimeOffset), CAST(0x007043018B380B3C000000 AS DateTimeOffset), NULL, NULL, NULL, N'en', N'en', NULL, NULL)--3, 1)
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'20867645-e679-e111-99c1-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(HLANG1)', CAST(0x0070430119360B3C000000 AS DateTimeOffset), CAST(0x007043011E370B3C000000 AS DateTimeOffset), NULL, NULL, NULL, N'en', N'en', NULL, NULL)--3, 1)
    INSERT [dbo].[Presentation] ([PresentationId], [CourseId], [Start], [End], [ApplyFrom], [ApplyUntil], [ApplyTo], [LanguageOfInstruction], [LanguageOfAssessment], [ProviderId], [LocationId]) VALUES (N'21867645-e679-e111-99c1-02f3e9ffdfeb', N'http://kelpiecollege.org.uk/courses(HLANG1)', CAST(0x0070430186370B3C000000 AS DateTimeOffset), CAST(0x007043018B380B3C000000 AS DateTimeOffset), NULL, NULL, NULL, N'en', N'en', NULL, NULL)--3, 1)
    /****** Object:  Table [dbo].[PresentationAttribute]    Script Date: 04/01/2012 18:57:33 ******/
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'00862458-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'00862458-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'DT', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'b0173b78-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'b0173b78-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'DR', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'c03d9d80-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'c03d9d80-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'DT', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'c09780ac-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'c09780ac-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'DR', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'90e902b8-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'90e902b8-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'CS', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'2061c3d6-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'2061c3d6-f87b-e111-8c49-02f3e9ffdfeb', N'en', N'DT', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'c0918328-1979-e111-99c1-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'c0918328-1979-e111-99c1-02f3e9ffdfeb', N'en', N'DT', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'c0918328-1979-e111-99c1-02f3e9ffdfeb', N'en', N'FL', N'http://xcri.org/profiles/catalog/1.2/studyMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'004da3f4-e579-e111-99c1-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'004da3f4-e579-e111-99c1-02f3e9ffdfeb', N'en', N'DT', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'004da3f4-e579-e111-99c1-02f3e9ffdfeb', N'en', N'FT', N'http://xcri.org/profiles/catalog/1.2/studyMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'20867645-e679-e111-99c1-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'20867645-e679-e111-99c1-02f3e9ffdfeb', N'en', N'DT', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'20867645-e679-e111-99c1-02f3e9ffdfeb', N'en', N'FT', N'http://xcri.org/profiles/catalog/1.2/studyMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'21867645-e679-e111-99c1-02f3e9ffdfeb', N'en', N'CM', N'http://xcri.org/profiles/catalog/1.2/attendanceMode', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'21867645-e679-e111-99c1-02f3e9ffdfeb', N'en', N'CS', N'http://xcri.org/profiles/catalog/1.2/attendancePattern', NULL)
    INSERT [dbo].[PresentationAttribute] ([PresentationId], [LanguageId], [TermId], [VocabularyId], [Text]) VALUES (N'21867645-e679-e111-99c1-02f3e9ffdfeb', N'en', N'PF', N'http://xcri.org/profiles/catalog/1.2/studyMode', NULL)
    GO
    -- Work around 'no query plan' problem by dropping FK, inserting data, then recreating the FK.
    ALTER TABLE [dbo].[ProviderVenue] DROP CONSTRAINT [FK_ProviderVenue_Location]
    ALTER TABLE [dbo].[ProviderVenue] DROP CONSTRAINT [FK_ProviderVenue_Organization]
    GO
    INSERT [dbo].[ProviderVenue] ([ProviderId], [LocationId]) VALUES (3, 1)
    INSERT [dbo].[ProviderVenue] ([ProviderId], [LocationId]) VALUES (4, 2)
    INSERT [dbo].[ProviderVenue] ([ProviderId], [LocationId]) VALUES (5, 4)
    INSERT [dbo].[ProviderVenue] ([ProviderId], [LocationId]) VALUES (6, 3)
    GO
    ALTER TABLE [dbo].[ProviderVenue]  WITH CHECK ADD  CONSTRAINT [FK_ProviderVenue_Location] FOREIGN KEY([LocationId])
    REFERENCES [dbo].[Location] ([LocationId])
    GO
    ALTER TABLE [dbo].[ProviderVenue] CHECK CONSTRAINT [FK_ProviderVenue_Location]
    GO
    /****** Object:  ForeignKey [FK_ProviderVenue_Organization]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[ProviderVenue]  WITH CHECK ADD  CONSTRAINT [FK_ProviderVenue_Organization] FOREIGN KEY([ProviderId])
    REFERENCES [dbo].[Organization] ([OrganizationId])
    GO
    ALTER TABLE [dbo].[ProviderVenue] CHECK CONSTRAINT [FK_ProviderVenue_Organization]
    GO

Now we can move on to extraction: [Sample SQL Server 2008 code for
extracting XCRI CAP 1.2 XML from a relational
database](Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html "Sample SQL Server 2008 code for extracting XCRI CAP 1.2 XML from a relational database").
--[Tavis](../index.php@title=User%253ATavis&action=edit.html "User:Tavis")
18:24, 1 April 2012 (BST)



Retrieved from
"[http://localhost/Populating\_the\_sample\_SQL\_Server\_2008\_XCRI-CAP-1.2-compatible\_relational\_database](Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database.html)"

















##### Views



-   

    

    [Article](Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database.html)
-   

    

    [Discussion](../index.php@title=Talk%253APopulating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database&action=edit.html)
-   

    

    [Edit](../index.php@title=Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database&action=edit.html)
-   

    

    [History](../index.php@title=Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database&action=history.html)







##### Personal tools



-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database.html)











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
    here](Special%253AWhatlinkshere/Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database&oldid=4371.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 22:53, 4 April 2012.
-   

    

    This page has been accessed 3,206 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




