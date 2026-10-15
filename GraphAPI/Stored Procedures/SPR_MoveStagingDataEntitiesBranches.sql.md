# Source: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataEntitiesBranches.sql`

- Repository commit: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- Original repository path: `DBs/AzureSingleDB/GraphAPI/Stored Procedures/SPR_MoveStagingDataEntitiesBranches.sql`
- SHA-256 of original file: `26873ef089b9f3129b0e3879be283a8f11a3375cf6ed902f26442305e72f6cc9`
- Content note: credential-like values are redacted where detected.

## Source Content

````sql
CREATE PROCEDURE [GraphAPI].[SPR_MoveStagingDataEntitiesBranches] @EntitiesBranches [GraphAPI].[EntitiesBranches] READONLY, @ETLRunId INT
AS
BEGIN
DECLARE @ETLRunDetailsId INT
DECLARE @ErrorMessage NVARCHAR(MAX)
DECLARE @NrOfRows INT
DECLARE @RunDetailTaskName NVARCHAR(255)= 'Stage GraphAPI EntitiesBranches'
EXEC ETL.SPR_LogStartRunDetail 
	@TaskName = @RunDetailTaskName,
	@SourceName = 'GraphAPI',
	@SchemaName = NULL,
	@TableName = 'EntitiesBranches',
	@ETLRunId = @ETLRunId,
	@ETLRunDetailsId = @ETLRunDetailsId OUTPUT
BEGIN TRY
	INSERT INTO [StagingGraphAPI].[EntitiesBranches] --WITH (TABLOCK)
		([AddressLine1],
		[CompanyLegalForm],
		[CompanyStatus],
		[CountryCodeAlpha3],
		[DemeOrganisationalStructureId],
		[EntityBranchActive],
		[EntityBranchId],
		[EntityBranchName],
		[EntityType],
		[Exclude],
		[GIDPBW],
		[Lead],
		[Place],
		[PostalCode],
		[QHSEScampaigns],
		[QHSESCampaignTopic],
		[QHSESEndDate],
		[QHSESStartDate],
		[SharepointId],
		[TibcoIdentifier])
	SELECT 
		H.[AddressLine1] AS [AddressLine1],
		H.[CompanyLegalForm] AS [CompanyLegalForm],
		H.[CompanyStatus] AS [CompanyStatus],
		H.[CountryCodeAlpha3] AS [CountryCodeAlpha3],
		H.[DemeOrganisationalStructureId] AS [DemeOrganisationalStructureId],
		H.[EntityBranchActive] AS [EntityBranchActive],
		H.[EntityBranchId] AS [EntityBranchId],
		H.[EntityBranchName] AS [EntityBranchName],
		H.[EntityType] AS [EntityType],
		H.[Exclude] AS [Exclude],
		H.[GIDPBW] AS [GIDPBW],
		H.[Lead] AS [Lead],
		H.[Place] AS [Place],
		H.[PostalCode] AS [PostalCode],
		H.[QHSEScampaigns] AS [QHSEScampaigns],
		H.[QHSESCampaignTopic] AS [QHSESCampaignTopic],
		H.[QHSESEndDate] AS [QHSESEndDate],
		H.[QHSESStartDate] AS [QHSESStartDate],
		H.[SharepointId] AS [SharepointId],
		H.[TibcoIdentifier] AS [TibcoIdentifier]
	FROM @EntitiesBranches H

	SELECT @NrOfRows = @@ROWCOUNT
	EXEC ETL.SPR_LogEndRunDetail @ETLRunDetailsId = @ETLRunDetailsId, @NrOfIn = @NrOfRows
END TRY
BEGIN CATCH
	SELECT @ErrorMessage=ERROR_MESSAGE()
	EXEC ETL.SPR_LogEndRunDetail @ETLRunDetailsId = @ETLRunDetailsId, @Status = N'Failed', @ErrorMessage = @ErrorMessage;
	THROW 51000, @ErrorMessage, 1
END CATCH
END
````