---
title: BuildingBlock Object (Word)
keywords: vbawd10.chm3107
f1_keywords:
- vbawd10.chm3107
ms.prod: word
api_name:
- Word.BuildingBlock
ms.assetid: 2558b89f-8552-bb71-fa40-101cab2635ba
ms.date: 06/08/2017
---


# BuildingBlock Object (Word)

Represents a building block in a template. A building block is pre-built content, similar to autotext, that may contain text, images, and formatting.


## Remarks

Each  **BuildingBlock** object is a member of the **[BuildingBlocks](../../../api/Word.BuildingBlocks.md)** and **[BuildingBlockEntries](../../../api/Word.BuildingBlockEntries.md)** collections. Building blocks are stored in Microsoft Word templates. Therefore, to access the building blocks available for a document, you need to access an attached template. Built-in building blocks are stored in the template named "Building Blocks.dotx".

 Use the **[Item](../../../api/Word.BuildingBlocks.Item.md)** method of the collection or the **BuildingBlocks** collection to return an individual building block. The following example accesses the first building block in the first template in the **[Templates](../../../api/Word.templates.md)** collection.




```
Dim objTemplate As Template 
Dim objBB As BuildingBlock 
 
Set objTemplate = Templates(1) 
Set objBB = objTemplate.BuildingBlockEntries.Item(1)
```


 **Note**  Depending on how you access the collection, the collection returned may change. For example, if you access a collection of building blocks with a type of  **wdTypeAutoText** with a category of "General", the returned collection may be different from the collection returned if you access a collection of building blocks with a type of **wdTypeAutoText** with a category of "Custom". It is also different from the collection returned if you access the collection of building blocks with a type of **wdTypeCustomAutoText** with a category of "General". Therefore, the first item in a collection accessed from the **BuildingBlockEntries** collection may be different from the first item in the collection accessed from the **BuildingBlocks** collection.

To create a new building block, you can use the  **Add** method for either the **BuildingBlockEntries** collection or the **BuildingBlocks** collection. However, the recommended way to create a new building block is by using the **[Add](../../../api/Word.BuildingBlockEntries.Add.md)** method for the **BuildingBlockEntries** collection. The following example adds the selected text to the watermarks building block gallery of the first template in the **[Templates](../../../api/Word.templates.md)** collection.




```
Dim objTemplate As Template 
Dim objBB As BuildingBlock 
 
Set objTemplate = Templates(1) 
 
Set objBB = objTemplate.BuildingBlockEntries _ 
 .Add(Name:="New Building Block Entry", _ 
 Type:=wdTypeWatermarks, _ 
 Category:="General", _ 
 Range:=Selection.Range)
```

Use the  **[Insert](../../../api/Word.BuildingBlock.Insert.md)** method to insert a new building block into a document. The following example inserts the first building block in the first template into the active document at the Insertion Point.




```
Dim objTemplate As Template 
Dim objBB As BuildingBlock 
 
Set objTemplate = Templates(1) 
Set objBB = objTemplate.BuildingBlockEntries.Item(1) 
 
objBB.Insert Selection.Range
```

Use the  **[Delete](../../../api/Word.BuildingBlock.Delete.md)** method to remove a building block from a template. The following example deletes the first building block from the first template in the **Templates** collection.




```
Dim objTemplate As Template 
 
Set objTemplate = Templates(1) 
 
objTemplate.BuildingBlockEntries(1).Delete
```

 Building blocks are organized by category and type. Use the **[BuildingBlockTypes](../../../api/Word.BuildingBlockTypes.md)** collection to access individual **[BuildingBlockType](buildingblocktype-object-word.md)** objects. Use the **[Categories](categories-object-word.md)** collection to access individual **[Category](../../../api/Word.BuildingBlock.Category.md)** objects. Then use the **BuildingBlocks** propery to access the **BuildingBlocks** collection for a **Category** object. The following example prints the type and category names of all the building blocks in the first template to the **Immediate Window**. (This example assumes that the **Immediate Window** is visible.)




```
Dim objTemplate As Template 
Dim objBBT As BuildingBlockType 
Dim objCat As Category 
Dim intCount As Integer 
Dim intCountCat As Integer 
 
Set objTemplate = Templates(1) 
 
For intCount = 1 To objTemplate.BuildingBlockTypes.Count 
 Set objBBT = objTemplate.BuildingBlockTypes(intCount) 
 If objBBT.Categories.Count > 0 Then 
 Debug.Print objBBT.Name 
 For intCountCat = 1 To objBBT.Categories.Count 
 Set objCat = objBBT.Categories(intCountCat) 
 Debug.Print vbTab &amp; objCat.Name 
 Next 
 End If 
Next
```

Each building block has properties that contain information that applies uniquely to it, such as  **[Name](../../../api/Word.BuildingBlock.Name.md)**, **[Description](../../../api/Word.BuildingBlock.Description.md)**, **[Type](../../../api/Word.BuildingBlock.Type.md)**, and **[Value](../../../api/Word.BuildingBlock.Value.md)**.

For more information about building blocks, see [Working with Building Blocks](./working-with-building-blocks.md).


## Methods



|**Name**|
|:-----|
|[Delete](../../../api/Word.BuildingBlock.Delete.md)|
|[Insert](../../../api/Word.BuildingBlock.Insert.md)|

## Properties



|**Name**|
|:-----|
|[Application](../../../api/Word.BuildingBlock.Application.md)|
|[Category](../../../api/Word.BuildingBlock.Category.md)|
|[Creator](../../../api/Word.BuildingBlock.Creator.md)|
|[Description](../../../api/Word.BuildingBlock.Description.md)|
|[ID](buildingblock-id-property-word.md)|
|[Index](buildingblock-index-property-word.md)|
|[InsertOptions](buildingblock-insertoptions-property-word.md)|
|[Name](../../../api/Word.BuildingBlock.Name.md)|
|[Parent](buildingblock-parent-property-word.md)|
|[Type](../../../api/Word.BuildingBlock.Type.md)|
|[Value](../../../api/Word.BuildingBlock.Value.md)|

## See also


#### Other resources


[Word Object Model Reference](../../../api/overview/object-model-word-vba-reference.md)