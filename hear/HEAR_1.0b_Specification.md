---
layout: default
---






HEAR 1.0b Specification 
=======================



### From Xcri 







Jump to: [navigation](HEAR_1.0b_Specification#column-one),
[search](HEAR_1.0b_Specification#searchInput)



+--------------------------------------------------------------------------+
|                                                       |
|                                                                          |
| Contents                                                                 |
| --------                                                                 |
|                                                                          |
|                                                                    |
|                                                                          |
| -   [1 About](HEAR_1.0b_Specification#About)         |
|     -   [1.1 Status](HEAR_1.0b_Specification#Status)   |
|     -   [1.2 Patents](HEAR_1.0b_Specification#Patents) |
|     -   [1.3 Copyright and                                    |
|         License](HEAR_1.0b_Specification#Copyright_and_License)   |
|     -   [1.4 Inspiration and                                  |
|         acknowledgements](HEAR_1.0b_Specification#Inspiration_and |
| _acknowledgements)                                                       |
| -   [2 Introduction](HEAR_1.0b_Specification#Introdu |
| ction)                                                                   |
| -   [3 Normative    |
|     References](HEAR_1.0b_Specification#Normative_References)     |
| -   [4 Conformance](HEAR_1.0b_Specification#Conforma |
| nce)                                                                     |
| -   [5 HEAR         |
|     Documents](HEAR_1.0b_Specification#HEAR_Documents)            |
|     -   [5.1 The    |
|         HEAR Template](HEAR_1.0b_Specification#The_HEAR_Template) |
|     -   [5.2 Contextual                                       |
|         Information](HEAR_1.0b_Specification#Contextual_Informati |
| on)                                                                      |
| -   [6 XML Document |
|     Structure](HEAR_1.0b_Specification#XML_Document_Structure)    |
|     -   [6.1 Constraints](HEAR_1.0b_Specification#Cons |
| traints)                                                                 |
|     -   [6.2 the    |
|         &lt;achievementReport&gt;                                        |
|         element](HEAR_1.0b_Specification#the_.3CachievementReport |
| .3E_element)                                                             |
|         -   [6.2.1 Definition](HEAR_1.0b_Specification#D |
| efinition)                                                               |
|         -   [6.2.2 Main elements used within the                |
|             achievementReport                                            |
|             element](HEAR_1.0b_Specification#Main_elements_used_w |
| ithin_the_achievementReport_element)                                     |
|         -   [6.2.3 Elements used in the                         |
|             &lt;achievementReport&gt;                                    |
|             element](HEAR_1.0b_Specification#Elements_used_in_the |
| _.3CachievementReport.3E_element)                                        |
|         -   [6.2.4 Attributes used in the                       |
|             &lt;achievementReport&gt;                                    |
|             element](HEAR_1.0b_Specification#Attributes_used_in_t |
| he_.3CachievementReport.3E_element)                                      |
| -   [7 Definition   |
|     of Common                                                            |
|     Elements](HEAR_1.0b_Specification#Definition_of_Common_Elemen |
| ts)                                                                      |
|     -   [7.1 the    |
|         &lt;identifier&gt;                                               |
|         element](HEAR_1.0b_Specification#the_.3Cidentifier.3E_ele |
| ment)                                                                    |
|         -   [7.1.1 Definition](HEAR_1.0b_Specification#D |
| efinition_2)                                                             |
|         -   [7.1.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces)                                                               |
|     -   [7.2 the    |
|         &lt;title&gt;                                                    |
|         element](HEAR_1.0b_Specification#the_.3Ctitle.3E_element) |
|         -   [7.2.1 Definition](HEAR_1.0b_Specification#D |
| efinition_3)                                                             |
|         -   [7.2.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_2)                                                             |
| -   [8 Definition   |
|     of Other                                                             |
|     Elements](HEAR_1.0b_Specification#Definition_of_Other_Element |
| s)                                                                       |
|     -   [8.1 the    |
|         &lt;accessRequirements&gt;                                       |
|         element](HEAR_1.0b_Specification#the_.3CaccessRequirement |
| s.3E_element)                                                            |
|         -   [8.1.1 Definition](HEAR_1.0b_Specification#D |
| efinition_4)                                                             |
|         -   [8.1.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_3)                                                             |
|     -   [8.2 the    |
|         &lt;additionalAwards&gt;                                         |
|         element](HEAR_1.0b_Specification#the_.3CadditionalAwards. |
| 3E_element)                                                              |
|         -   [8.2.1 Definition](HEAR_1.0b_Specification#D |
| efinition_5)                                                             |
|         -   [8.2.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_4)                                                             |
|     -   [8.3 the    |
|         &lt;additionalInformation&gt;                                    |
|         element](HEAR_1.0b_Specification#the_.3CadditionalInforma |
| tion.3E_element)                                                         |
|         -   [8.3.1 Definition](HEAR_1.0b_Specification#D |
| efinition_6)                                                             |
|         -   [8.3.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_5)                                                             |
|         -   [8.3.3 Elements used in the                         |
|             &lt;additionalInformation&gt;                                |
|             element](HEAR_1.0b_Specification#Elements_used_in_the |
| _.3CadditionalInformation.3E_element)                                    |
|     -   [8.4 the    |
|         &lt;aim&gt;                                                      |
|         element](HEAR_1.0b_Specification#the_.3Caim.3E_element)   |
|         -   [8.4.1 Definition](HEAR_1.0b_Specification#D |
| efinition_7)                                                             |
|         -   [8.4.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_6)                                                             |
|     -   [8.5 the    |
|         &lt;assessment&gt;                                               |
|         element](HEAR_1.0b_Specification#the_.3Cassessment.3E_ele |
| ment)                                                                    |
|         -   [8.5.1 Definition](HEAR_1.0b_Specification#D |
| efinition_8)                                                             |
|         -   [8.5.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_7)                                                             |
|         -   [8.5.3 Elements used in the &lt;assessment&gt;      |
|             element](HEAR_1.0b_Specification#Elements_used_in_the |
| _.3Cassessment.3E_element)                                               |
|     -   [8.6 the    |
|         &lt;assessmentType&gt;                                           |
|         element](HEAR_1.0b_Specification#the_.3CassessmentType.3E |
| _element)                                                                |
|         -   [8.6.1 Definition](HEAR_1.0b_Specification#D |
| efinition_9)                                                             |
|     -   [8.7 the    |
|         &lt;assessmentWeight&gt;                                         |
|         element](HEAR_1.0b_Specification#the_.3CassessmentWeight. |
| 3E_element)                                                              |
|         -   [8.7.1 Definition](HEAR_1.0b_Specification#D |
| efinition_10)                                                            |
|     -   [8.8 the    |
|         &lt;attempts&gt;                                                 |
|         element](HEAR_1.0b_Specification#the_.3Cattempts.3E_eleme |
| nt)                                                                      |
|         -   [8.8.1 Definition](HEAR_1.0b_Specification#D |
| efinition_11)                                                            |
|     -   [8.9 the    |
|         &lt;awardedBy&gt;                                                |
|         element](HEAR_1.0b_Specification#the_.3CawardedBy.3E_elem |
| ent)                                                                     |
|         -   [8.9.1 Definition](HEAR_1.0b_Specification#D |
| efinition_12)                                                            |
|         -   [8.9.2 Attributes](HEAR_1.0b_Specification#A |
| ttributes)                                                               |
|     -   [8.10 the   |
|         &lt;capacity&gt;                                                 |
|         element](HEAR_1.0b_Specification#the_.3Ccapacity.3E_eleme |
| nt)                                                                      |
|         -   [8.10.1 Definition](HEAR_1.0b_Specification#D |
| efinition_13)                                                            |
|     -   [8.11 the   |
|         &lt;certificationOfTheHEAR&gt;                                   |
|         element](HEAR_1.0b_Specification#the_.3CcertificationOfTh |
| eHEAR.3E_element)                                                        |
|         -   [8.11.1 Definition](HEAR_1.0b_Specification#D |
| efinition_14)                                                            |
|         -   [8.11.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_8)                                                             |
|         -   [8.11.3 Elements used in the                         |
|             &lt;certificationOfTheHEAR&gt;                               |
|             element](HEAR_1.0b_Specification#Elements_used_in_the |
| _.3CcertificationOfTheHEAR.3E_element)                                   |
|     -   [8.12 the   |
|         &lt;course&gt;                                                   |
|         element](HEAR_1.0b_Specification#the_.3Ccourse.3E_element |
| )                                                                        |
|         -   [8.12.1 Definition](HEAR_1.0b_Specification#D |
| efinition_15)                                                            |
|         -   [8.12.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_9)                                                             |
|         -   [8.12.3 Common elements used in the &lt;course&gt;   |
|             element at all                                               |
|             levels](HEAR_1.0b_Specification#Common_elements_used_ |
| in_the_.3Ccourse.3E_element_at_all_levels)                               |
|         -   [8.12.4 Additional elements used in the              |
|             &lt;course&gt; element at Programme                          |
|             Level](HEAR_1.0b_Specification#Additional_elements_us |
| ed_in_the_.3Ccourse.3E_element_at_Programme_Level)                       |
|         -   [8.12.5 Additional elements used in the              |
|             &lt;course&gt; element at other                              |
|             levels](HEAR_1.0b_Specification#Additional_elements_u |
| sed_in_the_.3Ccourse.3E_element_at_other_levels)                         |
|     -   [8.13 the   |
|         &lt;dateOfBirth&gt;                                              |
|         element](HEAR_1.0b_Specification#the_.3CdateOfBirth.3E_el |
| ement)                                                                   |
|         -   [8.13.1 Definition](HEAR_1.0b_Specification#D |
| efinition_16)                                                            |
|         -   [8.13.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_10)                                                            |
|     -   [8.14 the   |
|         &lt;dualAward&gt;                                                |
|         element](HEAR_1.0b_Specification#the_.3CdualAward.3E_elem |
| ent)                                                                     |
|         -   [8.14.1 Definition](HEAR_1.0b_Specification#D |
| efinition_17)                                                            |
|         -   [8.14.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_11)                                                            |
|     -   [8.15 the   |
|         &lt;duration&gt;                                                 |
|         element](HEAR_1.0b_Specification#the_.3Cduration.3E_eleme |
| nt)                                                                      |
|         -   [8.15.1 Definition](HEAR_1.0b_Specification#D |
| efinition_18)                                                            |
|     -   [8.16 the   |
|         &lt;ePortfolioUrl&gt;                                            |
|         element](HEAR_1.0b_Specification#the_.3CePortfolioUrl.3E_ |
| element)                                                                 |
|         -   [8.16.1 Definition](HEAR_1.0b_Specification#D |
| efinition_19)                                                            |
|     -   [8.17 the   |
|         &lt;familyName&gt;                                               |
|         element](HEAR_1.0b_Specification#the_.3CfamilyName.3E_ele |
| ment)                                                                    |
|         -   [8.17.1 Definition](HEAR_1.0b_Specification#D |
| efinition_20)                                                            |
|         -   [8.17.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_12)                                                            |
|     -   [8.18 the   |
|         &lt;fullName&gt;                                                 |
|         element](HEAR_1.0b_Specification#the_.3CfullName.3E_eleme |
| nt)                                                                      |
|         -   [8.18.1 Definition](HEAR_1.0b_Specification#D |
| efinition_21)                                                            |
|         -   [8.18.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_13)                                                            |
|     -   [8.19 the   |
|         &lt;fullNameOfficial&gt;](HEAR_1.0b_Specification#the_.3C |
| fullNameOfficial.3E)                                                     |
|         -   [8.19.1 Definition](HEAR_1.0b_Specification#D |
| efinition_22)                                                            |
|     -   [8.20 the   |
|         &lt;furtherInformation&gt;                                       |
|         element](HEAR_1.0b_Specification#the_.3CfurtherInformatio |
| n.3E_element)                                                            |
|         -   [8.20.1 Definition](HEAR_1.0b_Specification#D |
| efinition_23)                                                            |
|         -   [8.20.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_14)                                                            |
|     -   [8.21 the   |
|         &lt;furtherStudy&gt;                                             |
|         element](HEAR_1.0b_Specification#the_.3CfurtherStudy.3E_e |
| lement)                                                                  |
|         -   [8.21.1 Definition](HEAR_1.0b_Specification#D |
| efinition_24)                                                            |
|         -   [8.21.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_15)                                                            |
|     -   [8.22 the   |
|         &lt;givenNames&gt;                                               |
|         element](HEAR_1.0b_Specification#the_.3CgivenNames.3E_ele |
| ment)                                                                    |
|         -   [8.22.1 Definition](HEAR_1.0b_Specification#D |
| efinition_25)                                                            |
|         -   [8.22.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_16)                                                            |
|     -   [8.23 the   |
|         &lt;gradingScheme&gt;                                            |
|         element](HEAR_1.0b_Specification#the_.3CgradingScheme.3E_ |
| element)                                                                 |
|         -   [8.23.1 Definition](HEAR_1.0b_Specification#D |
| efinition_26)                                                            |
|     -   [8.24 the   |
|         &lt;identifierDescription&gt;                                    |
|         element](HEAR_1.0b_Specification#the_.3CidentifierDescrip |
| tion.3E_element)                                                         |
|         -   [8.24.1 Definition](HEAR_1.0b_Specification#D |
| efinition_27)                                                            |
|         -   [8.24.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_17)                                                            |
|     -   [8.25 the   |
|         &lt;informationSources&gt;                                       |
|         element](HEAR_1.0b_Specification#the_.3CinformationSource |
| s.3E_element)                                                            |
|         -   [8.25.1 Definition](HEAR_1.0b_Specification#D |
| efinition_28)                                                            |
|         -   [8.25.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_18)                                                            |
|     -   [8.26 the   |
|         &lt;isPartOf&gt;                                                 |
|         element](HEAR_1.0b_Specification#the_.3CisPartOf.3E_eleme |
| nt)                                                                      |
|         -   [8.26.1 Definition](HEAR_1.0b_Specification#D |
| efinition_29)                                                            |
|     -   [8.27 the   |
|         &lt;issueDateHear&gt;                                            |
|         element](HEAR_1.0b_Specification#the_.3CissueDateHear.3E_ |
| element)                                                                 |
|         -   [8.27.1 Definition](HEAR_1.0b_Specification#D |
| efinition_30)                                                            |
|         -   [8.27.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_19)                                                            |
|     -   [8.28 the   |
|         &lt;issueDateQualification&gt;                                   |
|         element](HEAR_1.0b_Specification#the_.3CissueDateQualific |
| ation.3E_element)                                                        |
|         -   [8.28.1 Definition](HEAR_1.0b_Specification#D |
| efinition_31)                                                            |
|         -   [8.28.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_20)                                                            |
|     -   [8.29 the   |
|         &lt;issuer&gt;                                                   |
|         element](HEAR_1.0b_Specification#the_.3Cissuer.3E_element |
| )                                                                        |
|         -   [8.29.1 Definition](HEAR_1.0b_Specification#D |
| efinition_32)                                                            |
|         -   [8.29.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_21)                                                            |
|         -   [8.29.3 Elements used in the &lt;issuer&gt;          |
|             element](HEAR_1.0b_Specification#Elements_used_in_the |
| _.3Cissuer.3E_element)                                                   |
|     -   [8.30 the   |
|         &lt;learner&gt;                                                  |
|         element](HEAR_1.0b_Specification#the_.3Clearner.3E_elemen |
| t)                                                                       |
|         -   [8.30.1 Definition](HEAR_1.0b_Specification#D |
| efinition_33)                                                            |
|         -   [8.30.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_22)                                                            |
|         -   [8.30.3 Elements used in the &lt;learner&gt;         |
|             element](HEAR_1.0b_Specification#Elements_used_in_the |
| _.3Clearner.3E_element)                                                  |
|     -   [8.31 the   |
|         &lt;learningOutcome&gt;                                          |
|         element](HEAR_1.0b_Specification#the_.3ClearningOutcome.3 |
| E_element)                                                               |
|         -   [8.31.1 Definition](HEAR_1.0b_Specification#D |
| efinition_34)                                                            |
|         -   [8.31.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_23)                                                            |
|     -   [8.32 the   |
|         &lt;level&gt;                                                    |
|         element](HEAR_1.0b_Specification#the_.3Clevel.3E_element) |
|         -   [8.32.1 Definition](HEAR_1.0b_Specification#D |
| efinition_35)                                                            |
|     -   [8.33 the   |
|         &lt;minimumStandards&gt;                                         |
|         element](HEAR_1.0b_Specification#the_.3CminimumStandards. |
| 3E_element)                                                              |
|         -   [8.33.1 Definition](HEAR_1.0b_Specification#D |
| efinition_36)                                                            |
|         -   [8.33.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_24)                                                            |
|     -   [8.34 the   |
|         &lt;presentation&gt;                                             |
|         element](HEAR_1.0b_Specification#the_.3Cpresentation.3E_e |
| lement)                                                                  |
|         -   [8.34.1 Definition](HEAR_1.0b_Specification#D |
| efinition_37)                                                            |
|         -   [8.34.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_25)                                                            |
|         -   [8.34.3 Common elements used in the                  |
|             &lt;presentation&gt; element at all                          |
|             levels](HEAR_1.0b_Specification#Common_elements_used_ |
| in_the_.3Cpresentation.3E_element_at_all_levels)                         |
|         -   [8.34.4 Elements used in the &lt;presentation&gt;    |
|             element at Programme Level                                   |
|             only](HEAR_1.0b_Specification#Elements_used_in_the_.3 |
| Cpresentation.3E_element_at_Programme_Level_only)                        |
|     -   [8.35 the   |
|         &lt;prizes&gt;                                                   |
|         element](HEAR_1.0b_Specification#the_.3Cprizes.3E_element |
| )                                                                        |
|         -   [8.35.1 Definition](HEAR_1.0b_Specification#D |
| efinition_38)                                                            |
|         -   [8.35.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_26)                                                            |
|     -   [8.36 the   |
|         &lt;professionalStatus&gt;                                       |
|         element](HEAR_1.0b_Specification#the_.3CprofessionalStatu |
| s.3E_element)                                                            |
|         -   [8.36.1 Definition](HEAR_1.0b_Specification#D |
| efinition_39)                                                            |
|         -   [8.36.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_27)                                                            |
|     -   [8.37 the   |
|         &lt;provider&gt;                                                 |
|         element](HEAR_1.0b_Specification#the_.3Cprovider.3E_eleme |
| nt)                                                                      |
|         -   [8.37.1 Definition](HEAR_1.0b_Specification#D |
| efinition_40)                                                            |
|         -   [8.37.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_28)                                                            |
|         -   [8.37.3 Elements used in the &lt;provider&gt;        |
|             element](HEAR_1.0b_Specification#Elements_used_in_the |
| _.3Cprovider.3E_element)                                                 |
|     -   [8.38 the   |
|         &lt;providerStatus&gt;                                           |
|         element](HEAR_1.0b_Specification#the_.3CproviderStatus.3E |
| _element)                                                                |
|         -   [8.38.1 Definition](HEAR_1.0b_Specification#D |
| efinition_41)                                                            |
|     -   [8.39 the   |
|         &lt;qualification&gt;                                            |
|         element](HEAR_1.0b_Specification#the_.3Cqualification.3E_ |
| element)                                                                 |
|         -   [8.39.1 Definition](HEAR_1.0b_Specification#D |
| efinition_42)                                                            |
|         -   [8.39.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_29)                                                            |
|         -   [8.39.3 Elements used in the &lt;qualification&gt;   |
|             element](HEAR_1.0b_Specification#Elements_used_in_the |
| _.3Cqualification.3E_element)                                            |
|     -   [8.40 the   |
|         &lt;qualificationHolderTitle&gt;                                 |
|         element](HEAR_1.0b_Specification#the_.3CqualificationHold |
| erTitle.3E_element)                                                      |
|         -   [8.40.1 Definition](HEAR_1.0b_Specification#D |
| efinition_43)                                                            |
|         -   [8.40.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_30)                                                            |
|     -   [8.41 the   |
|         &lt;recognisedActivities&gt;                                     |
|         element](HEAR_1.0b_Specification#the_.3CrecognisedActivit |
| ies.3E_element)                                                          |
|         -   [8.41.1 Definition](HEAR_1.0b_Specification#D |
| efinition_44)                                                            |
|         -   [8.41.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_31)                                                            |
|     -   [8.42 the   |
|         &lt;referenceData&gt;                                            |
|         element](HEAR_1.0b_Specification#the_.3CreferenceData.3E_ |
| element)                                                                 |
|         -   [8.42.1 Definition](HEAR_1.0b_Specification#D |
| efinition_45)                                                            |
|         -   [8.42.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_32)                                                            |
|         -   [8.42.3 Elements used in the &lt;referenceData&gt;   |
|             element](HEAR_1.0b_Specification#Elements_used_in_the |
| _.3CreferenceData.3E_element)                                            |
|     -   [8.43 the   |
|         &lt;referenceDataItem&gt;                                        |
|         element](HEAR_1.0b_Specification#the_.3CreferenceDataItem |
| .3E_element)                                                             |
|         -   [8.43.1 Definition](HEAR_1.0b_Specification#D |
| efinition_46)                                                            |
|         -   [8.43.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_33)                                                            |
|     -   [8.44 the   |
|         &lt;regulations&gt;                                              |
|         element](HEAR_1.0b_Specification#the_.3Cregulations.3E_el |
| ement)                                                                   |
|         -   [8.44.1 Definition](HEAR_1.0b_Specification#D |
| efinition_47)                                                            |
|         -   [8.44.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_34)                                                            |
|     -   [8.45 the   |
|         &lt;result&gt;                                                   |
|         element](HEAR_1.0b_Specification#the_.3Cresult.3E_element |
| )                                                                        |
|         -   [8.45.1 Definition](HEAR_1.0b_Specification#D |
| efinition_48)                                                            |
|         -   [8.45.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_35)                                                            |
|         -   [8.45.3 Attributes used in the &lt;result&gt;        |
|             element](HEAR_1.0b_Specification#Attributes_used_in_t |
| he_.3Cresult.3E_element)                                                 |
|     -   [8.46 the   |
|         &lt;signature&gt;                                                |
|         element](HEAR_1.0b_Specification#the_.3Csignature.3E_elem |
| ent)                                                                     |
|         -   [8.46.1 Definition](HEAR_1.0b_Specification#D |
| efinition_49)                                                            |
|         -   [8.46.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_36)                                                            |
|     -   [8.47 the   |
|         &lt;specialFeature&gt;                                           |
|         element](HEAR_1.0b_Specification#the_.3CspecialFeature.3E |
| _element)                                                                |
|         -   [8.47.1 Definition](HEAR_1.0b_Specification#D |
| efinition_50)                                                            |
|         -   [8.47.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_37)                                                            |
|     -   [8.48 the   |
|         &lt;subject&gt;                                                  |
|         element](HEAR_1.0b_Specification#the_.3Csubject.3E_elemen |
| t)                                                                       |
|         -   [8.48.1 Definition](HEAR_1.0b_Specification#D |
| efinition_51)                                                            |
|         -   [8.48.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_38)                                                            |
|     -   [8.49 the   |
|         &lt;terminalAward&gt;                                            |
|         element](HEAR_1.0b_Specification#the_.3CterminalAward.3E_ |
| element)                                                                 |
|         -   [8.49.1 Definition](HEAR_1.0b_Specification#D |
| efinition_52)                                                            |
|         -   [8.49.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_39)                                                            |
|     -   [8.50 the   |
|         &lt;type&gt;                                                     |
|         element](HEAR_1.0b_Specification#the_.3Ctype.3E_element)  |
|         -   [8.50.1 Definition](HEAR_1.0b_Specification#D |
| efinition_53)                                                            |
|         -   [8.50.2 Namespaces](HEAR_1.0b_Specification#N |
| amespaces_40)                                                            |
| -   [9 XML Schema   |
|     and                                                                  |
|     Instance](HEAR_1.0b_Specification#XML_Schema_and_Instance)    |
+--------------------------------------------------------------------------+


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=1 "Edit section: About")\] About
================================================================================================================================================================================================

*Back to [HEAR
home](HEAR "http://www.xcri.org/HEAR")*

Authors and Editors:

-   Alan Paull (alan@alanpaull.co.uk)
-   Scott Wilson (scott.bradley.wilson@gmail.com)


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=2 "Edit section: Status")\] Status

This is currently a working draft of version 1.0b.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=3 "Edit section: Patents")\] Patents

This specification is subject to a royalty free patent policy.

There are no known patents covering any of this work. If you think that
part of this work may be subject to an existing or pending patent,
please email the editors.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=4 "Edit section: Copyright and License")\] Copyright and License

TBC


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=5 "Edit section: Inspiration and acknowledgements")\] Inspiration and acknowledgements

The authors wish to acknowledge the work of the supporting HEAR
Technical Specification Working Group, in particular:

-   John Bolland
-   Sarah Davies
-   Andy Dowling
-   Richard Entwistle
-   Simon Grant
-   Rob Ward
-   James Wong
-   Andy Youell


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=6 "Edit section: Introduction")\] Introduction
==============================================================================================================================================================================================================

The Higher Education Achievement Report (HEAR) technical specification
defines an XML format for the content of the HEAR. It is intended to
enable the interoperability of descriptions of the Higher Education
achievement of learners between Higher Education providers, employers,
brokers and other relevant organisations. It is compliant with the \[CEN
European Learner Mobility Workshop Agreement CWA 16132
\]

\
A HEAR XML instance document typically consists of a top-level
&lt;achievementReport&gt; element, encapsulating:

-   a single &lt;issuer&gt; responsible for issuing the HEAR,
-   a single &lt;learner&gt;, the subject of the HEAR,
-   one or more &lt;provider&gt; elements, containing descriptions of
    the learning undertaken and a single exit qualification awarded as a
    result,
-   additional information about academic and non-academic achievements
    during the period of study not directly related to the qualification
    awarded,
-   formal certification of the HEAR.

The following diagram illustrates the main elements of the
specification.

[![Image:HEAROutlineInformationModel2011-02-17.png](http://www.xcri.org/wiki/images/4/42/HEAROutlineInformationModel2011-02-17.png){width="449"
height="485"}](./Image:HEAROutlineInformationModel2011-02-17.png "Image:HEAROutlineInformationModel2011-02-17.png")


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=7 "Edit section: Normative References")\] Normative References
==============================================================================================================================================================================================================================

*Back to [HEAR
home](HEAR "http://www.xcri.org/HEAR")*

\[XCRI-CAP 1.2\] eXchanging Course Related Information Course
Advertising Profile. See
[http://www.xcri.org/XCRI\_CAP\_1.2](XCRI_CAP_1.2 "http://www.xcri.org/XCRI_CAP_1.2"){.external
.free}

\[EN 15982\] EN 15982: Metadata For Learning Opportunities (Advertising)

\[ISO 15836\] ISO 15836: Dublin Core Element Set

\[ISO 8601\] ISO 8601:Data elements and interchange formats ‚Äî
Information interchange ‚Äî Representation of dates and times

\[W3C DTF\] W3C Date and Time Formats. See


\[W3C XML Schema\] W3C XML Schema. See 

\[CWA 16077\] CWA 16077: Educational Credit Information Model


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=8 "Edit section: Conformance")\] Conformance
============================================================================================================================================================================================================

