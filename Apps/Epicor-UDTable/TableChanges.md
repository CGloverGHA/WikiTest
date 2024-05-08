---
title: UD Table Database Changes
description: 
published: true
date: 2024-01-19T15:00:53.437Z
tags: 
editor: markdown
dateCreated: 2023-03-15T12:38:21.167Z
---

# SQL Changes for UD Tables Reset


SQL to insert UD Table in GHALincensePortal:


`SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
create TABLE [dbo].[ErpColumns](
    [RequestId][uniqueidentifier] NOT NULL,
	[CustomerId] [uniqueidentifier] NOT NULL,
	[UserId] [uniqueidentifier] NOT NULL,
	[DateRequested] [datetime] NOT NULL,
	[DataTableID] [nvarchar](30) NOT NULL,
	[LikeDataFieldSystemCode] [nvarchar](8) NOT NULL,
	[LikeDataFieldTableID] [nvarchar](30) NOT NULL,
	[FieldName] [nvarchar](128) NOT NULL,
	[LikeDataFieldName] [nvarchar](128) NOT NULL,
	[Description] [nvarchar](max) NOT NULL,
	[DataType] [nvarchar](30) NOT NULL,
	[FieldScale] [int] NOT NULL,
	[FieldFormat] [nvarchar](100) NOT NULL,
	[FieldLabel] [nvarchar](50) NOT NULL,
	[InitialValue] [nvarchar](128) NOT NULL,
	[Required] [bit] NOT NULL,
	[IsHidden] [bit] NOT NULL,
	[DateActioned] [datetime] NOT NULL,
	[Actioned] [bit] NOT NULL,
	[Success] [bit] NOT NULL,
    [Suspended] [bit] NOT NULL
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO`
