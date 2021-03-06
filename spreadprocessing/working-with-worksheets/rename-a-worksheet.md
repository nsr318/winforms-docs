---
title: Rename a Worksheet
page_title: Rename a Worksheet | UI for WinForms Documentation
description: Rename a Worksheet
slug: winforms/spreadprocessing/working-with-worksheets/rename-a-worksheet
tags: rename,a,worksheet
published: True
position: 3
previous_url: spreadprocessing-working-with-worksheets-rename-worksheet
---

# Rename a Worksheet

Workbooks are designed to hold multiple worksheets in order to allow efficient organization and consolidation of data and, often, workbooks comprise worksheets that contain related data. In such cases naming the worksheets appropriately can highly facilitate the process of finding and retrieving information from the workbook.

## 

When you add a new worksheet to a workbook's collection it is automatically assigned the first available name in the sequence Sheet1, Sheet2, Sheet3, Sheet4… Once the worksheet is added to the workbook, you can access it and change its name via the __Name__ property.

Note that there are several constrains on the worksheet name:

| Worksheet validation rules |
| ------ |
|Each worksheet should have a unique name in the workbook. The comparison of the worksheet names is case insensitive. That said, sheets with names "Sheet1" and "sheet1" cannot reside within the same workbook. If you attempt to set a name that already appears in the collection, an exception is raised.|
|The name of the worksheet cannot contain the following symbols: __\ / ? * [ ] :__ |
|The name of the worksheet should not start or end with single quote ('), however, the symbol may appear inside the worksheet name. For example, "Sam's Worksheet" is a correct name and "Sam'" is an invalid worksheet title.|
|The name of the worksheet cannot be an empty string.|
|The name of the worksheet cannot exceed 31 characters.|

__Example 1__ creates a new workbook, adds a single worksheet to it and renames the newly added worksheet:

#### Example 1: Create and rename a worksheet

{{source=..\SamplesCS\RadSpreadProcessing\WorkingWithWorksheets\RadSpreadProcessingRenameAWorksheet.cs region=radspreadprocessing-working-with-worksheets-rename-worksheet_0}} 
{{source=..\SamplesVB\RadSpreadProcessing\WorkingWithWorksheets\RadSpreadProcessingRenameAWorksheet.vb region=radspreadprocessing-working-with-worksheets-rename-worksheet_0}} 

````C#
Workbook workbook = new Workbook();
Worksheet worksheet = workbook.Worksheets.Add();
worksheet.Name = "Sam's Worksheet";

````
````VB.NET
Dim workbook As New Workbook()
Dim worksheet As Worksheet = workbook.Worksheets.Add()
worksheet.Name = "Sam's Worksheet"

````

{{endregion}} 

__Example 2__ creates a new workbook and adds two worksheets to it. The snippet illustrates how to rename the worksheet with index 0 to "July's Worksheet". To ensure name uniqueness the sample code checks if the workbook already contains a worksheet with the name we would like to set:

#### Example 2: Rename a worksheet

{{source=..\SamplesCS\RadSpreadProcessing\WorkingWithWorksheets\RadSpreadProcessingRenameAWorksheet.cs region=radspreadprocessing-working-with-worksheets-rename-worksheet_1}} 
{{source=..\SamplesVB\RadSpreadProcessing\WorkingWithWorksheets\RadSpreadProcessingRenameAWorksheet.vb region=radspreadprocessing-working-with-worksheets-rename-worksheet_1}} 

````C#
Workbook workbook = new Workbook();
workbook.Worksheets.Add();
workbook.Worksheets.Add();
string newWorksheetName = "July's Worksheet";
int indexOfWorksheetToRename = 0;
int index = workbook.Worksheets.IndexOf(newWorksheetName);
if (index == -1 || index == indexOfWorksheetToRename)
{
    workbook.Worksheets[indexOfWorksheetToRename].Name = newWorksheetName;
}
else
{
    // There already exists worksheet with this name
}

````
````VB.NET
Dim workbook As New Workbook()
workbook.Worksheets.Add()
workbook.Worksheets.Add()
Dim newWorksheetName As String = "July's Worksheet"
Dim indexOfWorksheetToRename As Integer = 0
Dim index As Integer = workbook.Worksheets.IndexOf(newWorksheetName)
If index = -1 OrElse index = indexOfWorksheetToRename Then
    workbook.Worksheets(indexOfWorksheetToRename).Name = newWorksheetName
Else
    ' There already exists worksheet with this name
End If

````

{{endregion}}