*Back to [HEAR
home](HEAR "http://www.xcri.org/HEAR")*

There are two classes of application that can conform to this
specification:

-   A *producer* is a class of application that produces HEAR XML
    documents
-   An *consumer* is a class of application that consumers HEAR XML
    documents

A product MAY belong to both classes.

A **strictly conforming instance** is a set of structured information
constituted only of elements and attributes defined by this
specification and *fully qualified refinements* of the elements defined
in this specification.

A **fully qualified refinement** is defined for the purpose of
conformance as an element that explicitly extends an element defined by
this specification. A fully qualified refinement must be capable of
being processed according to the semantics of the element it extends.

A **conforming instance** MAY contain additional elements and attributes
not defined by this specification.

A **conforming producer** MUST be capable of generating and sharing
*strictly conforming instances*.

A **conforming consumer** MUST be capable of processing *strictly
conforming instances*.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=9 "Edit section: HEAR Documents")\] HEAR Documents
==================================================================================================================================================================================================================

A producer MUST create HEAR documents that are valid XML documents.

A producer MUST create HEAR documents with the achievementReport element
as its top-level element.

A consumer MUST be able to process a valid HEAR XML document.




Guidelines *This section is not normative*

**Multilingual HEAR data sets:** Producers should create multiple XML
instances for HEAR data sets required entirely in more than one
language, for example English and Welsh.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=10 "Edit section: The HEAR Template")\] The HEAR Template
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*This section is not normative*

