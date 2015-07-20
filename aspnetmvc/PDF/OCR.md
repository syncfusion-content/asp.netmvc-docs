---
layout: post
title: OCR
description: ocr
platform: ejmvc
control: PDF
documentation: ug
---

## OCR

The Tesseract Optical Character Recognition (OCR) engine is originally developed by Hewlett-Packard. It is one of the top three engines in the 1995 UNLV accuracy test and is probably one of the most accurate open-source OCR engines available. It is extensively revised with sponsorship from Google. Essential PDF uses the Tesseract OCR engine to perform OCR on a PDF file. Essential PDF eliminates the 32-bit restriction of Tesseract and allows you to work either in x86-bit or x64-bit platforms without any deployment changes.

Use Case Scenarios

* This converts an unsearchable PDF document into a searchable PDF document.
* It allows you to search, select, and copy text from images found in the PDF document.
### Tables for Properties and Methods


Properties

_Table_ _32__: Property Table_

<table>
<tr>
<td>
Property</td><td>
Description</td></tr>
<tr>
<td>
Settings</td><td>
Gets or sets the settings for performing OCR.</td></tr>
<tr>
<td>
Paginate</td><td>
Gets or sets image pagination in the PDF document.</td></tr>
<tr>
<td>
Regions</td><td>
Gets or sets page regions for performing OCR. </td></tr>
<tr>
<td>
Language</td><td>
Gets or sets the OCR language to process.</td></tr>
<tr>
<td>
PageIndex</td><td>
Gets or sets page index to process OCR.</td></tr>
<tr>
<td>
PageRegions</td><td>
Gets or sets rectangular array for the page to process OCR in specific regions.</td></tr>
<tr>
<td>
Performance</td><td>
Gets or sets the perfomance of OCR. </td></tr>
<tr>
<td>
BlackList</td><td>
Gets or sets the black-list values. Blacklist of characters not to recognize.</td></tr>
<tr>
<td>
WhiteList</td><td>
Gets or sets the white-list values. Whitelist of characters to recognize.</td></tr>
</table>
Methods

_Table_ _33__: Method Table_

<table>
<tr>
<th>
Method</th><th>
Description</th></tr>
<tr>
<th>
PerformOCR</th><th>
Performs OCR on images in the loaded PDF document.</th></tr>
</table>
### Deploying OCR 

#### Assemblies

The following assemblies need to be referenced in your application to use the Tesseract OCR engine.

Syncfusion Assemblies

* Syncfusion.Core.dll
* Syncfusion.Compression.Base.dll
* Syncfusion.Pdf.Base.dll
* Syncfusion.OcrProcessor.dll

Tesseract Assemblies

* SyncfusionTesseract.dll (Tesseract version 3.0)
* liblept168.dll (Leptonica image processing library used by the Tesseract OCR engine since version 3)
#### Referencing Syncfusion.OCRProcessor.Base from a .Net project


To use a component in your application, you need to add a reference to it

 1.   Open Solution Explorer of the application you have created. Right-click Reference folder and then click Add References.

2.   Add the following assemblies as references in the application.

* Syncfusion.Core.dll
* Syncfusion.Compression.Base.dll
* Syncfusion.Pdf.Base.dll
* Syncfusion.OCRProcessor.Base.dll

3. Place the SyncfusionTesseract.dll and liblept168.dll assemblies in the local system and provide an assembly path to the OCR processor.

### Performing OCR for a Complete PDF Document

To perform OCR on PDF using OCR processor, first you need to create an OCRProcessor with the tesseract assemblies and then you have to load the PDF document and finally perform OCR for the loaded PDF document

The following code example illustrates how to perform OCR for a complete PDF document.



[C#]



//Initializes the OCR processor by providing tesseract binaries(SyncfusionTesseract.dll and liblept168.dll)

//to the OCR processor overload.

using (OCRProcessor processor = new OCRProcessor(@"TesseractBinaries\"))

{

//Loads a PDF document.

PdfLoadedDocument lDoc = new PdfLoadedDocument("Input.pdf");

//Sets OCR language to process.

processor.Settings.Language = Languages.English;

//Processes OCR by providing PDF document, data dictionary and language.

processor.PerformOCR(lDoc, @"Tessdata\");

//Saves the OCR processed PDF document in a disk.

lDoc.Save("Sample.pdf");

lDoc.Close(true);

}



[VB]



'Initializes OCR processor by providing tesseract binaries          (SyncfusionTesseract.dll and liblept168.dll) to the OCR processor overload.

Using processor As New OCRProcessor("TesseractBinaries\")

'Loads a PDF document.

Dim lDoc As New PdfLoadedDocument("Input.pdf")

'Sets OCR language to process.

processor.Settings.Language = Languages.English

'Processes OCR by providing PDF document, data dictionary and language.

processor.PerformOCR(lDoc, "Tessdata\")

'Saves the OCR processed PDF document in a disk.

lDoc.Save("Sample.pdf")

lDoc.Close(True)

End Using

### Perform OCR for a Specific Region of PDF Document

Essential PDF OCR processor allows you to process the part of the PDF document.

The following code example explains you how to perform OCR for a specific region of the PDF document.



[C#]

//Initializes OCR processor by providing tesseract binaries (SyncfusionTesseract.dll and liblept168.dll)to the OCR processor overload.

using (OCRProcessor processor = new OCRProcessor(@"TesseractBinaries\"))

{

//Loads a PDF document

PdfLoadedDocument lDoc = new PdfLoadedDocument("Input.pdf");

//Sets OCR language to process.

processor.Settings.Language = Languages.English;

RectangleF rect = new RectangleF(0, 100, 950, 150);

//Assigns rectangles to the page

PageRegion region = new PageRegion();

List<PageRegion> pageRegions = new List<PageRegion>();

region.PageIndex = 1;

region.PageRegions = new RectangleF[] { rect };

pageRegions.Add(region);

processor.Settings.Regions = pageRegions;

//Processes OCR by providing the PDF document, data dictionary and language

processor.PerformOCR(lDoc, @"Tessdata\");

//Saves the OCR processed PDF document in a disk.

lDoc.Save("Sample.pdf");

lDoc.Close(true);

}



[VB]



'Initializes the OCR processor by providing tesseract binaries (SyncfusionTesseract.dll and liblept168.dll) to the OCR processor overload.

Using processor As New OCRProcessor("TesseractBinaries\")

'Loads a PDF document.

Dim lDoc As New PdfLoadedDocument("Input.pdf")

'Sets OCR language to process

processor.Settings.Language = Languages.English

Dim rect As New RectangleF(0, 100, 950, 150)

'Assigns rectangles to the page.

Dim region As New PageRegion()

Dim pageRegions As New List(Of PageRegion)()

region.PageIndex = 1

region.PageRegions = New RectangleF() {rect}

pageRegions.Add(region)

processor.Settings.Regions = pageRegions

'Processes OCR by providing the PDF document, data dictionary and language.

processor.PerformOCR(lDoc, "Tessdata\")

'Saves the OCR processed PDF document in a disk.

lDoc.Save("Sample.pdf")

lDoc.Close(True)

{{ '![http://help.syncfusion.com/ug/windows%20forms/pdf/ImagesExt/image517_36.jpg](OCR_images/OCR_img1.jpeg)' | markdownify }}
{:.image }
_Note: The Tesseract binaries, namely SyncfusionTessaract.dll, liblept168.dll, and language pack (tessdata), will be available in the following location._

<<Installation Location>>\Syncfusion\Essential Studio\<<Version Number>>\OCRProcessor

