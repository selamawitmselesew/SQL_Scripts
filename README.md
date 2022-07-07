# SQL_Scripts
SELECT* FROM Tbl
USE [AGIP]
GO
/****** Object:  StoredProcedure [dbo].[Proc_test]    Script Date: 7/7/2022 9:10:36 AM *****
Created By  (Sally) Selamawit Melesew
			7/5/2022
*/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
ALTER PROC [dbo].[Proc_test]
		@ShiftDate DATETIME,
		@SiteID	   INT,
		@inventoryid VARCHAR (20) 
AS
BEGIN 
		select  [ShiftDate]
			  ,[ShiftID]
			  ,[ForemanKey]
			  ,[Foreman_Name]
			  ,[dailyproductionentrykey]
			  ,[runtypeid]
			  ,[InventoryID]
			  ,[descr]
			  ,[ProductionLineKey]
			  ,[Name]
			  ,[SiteID]
			  ,[Expr1]
			  ,[GrossMinutes]
			  ,[NetMinutes]
			  ,[MinutesDelayed]
			  ,[AvgLineSpeed]
			  ,[GrossSqFt]
			  ,[WetWaste]
			  ,[WetSample]
			  ,[DryWaste]
			  ,[SawTrim]
			  ,[NetSqFt]
			  ,[NetPieces]
			  ,[BoardSqFt]
			  ,[ReclaimedSqFt]
			  ,[RecliamPieces]
			  ,[Adjustrecliampieces]
			  ,[AdjustReclaimSQFT]
			  ,[WarehouseSqFt]
			  ,[WarehousePieces]
			  ,[PlannedProduct]
			  ,[RuntypeDescr]
			  ,[Fraction]
			  ,[Thickness]
			  ,[ClassID]
			  ,[ClassDescr] 
INTO		#NEW_proc1
FROM		vwProductionByProductAndDate_PAST 
SELECT		* 
FROM		#NEW_proc1
WHERE		ShiftID <> 0
  AND		ShiftDate >= @ShiftDate
  AND		SiteID = @SiteID
  AND		inventoryid = @inventoryid
DROP TABLE	#NEW_proc1
END