This specification covers the structure of the XML representation of the
HEAR data; it does not define the structure of the HEAR document per se.
The following information is provided to give context to the
specification of the data elements. Readers are asked to refer to the
[HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf"){.external
.text} for more details.

A HEAR must adhere to the prescribed template described in the [HEAR
Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf "http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf"){.external
.text}. The Guidance defines the sections of the HEAR and requires that
sections are numbered and follow the sequence and explanatory guidance
given in the Guidance Document.

The structure of the template for a HEAR is as follows:

-   Contextual information
-   Section 1. Information identifying the holder of the qualification
-   Section 2. Information identifying the qualification
-   Section 3. Information on the level of the qualification
-   Section 4. Information on the contents and results gained
-   Section 5. Information on the function of the qualification
-   Section 6. Additional information
-   Section 7. Certification of the HEAR
-   Section 8. Information on the national higher education system

On output for printing or for viewing electronically a HEAR should
contain section numbering and standard statements as described in the
[HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf "http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf"){.external
.text}.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=11 "Edit section: Contextual Information")\] Contextual Information
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

*This section is not normative*

The [HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf "http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf"){.external
.text} gives details of statements that should be included in the HEAR
at specified points, for example a standard statement at the start of
the HEAR should be included in order to meet the requirements of the
European Diploma Supplement (DS). Information about these statements is
included in the Guidance sections of this specification.




