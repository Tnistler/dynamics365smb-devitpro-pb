---
title: "HttpHeaders.TryAddWithoutValidation(Text, Text) Method"
description: "Adds the specified header and its value into the HttpHeaders collection."
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
# HttpHeaders.TryAddWithoutValidation(Text, Text) Method
> **Version**: _Available or changed with runtime version 3.0._

Adds the specified header and its value into the HttpHeaders collection. Doesn't validate the provided value.


## Syntax
```AL
[Ok := ]  HttpHeaders.TryAddWithoutValidation(Name: Text, Value: Text)
```
## Parameters
*HttpHeaders*  
&emsp;Type: [HttpHeaders](httpheaders-data-type.md)  
An instance of the [HttpHeaders](httpheaders-data-type.md) data type.  

*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
The header to add to the collection.  

*Value*  
&emsp;Type: [Text](../text/text-data-type.md)  
The content of the header.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the value was added successfully, otherwise **false**. If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[HttpHeaders Data Type](httpheaders-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)