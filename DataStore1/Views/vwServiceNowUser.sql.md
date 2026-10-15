# Source: `DBs/AzureSingleDB/DataStore1/Views/vwServiceNowUser.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/DataStore1/Views/vwServiceNowUser.sql`
- SHA-256 of original file: `41fd0d52b3639e9fa54d37dcba9b5a12d5ba21076ba93245243a111a4eff7ec1`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql

CREATE VIEW [DataStore1].[vwServiceNowUser]
AS
SELECT
    TRY_CAST(
        SUBSTRING(U.[sys_id], 1, 8) + '-' + 
        SUBSTRING(U.[sys_id], 9, 4) + '-' + 
        SUBSTRING(U.[sys_id], 13, 4) + '-' +
        SUBSTRING(U.[sys_id], 17, 4) + '-' + 
        SUBSTRING(U.[sys_id], 21, 12)
    AS UNIQUEIDENTIFIER)                                                                    AS [Id]
    ,COALESCE(DU.[u_organization_unit], '_N/A')                                             AS [OrganizationUnit]
    ,COALESCE(DU.[u_organization_unit_description], '_N/A')                                 AS [OrganizationUnitDescription]
    ,CASE 
        WHEN U.[sys_class_name] = 'u_users_deme_user' THEN 'User'
        WHEN U.[sys_class_name] = 'u_users_deme_vessel' THEN 'Vessel'
        WHEN U.[sys_class_name] = 'u_users_deme_vessel_function' THEN 'Vessel Function'
        ELSE '_N/A'
    END                                                                                     AS [UserType]
    ,COALESCE(U.[u_payroll_company], '_N/A')                                                AS [PayrollCompany]
    ,COALESCE(DU.[u_payroll_company_code], '_N/A')                                          AS [PayrollCompanyCode]
    ,COALESCE(DU.[u_vip_type], '_N/A')                                                      AS [VipType]
    ,COALESCE(DU.[u_jobgroupdescription], '_N/A')                                           AS [JobGroupDescription]
    ,COALESCE(DU.[u_statute], '_N/A')                                                       AS [Statute]
    ,COALESCE(DU.[u_organizationmatrixunittype], '_N/A')                                    AS [OrganizationMatrixUnitType]
    ,COALESCE(DU.[u_jobdescription], '_N/A')                                                AS [JobDescription]
    ,COALESCE(U.[vip], '_N/A')                                                              AS [Vip]                      
    ,COALESCE(U.[name], '_N/A')                                                             AS [Name]
    ,COALESCE(U.[first_name], '_N/A')                                                       AS [FirstName]
    ,COALESCE(U.[user_name], '_N/A')                                                        AS [UserName]
    ,COALESCE(U.[employee_number], '_N/A')                                                  AS [EmployeeNumber]
    ,COALESCE(U.[email], '_N/A')                                                            AS [Email]
    ,CASE 
        WHEN U.[employee_number] IS NOT NULL THEN CONCAT(
            'https://demeprdweustoraw.blob.core.windows.net/datamarket-employeepictures/'
            ,U.[employee_number]
            -- SAS valid until 01/04/2026
            ,'.jpg?sp=r&st=2025-04-01T08:02:40Z&se=2026-04-01T16:02:40Z&spr=https&sv=2024-11-04&sr=c&sig=bzZ3%2B301IVNd8tyqA0S7HWk0dzoj56qhQLGqo%2FxJIgY%3D'
        ) 
        ELSE '_N/A' 
    END                                                                                     AS [EmployeePictureUrl]
    ,CASE E.[DEME_ORGANIZATIONUNIT3]
        WHEN 'D_CM' THEN 'Commercial Management'
        WHEN 'D_COMM' THEN 'Communications'
        WHEN 'D_DEME_MGT' THEN 'DEME Management'
        WHEN 'D_FM' THEN 'Finance Management'
        WHEN 'D_H_DEME_MGT' THEN 'DEME Management'
        WHEN 'D_H_OM' THEN 'Operations Management'
        WHEN 'D_H_OM_PO' THEN 'OM - Project Office'
        WHEN 'D_HRM' THEN 'HR Management'
        WHEN 'D_LM' THEN 'Legal Management'
        WHEN 'D_OM' THEN 'Operations Management'
        WHEN 'D_OM_ADI' THEN 'OM - Applied Development & Innovation'
        WHEN 'D_OM_BISS' THEN 'OM - DIGITAL OFFICE'
        WHEN 'D_OM_COM' THEN 'Compliance Management'
        WHEN 'D_OM_EDT' THEN 'OM - EDT'
        WHEN 'D_OM_FM' THEN 'OM - Facility Management'
        WHEN 'D_OM_OPS_CREW' THEN 'OM - Operations Crew'
        WHEN 'D_OM_OPS_STAFF' THEN 'OM - Operations Staff'
        WHEN 'D_OM_OPS_WORKMEN' THEN 'OM - Operations Workmen'
        WHEN 'D_OM_PMO' THEN 'OM - Project Management Office'
        WHEN 'D_OM_PO' THEN 'OM - Project Office'
        WHEN 'D_OM_PO_PO' THEN 'OM - PO - Project Office'
        WHEN 'D_OM_PO_SUR' THEN 'OM - PO - Survey'
        WHEN 'D_OM_PROC' THEN 'OM - Procurement'
        WHEN 'D_OM_QHSE-S' THEN 'OM - QHSE-S'
        WHEN 'D_OM_SP_G' THEN 'Strategic Planning & Growth Management'
        WHEN 'D_OM_TECH' THEN 'OM - Technical'
        WHEN 'D_OM_TM' THEN 'OM - Tender Management'
        ELSE '_N/A'
    END AS [Department]

FROM [StagingServiceNowAPI].[sys_user] U
LEFT JOIN [StagingServiceNowAPI].[u_users_deme_user] DU ON U.[sys_id] = DU.[sys_id]
LEFT JOIN [StagingServiceNowAPI].[u_users_deme_vessel] DV ON U.[sys_id] = DV.[sys_id]
LEFT JOIN [StagingServiceNowAPI].[u_users_deme_vessel_function] DVF ON U.[sys_id] = DVF.[sys_id]
LEFT JOIN [StagingDataMarket].[EmployeeAll] E ON U.[employee_number] = E.[EmployeeId]
WHERE U.[sys_class_name] IN ('u_users_deme_user', 'u_users_deme_vessel', 'u_users_deme_vessel_function')
GO
````