Guidelines In the Contextual Information of the HEAR,
institutions are advised to include the following statements:

*This Higher Education Achievement Report follows the model developed by
the European Commission, Council of Europe and UNESCO/CEPES for the
Diploma Supplement.*

*The purpose of the Supplement is to provide sufficient recognition of
qualifications (diplomas, degrees, certificates etc). It is designed to
provide a description of the nature, level, context and status of the
studies that were pursued and successfully completed by the individual
named on the original qualifications to which this Supplement is
appended. It should be free from any value judgements, equivalence
statements or suggestions about recognition. Information in all eight
sections should be provided. Where information is not provided, an
explanation should give the reason why.*

Producers are not required to include these statements or any other
statements recommended by the HEAR Implementation Steering Group within
the HEAR XML Data Set. Inclusion of these statements within HEAR
documents can be implemented using a variety of methods. This
specification makes provision for inclusion of of these statements in
the HEAR XML Data Set if desired by systems designers.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=12 "Edit section: XML Document Structure")\] XML Document Structure
===================================================================================================================================================================================================================================

This section defines the root achievementReport element and relates the
main information elements of the HEAR XML document structure to this
root element. Definitions of the other elements are given in [Definition
of Common
Elements](HEAR_1.0b_Specification#Definition_of_Common_Elements "http://www.xcri.org/HEAR_1.0b_Specification#Definition_of_Common_Elements"){.external
.text} and [Definition of Other
Elements](HEAR_1.0b_Specification#Definition_of_Other_Elements "http://www.xcri.org/HEAR_1.0b_Specification#Definition_of_Other_Elements"){.external
.text} sections.

A HEAR XML document includes information drawn from Student Records
Systems, Course Information Systems and supporting systems that will be
created and maintained by various different administrative processes and
academic practices within academic institutions. The XML document
specification builds upon information about learners, descriptions of
programmes and other learning opportunity structures, information about
modules and other educational components enrolled on by learners,
assessment results and other accredited achievements for each completed
learning opportunity, and information about the awarding and providing
organisations themselves.

[Click for a diagram of the HEAR XML data set
structure.](./Image:AchievementReport2.png "http://www.xcri.org/Image:AchievementReport2.png"){.external
.text}


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=13 "Edit section: Constraints")\] Constraints
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1.  A valid HEAR MUST contain exactly one issuer element.
2.  A valid HEAR MUST contain exactly one learner element.
3.  A valid HEAR MUST contain one or more provider element.
4.  A valid HEAR MUST contain exactly one qualification element.
5.  A valid HEAR MUST contain exactly one top level course element.
6.  A valid HEAR MUST contain exactly one additionalInformation element.
    Guidance on its contents is given in the [HEAR Guidance
    Document](http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf "http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf").
7.  A valid HEAR MUST contain exactly one
    certificationOfTheHEAR element.
8.  A valid exit HEAR &lt;achievementReport @status="1"&gt; MUST contain
    an assessment element for the programme and for each module or
    course component that the learner took as part of the programme or
    that is an additional academic credit-bearing student achievement
    detailed in the HEAR.
9.  A valid exit HEAR &lt;achievementReport @status="1"&gt; MUST contain
    exactly one result element for each presentation taken by
    the learner.
10. The qualification instance MUST relate to the learner specified in
    the learner element.
11. The qualification MUST have been achieved as a result of completion
    of exactly one top level course instance.
12. Producers MUST ensure that the qualification instance of the HEAR
    relates directly to the top level course instance in a
    one-to-one relationship.
13. Producers MUST ensure that provider elements contain information
    only about providers of courses undertaken by the learner in the
    context of the qualification awarded.
14. Each assessment element MUST relate only to the learner and the
    specific version of the presentation on which the learner
    was assessed.
15. The level element MUST contain the numerical position of the
    qualification in the relevant national qualifications framework.
