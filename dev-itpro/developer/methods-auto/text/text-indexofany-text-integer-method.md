---
title: "Text.IndexOfAny(Text [, Integer]) Method"
description: "Reports the one-based index of the first occurrence of the specified string in this instance."
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
# Text.IndexOfAny(Text [, Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Reports the one-based index of the first occurrence of the specified string in this instance. The search starts at a specified character position.


## Syntax
```AL
Index :=   Text.IndexOfAny(Values: Text [, StartIndex: Integer])
```
## Parameters
*Text*  
&emsp;Type: [Text](text-data-type.md)  
An instance of the [Text](text-data-type.md) data type.  

*Values*  
&emsp;Type: [Text](text-data-type.md)  
The collection of characters to seek.
        

*[Optional] StartIndex*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The one-based search starting position.  


## Return Value
*Index*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
The one-based index of the first occurrence of the specified string in this instance. If the index returned is 0, the value is not present in the string.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Text Data Type](text-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)