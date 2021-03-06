---
title: RadFixedDocumentEditor
page_title: RadFixedDocumentEditor | UI for WinForms Documentation
description: RadFixedDocumentEditor
slug: winforms/pdfprocessing/editing/radfixeddocumenteditor
tags: radfixeddocumenteditor
published: True
position: 3
previous_url: pdfprocessing-editing-radfixeddocumenteditor
---

# RadFixedDocumentEditor

__RadFixedDocumentEditor__ is a utility class aiming to allow the creation of [RadFixedDocument]({%slug winforms/pdfprocessing/model/radfixeddocument%}) in a flow-like manner. The editor provides methods that enable the generation of documents which automatically flows to pages.

>caution Although RadFixedDocumentEditor and this article operate with classes and concepts for Section, Block, Inline, these classes are different from the ones used in genuine flow editing libraries. RadFixedDocumentEditor ultimately creates a fixed document. If you are trying to create a flow document, try out our [RadWordsProcessing library](d17653ff-fe96-41c5-8739-01671fb45fba) instead.
>

* [Creating RadFixedDocumentEditor](#creating-radfixeddocumenteditor)

* [Sections](#sections)

* [Starting New Section](#starting-new-section)

* [Paragraphs](#paragraphs)

* [Inlines](#inlines)

* [Tables](#tables)

* [Lists](#lists)

## Creating RadFixedDocumentEditor

__Example 1__ demonstrates how a RadFixedDocumentEditor instance can be created.

#### Create RadFixedDocumentEditor

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=radpdfprocessing-editing-radfixeddocumenteditor_0}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=radpdfprocessing-editing-radfixeddocumenteditor_0}} 

````C#
RadFixedDocumentEditor editor = new RadFixedDocumentEditor(radFixedDocument);

````
````VB.NET
Dim editor As New RadFixedDocumentEditor(radFixedDocument)

````

{{endregion}}

>note  __RadFixedDocumentEditor__ inherits from __IDisposable__ so it should be properly disposed when the document is created. Otherwise, some of the content may not be finished, i.e. it might not appear on the PDF document.
>

## Sections

__Section__ is a sequence of [RadFixedPages]({%slug winforms/pdfprocessing/model/radfixedpage%}) with the same properties.

### SectionProperties

The section properties are responsible for the page size, margins and orientation of __RadFixedPages__ in a section. Below is the complete list of section properties.

* __PageSize__: The size of the pages that are part of the section.

* __PageMargins__: The page margins of a page.

* __PageRotation__: The page rotation. This is enum that can take one of the following values.

* __Rotate0__: The page is not rotated. This is the default value.

* __Rotate90__: The page is rotated to 90°.

* __Rotate180__: The page is rotated to 180°.

* __Rotate270__: The page is rotated to 270°.

### Starting New Section

The first section in a document starts as soon as a content is inserted to the editor. You can change the Section properties before inserting any content and they will be applied to the section that is automatically created.

Adding an additional section is achieved with the __InsertSectionBreak()__ method as demonstrated in __Example 2__.

#### Example 2: Start a Section

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=radpdfprocessing-editing-radfixeddocumenteditor_1}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=radpdfprocessing-editing-radfixeddocumenteditor_1}} 

````C#
editor.InsertSectionBreak();

````
````VB.NET
editor.InsertSectionBreak()

````

{{endregion}}

If you want to change the properties of the next section, make sure to do it __before__ you insert the section break. New properties are only used for newly created sections.

All pages that have the same __SectionProperties__ are part of the current section. To start a new page you can use the following code:

#### Example 3: Start new Page

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=PageBreak}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=PageBreak}} 

````C#
editor.InsertPageBreak();

````
````VB.NET
editor.InsertPageBreak()

````

{{endregion}}

## Paragraphs

__Paragraphs__ are blocks of flowing inlines - images and text.

### ParagraphProperties

Similar to the section properties, paragraph has its own properties that are responsible for the way it looks.

* __SpacingBefore__: Represent the spacing before.

* __SpacingAfter__: Represents the spacing after.

* __LineSpacing__: The spacing between the lines.

* __LineSpacingType__: Specifies how to interpret the line spacing.

* __FirstLineIndent__: The indent for the first line.

* __LeftIndent__: The left indent.

* __RightIndent__: The right indent.

* __BackgroundColor__: The background color.

* __HorizontalAlignment__: The horizontal alignment of the content.

* __ListId__: The id of the list the paragraph belongs to. If null, then the paragraph belongs to no list.

* __ListLevel__: The list level the paragraph belongs to.

### Starting New Paragraph

The first paragraph is created as soon as content is inserted in the editor. You can change paragraph properties before inserting content and when the first paragraph is created automatically, it will use the desired properties.

In order to start a new paragraph use the code in __Example 4__.

#### Start a Paragraph

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=radpdfprocessing-editing-radfixeddocumenteditor_2}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=radpdfprocessing-editing-radfixeddocumenteditor_2}} 

````C#
editor.InsertParagraph();

````
````VB.NET
editor.InsertParagraph()

````

{{endregion}}

The result of this method is that new paragraph is started and it uses the current paragraph properties. Until a new paragraph is started, changes in the paragraph properties are not applied.

### Inlines

A Paragraph is built of two types of inlines - runs and images.

### Runs

__Run__ represents a collection of characters that have the same properties.

__CharacterProperties__

The character properties that are responsible for the look of the runs are listed below.

* __FontSize__: The font size.

* __Font__: The font.

* __ForegroundColor__: The foreground color.

