---
title: "XmlText.SelectNodes(Text, var XmlNodeList) Method"
description: "Selects a list of nodes matching the XPath expression."
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
# XmlText.SelectNodes(Text, var XmlNodeList) Method
> **Version**: _Available or changed with runtime version 1.0._

Selects a list of nodes matching the XPath expression.


## Syntax
```AL
[Ok := ]  XmlText.SelectNodes(XPath: Text, var NodeList: XmlNodeList)
```
## Parameters
*XmlText*  
&emsp;Type: [XmlText](xmltext-data-type.md)  
An instance of the [XmlText](xmltext-data-type.md) data type.  

*XPath*  
&emsp;Type: [Text](../text/text-data-type.md)  
The XPath expression.
        

*NodeList*  
&emsp;Type: [XmlNodeList](../xmlnodelist/xmlnodelist-data-type.md)  
An XmlNodeList containing a collection of nodes matching the XPath expression.  


## Return Value
*[Optional] Ok*  
&emsp;Type: [Boolean](../boolean/boolean-data-type.md)  
**true** if the operation was successful; otherwise **false**.   If you omit this optional return value and the operation does not execute successfully, a runtime error will occur.  


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlText Data Type](xmltext-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)