16. Where an element has more than one identifier, it MUST NOT contain
    more than one identifier without an explicitly-defined encoding
    scheme, and this MUST be A Uniform Resource Identifier (URI)
    conforming to the URL scheme as specified by [IETF RFC
    3986](http://tools.ietf.org/html/rfc3986 "http://tools.ietf.org/html/rfc3986").
17. The top level course instance SHOULD define the Programme Level
    learning opportunity undertaken by the learner.
18. Course instances at levels lower than programme level SHOULD be
    related to the top level course instance using the isPartOf element,
    either directly through inclusion of the identifier of the top level
    course, or indirectly through inclusion of the identifier of another
    course element. See
    [example](HEAR_1.0b_Specification#Additional_elements_used_in_the_.3Ccourse.3E_element_at_other_levels "http://www.xcri.org/HEAR_1.0b_Specification#Additional_elements_used_in_the_.3Ccourse.3E_element_at_other_levels").
19. Instances of associate qualifications or other achievements not
    forming part of the learner's academic achievements as a result of
    following the indicated programme of study MAY be recorded in the
    Additional Information element.
20. Further course elements MAY be included to reflect the institution's
    programme component structures.
21. A valid HEAR MAY contain zero or one referenceData elements
    containing 'boilerplate' text.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=14 "Edit section: the &lt;achievementReport&gt; element")\] the &lt;achievementReport&gt; element
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=15 "Edit section: Definition")\] Definition

The default root element for a HEAR.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=16 "Edit section: Main elements used within the achievementReport element")\] Main elements used within the achievementReport element

*This section is not normative*

These main elements are listed here, so that the major components of a
HEAR are clearly indicated. Some of these elements are sub-elements of
top level elements, as noted in this guidance.

-   issuer
-   learner
-   awardedBy
-   qualification
-   provider
-   course
-   presentation
-   assessment
-   certificationOfTheHEAR
-   additionalInformation

**awardedBy:** A component of qualification (see
[XCRI-CAP](XCRI_CAP_1.2#the_.3Cqualification.3E_element "http://www.xcri.org/XCRI_CAP_1.2#the_.3Cqualification.3E_element"){.external
.text} specification).

**qualification:** A component of course (see
[XCRI-CAP](XCRI_CAP_1.2#the_.3Cqualification.3E_element "http://www.xcri.org/XCRI_CAP_1.2#the_.3Cqualification.3E_element"){.external
.text} specification).

**course:** A component of provider (see
[XCRI-CAP](XCRI_CAP_1.2#the_.3Ccourse.3E_element "http://www.xcri.org/XCRI_CAP_1.2#the_.3Ccourse.3E_element"){.external
.text} specification).

**presentation:** A component of course (see
[XCRI-CAP](XCRI_CAP_1.2#the_.3Cpresentation.3E_element "http://www.xcri.org/XCRI_CAP_1.2#the_.3Cpresentation.3E_element"){.external
.text} specification).

**assessment:** A component of presentation (see
[XCRI-CAP](XCRI_CAP_1.2#the_.3Cassessment.3E_element "http://www.xcri.org/XCRI_CAP_1.2#the_.3Cassessment.3E_element"){.external
.text} specification)


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=17 "Edit section: Elements used in the &lt;achievementReport&gt; element")\] Elements used in the &lt;achievementReport&gt; element

-   referenceData (optional, zero or one)
-   issuer (required, exactly one)
-   learner (required, exactly one)
-   provider (required, one or more)
-   additionalInformation (required, exactly one)
-   certificationOfTheHEAR (required, exactly one)


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=18 "Edit section: Attributes used in the &lt;achievementReport&gt; element")\] Attributes used in the &lt;achievementReport&gt; element

-   @id\. Unique identifier for this HEAR.
-   @status\. Defines the type of this HEAR; enumeration: 1=Exit,
    2=Formative, 3=Deleted.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=19 "Edit section: Definition of Common Elements")\] Definition of Common Elements
=================================================================================================================================================================================================================================================

Many of the elements in the HEAR use the following common elements. Also
see [Definition of Other
Elements](HEAR_1.0b_Specification#Definition_of_Other_Elements "http://www.xcri.org/HEAR_1.0b_Specification#Definition_of_Other_Elements"){.external
.text}. For elements re-used from other namespaces (for example Dublin
Core, XCRI) refer to documentation for those specifications.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=20 "Edit section: the &lt;identifier&gt; element")\] the &lt;identifier&gt; element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=21 "Edit section: Definition")\] Definition

An unambiguous reference to the resource within a given context. See
\[EN 15982\] and \[ISO 15836\].


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=22 "Edit section: Namespaces")\] Namespaces

Uses namespace dc: .

Example:

     http://www.bolton.ac.uk
     23424341414
     1234


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=23 "Edit section: the &lt;title&gt; element")\] the &lt;title&gt; element
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=24 "Edit section: Definition")\] Definition

The name of the resource.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=25 "Edit section: Namespaces")\] Namespaces

See \[EN 15982\] and \[ISO 15836\].

Uses namespace dc: .


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=26 "Edit section: Definition of Other Elements")\] Definition of Other Elements
===============================================================================================================================================================================================================================================


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=27 "Edit section: the &lt;accessRequirements&gt; element")\] the &lt;accessRequirements&gt; element
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=28 "Edit section: Definition")\] Definition

Details of the nature and length of qualifications or periods of study
required before starting the programme.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=29 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=30 "Edit section: the &lt;additionalAwards&gt; element")\] the &lt;additionalAwards&gt; element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=31 "Edit section: Definition")\] Definition

Information about academic (credit-based) and non-academic awards made
to the learner.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=32 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=33 "Edit section: the &lt;additionalInformation&gt; element")\] the &lt;additionalInformation&gt; element
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=34 "Edit section: Definition")\] Definition

Details of the richer picture of verified student achievement, including
additional awards (with or without academic credit), additional
recognised activities, and university, professional and departmental
prizes.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=35 "Edit section: Namespaces")\] Namespaces

Uses elm: European Learner Mobility Achievement Information (EuroLMAI),
for which see CWA 16132.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=36 "Edit section: Elements used in the &lt;additionalInformation&gt; element")\] Elements used in the &lt;additionalInformation&gt; element

-   **prizes** (optional, zero, one or many)
-   **additionalAwards** (optional, zero, one or many)
-   **recognisedActivities** (optional, zero, one or many)
-   **informationSources** (optional, zero, one or many)
-   **ePortfolioUrl** (optional, zero or one)
-   **furtherInformation** (optional, zero, one or many)


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=37 "Edit section: the &lt;aim&gt; element")\] the &lt;aim&gt; element
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=38 "Edit section: Definition")\] Definition

Describes the aim(s) of the programme.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=39 "Edit section: Namespaces")\] Namespaces

Uses mlo:\[EN 15982\] EN 15982: Metadata For Learning Opportunities
(Advertising)

Represented as mlo:objective.




Guidelines *This section is not normative*

    
    ...
         
              
                   
                        To provide flexible teaching and learning programmes of high quality, in which students can develop their own interests.
                        To provide a stimulating and supportive environment for all students to work in.
                        To provide an education that will enable graduates to follow a variety of careers, including higher degrees and research.
                        To enable all students to have a broad appreciation of Biological Sciences and advanced knowledge of one or more areas.
                        To enable all students to develop subject-specific knowledge with practical and transferable skills.
                        To enable all students to experience, within the 4 year options, work in an external research laboratory or European University.
                   
              
         
    




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=40 "Edit section: the &lt;assessment&gt; element")\] the &lt;assessment&gt; element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=41 "Edit section: Definition")\] Definition

The details of the way in which the learner's performance in the
presentation of the course was judged.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=42 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Uses elm: European Learner Mobility Achievement Information (EuroLMAI),
for which see [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf"){.external
.text}.

Uses eds: [European Diploma
Supplement](http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp "http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp"){.external
.text}


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=43 "Edit section: Elements used in the &lt;assessment&gt; element")\] Elements used in the &lt;assessment&gt; element

-   **identifier** (required, exactly one), dc:identifier
-   **assessmentType** (required, exactly one)
-   **assessmentWeight** (optional, zero or one)
-   **attempts** (optional, zero or one)
-   **result** (optional, zero, one or many)
-   **gradingScheme** (required, exactly one)




Guidelines **result:** Required in an exit HEAR, at least one per
assessment.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=44 "Edit section: the &lt;assessmentType&gt; element")\] the &lt;assessmentType&gt; element
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=45 "Edit section: Definition")\] Definition

Description of the style of the assessment.




Guidelines *This section is not normative*

**assessmentType:** It is recommended that producers use an encoding
scheme or controlled vocabulary for this item.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=46 "Edit section: the &lt;assessmentWeight&gt; element")\] the &lt;assessmentWeight&gt; element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=47 "Edit section: Definition")\] Definition

Weighting of the assessment result as a proportion of the overall
assessment for the presentation.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=48 "Edit section: the &lt;attempts&gt; element")\] the &lt;attempts&gt; element
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=49 "Edit section: Definition")\] Definition

