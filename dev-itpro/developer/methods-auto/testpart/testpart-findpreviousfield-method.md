---
title: "TestPart.FindPreviousField(TestField, Any) Method"
description: "Finds the previous field in the data set that is displayed on a test page."
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
# TestPart.FindPreviousField(TestField, Any) Method
> **Version**: _Available or changed with runtime version 1.0._

Finds the previous field in the data set that is displayed on a test page.


## Syntax
```AL
[Ok := ]  TestPart.FindPreviousField(Field: TestField, Value: Any)
```
## Parameters
*TestPart*  
&emsp;Type: [TestPart](testpart-data-type.md)  
An instance of the [TestPart](testpart-data-type.md) data type.  

*Field*  
&emsp;Type: [TestField](../testfield/testfield-data-type.md)  
The field to find.  
*Value*  
&emsp;Type: [Any](../any/any-data-type.md)  
 The value of the field.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[TestPart Data Type](testpart-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)