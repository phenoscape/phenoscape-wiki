---
title: CoF schema
permalink: wiki/CoF_schema
layout: wiki
tags:
 - Informatics
 - Taxonomy
 - Database
redirect_from:
 - wiki/Cof_schema
---

    GENERA
        [CAS_GEN] [int]                 -- Unique identifying number.
        [GEN_NAME] [nvarchar] (25)      -- Genus or subgenus name.
        [SUBGEN] [nvarchar] (25)        -- If Gen_name is a subgenus, then this is the genus .
        [AUTH] [nvarchar] (75)          -- Author - person who described the genus/subgenus.
        [QUALIFICATION] [nvarchar] (65) -- Author of publication in which the description appears if not the same as genus author.
        [YR] [nvarchar] (5)             -- Year of description publication.
        [DESPP] [nvarchar] (17)         -- Page numbers on which description appears.
        [LineageID] [int]               -- Link to Lineage table.
        [PP] [nvarchar] (4)             -- Ignore.
        [CAS_REF_NO] [int]              -- Link to Referenc table.
        [GEND] [nvarchar] (1)           -- Gender.
        [DONE] [nvarchar] (1)           -- Once used to track data entry status; no longer used.
        [TYP_SP] [nvarchar] (43)        -- Type species of the genus-level name.
        [AUT_TYP_SP] [nvarchar] (60)    -- Author of the type species.
        [YR_TYP_SP] [nvarchar] (5)      -- Year type species was described.
        [SEN_OB_SYN] [nvarchar] (50)    -- Senior objective synonym - name which the type species is now recognized as.
        [HOW] [nvarchar] (3)            -- Abbreviation for type_desig?.
        [TYPE_DESIG] [nvarchar] (80)    -- Type designation.
        [AVAIL] [nvarchar] (1)          -- Available.
        [NOTES] [nvarchar] (146)
        [STATUS] [ntext]
        [COMMENTS] [ntext]
        [STAT_CODE] [nvarchar] (9)      -- Values=Valid,Synonym,Uncertain,Unknown.
        [STAT_CODE1] [nvarchar] (20)    -- Further explanation of Stat_Code.
        [CURR_GEN] [nvarchar] (25)      -- Ignore. Use CurrentGenusID instead.
        [CURR_AUTH] [nvarchar] (80)     -- Ignore. Use CurrentGenusID to find linked record to find current genus author.
        [CURR_SUBGEN] [nvarchar] (25)   -- Current subgenus that this taxon is recognized as.
        [CURR_AUTHYRSub] [nvarchar] (60)    -- Author of current subgenus.
        [REMARKS] [ntext]
        [LIST] [nvarchar] (1)
        [ENTERED] [nvarchar] (5)
        [DATEENTERED] [smalldatetime]
        [CHECKED] [nvarchar] (5)
        [DATECHECKED] [smalldatetime]
        [TimeStamp] [datetime]
        [CurrentGenusID] [int]          -- Current genus that this taxon is recognized as being, or being under if this is a subgenus. Link to Genera table.


    SPECIES
        [CAS_SPC] [int]                 -- Unique identifying number.
        [ORIG_NAME] [nvarchar] (40)     -- Original upper part of the scientific name, i.e. Genus if orig_level is species, Genus and species if orig_level is subspecies.
        [TAXON_NAME] [nvarchar] (25)    -- Original taxon name.
        [ORIG_LEVEL] [nvarchar] (10)    -- Values=species,subspecies,variety.
        [VARIETY] [nvarchar] (7)        -- Further explanation of orig_level.
        [AUTHOR] [nvarchar] (75)        -- Author of taxon.
        [QUALIFICATION] [nvarchar] (65) -- Author of publication in which the description appears if not the same as taxon author.
        [YR] [nvarchar] (8)             -- Year of description publication.
        [JOUR_delete] [nvarchar] (7)    -- Ignore.
        [JOUR_NAME_delete] [nvarchar] (60)  -- Ignore.
        [CITATION] [nvarchar] (23)      -- Ignore.
        [DESCR_PP] [nvarchar] (20)      -- Page numbers on which description appears.
        [ILLUS] [nvarchar] (50)         -- Illustrations and figures.
        [CAS_REF_NO] [int]              -- Link to Referenc table.
        [DONE] [nvarchar] (1)           -- ?
        [LineageID] [int]               -- Link to Lineage table.
        [CURR_GENUS] [nvarchar] (40)    -- Ignore. Use Curr_GenusID instead.
        [CURR_NAME] [nvarchar] (25)     -- Current taxon which this taxon is now recognized as.
        [CURR_AUTH] [nvarchar] (80)     -- Author and year of description of current taxon.
        [CURR_YR] [nvarchar] (8)        -- Year of description of current taxon.
        [CURR_SUBSP] [nvarchar] (25)    -- Current subspecies which this taxon is now recognized as.
        [CURR_AUTHYRSub] [nvarchar] (75)    -- Author and year of publication of description of current subspecies.
        [AVAILABLE] [nvarchar] (1)
        [STAT_CODE] [nvarchar] (9)      -- Values=Valid,Synonym,Uncertain,Unknown.
        [STAT_CODE1] [nvarchar] (20)    -- Further explanation of Stat_Code.
        [CURRSTATUS] [ntext]
        [COMMENTS] [ntext]
        [TYPECAT] [nvarchar] (255)
        [PRIM_CODE] [nvarchar] (25)
        [PRIM_TYPE] [nvarchar] (50)
        [TYPE_LOCAL] [nvarchar] (255)
        [DISTRIBUTION] [ntext]
        [TYPES] [ntext]
        [NOTES] [nvarchar] (200)
        [Fresh] [bit]
        [Brackish] [bit]
        [Marine] [bit]
        [LIST] [nvarchar] (1)
        [REMARKS] [ntext]
        [ENTERED] [nvarchar] (5)
        [DATEENTERED] [smalldatetime]
        [CHECKED] [nvarchar] (5)
        [DATECHECKED] [smalldatetime]
        [TimeStamp] [datetime]
        [Curr_GenusID] [int]            -- ID of genus in which this taxon is currently classified. FK to Genera table.


    LINEAGES    (This is a flat table and is not recursive)
        [LineageID] [int]               -- Unique identifying number.
        [NAME] [nvarchar] (30)          -- Taxon name.
        [AUTHOR_DATE] [nvarchar] (30)   -- Author and date of taxon.
        [COMMONNAME] [nvarchar] (75)    -- Common name.
        [INDEXNAME] [nvarchar] (70)     -- keywords.
        [SYN] [bit]
        [CLASS_NM] [nvarchar] (30)      -- Class.
        [ORD_NM] [nvarchar] (30)        -- Order.
        [SO_NM] [nvarchar] (30)         -- Suborder.
        [FAM_NM] [nvarchar] (30)        -- Family.
        [SF_NM] [nvarchar] (30)         -- Subfamily.
        [REMARKS] [ntext]
        [FAMILYDESCR] [ntext]           -- Family description.
        [AUTHOR] [nvarchar] (255)       -- Author of family description.
        [ADDRESS] [ntext]
        [ACKNOWLEDGE] [ntext]
        [ClassNum] [int]                -- Class number.
        [OrderNum] [decimal](4, 2)      -- Order number.
        [SuborderNum] [decimal](4, 2)   -- Suborder number.
        [FamilyNum] [decimal](6, 2)     -- Family number.
        [SubfamilyNum] [int]            -- Subfamily number.
        [TimeStamp] [datetime]


    REFERENC
        [CAS_REF_NO] [int]              -- Unique identifying number.
        [NAME_1] [nvarchar] (25)        -- First author's last name.
        [INIT_1] [nvarchar] (20)        -- First author's first and middle initials.
        [NAME_2] [nvarchar] (25)        -- Second author's last name.
        [INIT_2] [nvarchar] (20)        -- Second author's first and middle initials.
        [ADD_AUTH] [nvarchar] (60)      -- Additional authors.
        [YR] [nvarchar] (10)            -- Year of publication.
        [MONTH_DAY] [nvarchar] (30)     -- Month and day of publication.
        [TITLE] [ntext]                 -- Title of publication.
        [JOUR] [nvarchar] (7)           -- Ignore.
        [JOUR_NAME] [nvarchar] (120)    -- Ignore.
        [CITATION] [nvarchar] (30)      -- Volume, etc. of publication.
        [PP] [nvarchar] (100)           -- Page numbers on which publication appears.
        [FIGS] [nvarchar] (30)          -- Figures, illustrations, and plates in publication.
        [CAS_CALLNUM] [nvarchar] (50)   -- CAS Library call numbers.
        [ICH_CALLNUM] [nvarchar] (50)   -- CAS-ICH Library call numbers.
        [ICH_REPRINT] [bit]
        [REMARKS1] [nvarchar] (160)
        [REMARKS2] [nvarchar] (255)
        [STATREF_GEN] [bit]
        [STATREF_SP] [bit]
        [BY] [nvarchar] (5)
        [DATEBY] [smalldatetime]
        [AVAIL] [nvarchar] (1)
        [ENTERED] [nvarchar] (5)
        [DATEENTERED] [smalldatetime]
        [PROOFED] [nvarchar] (5)
        [DATEPROOFED] [smalldatetime]
        [JourID] [int]                  -- Link to Journal table.
        [TimeStamp] [datetime]

    JOURNAL
        [JourID] [int]                  -- Unique identifying number.
        [JOUR] [nvarchar] (7)           -- Journal acronym.
        [JOUR_NAME] [nvarchar] (60)     -- Abbreviated journal name.
        [FULL_NAME] [nvarchar] (250)    -- Full journal name.
        [CALLNUMBER] [nvarchar] (50)
        [NOTES] [nvarchar] (138)
        [REMARKS] [nvarchar] (255)
        [TimeStamp] [datetime]
