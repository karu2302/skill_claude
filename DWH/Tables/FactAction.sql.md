# Source: `DBs/AzureSingleDB/DWH/Tables/FactAction.sql`

- Original repository path: `DBs/AzureSingleDB/DWH/Tables/FactAction.sql`
- Repository HEAD: `1122f06f98e5b064cddbeba383a4385c0fe83ff5`
- SHA-256 of original file: `8e939d4c5fdf628398703c811cb515c3877a6f9cf22e797c2dc5526217473eef`
- Content note: credential-like values are redacted where detected.

## Source Content

``sql
CREATE TABLE [DWH].[FactAction] (
    [FactActionId]                       INT             IDENTITY (1, 1) NOT NULL,
    [DimProjectId]                       INT             NOT NULL,
    [DimVesselId]                        INT             NOT NULL,
    [DimOtherSiteId]                     INT             NOT NULL,
    [DimSupportingServiceId]             INT             NOT NULL,
    [DimActionDate]                      INT             NOT NULL,
    [DimEntityId]                        INT             NOT NULL,
    [ActionId]                           NVARCHAR (255)  NULL,
    [CustomProcessID]                    NVARCHAR (255)  NULL,
    [EventId]                            NVARCHAR (255)  NULL,
    [SupportingServiceCode]              NVARCHAR (255)  NULL,
    [SourceName]                         NVARCHAR (255)  NOT NULL,
    [SourceId]                           NVARCHAR (255)  NULL,
    [ProcessURLId]                       NVARCHAR (255)  NULL,
    [Duedate]                            DATETIME        NULL,
    [DateActionCompleted]                DATETIME        NULL,
    [ActionDateTime]                     DATETIME        NULL,
    [ActionCompletedBy]                  NVARCHAR (255)  NOT NULL,
    [InitiatedBy]                        NVARCHAR (255)  NOT NULL,
    [PersonAssignedForHandlingTheAction] NVARCHAR (255)  NOT NULL,
    [ProcessCloser]                      NVARCHAR (255)  NOT NULL,
    [ResponsibleUsers]                   NVARCHAR (255)  NOT NULL,
    [ActionTopic]                        NVARCHAR (MAX)  NOT NULL,
    [Status]                             NVARCHAR (255)  NOT NULL,
    [Substatus]                          NVARCHAR (255)  NOT NULL,
    [ActionType]                         NVARCHAR (255)  NOT NULL,
    [ActionTakenDescription]             NVARCHAR (MAX)  NOT NULL,
    [Group]                              NVARCHAR (255)  NOT NULL,
    [ImmediateActionTaken]               NVARCHAR (255)  NOT NULL,
    [ImmediateActionTaken2]              NVARCHAR (MAX)  NOT NULL,
    [LessonsLearned]                     NVARCHAR (MAX)  NOT NULL,
    [Priority]                           NVARCHAR (255)  NOT NULL,
    [ReasonForRejection]                 NVARCHAR (MAX)  NOT NULL,
    [SupportingService]                  NVARCHAR (255)  NOT NULL,
    [WhatActionHasToBeTaken]             NVARCHAR (MAX)  NOT NULL,
    [DataSource]                         VARCHAR (7)     NOT NULL,
    [PlanCategoryDescription]            NVARCHAR (255)  NOT NULL,
    [EventType]                          NVARCHAR (255)  NULL,
    [EventTypeOfMeeting]                 NVARCHAR (255)  NOT NULL,
    [StatusPerformance]                  VARCHAR (9)     NOT NULL,
    [POVOSource]                         NVARCHAR (4000) NOT NULL,
    [SourceItemId]                       NVARCHAR (255)  NOT NULL,
    [CreatedETLRunId]                    INT             NOT NULL,
    [ModifiedETLRunId]                   INT             NULL,
    CONSTRAINT [PK_DWH_FactAction] PRIMARY KEY CLUSTERED ([FactActionId] ASC),
    CONSTRAINT [FK_DWH_FactAction_DimActionDate] FOREIGN KEY ([DimActionDate]) REFERENCES [DWH].[DimDate] ([DimDateId]),
    CONSTRAINT [FK_DWH_FactAction_DimEntityId] FOREIGN KEY ([DimEntityId]) REFERENCES [DWH].[DimEntity] ([DimEntityId]),
    CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId] FOREIGN KEY ([DimOtherSiteId]) REFERENCES [DWH].[DimOtherSite] ([DimOtherSiteId]),
    CONSTRAINT [FK_DWH_FactAction_DimProjectId] FOREIGN KEY ([DimProjectId]) REFERENCES [DWH].[DimProject] ([DimProjectId]),
    CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId] FOREIGN KEY ([DimSupportingServiceId]) REFERENCES [DWH].[DimSupportingService] ([DimSupportingServiceId]),
    CONSTRAINT [FK_DWH_FactAction_DimVesselId] FOREIGN KEY ([DimVesselId]) REFERENCES [DWH].[DimVessel] ([DimVesselId])
);


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimEntityId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimProjectId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimVesselId];




GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimEntityId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimProjectId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimVesselId];




GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimEntityId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimProjectId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimVesselId];




GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimEntityId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimProjectId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimVesselId];




GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimEntityId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimProjectId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimVesselId];




GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimEntityId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimProjectId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimVesselId];




GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimEntityId];


GO



GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimProjectId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimVesselId];




GO



GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimProjectId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimVesselId];




GO



GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimOtherSiteId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimProjectId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimSupportingServiceId];


GO
ALTER TABLE [DWH].[FactAction] NOCHECK CONSTRAINT [FK_DWH_FactAction_DimVesselId];


GO
CREATE UNIQUE NONCLUSTERED INDEX [UC_DWH_FactAction]
    ON [DWH].[FactAction]([ActionId] ASC);


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ModifiedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_IsHidden', @value = '1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'CreatedETLRunId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'POVOSource';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'StatusPerformance';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'EventType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'PlanCategoryDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'DataSource';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'WhatActionHasToBeTaken';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'SupportingService';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ReasonForRejection';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'Priority';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'LessonsLearned';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ImmediateActionTaken2';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ImmediateActionTaken';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'Group';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ActionTakenDescription';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ActionType';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'Substatus';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'Status';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ActionTopic';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ResponsibleUsers';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ProcessCloser';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'PersonAssignedForHandlingTheAction';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'InitiatedBy';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ActionCompletedBy';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ActionDateTime';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'DateActionCompleted';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'Duedate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ProcessURLId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'SourceId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'SourceName';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'CustomProcessID';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'BK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'ActionId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'DimActionDate';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'DimSupportingServiceId';


GO



GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'DimOtherSiteId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'DimVesselId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'DimProjectId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'PK', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'FactActionId';


GO
EXECUTE sp_addextendedproperty @name = N'MDM_Description', @value = 'FactAction', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'EventId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'DimEntityId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'EventTypeOfMeeting';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'SourceItemId';


GO
EXECUTE sp_addextendedproperty @name = N'SCDType', @value = 'SCD1', @level0type = N'SCHEMA', @level0name = N'DWH', @level1type = N'TABLE', @level1name = N'FactAction', @level2type = N'COLUMN', @level2name = N'SupportingServiceCode';


``