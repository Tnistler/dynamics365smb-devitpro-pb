---
title: "FieldRef.GetEnumValueCaption(Integer) Method"
description: "Gets an Enum value (or Option member) caption for the from the Enum metadata for the field that is currently selected."
ms.author: solsen
ms.custom: na
ms.date: 03/24/2022
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# FieldRef.GetEnumValueCaption(Integer) Method
> **Version**: _Available or changed with runtime version 7.0._

Gets an Enum value (or Option member) caption for the from the Enum metadata for the field that is currently selected.


## Syntax
```AL
The Enum value caption :=   FieldRef.GetEnumValueCaption(Index: Integer)
```
## Parameters
*FieldRef*  
&emsp;Type: [FieldRef](fieldref-data-type.md)  
An instance of the [FieldRef](fieldref-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The index in the list of Enum values to get the Enum value (or Option member) caption for. The index is 1-based.  


## Return Value
*The Enum value caption*  
&emsp;Type: [Text](../text/text-data-type.md)  
The Enum value caption.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[FieldRef Data Type](fieldref-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)