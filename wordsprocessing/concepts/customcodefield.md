---
title: CustomCodeField
page_title: CustomCodeField | UI for WinForms Documentation
description: CustomCodeField
slug: winforms/wordsprocessing/concepts/customcodefield
tags: customcodefield
published: True
position: 2
previous_url: wordsprocessing-concepts-customcodefield
---

# CustomCodeField



__Fields__ in __RadFlowDocumet__ consist of code fragment and result fragment as explained in the [Fields]({%slug winforms/wordsprocessing/concepts/fields%}) article. Some fields have direct representation in the document model – for example [Hyperlinks]({%slug winforms/wordsprocessing/concepts/hyperlinks%}). For all other fields you can use the __CustomCodeField__ class – however you will need some knowledge of how to correctly form the code of the field.
      

## Syntax

Here is the basic syntax of a field code:
        

`field-type [field-argument] [switches]`

* `field-type`: The type of the field. For example: HYPERINK.
            

* `argument`: The argument of the field. This is optional as some of the fields do not require an argument.
            

* `switches`: Switches define additional properties of the field. The syntax of a switch is the following: `\switch-character [switch-argument]`

* `switch-character`: Character defining the switch. For example the "\o" switch for HYPERINK fields defines the tooltip switch.
                

* `switch-argument`: The argument of the switch. The argument is optional as not all switches require an argument.
                

Below is an example of field code:

![wordsprocessing-concepts-customcodefield 001](images/wordsprocessing-concepts-customcodefield001.png)

## Inserting

The suggested approach for inserting code fields is by using [RadFlowDocumentEditor]({%slug winforms/wordsprocessing/editing/radflowdocumenteditor%}). The __InsertField()__ method accepts code as a first argument and the result as a second argument.
        

Here are some commonly used fields. The complete list of field codes and the switches for each of them can be found in the [Docx specification](http://www.ecma-international.org/publications/standards/Ecma-376.htm).
        

>note In all examples the result fragment is also inserted. However, if you export the document to[Docx format](97359ebe-08c6-4c81-a64a-d40270199454), you can make use of the __AutoUpdateFields__ property. It forces all fields to be updated when the document is opened in MS Word or another editor.
>


### Inserting PAGE Field

Here is how to insert __PAGE__ field representing the current page number in the document:

{{source=..\SamplesCS\WordsProcessing\Concepts\WordsProcessingCustomCodeField.cs region=radwordsprocessing-concepts-customcodefield_0}} 
{{source=..\SamplesVB\WordsProcessing\Concepts\WordsProcessingCustomCodeField.vb region=radwordsprocessing-concepts-customcodefield_0}} 

````C#
editor.InsertField("PAGE  \\* ROMAN", "VII");

````
````VB.NET
editor.InsertField("PAGE \* ROMAN", "VII")

````

{{endregion}} 


The __\* ROMAN__ is general formatting switch that formats a numeric result using uppercase Roman numerals.
            

### Inserting NUMPAGE Field

Here is how a combination of __PAGE__ and __NUMPAGES__ fields can be inserted to show which is the current page as well as the total page count in the document:

{{source=..\SamplesCS\WordsProcessing\Concepts\WordsProcessingCustomCodeField.cs region=radwordsprocessing-concepts-customcodefield_1}} 
{{source=..\SamplesVB\WordsProcessing\Concepts\WordsProcessingCustomCodeField.vb region=radwordsprocessing-concepts-customcodefield_1}} 

````C#
editor.InsertText("Page ");
editor.InsertField("PAGE", "3");
editor.InsertText(" of ");
editor.InsertField("NUMPAGES", "5");

````
````VB.NET
editor.InsertText("Page ")
editor.InsertField("PAGE", "3")
editor.InsertText(" of ")
editor.InsertField("NUMPAGES", "5")

````

{{endregion}} 

### Inserting AUTHOR Field

Here is how to insert __AUTHOR__ field showing the name of the author of the document.

{{source=..\SamplesCS\WordsProcessing\Concepts\WordsProcessingCustomCodeField.cs region=radwordsprocessing-concepts-customcodefield_3}} 
{{source=..\SamplesVB\WordsProcessing\Concepts\WordsProcessingCustomCodeField.vb region=radwordsprocessing-concepts-customcodefield_3}} 

````C#
editor.InsertField("AUTHOR  \\* Upper", "JOHN DOE");

````
````VB.NET
editor.InsertField("AUTHOR \* Upper", "JOHN DOE")

````

{{endregion}} 

The __\* Upper__ switch will convert all letters in the result to uppercase.

### Inserting Table of Contents Field

Here is how to insert table of contents (TOC) field:

{{source=..\SamplesCS\WordsProcessing\Concepts\WordsProcessingCustomCodeField.cs region=radwordsprocessing-concepts-customcodefield_4}} 
{{source=..\SamplesVB\WordsProcessing\Concepts\WordsProcessingCustomCodeField.vb region=radwordsprocessing-concepts-customcodefield_4}} 

````C#
FieldInfo tocField = editor.InsertField("TOC \\o \"1-3\" \\h \\z \\u", "result");
tocField.IsDirty = true;

````
````VB.NET
Dim tocField As FieldInfo = editor.InsertField("TOC \o ""1-3"" \h \z \u", "result")

````

{{endregion}}

There are several switches which can be used for this field:

* __\o "1-3"__: Specifies that the first 3 heading levels should be included in the table of contents.
                

* __\h__: Makes the table of contents entries hyperlinks.
                

* __\z__: Hides tab leader and page numbers in Web layout view.
                

* __\u__: Uses the applied paragraph outline level.
                

The __IsDirty__ property is set so that the TOC field is updated when the document is loaded inside an editor like Microsoft Word.
            

# See Also

 * [Fields]({%slug winforms/wordsprocessing/concepts/fields%})

 * [RadFlowDocument]({%slug winforms/wordsprocessing/model/radflowdocument%})

 * [RadFlowDocumentEditor]({%slug winforms/wordsprocessing/editing/radflowdocumenteditor%})