Number of times the learner has made at the assessment.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=50 "Edit section: the &lt;awardedBy&gt; element")\] the &lt;awardedBy&gt; element
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=51 "Edit section: Definition")\] Definition

This element identifies and names the recognised organisation (Awarding
Body) that confers the qualification upon the learner.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=52 "Edit section: Attributes")\] Attributes

-   @idRef\. The idRef attribute MUST identify the Awarding Body specified in
    the awardedBy element. It MUST be A Uniform Resource Identifier (URI)
    conforming to the URL scheme as specified by [IETF RFC
    3986](http://tools.ietf.org/html/rfc3986 "http://tools.ietf.org/html/rfc3986").




Note Where the Awarding Body is not the provider, a second
provider element should be created that contains the relevant details of
the awarding body. The identifier in the awardedBy element identifies
this organisation, and the provider element for the awarding body must
contain &lt;providerStatus&gt; and a course element that identifies the
programme, the qualification and confirms the awarding body through the
&lt;qualification&gt; and &lt;awardedBy&gt; structure. This structure
enables compliance with XCRI-CAP and EuroLMI.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=53 "Edit section: the &lt;capacity&gt; element")\] the &lt;capacity&gt; element
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=54 "Edit section: Definition")\] Definition

The official post of the certifying individual.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=55 "Edit section: the &lt;certificationOfTheHEAR&gt; element")\] the &lt;certificationOfTheHEAR&gt; element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=56 "Edit section: Definition")\] Definition

Provides evidence that the HEAR is a genuine document produced by the
authorised organisation.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=57 "Edit section: Namespaces")\] Namespaces

Uses namespace dc: 


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=58 "Edit section: Elements used in the &lt;certificationOfTheHEAR&gt; element")\] Elements used in the &lt;certificationOfTheHEAR&gt; element

-   **identifier** (required, exactly one), dc:identifier. Uniquely
    identifies this version of the HEAR data set for this learner.
-   **issueDateHear** (required, exactly one)
-   **fullNameOfficial** (required, exactly one)
-   **capacity** (required, exactly one)
-   **signature** (optional, zero or one).


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=59 "Edit section: the &lt;course&gt; element")\] the &lt;course&gt; element
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=60 "Edit section: Definition")\] Definition

A course element provides details of a learning opportunity offered by a
learning provider.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=61 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Uses mlo: \[EN 15982\] EN 15982: Metadata For Learning Opportunities
(Advertising)

Uses namespace dc: 


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=62 "Edit section: Common elements used in the &lt;course&gt; element at all levels")\] Common elements used in the &lt;course&gt; element at all levels

-   **identifier** (required, exactly one), dc:identifier
-   **title** (required, exactly one), dc:title. Full official name of
    the programme.
-   **type** (required, exactly one), dc:type
-   **credit** (optional, multiple), mlo:credit (defined in mlo)
-   **presentation** (required, exactly one)


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=63 "Edit section: Additional elements used in the &lt;course&gt; element at Programme Level")\] Additional elements used in the &lt;course&gt; element at Programme Level

-   **aim** (required, exactly one), mlo:objective.
-   **learningOutcome** (required, one or more)
-   **specialFeature** (optional, zero, one or many)
-   **qualification** (required, exactly one)


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=64 "Edit section: Additional elements used in the &lt;course&gt; element at other levels")\] Additional elements used in the &lt;course&gt; element at other levels

-   **isPartOf** (required, exactly one)




Guidelines *This section is not normative*

Programme and course component linkage example, in relation to
constraint 'Course instances at levels lower than programme level should
be related to the top level course instance using the isPartOf element,
either directly through inclusion of the identifier of the top level
course, or indirectly through inclusion of the identifier of another
course element':

        
            
            1234
            Information and Communications Undergraduate Programme
        
        
            
            1234-01
            Digital Media and Communications - Stage 1
            1234
        
        
            
            M223
            Information Literacies for the Digital Age
            1234-01
        

**credit:** credit values should contain credits achieved by the
learner. If this is not possible, display required credits.

\




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=65 "Edit section: the &lt;dateOfBirth&gt; element")\] the &lt;dateOfBirth&gt; element
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=66 "Edit section: Definition")\] Definition

Date when the learner was born. This value MUST be in ISO 8601 date
format as refined by W3C DTF 'Complete Date': yyyy-mm-dd (example:
"1985-05-16").


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=67 "Edit section: Namespaces")\] Namespaces

Uses scop: the SEMIC-EU Core Person Specification (not yet published in
machine readable form), which is compatible with EuroLMAI.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=68 "Edit section: the &lt;dualAward&gt; element")\] the &lt;dualAward&gt; element
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=69 "Edit section: Definition")\] Definition

Gives details if the qualification is a dual award, for example between
two UK institutions or between a UK and European institution.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=70 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=71 "Edit section: the &lt;duration&gt; element")\] the &lt;duration&gt; element
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=72 "Edit section: Definition")\] Definition

The length of the programme.

The content of this element MUST be human readable text of the form
'value' followed by 'unit of time', for example 'Three years'. The
duration SHOULD be expressed in years, unless the course is shorter than
two years, in which case an expression in months or weeks is acceptable.

Producers MAY include a machine-readable attribute 'interval' that
follows the ISO 8601 standard.




Guidelines *This section is not normative*

Example

        Three years




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=73 "Edit section: the &lt;ePortfolioUrl&gt; element")\] the &lt;ePortfolioUrl&gt; element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=74 "Edit section: Definition")\] Definition

A hypertext link to the learner's ePortfolio.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=75 "Edit section: the &lt;familyName&gt; element")\] the &lt;familyName&gt; element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=76 "Edit section: Definition")\] Definition

Full family or surname, as included on official documents, such as a
passport.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=77 "Edit section: Namespaces")\] Namespaces

Uses elm: European Learner Mobility Achievement Information (EuroLMAI).


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=78 "Edit section: the &lt;fullName&gt; element")\] the &lt;fullName&gt; element
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=79 "Edit section: Definition")\] Definition

The complete name of the learner; components should be those included on
official documents, such as a passport.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=80 "Edit section: Namespaces")\] Namespaces

Uses elm: European Learner Mobility Achievement Information (EuroLMAI).


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=81 "Edit section: the &lt;fullNameOfficial&gt;")\] the &lt;fullNameOfficial&gt;
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=82 "Edit section: Definition")\] Definition

Full name of the official certifying the HEAR.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=83 "Edit section: the &lt;furtherInformation&gt; element")\] the &lt;furtherInformation&gt; element
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=84 "Edit section: Definition")\] Definition

Information within the Additional Information element not covered
elsewhere.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=85 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=86 "Edit section: the &lt;furtherStudy&gt; element")\] the &lt;furtherStudy&gt; element
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=87 "Edit section: Definition")\] Definition

Indicates if, within the country of origin, the qualification normally
provides access (not admission) to further academic and/or professional
study, especially leading to any specific qualifications, or levels of
study.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=88 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.




Guidelines *This section is not normative*

**furtherStudy:** Include the grades or standards normally necessary to
allow progression within the EHEA.

For example:

*Access to postgraduate study: Bologna FQ-EHEA 3rd cycle PhD or MD.*

*Access to postgraduate study: Bologna FQ-EHEA 2nd cycle degree or
diploma.*




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=89 "Edit section: the &lt;givenNames&gt; element")\] the &lt;givenNames&gt; element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=90 "Edit section: Definition")\] Definition

All given or first names in the order specified by the learner, as
included on official documents, such as a passport.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=91 "Edit section: Namespaces")\] Namespaces

Uses elm: European Learner Mobility Achievement Information (EuroLMAI).


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=92 "Edit section: the &lt;gradingScheme&gt; element")\] the &lt;gradingScheme&gt; element
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=93 "Edit section: Definition")\] Definition

Information about the grading scheme used for the assessment of a
presentation.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=94 "Edit section: the &lt;identifierDescription&gt; element")\] the &lt;identifierDescription&gt; element
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=95 "Edit section: Definition")\] Definition

Used to indicate the provenance of the identifier or identifiers.
Required text for the HUSID is as follows:

"HUSID (HESA Unique Student Identifier) is the unique national
identifying number for students registered at a UK university. It is
defined by HESA, the UK's Higher Education Statistics Agency."


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=96 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=97 "Edit section: the &lt;informationSources&gt; element")\]  the &lt;informationSources&gt; element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=98 "Edit section: Definition")\] Definition

Further information sources and references where more details on the
qualification could be sought.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=99 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=100 "Edit section: the &lt;isPartOf&gt; element")\] the &lt;isPartOf&gt; element
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=101 "Edit section: Definition")\] Definition

