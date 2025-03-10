---
title: "RecordRef.Next([Integer]) Method"
description: "Steps through a specified number of records and retrieves a record."
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
# RecordRef.Next([Integer]) Method
> **Version**: _Available or changed with runtime version 1.0._

Steps through a specified number of records and retrieves a record.


## Syntax
```AL
[Steps := ]  RecordRef.Next([Steps: Integer])
```
## Parameters
*RecordRef*  
&emsp;Type: [RecordRef](recordref-data-type.md)  
An instance of the [RecordRef](recordref-data-type.md) data type.  

*[Optional] Steps*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
Defines the direction of the search and how many records to step include. If this parameter is greater than zero, the method will search the number of records specified in Steps forward in the table. If this parameter is less than zero, the method will search the number of records specified in Steps backward in the table. If this parameter is 0, no records are stepped over. If you do not specify this parameter, the method finds the next record.  


## Return Value
*[Optional] Steps*  
&emsp;Type: [Integer](../integer/integer-data-type.md)  
Defines the direction of the search and how many records to include.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks  
 This method locates a record positioned a given number of steps forward or backward from the record specified by *RecordRef*. Movement through the table is governed by the filters and the current key associated with the records. The fields in the record which will be compared with the current key fields must contain appropriate values before the method is called.  
  
 This method works the same as the [Next Method \(Record\)](../record/record-next-method.md).  
  
## Example  
 The following example opens the Customer table as a RecordRef object, creates a reference to the first \(No.\) field, and stores the reference in the MyFieldRef variable. The SetRange method sets a filter that selects all records from 10000 to 40000 in the No. field. The [Find Method \(RecordRef\)](recordref-find-method.md) searches and selects the first record in the filter and counts the number of records that are found. The number of records is stored in the Count variable. The process is repeated by looping through all the records in the filter until no more records are found. The Next method steps through the records and finds the next record because no value is specified for the *Steps* parameter. The number of records that are found in the range is stored in the Count variable and displayed in a message box. 
  
```al
var
    CustomerRecref: RecordRef;
    MyFieldRef: FieldRef;
    Count: Integer;
    Text000: Label '%1 records were retrieved.'; 
begin    
    CustomerRecref.Open(Database::Customer);  
    MyFieldRef := CustomerRecref.Field(1);  
    MyFieldRef.SetRange('10000' , '40000');  
    Count := 0;  
    if CustomerRecref.Find('-') then  
      repeat  
        Count := Count + 1;  
      until CustomerRecref.Next = 0;  
    Message(Text000 , Count);  
end;
``` 

## See Also
[RecordRef Data Type](recordref-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)