* __HighlightColor__: The highlight color.

* __BaselineAlignment__: Describes how the baseline for a text-based element is positioned on the vertical axis, relative to the established baseline for text.

* __Baseline__: A baseline that is aligned at the actual baseline of the containing box.

* __Subscript__: A baseline that is aligned at the subscript position of the containing box.

* __Superscript__: A baseline that is aligned at the superscript position of the containing box.

* __UnderlinePattern__: Тhe underline pattern. Two patterns are supported.

* __None__: There is no underline. This is the default value.

* __Single__: The underline is a single line.

* __UnderlineColor__: The color of the underline.

__Inserting a Run__

There are a number of overloads that insert a run. The code snippet in __Example 5__ inserts a a couple of new runs with specific font family, style and weight. 

#### Insert Run

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=radpdfprocessing-editing-radfixeddocumenteditor_3}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=radpdfprocessing-editing-radfixeddocumenteditor_3}} 

````C#
editor.InsertRun("text");
editor.InsertRun(fontFamily, "text");

````
````VB.NET
editor.InsertRun("text")
editor.InsertRun(fontFamily, "text")

````

{{endregion}}

There are a number of overloads that insert a run. The code snippet in __Example 5__ inserts a a couple of new runs, one of which with a specific font family.

>The '\r' and '\n' characters don't have the usual meaning of "go to next line" when they are inserted in a PDF document and you cannot simply insert text containing these characters to produce multiline text. Instead, you should split the text and insert a line break.

The code in __Example 6__ inserts a new run and a line break after it.

#### Insert Run and Break Line

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=radpdfprocessing-editing-radfixeddocumenteditor_4}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=radpdfprocessing-editing-radfixeddocumenteditor_4}} 

````C#
editor.InsertLine("Line of text");

````
````VB.NET
editor.InsertLine("Line of text")

````

{{endregion}}

### Images

Image inline is a combination of an [ImageSource]({%slug winforms/pdfprocessing/model/imagesource%}) object and its desired size.   

__Inserting an Image__

You can insert image inline using one of the following methods:

#### Example 7: Insert ImageInline

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=Image}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=Image}} 

````C#
editor.InsertImageInline(imageSource);
editor.InsertImageInline(imageSource, size);

````
````VB.NET
editor.InsertImageInline(imageSource)
editor.InsertImageInline(imageSource, size)

````

{{endregion}}

## Tables

The __Table__ class implements the __IBlockElement__ interface and an instance of this class can be easily inserted as a new block in the document. You could insert the table using the __InsertTable()__ method like illustrated in __Example 8__. __RadFixedDocumentEditor__ takes care for positioning, measuring and splitting the table onto pages.

#### Insert Table

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=radpdfprocessing-editing-radfixeddocumenteditor_5}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=radpdfprocessing-editing-radfixeddocumenteditor_5}} 

````C#
editor.InsertTable(table);

````
````VB.NET
editor.InsertTable(table)

````

{{endregion}}

For more detailed information on tables follow this link to [Table]({%slug winforms/pdfprocessing/editing/table%}) documentation article.        

## Block Elements

The __IBlockElement__ interface allows you to easily draw and split some block content onto pages. The interface is implemented by [Block]({%slug winforms/pdfprocessing/editing/block%}) and [Table]({%slug winforms/pdfprocessing/editing/table%}) classes. You can easily add some block element instance with RadFixedDocumentEditor using InsertBlock() method like illustrated the following example. 

#### Insert Block Element

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=block}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=block}} 

````C#
editor.InsertBlock(blockElement);

````
````VB.NET
editor.InsertBlock(blockElement)

````

{{endregion}} 

## Lists
      

You can easily insert list items with __RadFixedDocumentEditor__. The first thing you have to do is add a __List__ in editor’s __ListCollection__ by using the __Lists__ property. Then each time you want to add list item you have to set the appropriate __ListId__ and __ListLevel__ property values through __RadFixedDocumentEditor__’s __ParagraphProperties__. Inserting a new paragraph will result in adding a new list item.
The following code snippet shows how to add new list to __RadFixedDocumentEditor’s ListCollection__ and after that insert a paragraph with the corresponding list properties:

#### Insert Block Element

{{source=..\SamplesCS\PdfProcessing\Editing\RadFixedDocumentEditor1.cs region=Lists}} 
{{source=..\SamplesVB\PdfProcessing\Editing\RadFixedDocumentEditor1.vb region=Lists}} 

````C#
Telerik.Windows.Documents.Fixed.Model.Editing.Lists.List list = editor.Lists.AddList(ListTemplateType.NumberedDefault);
editor.ParagraphProperties.ListId = list.Id;
editor.ParagraphProperties.ListLevel = 0;
editor.InsertParagraph();

````
````VB.NET
Dim myList As Telerik.Windows.Documents.Fixed.Model.Editing.Lists.List = editor.Lists.AddList(ListTemplateType.NumberedDefault)
editor.ParagraphProperties.ListId = myList.Id
editor.ParagraphProperties.ListLevel = 0
editor.InsertParagraph()

````

{{endregion}}

For more information about lists you can follow this link to [List documetation article ]({%slug winforms/pdfprocessing/editing/list%}) .

# See Also

 * [RadFixedDocument]({%slug winforms/pdfprocessing/model/radfixeddocument%})

 * [RadFixedPage]({%slug winforms/pdfprocessing/model/radfixedpage%})

 * [ImageSource]({%slug winforms/pdfprocessing/model/imagesource%})

 * [Table]({%slug winforms/pdfprocessing/editing/table%})