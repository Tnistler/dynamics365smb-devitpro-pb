---
title: "List.GetRange(Integer, Integer, var List of [T]) Method"
description: "Get a shallow copy of a range of elements in the source."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# List.GetRange(Integer, Integer, var List of [T]) Method
> **Version**: _Available or changed with runtime version 1.0._

Get a shallow copy of a range of elements in the source.


## Syntax
```AL
[Ok := ]  List.GetRange(Index: Integer, Count: Integer, var Result: List of [T])
```
## Parameters
*List*  
&emsp;Type: [List](list-data-type.md)  
An instance of the [List](list-data-type.md) data type.  

*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The one-based List index at which the range starts.
        
*Count*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The number of elements in the range.
        
*Result*  
&emsp;Type: [List of [T]](list-data-type.md)  
A shallow copy of a range of elements in the source List.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the range is a valid range, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[List Data Type](list-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)