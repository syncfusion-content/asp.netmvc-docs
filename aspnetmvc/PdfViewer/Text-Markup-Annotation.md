---
layout: post
title: Text markup annotation | PDF viewer | ASP .NET MVC | Syncfusion
description: You can learn here about text markup annotation support in Syncfusion ASP.NET MVC PDF Viewer control and more details.
platform: ejmvc
control: PDF viewer
documentation: ug
---

## Text Markup Annotation in ASP.NET MVC PDF Viewer

The PDF viewer control supports adding text markup annotations in the PDF documents. The control also renders the existing text markup annotations from the PDF document when the document is loaded in it.

The text markup annotation tools in the default toolbar can be enabled or disabled using the toolbarSettings property.

The following code snippet describes how to show only the text markup annotation tools in the control.

{% highlight javascript %}
(Html.EJ().PdfViewer("pdfviewer").ServiceUrl(VirtualPathUtility.ToAbsolute("~/api/PdfViewer")).ToolbarSettings(t => t.Items(Syncfusion.JavaScript.PdfViewerEnums.ToolbarItems.TextMarkupAnnotationTools)))
{% endhighlight %}

The following screenshot shows the PDF viewer with the PDF documents containing text markup annotations:

![Text markup annotation icon](Text-Markup-Annotation_images/Text_Markup_Annotations_img1.png)

**Enable or Disable the text markup annotations**

The adding and modifying of the text markup annotations can be enabled or disabled using the EnableTextMarkupAnnotations property.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").EnableTextMarkupAnnotations(true))
{% endhighlight %}

The adding and modifying of the highlight annotations can be enabled or disabled using the EnableHighlightAnnotation property.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").EnableHighlightAnnotation(true))
{% endhighlight %}

The adding and modifying of the strikethrough annotations can be enabled or disabled using the EnableStrikethroughAnnotation property.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").EnableStrikethroughAnnotation(true))
{% endhighlight %}

The adding and modifying of the underline annotations can be enabled or disabled using the EnableUnderlineAnnotation property.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").EnableUnderlineAnnotation(true))
{% endhighlight %}

**Providing settings for text markup annotations**

You can get or set the settings of the highlight annotations using the highlightSettings property. The highlightSettings property is used to set the color, opacity, author, subject, modifiedDate and isLocked properties of the highlight annotations.

{% highlight javascript %}
 $(function () {
            $("#pdfviewer").ejPdfViewer({ highlightSettings: { color: "#ffff00", author: "Guest", opacity: 0.5, subject: "highlight", modifiedDate: "2017-03-27 12:00:51", isLocked: true} });
        });
{% endhighlight %}

You can get or set the settings of the strikethrough annotations using the strikethroughSettings property. The strikethroughSettings property is used to set the color, opacity, author, subject, modifiedDate, and isLocked properties of the strikethrough annotations.

{% highlight javascript %}
 $(function () {
            $("#pdfviewer").ejPdfViewer({ strikethroughSettings: { color: "#ff0000", author: "Guest", opacity: 0.5, subject: "strikethrough", modifiedDate: "2017-03-27 12:00:51", isLocked: true
	} });
        });
{% endhighlight %}

You can get or set the settings of the underline annotations using the underlineSettings property. The underlineSettings property is used to set the color, opacity, author, subject, modifiedDate, and isLocked properties of the underline annotations.

{% highlight javascript %}
 $(function () {
            $("#pdfviewer").ejPdfViewer({ underlineSettings: { color: "#00ff00", author: "Guest", opacity: 0.5, subject: "underline", modifiedDate: "2017-03-27 12:00:51", isLocked: true
	} });
        });
{% endhighlight %}

**Adding text markup annotations**

The text markup annotations are added to the PDF document using the text markup annotation tools provided in the toolbar of the PDF viewer control.

The annotations can be added to the PDF document from the client side using the annotationType property and addAnnotation method.

{% highlight javascript %}
var pdfviewerObj = $("#pdfviewer").data("ejPdfViewer");
pdfviewerObj.addAnnotation(ej.PdfViewer.AnnotationType.Underline);
{% endhighlight %}

The colorpicker control is provided in the text markup annotation tools to select the desired color for the text markup annotation to be added in the document.

![Text markup annotation colorpicker](Text-Markup-Annotation_images/Text_Markup_Annotations_img2.png)

When the text markup annotation is added in the PDF document, the annotationAdd event will be triggered in the control. The event method can be defined using the AnnotationAdd property of the control.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").ClientSideEvents(e=>e.AnnotationAdd(“annotationAdded”)))

        function annotationAdded(args) {
            alert("A text markup annotation is added in the PDF document”);
        }

{% endhighlight %}

**Adding notes to the text markup annotation**

The notes can be added to the text markup annotations using the context menu  in the PDF viewer control.

Right click the text markup annotation in the PDF document, the context menu will be opened in the PDF viewer control. You can select the option **Open Pop-up Note** to add the note to the annotation.

The following screenshot shows that the notes have been added to a text markup annotation in the PDF document:

![Text markup annotation notes](Text-Markup-Annotation_images/Text_Markup_Annotations_img3.png)

**Editing the text markup annotation**

The properties of the text markup annotations in the PDF document can be edited using the properties window provided in the PDF viewer control. The color, opacity, author, and subject of the text markup annotation can be modified. The properties of the text markup annotation can also be locked using the locked checkbox in the properties window.

N> The isLocked property of the text markup annotation will lock the properties of the selected annotation. The property of the text markup annotation can be modified once the isLocked property is disabled.

When a property of the text markup annotation is changed in the PDF viewer control, annotationPropertiesChange event will be triggered in the control. The event method can be defined using the AnnotationPropertiesChange property of the control.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").ClientSideEvents(e=>e.AnnotationPropertiesChange(“annotationPropertiesChanged”)))
function annotationPropertiesChanged(args) {
            alert("The properties of a text markup annotation is modified in the PDF viewer”);
        }
{% endhighlight %}

The following screenshot shows the properties window used for editing the properties of a text markup annotation:

![Text markup annotation properties](Text-Markup-Annotation_images/Text_Markup_Annotations_img4.png)

The annotationDelete event will be triggered in the control when the text markup annotation in the PDF document is deleted. The event method can be defined using the AnnotationDelete property of the control.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").ClientSideEvents(e=>e.AnnotationDelete(“annotationDeleted”)))
function annotationDeleted (args) {
            alert("A text markup annotation is deleted in the PDF document”);
        }
{% endhighlight %}

You can undo and redo the changes made to text markup annotations included in the PDF documents using the undo() and redo() methods.

{% highlight javascript %}
 function undoChanges() {
        $(“#pdfviewer”).data(“ejPdfViewer”).undo();
    }
    function redoChanges() {
        $(“#pdfviewer”).data(“ejPdfViewer”).redo();
    }
{% endhighlight %}

**Saving the text markup annotation**

When the download tool is selected in the toolbar, the text markup annotations will be saved in the PDF document. This action will not affect the original document.

**Printing the text markup annotation**

When the print tool is selected in the toolbar, the PDF document will be printed along with the text markup annotations added to the pages. This action will not affect the original document.
