---
title: "XmlDocumentType.Create(Text) Method"
description: "Creates an XmlDocumentType node."
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
# XmlDocumentType.Create(Text) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates an XmlDocumentType node.


## Syntax
```AL
XmlDocumentType :=   XmlDocumentType.Create(Name: Text)
```
## Parameters
*Name*  
&emsp;Type: [Text](../text/text-data-type.md)  
A string that contains the qualified name of the DTD, which is the same as the qualified name of the root element of the XML document.  


## Return Value
*XmlDocumentType*  
&emsp;Type: [XmlDocumentType](xmldocumenttype-data-type.md)  
The created XmlDocumentType node.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlDocumentType Data Type](xmldocumenttype-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)