Indicates the parent course element.

The isPartOf element MUST contain only the identifier of the parent
course element.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=102 "Edit section: the &lt;issueDateHear&gt; element")\] the &lt;issueDateHear&gt; element
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=103 "Edit section: Definition")\] Definition

Date and time of the production of this HEAR.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=104 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

xcri:dateOrDateTimeDType


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=105 "Edit section: the &lt;issueDateQualification&gt; element")\] the &lt;issueDateQualification&gt; element
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=106 "Edit section: Definition")\] Definition

Date on which the qualification was awarded.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=107 "Edit section: Namespaces")\] Namespaces

Uses elm: European Learner Mobility Achievement Information (EuroLMAI),
for which see CWA 16132.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=108 "Edit section: the &lt;issuer&gt; element")\] the &lt;issuer&gt; element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=109 "Edit section: Definition")\] Definition

The organisation that is responsible for producing the HEAR.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=110 "Edit section: Namespaces")\] Namespaces

Uses namespace dc: 


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=111 "Edit section: Elements used in the &lt;issuer&gt; element")\] Elements used in the &lt;issuer&gt; element

-   **identifier**, dc:identifier (required, one or more)
-   **title**, dc:title (required, one or more)




Guidelines *This section is not normative*

**identifier**: This element identifiers the issuing organisation, which
may be a different organisation from the provider or the awarding body,
for example a broker.

**issuer**: This element must not contain any other elements. Further
elements describing the organisation(s) offering the course or awarding
the qualification must be contained in the provider element.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=112 "Edit section: the &lt;learner&gt; element")\] the &lt;learner&gt; element
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=113 "Edit section: Definition")\] Definition

Information identifying the holder of the qualification.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=114 "Edit section: Namespaces")\] Namespaces

Uses elm: European Learner Mobility Achievement Information (EuroLMAI).

Uses scop: the SEMIC-EU Core Person Specification (not yet published in
machine readable form), which is compatible with EuroLMAI.

Uses namespace dc: 


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=115 "Edit section: Elements used in the &lt;learner&gt; element")\] Elements used in the &lt;learner&gt; element

-   **identifier** (required, one or more), dc:identifier. Unique
    identifier for the learner. Where the HESA Unique Student
    Identifier (HUSID) is known, for example stored in the Student
    Record System, this value MUST be the learner's HUSID. In other
    cases a different authoritative identifier MUST be used. For
    identifiers other than the HUSID, ULN or SCN implementers MUST
    either extend the identifier element to include another namespace or
    indicate the provenance of the identifier in the comment attribute.
-   **identifierDescription** (optional, zero, one or more)
-   **familyName** (required, exactly one)
-   **givenNames** (required, exactly one)
-   **fullName** (required, exactly one)
-   **dateOfBirth** (required, exactly one)




Guidelines *This section is not normative*

**identifier**: Alternatives recommended in this specification include
the Unique Learner Number (ULN) and the Scottish Candidate Number (SCN).
Namespace refinements for these identifiers are included in the HEAR XML
schema. An internal identifier from an issuer, provider or awarding body
can also be included.

**dateOfBirth**: Note that this specification does not prescribe the
final form output for date (for example in a PDF or paper document);
implementers may wish to present the date to end users in an alternative
format. Additionally there may be applications, such as outputs for
employers, in which the inclusion of the learner's birthday is not
required.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=116 "Edit section: the &lt;learningOutcome&gt; element")\] the &lt;learningOutcome&gt; element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=117 "Edit section: Definition")\] Definition

Describes the overall learning outcome(s) of the programme.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=118 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=119 "Edit section: the &lt;level&gt; element")\] the &lt;level&gt; element
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=120 "Edit section: Definition")\] Definition

Numerical position of the qualification in the relevant national
qualifications framework.

The level element MUST contain the numerical position of the
qualification in the relevant national qualifications framework.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=121 "Edit section: the &lt;minimumStandards&gt; element")\] the &lt;minimumStandards&gt; element
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=122 "Edit section: Definition")\] Definition

Details of the regulations covering the minimum standards required to
secure the qualification; therefore applies to the Programme only.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=123 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=124 "Edit section: the &lt;presentation&gt; element")\] the &lt;presentation&gt; element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=125 "Edit section: Definition")\] Definition

Details of the instance or version of the course enrolled on.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=126 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Uses mlo: \[EN 15982\] EN 15982: Metadata For Learning Opportunities
(Advertising)

Uses namespace dc: 


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=127 "Edit section: Common elements used in the &lt;presentation&gt; element at all levels")\] Common elements used in the &lt;presentation&gt; element at all levels

-   **identifier** (required, exactly one), dc:identifier. Where
    presentation does not have its own identifier, producers SHOULD use
    and repeat the host course identifier
-   **assessment** (optional, zero, one or many). In an exit HEAR this
    element MUST be present for each presentation, otherwise it
    is optional.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=128 "Edit section: Elements used in the &lt;presentation&gt; element at Programme Level only")\] Elements used in the &lt;presentation&gt; element at Programme Level only

-   **start** (required, exactly one), mlo:start (defined in mlo)
-   **end** (required, exactly one), xcri:end (defined in xcri)
-   **accessRequirements** (required, exactly one)
-   **minimumStandards** (required, exactly one)
-   **duration** (required, exactly one)
-   **studyMode** (required, exactly one), xcri:studyMode (defined
    in xcri)
-   **languageOfInstruction** (required, at least one),
    mlo:languageOfInstruction (defined in mlo)
-   **languageOfAssessment** (required, at least one),
    xcri:languageOfAssessment (defined in xcri)




Guidelines *This section is not normative*

There are no additional elements only used in the &lt;presentation&gt;
element at other levels.

**title:** Producers should draw the title from the course element, not
the presentation element.

**accessRequirements**: Producers may implement this content using
'boilerplate' text and a hyperlink to specific documents held elsewhere;
in this case, implementers should have regard to the persistence of the
hyperlinks and the associated content, for example: "Detailed
information regarding admission to the programme is available in the
University‚Äôs on-line Prospectus at:
www.easthampton.ac.uk/admissions/ugprospectus/06." See [HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf "http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf"){.external
.text}, section 3.3.

**minimumStandards**: See [HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf "http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf"){.external
.text}, section 4.2.

**Output of languageOfInstruction and languageOfAssessment:** Consumers
should present final form output of these elements as human readable
text.

**Absence of languageOfInstruction and languageOfAssessment:** Where
these elements are missing, consumers should interpret this as meaning
that the language of instruction and assessment was English (en-GB).




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=129 "Edit section: the &lt;prizes&gt; element")\] the &lt;prizes&gt; element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=130 "Edit section: Definition")\] Definition

Information about university, professional and departmental prizes
awarded to the learner.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=131 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=132 "Edit section: the &lt;professionalStatus&gt; element")\] the &lt;professionalStatus&gt; element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=133 "Edit section: Definition")\] Definition

Details of any rights to practise or other professional standing
accorded to holders of the award.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=134 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.




Guidelines *This section is not normative*

The institution may use a generic statement from a professional body or
one of its own devising (see [HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf "http://www.alanpaull.co.uk/HEAR/documents/Integrated_HEAR_UPDATE_Pack_140411.pdf"){.external
.text}).




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=135 "Edit section: the &lt;provider&gt; element")\] the &lt;provider&gt; element
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=136 "Edit section: Definition")\] Definition

An organisation that offers one or more courses.




Note Where the provider is also the awarding body, the provider
identifier MUST match the awardedBy identifier.




### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=137 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: 


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=138 "Edit section: Elements used in the &lt;provider&gt; element")\] Elements used in the &lt;provider&gt; element

-   **identifier** (required, at least one), dc:identifier. Unique
    identifier for the provider.
-   **title** (required, at least one), dc:title. Full official name of
    the provider.
-   **description** (optional, zero or one), dc:description
-   **providerStatus** (required, one only)
-   **course** (required, at least one)


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=139 "Edit section: the &lt;providerStatus&gt; element")\] the &lt;providerStatus&gt; element
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=140 "Edit section: Definition")\] Definition

Describes the legal status of the provider, for example as either a
'recognised body' or a 'listed body'.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=141 "Edit section: the &lt;qualification&gt; element")\] the &lt;qualification&gt; element
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=142 "Edit section: Definition")\] Definition

A status awarded to or conferred on a learner by an awarding body.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=143 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Uses elm: European Learner Mobility Achievement Information (EuroLMAI),
for which see [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf"){.external
.text}.

Uses eds: [European Diploma
Supplement](http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp "http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp"){.external
.text}

