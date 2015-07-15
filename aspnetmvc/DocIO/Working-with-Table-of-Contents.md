---
layout: post
title: Working-with-Table-of-Contents
description: working with table of contents
platform: ejmvc
control: DocIO
documentation: ug
---

## Working with Table of Contents

The TableOfContent class represents the Table Of Contents (TOC) in a Word document.

The following steps illustrate how to add the Table of Contents to a Microsoft Word document.

1. On the Insert menu, click Field.
2. Then, select the TOC field type.



Essential DocIO allows you to add a TOC to the Word document by using AppendTOC method of the WParagraph class.

UpperHeadingLevel and LowerHeadingLevel define the number of heading levels to be displayed for the TOC. For example, when UpperHeadingLevel is set to 4 and LowerHeadingLevel is set to 3, then TOC displays the heading levels from third to fourth.

SetTOCLevelStyle method sets the style for each TOC level. For example, SetTOCLevelStyle(1, "Normal") sets the Normal style to the first level of TOC.

Class Hierarchy

ParagraphItem

|

TableOfContent



Public Constructors

_Table_ _89__: Public Constructors_

<table>
<tr>
<td>
Constructor Name</td><td>
Description</td></tr>
<tr>
<td>
TableOfContent.TableOfContent (IWordDocument)</td><td>
Initializes a new instance of the TableOfContent class. </td></tr>
<tr>
<td>
TableOfContent.TableOfContent (IWordDocument, string)</td><td>
Initializes a new instance of the TableOfContent class.  </td></tr>
</table>


Public Properties

_Table_ _90__: Public Properties_

<table>
<tr>
<td>
Property Name</td><td>
Description</td></tr>
<tr>
<td>
EntityType</td><td>
Gets the type of the entity.</td></tr>
<tr>
<td>
IncludePageNumbers</td><td>
Gets or sets a value indicating whether to include page numbers in TOC. Default value is true.</td></tr>
<tr>
<td>
LowerHeadingLevel</td><td>
Gets or sets the lower heading level (in interger).</td></tr>
<tr>
<td>
RightAlignPageNumbers</td><td>
Gets or sets a value indicating whether to align page numbers on the right side. Default value is true.</td></tr>
<tr>
<td>
TableID</td><td>
Gets or sets the table ID (for TC fields).</td></tr>
<tr>
<td>
UpperHeadingLevel</td><td>
Gets or sets upper heading level (in interger).</td></tr>
<tr>
<td>
UseHeadingStyles</td><td>
Gets or sets a value indicating whether to use base heading style (Heading 1…Heading 9).</td></tr>
<tr>
<td>
UseHyperlinks</td><td>
Gets or sets a value indicating whether to insert TOC entries as hyperlinks.</td></tr>
<tr>
<td>
UseOutlineLevels</td><td>
Gets or sets a value indicating whether to use outline levels.</td></tr>
<tr>
<td>
UseTableEntryFields</td><td>
Gets or sets a value indicating whether the table is built from TC fields. When the TableID property is defined, the table is built only from TC fields with the same identifier.</td></tr>
</table>


{ ![](Working-with-Table-of-Contents_images/Working-with-Table-of-Contents_img1.jpeg) | markdownify }
{:.image }
_Note: DocIO cannot create Outline levels. However, by turning on the UseOutlineLevels property, you can create TOC from existing outline levels._



{ ![](Working-with-Table-of-Contents_images/Working-with-Table-of-Contents_img2.png) | markdownify }
{:.image }




Public Methods

_Table_ _91__: Public Methods_

<table>
<tr>
<td>
Method Name</td><td>
Description</td></tr>
<tr>
<td>
GetTOCLevelStyleName</td><td>
Gets the style name for TOC level.</td></tr>
<tr>
<td>
SetTOCLevelStyle </td><td>
Specifies the style for TOC level.</td></tr>
</table>
The following code example illustrates how to insert TOC based on custom styles.

<table>
<tr>
<td>
[C#]WordDocument doc = new WordDocument();doc.EnsureMinimal();WParagraph para = doc.LastParagraph;TableOfContent toc = para.AppendTOC(1, 1);toc.UseHeadingStyles = false;//Sets the TOC level style based on which the TOC should be created.toc. SetTOCLevelStyle(1, "MyStyle1");WSection section = doc.LastSection;WParagraph newPara = section.AddParagraph() as WParagraph;WTextRange text = newPara.AppendText("My Style1") as WTextRange;newPara.ApplyStyle("MyStyle1");//Updates the table of contents.doc.UpdateTableOfContents();</td></tr>
<tr>
<td>
[VB.NET]Dim doc As New WordDocument()doc.EnsureMinimal()Dim para As WParagraph = doc.LastParagraphDim toc As TableOfContent = para.AppendTOC(1, 1)toc.UseHeadingStyles = False'Sets the TOC level style based on which the TOC should be created.toc.SetTOCLevelStyle(1, "MyStyle1")Dim section As WSection = doc.LastSectionDim newPara As WParagraph = TryCast(section.AddParagraph(), WParagraph)Dim text As WTextRange = TryCast(newPara.AppendText("My Style1"), WTextRange)newPara.ApplyStyle("MyStyle1")'Updates the table of contents.doc.UpdateTableOfContents()</td></tr>
</table>


### Updating Table of contents

UpdatingTableOfContents method of WordDocument class updates table of contents field in the Word document. Internally, Essential DocIO updates page numbers in table of contents by using the Word to PDF layout engine. Hence, the limitations of updating page numbers are similar to the limitations of Word to PDF lay outing.



> { ![](Working-with-Table-of-Contents_images/Working-with-Table-of-Contents_img3.jpeg) | markdownify }
{:.image }
_Note: UpdatingTableOfContents is not supported in Silverlight, WinRT, or Windows Phone applications._



Known Limitations

The following are the known limitations:

* Currently shapes, drawing canvas, and table auto resizing are not supported in Word to PDF lay outing as they may lead to updation of incorrect page number.
* Text wrapping support is partially handled in Word to PDF lay outing as it may lead to updation of incorrect page number.



The following code example illustrates how to update TOC.

<table>
<tr>
<td>
[C#]WordDocument doc = new WordDocument(“Sample.docx”);//Updates the table of contents.doc.UpdateTableOfContents();</td></tr>
<tr>
<td>
[VB.NET]Dim doc As New WordDocument(“Sample.docx”)'Updates the table of contents.doc.UpdateTableOfContents()</td></tr>
</table>


