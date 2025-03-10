---
title: "Report.WordLayout(Integer, InStream) Method"
description: "Gets the Word report layout that is used on a report and returns it as a data stream."
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
# Report.WordLayout(Integer, InStream) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the Word report layout that is used on a report and returns it as a data stream.


## Syntax
```AL
[Ok := ]  Report.WordLayout(Number: Integer, InStream: InStream)
```
## Parameters
*Number*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The ID of the report object for which you want to get the Word report layout.
          

*InStream*  
&emsp;Type: [InStream](../instream/instream-data-type.md)  
The variable in which to return the Word report layout.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 Using the return value is optional. When you use the return value, if the Word report layout cannot be retrieved at run-time, then the system returns **false** and no error recorded. When you omit the return value, if the Word report layout cannot be retrieved at run-time, then an error occurs, which states that the Word report could not be retrieved.  
  

## See Also
[Report Data Type](report-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)