Uses namespace dc: 


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=144 "Edit section: Elements used in the &lt;qualification&gt; element")\] Elements used in the &lt;qualification&gt; element

-   **identifier** (required, exactly one), dc:identifier. Unique
    identifier for the qualification.
-   **title** (required, exactly one), dc:title. Full official name of
    the award.
-   **regulations** (required, exactly one)
-   **dualAward** (optional, zero or one)
-   **professionalStatus** (optional, zero or one)
-   **furtherStudy** (optional, zero or one)
-   **terminalAward** (optional, zero or one)
-   **subject** (required, at least one), dc:subject
-   **level** (required, exactly one)
-   **qualificationHolderTitle** (optional, zero or one),
    qualificationHolderTitle (eds)
-   **issueDateQualification** (required, exactly one), issueDate (elm)
-   **awardedBy** (required, exactly one)


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=145 "Edit section: the &lt;qualificationHolderTitle&gt; element")\] the &lt;qualificationHolderTitle&gt; element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=146 "Edit section: Definition")\] Definition

Nationally accepted title conferred by the award, for example *Bachelor
of Science (Honours)*.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=147 "Edit section: Namespaces")\] Namespaces

Uses eds: [European Diploma
Supplement](http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp "http://europass.cedefop.europa.eu/europass/home/vernav/InformationOn/EuropassDiplomaSupplement.csp"){.external
.text}


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=148 "Edit section: the &lt;recognisedActivities&gt; element")\] the &lt;recognisedActivities&gt; element
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=149 "Edit section: Definition")\] Definition

Information about other recognised non-credit-bearing activities
undertaken by the learner.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=150 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=151 "Edit section: the &lt;referenceData&gt; element")\] the &lt;referenceData&gt; element
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=152 "Edit section: Definition")\] Definition

Container for standard, repeated or generic text used in the HEAR.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=153 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=154 "Edit section: Elements used in the &lt;referenceData&gt; element")\] Elements used in the &lt;referenceData&gt; element

-   **referenceDataItem** (required, one or more)


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=155 "Edit section: the &lt;referenceDataItem&gt; element")\] the &lt;referenceDataItem&gt; element
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=156 "Edit section: Definition")\] Definition

Holds standard, repeated or generic text ('boilerplate' text). This text
will typically be recommended text from the [HEAR Guidance
Document](http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf "http://www.alanpaull.co.uk/HEAR/documents/HEAR_Guidance_DRAFT_FINAL_V6.pdf"){.external
.text}. It can also be used for generic assessment grading schemes that
might be repeated for a large number of modules, or for standardised
learning outcomes, so that these pieces of text can be referenced rather
than repeated.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=157 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=158 "Edit section: the &lt;regulations&gt; element")\] the &lt;regulations&gt; element
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=159 "Edit section: Definition")\] Definition

Describes the regulations concerning degree-awarding powers in the UK.




Guidelines *This section is not normative*

The recommended text is: "The power to award degrees is regulated by law
in the UK."




### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=160 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=161 "Edit section: the &lt;result&gt; element")\] the &lt;result&gt; element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=162 "Edit section: Definition")\] Definition

The actual outcome of a presentation for a learner as stated by a
provider or issuer.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=163 "Edit section: Namespaces")\] Namespaces

Uses elm: European Learner Mobility Achievement Information (EuroLMAI),
for which see [CWA
16132](http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf "http://www.cen-wslt.din.de/sixcms_upload/media/3378/CWA16132.pdf"){.external
.text}.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=164 "Edit section: Attributes used in the &lt;result&gt; element")\] Attributes used in the &lt;result&gt; element

-   @resultType. Indicates whether the result is a mark, grade
    or similar.




Guidelines *This section is not normative*

-   **result**: Where any zeros or mark reductions have occurred, it is
    recommended that producers record them here.



-   **@resultType**: It is recommended that producers use an encoding
    scheme or controlled vocabulary for this item.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=165 "Edit section: the &lt;signature&gt; element")\] the &lt;signature&gt; element
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=166 "Edit section: Definition")\] Definition

A reference to an image of a signature of the responsible official.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=167 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Represented as xcri:imageDType.




Guidelines *This section is not normative*

Producers should implement specific security measures to protect the
image. This element is concerned with the graphical image of the
signature, not with the digital signature. The actual graphical image
should be external to the XML.

It is recommended that producers protect any HEAR document with an
appropriate digital signature to ensure document authenticity and
integrity.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=168 "Edit section: the &lt;specialFeature&gt; element")\] the &lt;specialFeature&gt; element
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=169 "Edit section: Definition")\] Definition

Any particular features that help define the programme that are not
covered elsewhere.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=170 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=171 "Edit section: the &lt;subject&gt; element")\] the &lt;subject&gt; element
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=172 "Edit section: Definition")\] Definition

Main field(s) of study for the qualification.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=173 "Edit section: Namespaces")\] Namespaces

Uses namespace dc: .




Guidelines *This section is not normative*

**subject:** Producers should put each main field of study in a separate
element. On output, the elements should be concatenated to form one
string. There is no nationally approved vocabulary for the subject in a
HEAR. Use the institution's own terminology. If subjects or fields of
study are not held in respect of qualifications, use the subjects in
respect of the top level course (programme) element.




\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=174 "Edit section: the &lt;terminalAward&gt; element")\] the &lt;terminalAward&gt; element
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=175 "Edit section: Definition")\] Definition

Specifies if the qualification is a terminal (end) award or part of a
hierarchy of awards.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=176 "Edit section: Namespaces")\] Namespaces

Uses namespace xcri: .

Extension of xcri:descriptionDType.


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=177 "Edit section: the &lt;type&gt; element")\] the &lt;type&gt; element
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=178 "Edit section: Definition")\] Definition

Indicates the position of the course in a hierarchy with Programme at
the top and Module or Unit at the bottom; for example programme, a
module-level component or a grouping component such as semester,
programme year, level or subject of a programme.


### \[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=179 "Edit section: Namespaces")\] Namespaces

Uses namespace dc: .


\[[edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit&section=180 "Edit section: XML Schema and Instance")\] XML Schema and Instance
======================================================================================================================================================================================================================================

*This section is not normative*

A W3C XML Schema is available at
.

A sample XML instance file is available at
.

XCRI-CAP 1.2 schema and supporting schemas are available from the XCRI
[subversion
repository](http://code.google.com/p/xcri-schemas/ "http://code.google.com/p/xcri-schemas/"){.external
.text}.



Retrieved from
"[http://www.xcri.org/HEAR\_1.0b\_Specification](HEAR_1.0b_Specification)"

















##### Views



-   

    

    [Article](HEAR_1.0b_Specification)
-   

    

    [Discussion](./Talk:HEAR_1.0b_Specification)
-   

    

    [Edit](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=edit)
-   

    

    [History](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&action=history)







##### Personal tools



-   

    

    [Log in / create
    account](http://www.xcri.org/wiki/index.php?title=Special:Userlogin&returnto=HEAR_1.0b_Specification)











[](XCRI_Wiki "XCRI Wiki")





##### Navigation



-   

    

    [XCRI Wiki](XCRI_Wiki)
-   

    

    [XCRI website](http://www.xcri.org/)
-   

    

    [Current events](Current_events)
-   

    

    [Recent changes](./Special:Recentchanges)
-   

    

    [Help](./Help:Contents)







##### Search





 









##### Toolbox



-   

    

    [What links here](./Special:Whatlinkshere/HEAR_1.0b_Specification)
-   

    

    [Related
    changes](./Special:Recentchangeslinked/HEAR_1.0b_Specification)
-   

    

    [Upload file](./Special:Upload)
-   

    

    [Special pages](./Special:Specialpages)
-   

    

    [Printable
    version](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&printable=yes)
-   

    

    [Permanent
    link](http://www.xcri.org/wiki/index.php?title=HEAR_1.0b_Specification&oldid=3902)















[![Powered by
MediaWiki](http://www.xcri.org/wiki/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.mediawiki.org/)





[![Attribution 3.0
](http://i.creativecommons.org/l/by/3.0/88x31.png)](http://creativecommons.org/licenses/by/3.0/)



-   

    

    This page was last modified 12:22, 19 January 2012.
-   

    

    This page has been accessed 68,737 times.
-   

    

    Content is available under [Attribution
    3.0](http://creativecommons.org/licenses/by/3.0/ "http://creativecommons.org/licenses/by/3.0/").
-   

    

    [Privacy policy](./Xcri:Privacy_policy "Xcri:Privacy policy")
-   

    

    [About Xcri](./Xcri:About "Xcri:About")
-   

    

    [Disclaimers](./Xcri:General_disclaimer "Xcri:General disclaimer")




