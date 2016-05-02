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







Sample SQL Server 2008 code for building an XCRI-CAP-1.2-compatible relational database 
=======================================================================================













### From Xcri 







Jump to:
[navigation](Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database.html#column-one),
[search](Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database.html#searchInput)



Here is a sample physical schema of a database designed to hold course
data, expressed in Microsoft SQL Server 2008 Transact-SQL. It's purpose
is mainly to illustrate some techniques and suggestions for data
modelling and abstraction (getting data into and out of the database as
XCRI CAP 1.2 and related formats such as VDEX) which will be covered on
separate pages.

+--------------------------------------------------------------------------+
|                                                       |
|                                                                          |
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
|                                                                    |
|                                                                          |
| -   [1 Disclaimers](Sample_SQL_Server_2008_code_for_ |
| building_an_XCRI-CAP-1.2-compatible_relational_database.html#Disclaimers |
| )                                                                        |
| -   [2 Diagram](Sample_SQL_Server_2008_code_for_buil |
| ding_an_XCRI-CAP-1.2-compatible_relational_database.html#Diagram)        |
| -   [3 Design       |
|     features and                                                         |
|     issues](Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP- |
| 1.2-compatible_relational_database.html#Design_features_and_issues)      |
| -   [4 Create the   |
|     database                                                             |
|     objects](Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP |
| -1.2-compatible_relational_database.html#Create_the_database_objects)    |
| -   [5 Further      |
|     topics](Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP- |
| 1.2-compatible_relational_database.html#Further_topics)                  |
+--------------------------------------------------------------------------+


\[[edit](../index.php@title=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&action=edit&section=1.html "Edit section: Disclaimers")\]  Disclaimers 
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   This is not an 'official' XCRI project database, and indeed one
    could not produce such a thing as XCRI is concerned with exchange as
    opposed to long term storage of information.
-   This is not intended for a production environment.
-   It has not been thoroughly tested (it won't work on SQL Server 2005
    as is, because the SQL uses new date datatypes) and some of the
    namespaces may not be as recommended.
-   If you spot any errors or have any comments, please contribute to
    the [Designing an 'XCRI' Data Model forum
    post](http://www.xcri.org/forum/topic.php?id=191 "http://www.xcri.org/forum/topic.php?id=191").


\[[edit](../index.php@title=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&action=edit&section=2.html "Edit section: Diagram")\]  Diagram 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[![Image:CoursesDbXcriCap1.2.png](http://localhost/wiki/images/b/b2/CoursesDbXcriCap1.2.png){width="2258"
height="1686"}](Image%253ACoursesDbXcriCap1.2.png "Image:CoursesDbXcriCap1.2.png")


\[[edit](../index.php@title=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&action=edit&section=3.html "Edit section: Design features and issues")\]  Design features and issues 
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   There is a user-defined data type for URI, and a custom XML schema
    for XHTML.
-   Generalization, where possible, was used instead of one-to-one
    matching of CAP elements to database tables. For example, course
    descriptions and course and presentation attributes are consolidated
    in three tables.
-   Extensibility (particularly geared towards ease of importing
    new vocabularies) was a design consideration.
-   Multiple language support.
-   A variety of primary keys were used (URIs, UNIQUEIDENTIFIERs,
    incrementing identity columns) for comparison, although not
    necessarily as good practice.
-   Pascal case table names, matching XCRI CAP 1.2 elements where they
    directly correspond.
-   Course title components allow for selective reordering and sorting
    (but not separate styling).


\[[edit](../index.php@title=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&action=edit&section=4.html "Edit section: Create the database objects")\]  Create the database objects 
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Create a new, empty database in a development SQL Server 2008
environment, and run the following T-SQL:

    --USE 
    --GO
    /*
    Sample SQL Server 2008 XCRI-CAP-1.2-compatible database
    Version 0.1
    2012-04-01
    Tavis Reddick
    This work is licensed under the Creative Commons Attribution 3.0 Unported License. To view a copy of this license, visit http://creativecommons.org/licenses/by/3.0/ or send a letter to Creative Commons, 444 Castro Street, Suite 900, Mountain View, California, 94041, USA.
    Please address comments to the XCRI forum:
    http://www.xcri.org/forum/topic.php?id=191
    */
    /****** Object:  Table [dbo].[Organization]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    SET ANSI_PADDING ON
    GO
    CREATE TABLE [dbo].[Organization](
        [OrganizationId] [smallint] IDENTITY(1,1) NOT NULL,
        [CommonName] [nvarchar](100) NOT NULL,
        [IndustryCode] [varchar](12) NULL,
        [IndustrialId] [varchar](12) NULL,
        [OrganizationalUnitOf] [smallint] NULL,
     CONSTRAINT [PK_Organization] PRIMARY KEY CLUSTERED 
    (
        [OrganizationId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    SET ANSI_PADDING OFF
    GO
    /****** Object:  XmlSchemaCollection [dbo].[XHTML]    Script Date: 04/01/2012 17:53:12 ******/
    CREATE XML SCHEMA COLLECTION [dbo].[XHTML] AS N''
    GO
    /****** Object:  UserDefinedDataType [dbo].[URI]    Script Date: 04/01/2012 17:53:11 ******/
    CREATE TYPE [dbo].[URI] FROM [nvarchar](100) NULL
    GO
    /****** Object:  Table [dbo].[Language]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[Language](
        [LanguageId] [nvarchar](50) NOT NULL,
        [ExtensionOf] [nvarchar](50) NULL,
        [ScriptOf] [nvarchar](50) NULL,
        [RegionOf] [nvarchar](50) NULL,
        [VariantOf] [nvarchar](50) NULL,
        [Description] [nvarchar](50) NOT NULL,
        [Comments] [nvarchar](255) NULL,
     CONSTRAINT [PK_Language] PRIMARY KEY CLUSTERED 
    (
        [LanguageId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'http://tools.ietf.org/rfc/bcp/bcp47.txt' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'Language'
    GO
    /****** Object:  Table [dbo].[Course]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[Course](
        [CourseId] [dbo].[URI] NOT NULL,
        [Url] [dbo].[URI] NULL,
     CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED 
    (
        [CourseId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'http://www.xcri.org/XCRI_CAP_1.2#the_.3Ccourse.3E_element' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'Course'
    GO
    /****** Object:  Table [dbo].[Vocabulary]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[Vocabulary](
        [VocabularyId] [dbo].[URI] NOT NULL,
        [Title] [nvarchar](255) NOT NULL,
        [Description] [nvarchar](255) NULL,
        [Creator] [nvarchar](255) NULL,
        [Source] [dbo].[URI] NULL,
        [Date] [date] NULL,
     CONSTRAINT [PK_Vocabulary] PRIMARY KEY CLUSTERED 
    (
        [VocabularyId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Persistent, unique, machine-readable URI.' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'Vocabulary', @level2type=N'COLUMN',@level2name=N'VocabularyId'
    GO
    EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Refer to Vocabulary Framework Document for the Course Data Programme.' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'Vocabulary'
    GO
    /****** Object:  Table [dbo].[Location]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    SET ANSI_PADDING ON
    GO
    CREATE TABLE [dbo].[Location](
        [LocationId] [smallint] IDENTITY(1,1) NOT NULL,
        [UriBase] [dbo].[URI] NULL,
        [Uri]  AS ([UriBase]+CONVERT([nvarchar](4),[LocationId],(0))) PERSISTED,
        [Address] [nvarchar](50) NULL,
        [Street] [nvarchar](50) NULL,
        [Town] [nvarchar](50) NULL,
        [Postcode] [nvarchar](12) NULL,
        [Phone] [nvarchar](20) NULL,
        [Fax] [nvarchar](20) NULL,
        [Email] [nvarchar](50) NULL,
        [Url] [dbo].[URI] NULL,
     CONSTRAINT [PK_Location] PRIMARY KEY CLUSTERED 
    (
        [LocationId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    SET ANSI_PADDING OFF
    GO
    /****** Object:  Table [dbo].[Qualification]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[Qualification](
        [QualificationId] [smallint] IDENTITY(1,1) NOT NULL,
        [Title] [nvarchar](100) NOT NULL,
        [Abbr] [nvarchar](10) NULL,
        [Description] [xml](DOCUMENT [dbo].[XHTML]) NULL,
        [EducationLevel] [nvarchar](255) NULL,
        [Type] [nvarchar](50) NULL,
        [Url] [nvarchar](50) NULL,
        [AwardedBy] [smallint] NULL,
        [AccreditedBy] [smallint] NULL,
     CONSTRAINT [PK_Qualification] PRIMARY KEY CLUSTERED 
    (
        [QualificationId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'http://www.xcri.org/XCRI_CAP_1.2#the_.3Cqualification.3E_element' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'Qualification'
    GO
    /****** Object:  Table [dbo].[ProviderVenue]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[ProviderVenue](
        [ProviderId] [smallint] NOT NULL,
        [LocationId] [smallint] NOT NULL,
     CONSTRAINT [PK_ProviderVenue] PRIMARY KEY CLUSTERED 
    (
        [ProviderId] ASC,
        [LocationId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    /****** Object:  Table [dbo].[CourseAbstract]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[CourseAbstract](
        [CourseId] [dbo].[URI] NOT NULL,
        [LanguageId] [nvarchar](50) NOT NULL,
        [Text] [nvarchar](140) NULL,
     CONSTRAINT [PK_CourseAbtract] PRIMARY KEY CLUSTERED 
    (
        [CourseId] ASC,
        [LanguageId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    /****** Object:  Table [dbo].[Term]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[Term](
        [TermId] [dbo].[URI] NOT NULL,
        [VocabularyId] [dbo].[URI] NOT NULL,
        [Language] [nvarchar](50) NULL,
        [Label] [nvarchar](100) NOT NULL,
        [Description] [nvarchar](255) NULL,
     CONSTRAINT [PK_Term] PRIMARY KEY CLUSTERED 
    (
        [TermId] ASC,
        [VocabularyId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Generic term entity.' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'Term'
    GO
    /****** Object:  Table [dbo].[CourseTitle]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[CourseTitle](
        [CourseId] [dbo].[URI] NOT NULL,
        [LanguageId] [nvarchar](50) NOT NULL,
        [Prefix] [nvarchar](50) NULL,
        [MainSort] [nvarchar](50) NOT NULL,
        [Suffix] [nvarchar](50) NULL,
     CONSTRAINT [PK_CourseTitle] PRIMARY KEY CLUSTERED 
    (
        [CourseId] ASC,
        [LanguageId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'Titles in 1+ languages broken into rearrangeable components.' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'CourseTitle'
    GO
    /****** Object:  Table [dbo].[CourseQualification]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[CourseQualification](
        [CourseId] [dbo].[URI] NOT NULL,
        [QualificationId] [smallint] NOT NULL,
     CONSTRAINT [PK_CourseQualification] PRIMARY KEY CLUSTERED 
    (
        [CourseId] ASC,
        [QualificationId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    /****** Object:  Table [dbo].[CourseDescription]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[CourseDescription](
        [CourseId] [dbo].[URI] NOT NULL,
        [LanguageId] [nvarchar](50) NOT NULL,
        [TermId] [dbo].[URI] NOT NULL,
        [VocabularyId] [dbo].[URI] NOT NULL,
        [Text] [xml](DOCUMENT [dbo].[XHTML]) NULL,
     CONSTRAINT [PK_Description] PRIMARY KEY CLUSTERED 
    (
        [CourseId] ASC,
        [LanguageId] ASC,
        [TermId] ASC,
        [VocabularyId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    /****** Object:  Table [dbo].[CourseCredit]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[CourseCredit](
        [CourseId] [dbo].[URI] NOT NULL,
        [CreditSchemeId] [dbo].[URI] NOT NULL,
        [CreditId] [dbo].[URI] NOT NULL,
        [Value] [smallint] NOT NULL,
     CONSTRAINT [PK_CourseCredit] PRIMARY KEY CLUSTERED 
    (
        [CourseId] ASC,
        [CreditSchemeId] ASC,
        [CreditId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    /****** Object:  Table [dbo].[CourseAttribute]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[CourseAttribute](
        [CourseId] [dbo].[URI] NOT NULL,
        [LanguageId] [nvarchar](50) NOT NULL,
        [TermId] [dbo].[URI] NOT NULL,
        [VocabularyId] [dbo].[URI] NOT NULL,
        [Text] [nvarchar](255) NULL,
     CONSTRAINT [PK_CourseSubject] PRIMARY KEY CLUSTERED 
    (
        [CourseId] ASC,
        [LanguageId] ASC,
        [TermId] ASC,
        [VocabularyId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    EXEC sys.sp_addextendedproperty @name=N'MS_Description', @value=N'http://www.xcri.org/XCRI_CAP_1.2#the_.3Csubject.3E_element' , @level0type=N'SCHEMA',@level0name=N'dbo', @level1type=N'TABLE',@level1name=N'CourseAttribute'
    GO
    /****** Object:  Table [dbo].[Presentation]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[Presentation](
        [PresentationId] [uniqueidentifier] ROWGUIDCOL  NOT NULL,
        [CourseId] [dbo].[URI] NOT NULL,
        [Start] [datetimeoffset](0) NULL,
        [End] [datetimeoffset](0) NULL,
        [ApplyFrom] [datetimeoffset](0) NULL,
        [ApplyUntil] [datetimeoffset](0) NULL,
        [ApplyTo] [dbo].[URI] NULL,
        [LanguageOfInstruction] [nvarchar](50) NULL,
        [LanguageOfAssessment] [nvarchar](50) NULL,
        [ProviderId] [smallint] NULL,
        [LocationId] [smallint] NULL,
     CONSTRAINT [PK__Presenta__B3613E5C42E1EEFE] PRIMARY KEY CLUSTERED 
    (
        [PresentationId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    /****** Object:  Table [dbo].[PresentationAttribute]    Script Date: 04/01/2012 17:53:11 ******/
    SET ANSI_NULLS ON
    GO
    SET QUOTED_IDENTIFIER ON
    GO
    CREATE TABLE [dbo].[PresentationAttribute](
        [PresentationId] [uniqueidentifier] NOT NULL,
        [LanguageId] [nvarchar](50) NOT NULL,
        [TermId] [dbo].[URI] NOT NULL,
        [VocabularyId] [dbo].[URI] NOT NULL,
        [Text] [nvarchar](255) NULL,
     CONSTRAINT [PK_PresentationAttribute] PRIMARY KEY CLUSTERED 
    (
        [PresentationId] ASC,
        [LanguageId] ASC,
        [TermId] ASC,
        [VocabularyId] ASC
    )WITH (PAD_INDEX  = OFF, STATISTICS_NORECOMPUTE  = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS  = ON, ALLOW_PAGE_LOCKS  = ON) ON [PRIMARY]
    ) ON [PRIMARY]
    GO
    /****** Object:  Default [DF_CourseAttribute_LanguageId]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseAttribute] ADD  CONSTRAINT [DF_CourseAttribute_LanguageId]  DEFAULT (N'en') FOR [LanguageId]
    GO
    /****** Object:  Default [DF__Presentat__Prese__44CA3770]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Presentation] ADD  CONSTRAINT [DF__Presentat__Prese__44CA3770]  DEFAULT (newsequentialid()) FOR [PresentationId]
    GO
    /****** Object:  Default [DF_Term_Language]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Term] ADD  CONSTRAINT [DF_Term_Language]  DEFAULT (N'en') FOR [Language]
    GO
    /****** Object:  ForeignKey [FK_CourseAbtract_Course]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseAbstract]  WITH CHECK ADD  CONSTRAINT [FK_CourseAbtract_Course] FOREIGN KEY([CourseId])
    REFERENCES [dbo].[Course] ([CourseId])
    GO
    ALTER TABLE [dbo].[CourseAbstract] CHECK CONSTRAINT [FK_CourseAbtract_Course]
    GO
    /****** Object:  ForeignKey [FK_CourseAbtract_Language]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseAbstract]  WITH CHECK ADD  CONSTRAINT [FK_CourseAbtract_Language] FOREIGN KEY([LanguageId])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[CourseAbstract] CHECK CONSTRAINT [FK_CourseAbtract_Language]
    GO
    /****** Object:  ForeignKey [FK_CourseAttribute_Course]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseAttribute]  WITH CHECK ADD  CONSTRAINT [FK_CourseAttribute_Course] FOREIGN KEY([CourseId])
    REFERENCES [dbo].[Course] ([CourseId])
    GO
    ALTER TABLE [dbo].[CourseAttribute] CHECK CONSTRAINT [FK_CourseAttribute_Course]
    GO
    /****** Object:  ForeignKey [FK_CourseAttribute_Language]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseAttribute]  WITH CHECK ADD  CONSTRAINT [FK_CourseAttribute_Language] FOREIGN KEY([LanguageId])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[CourseAttribute] CHECK CONSTRAINT [FK_CourseAttribute_Language]
    GO
    /****** Object:  ForeignKey [FK_CourseAttribute_Term]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseAttribute]  WITH CHECK ADD  CONSTRAINT [FK_CourseAttribute_Term] FOREIGN KEY([TermId], [VocabularyId])
    REFERENCES [dbo].[Term] ([TermId], [VocabularyId])
    GO
    ALTER TABLE [dbo].[CourseAttribute] CHECK CONSTRAINT [FK_CourseAttribute_Term]
    GO
    /****** Object:  ForeignKey [FK_CourseCredit_Course]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseCredit]  WITH CHECK ADD  CONSTRAINT [FK_CourseCredit_Course] FOREIGN KEY([CourseId])
    REFERENCES [dbo].[Course] ([CourseId])
    GO
    ALTER TABLE [dbo].[CourseCredit] CHECK CONSTRAINT [FK_CourseCredit_Course]
    GO
    /****** Object:  ForeignKey [FK_CourseCredit_Scheme]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseCredit]  WITH CHECK ADD  CONSTRAINT [FK_CourseCredit_Scheme] FOREIGN KEY([CreditId], [CreditSchemeId])
    REFERENCES [dbo].[Term] ([TermId], [VocabularyId])
    GO
    ALTER TABLE [dbo].[CourseCredit] CHECK CONSTRAINT [FK_CourseCredit_Scheme]
    GO
    /****** Object:  ForeignKey [FK_CourseDescription_Course]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseDescription]  WITH CHECK ADD  CONSTRAINT [FK_CourseDescription_Course] FOREIGN KEY([CourseId])
    REFERENCES [dbo].[Course] ([CourseId])
    GO
    ALTER TABLE [dbo].[CourseDescription] CHECK CONSTRAINT [FK_CourseDescription_Course]
    GO
    /****** Object:  ForeignKey [FK_CourseDescription_Language]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseDescription]  WITH CHECK ADD  CONSTRAINT [FK_CourseDescription_Language] FOREIGN KEY([LanguageId])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[CourseDescription] CHECK CONSTRAINT [FK_CourseDescription_Language]
    GO
    /****** Object:  ForeignKey [FK_CourseDescription_Term]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseDescription]  WITH CHECK ADD  CONSTRAINT [FK_CourseDescription_Term] FOREIGN KEY([TermId], [VocabularyId])
    REFERENCES [dbo].[Term] ([TermId], [VocabularyId])
    GO
    ALTER TABLE [dbo].[CourseDescription] CHECK CONSTRAINT [FK_CourseDescription_Term]
    GO
    /****** Object:  ForeignKey [FK_CourseQualification_Course]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseQualification]  WITH CHECK ADD  CONSTRAINT [FK_CourseQualification_Course] FOREIGN KEY([CourseId])
    REFERENCES [dbo].[Course] ([CourseId])
    GO
    ALTER TABLE [dbo].[CourseQualification] CHECK CONSTRAINT [FK_CourseQualification_Course]
    GO
    /****** Object:  ForeignKey [FK_CourseQualification_Qualification]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseQualification]  WITH CHECK ADD  CONSTRAINT [FK_CourseQualification_Qualification] FOREIGN KEY([QualificationId])
    REFERENCES [dbo].[Qualification] ([QualificationId])
    GO
    ALTER TABLE [dbo].[CourseQualification] CHECK CONSTRAINT [FK_CourseQualification_Qualification]
    GO
    /****** Object:  ForeignKey [FK_CourseTitle_Course]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseTitle]  WITH CHECK ADD  CONSTRAINT [FK_CourseTitle_Course] FOREIGN KEY([CourseId])
    REFERENCES [dbo].[Course] ([CourseId])
    GO
    ALTER TABLE [dbo].[CourseTitle] CHECK CONSTRAINT [FK_CourseTitle_Course]
    GO
    /****** Object:  ForeignKey [FK_CourseTitle_Language]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[CourseTitle]  WITH CHECK ADD  CONSTRAINT [FK_CourseTitle_Language] FOREIGN KEY([LanguageId])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[CourseTitle] CHECK CONSTRAINT [FK_CourseTitle_Language]
    GO
    /****** Object:  ForeignKey [FK_Language_Language]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Language]  WITH CHECK ADD  CONSTRAINT [FK_Language_Language] FOREIGN KEY([ExtensionOf])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[Language] CHECK CONSTRAINT [FK_Language_Language]
    GO
    /****** Object:  ForeignKey [FK_Language_Language1]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Language]  WITH CHECK ADD  CONSTRAINT [FK_Language_Language1] FOREIGN KEY([ScriptOf])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[Language] CHECK CONSTRAINT [FK_Language_Language1]
    GO
    /****** Object:  ForeignKey [FK_Language_Language2]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Language]  WITH CHECK ADD  CONSTRAINT [FK_Language_Language2] FOREIGN KEY([RegionOf])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[Language] CHECK CONSTRAINT [FK_Language_Language2]
    GO
    /****** Object:  ForeignKey [FK_Language_Language3]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Language]  WITH CHECK ADD  CONSTRAINT [FK_Language_Language3] FOREIGN KEY([VariantOf])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[Language] CHECK CONSTRAINT [FK_Language_Language3]
    GO
    /****** Object:  ForeignKey [FK_Organization_Organization]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Organization]  WITH CHECK ADD  CONSTRAINT [FK_Organization_Organization] FOREIGN KEY([OrganizationalUnitOf])
    REFERENCES [dbo].[Organization] ([OrganizationId])
    GO
    ALTER TABLE [dbo].[Organization] CHECK CONSTRAINT [FK_Organization_Organization]
    GO
    /****** Object:  ForeignKey [FK_Presentation_Course]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Presentation]  WITH CHECK ADD  CONSTRAINT [FK_Presentation_Course] FOREIGN KEY([CourseId])
    REFERENCES [dbo].[Course] ([CourseId])
    GO
    ALTER TABLE [dbo].[Presentation] CHECK CONSTRAINT [FK_Presentation_Course]
    GO
    /****** Object:  ForeignKey [FK_Presentation_LanguageOfAssessment]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Presentation]  WITH CHECK ADD  CONSTRAINT [FK_Presentation_LanguageOfAssessment] FOREIGN KEY([LanguageOfAssessment])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[Presentation] CHECK CONSTRAINT [FK_Presentation_LanguageOfAssessment]
    GO
    /****** Object:  ForeignKey [FK_Presentation_LanguageOfInstruction]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Presentation]  WITH CHECK ADD  CONSTRAINT [FK_Presentation_LanguageOfInstruction] FOREIGN KEY([LanguageOfInstruction])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[Presentation] CHECK CONSTRAINT [FK_Presentation_LanguageOfInstruction]
    GO
    /****** Object:  ForeignKey [FK_Presentation_ProviderVenue]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Presentation]  WITH CHECK ADD  CONSTRAINT [FK_Presentation_ProviderVenue] FOREIGN KEY([ProviderId], [LocationId])
    REFERENCES [dbo].[ProviderVenue] ([ProviderId], [LocationId])
    GO
    ALTER TABLE [dbo].[Presentation] CHECK CONSTRAINT [FK_Presentation_ProviderVenue]
    GO
    /****** Object:  ForeignKey [FK_PresentationAttribute_Language]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[PresentationAttribute]  WITH CHECK ADD  CONSTRAINT [FK_PresentationAttribute_Language] FOREIGN KEY([LanguageId])
    REFERENCES [dbo].[Language] ([LanguageId])
    GO
    ALTER TABLE [dbo].[PresentationAttribute] CHECK CONSTRAINT [FK_PresentationAttribute_Language]
    GO
    /****** Object:  ForeignKey [FK_PresentationAttribute_Presentation]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[PresentationAttribute]  WITH CHECK ADD  CONSTRAINT [FK_PresentationAttribute_Presentation] FOREIGN KEY([PresentationId])
    REFERENCES [dbo].[Presentation] ([PresentationId])
    GO
    ALTER TABLE [dbo].[PresentationAttribute] CHECK CONSTRAINT [FK_PresentationAttribute_Presentation]
    GO
    /****** Object:  ForeignKey [FK_PresentationAttribute_Term]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[PresentationAttribute]  WITH CHECK ADD  CONSTRAINT [FK_PresentationAttribute_Term] FOREIGN KEY([TermId], [VocabularyId])
    REFERENCES [dbo].[Term] ([TermId], [VocabularyId])
    GO
    ALTER TABLE [dbo].[PresentationAttribute] CHECK CONSTRAINT [FK_PresentationAttribute_Term]
    GO
    /****** Object:  ForeignKey [FK_ProviderVenue_Location]    Script Date: 04/01/2012 17:53:11 ******/
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
    /****** Object:  ForeignKey [FK_Qualification_AccreditedByOrganization]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Qualification]  WITH CHECK ADD  CONSTRAINT [FK_Qualification_AccreditedByOrganization] FOREIGN KEY([AccreditedBy])
    REFERENCES [dbo].[Organization] ([OrganizationId])
    GO
    ALTER TABLE [dbo].[Qualification] CHECK CONSTRAINT [FK_Qualification_AccreditedByOrganization]
    GO
    /****** Object:  ForeignKey [FK_Qualification_AwardedByOrganization]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Qualification]  WITH CHECK ADD  CONSTRAINT [FK_Qualification_AwardedByOrganization] FOREIGN KEY([AwardedBy])
    REFERENCES [dbo].[Organization] ([OrganizationId])
    GO
    ALTER TABLE [dbo].[Qualification] CHECK CONSTRAINT [FK_Qualification_AwardedByOrganization]
    GO
    /****** Object:  ForeignKey [FK_Term_Vocabulary]    Script Date: 04/01/2012 17:53:11 ******/
    ALTER TABLE [dbo].[Term]  WITH CHECK ADD  CONSTRAINT [FK_Term_Vocabulary] FOREIGN KEY([VocabularyId])
    REFERENCES [dbo].[Vocabulary] ([VocabularyId])
    ON UPDATE CASCADE
    ON DELETE CASCADE
    GO
    ALTER TABLE [dbo].[Term] CHECK CONSTRAINT [FK_Term_Vocabulary]
    GO


\[[edit](../index.php@title=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&action=edit&section=5.html "Edit section: Further topics")\]  Further topics 
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   Importing data is discussed in [Populating the sample SQL Server
    2008 XCRI-CAP-1.2-compatible relational
    database](Populating_the_sample_SQL_Server_2008_XCRI-CAP-1.2-compatible_relational_database.html "Populating the sample SQL Server 2008 XCRI-CAP-1.2-compatible relational database").
-   Exporting data as XCRI CAP 1.2 is discussed in [Sample SQL Server
    2008 code for extracting XCRI CAP 1.2 XML from a relational
    database](Sample_SQL_Server_2008_code_for_extracting_XCRI_CAP_1.2_XML_from_a_relational_database.html "Sample SQL Server 2008 code for extracting XCRI CAP 1.2 XML from a relational database").
-   Validation of output in the database
-   Storing of snapshots (in XML columns performing validation
    as above?)



Retrieved from
"[http://localhost/Sample\_SQL\_Server\_2008\_code\_for\_building\_an\_XCRI-CAP-1.2-compatible\_relational\_database](Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database.html)"

















##### Views



-   

    

    [Article](Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database.html)
-   

    

    [Discussion](../index.php@title=Talk%253ASample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&action=edit.html)
-   

    

    [Edit](../index.php@title=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&action=edit.html)
-   

    

    [History](../index.php@title=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&action=history.html)







##### Personal tools



-   

    

    [Log in / create
    account](../index.php@title=Special%253AUserlogin&returnto=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database.html)











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
    here](Special%253AWhatlinkshere/Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database.html)
-   

    

    [Related
    changes](Special%253ARecentchangeslinked/Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database.html)
-   

    

    [Upload file](Special%253AUpload.html)
-   

    

    [Special pages](Special%253ASpecialpages.html)
-   

    

    [Printable
    version](../index.php@title=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&printable=yes.html)
-   

    

    [Permanent
    link](../index.php@title=Sample_SQL_Server_2008_code_for_building_an_XCRI-CAP-1.2-compatible_relational_database&oldid=4368.html)















[![Powered by
MediaWiki](../skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 08:50, 2 April 2012.
-   

    

    This page has been accessed 4,705 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](Xcri%253APrivacy_policy.html "Xcri:Privacy policy")
-   

    

    [About Xcri](Xcri%253AAbout.html "Xcri:About")
-   

    

    [Disclaimers](Xcri%253AGeneral_disclaimer.html "Xcri:General disclaimer")




