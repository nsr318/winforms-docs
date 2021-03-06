---
title: Run
page_title: Run | UI for WinForms Documentation
description: Run
slug: winforms/wordsprocessing/model/run
tags: run
published: True
position: 3
previous_url: wordsprocessing-model-run
---

# Run

__Run__ element is an inline-level flow content element intended to contain a run of formatted text.

* [Inserting a Run](#inserting-a-run)

* [Modifying a Run](#modifying-a-run)

## Inserting a Run

The following code snippet creates a __Run__ elements and adds it to a [Paragraph]({%slug winforms/wordsprocessing/model/paragraph%}).

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRun.cs region=radwordsprocessing-model-run_0}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRun.vb region=radwordsprocessing-model-run_0}} 

````C#
Run run = new Run(document);
paragraph.Inlines.Add(run);

````
````VB.NET
Dim run As New Run(document)
paragraph.Inlines.Add(run)

````

{{endregion}} 

>tip The parent __Paragraph__ should belong to the same document that is passed to the constructor of the __Run__ .
>

You can add a run at a specific index in the __Inlines__ collection of a paragraph using the __Insert()__ method. Here is how to add a run at the beginning of a paragraph:

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRun.cs region=radwordsprocessing-model-run_1}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRun.vb region=radwordsprocessing-model-run_1}} 

````C#
Run run = new Run(document);
paragraph.Inlines.Insert(0, run);

````
````VB.NET
Dim run As New Run(document)
paragraph.Inlines.Insert(0, run)

````

{{endregion}} 

You can also use the __AddRun()__ method of the __Inlines__ collection of a paragraph. The method creates a new __Run__ instance, adds it to the container and returns it:

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRun.cs region=radwordsprocessing-model-run_2}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRun.vb region=radwordsprocessing-model-run_2}} 

````C#
// Adds an empty run.
Run run1 = paragraph.Inlines.AddRun();
// Adds a run and set the text to the text property.
Run run2 = paragraph.Inlines.AddRun("The text.");

````
````VB.NET
' Adds an empty run.
Dim run1 As Run = paragraph.Inlines.AddRun()
' Adds a run and set the text to the text property.
Dim run2 As Run = paragraph.Inlines.AddRun("The text.")

````

{{endregion}}

Inserting text in the document can also be achieved with the [](6a2a5fb7-6df2-48a1-9d21-d8d25526695d) class:

{{source=..\SamplesCS\WordsProcessing\Model\WordsProcessingRun.cs region=radwordsprocessing-model-run_3}} 
{{source=..\SamplesVB\WordsProcessing\Model\WordsProcessingRun.vb region=radwordsprocessing-model-run_3}} 

````C#
RadFlowDocumentEditor editor = new RadFlowDocumentEditor(new RadFlowDocument());
// Adds new run to the document
Run run1 = editor.InsertText("First run ");
// Adds new run and starts new paragraph
Run run2 = editor.InsertLine("Second run");

````
````VB.NET
Dim editor As New RadFlowDocumentEditor(New RadFlowDocument())
' Adds new run to the document
Dim run1 As Run = editor.InsertText("First run ")
' Adds new run and starts new paragraph
Dim run2 As Run = editor.InsertLine("Second run")

````

{{endregion}}

## Modifying a Run

The Run exposes several properties that allow you to customize how it is rendered and formatted.


* __Properties__: Retrieves all __CharacterProperties__ for this element. For more information about the CharacterProperties see [this article]({%slug winforms/wordsprocessing/concepts/style-properties%}).
            

* __Text__: Specifies the text for the run.
            

* __StyleId__: Represents the ID of the style that is applied to this run.

* __FlowDirection__: Represents the flow direction of the run:

  * __LeftToRight__: Indicates that the text should flow from left to right.

  * __RightToLeft__: Indicates that the text should flow from right to left.
            

* __FontFamily__: Specifies the font family that is used to render the text. *Style property. The value is themable object.*

* __FontSize__: Specifies the size of the font. *Style property.*

* __Shading__: Represents the shading applied to the run. It is a composite object and is read-only. You can obtain the following properties from it:

  * __BackgroundColor__: Specifies the background color for the shading. *Style property. The value is themable object.*

  * __PatternColor__: Specifies the pattern color for the shading. *Style property. The value is themable object.*

  * __Pattern__: Specifies the pattern which is used to lay the pattern color over the background color for the shading. *Style property.*

* __FontStyle__: Specifies the font style. *Style property.*

* __FontWeight__:  Specifies the font weight. *Style property.*

* __ForegroundColor__:  Specifies the foreground color. *Style property. The value is themable object.*

* __HighlightColor__: Specifies the highlight color. *Style property.*

* __BaselineAlignment__: Specifies how the baseline is positioned on the vertical axis, relative to the established baseline for text. *Style property.*

* __Strikethrough__: Specifies if the text is stroked trough. *Style property.*

* __Underline__: Specifies the underline for the run. It is composite object and is read-only. You can obtain the following properties from it:
            
  * __Color__: Indicates the underline color. *Style property.*

  * __Pattern__: Indicates the underline pattern. *Style property.*

>tip Style properties are properties that can be inherited from a style. For more information about styles see [this article]({%slug winforms/wordsprocessing/concepts/style-properties%}).
>


>tip Themable objects are objects that can be inherited from a theme. For more information about themes check [this article]({%slug winforms/wordsprocessing/concepts/document-themes%}).
>


# See Also

 * [Run API Reference](http://www.telerik.com/help/winforms/allmembers_t_telerik_windows_documents_flow_model_run.html)

 * [Paragraph]({%slug winforms/wordsprocessing/model/paragraph%})

 * [Style Properties]({%slug winforms/wordsprocessing/concepts/style-properties%})

 * [Document Themes]({%slug winforms/wordsprocessing/concepts/document-themes%})
