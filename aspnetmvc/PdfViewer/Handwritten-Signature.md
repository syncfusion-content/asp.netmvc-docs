---
layout: post
title: Hand written signature| PDF viewer | ASP .NET MVC | Syncfusion
description: Hand written signature
platform: ejmvc
control: PDF viewer
documentation: ug
---

## Handwritten Signature

The PDF viewer supports adding handwritten signatures into the PDF document. The handwritten signature reduces the paper work of reviewing the content and verifies it digitally.

The PDF viewer control has an option in the toolbarSettings property to enable or disable the signature button in the default toolbar.

The following code snippet describes how to disable the signature tool in the widget.

{% highlight javascript %}
<div style="width:100%;height:780px;">
    @(Html.EJ().PdfViewer("pdfviewer").ServiceUrl(VirtualPathUtility.ToAbsolute("~/api/PdfViewer"))
        .ToolbarSettings(t=>t.Items(Syncfusion.JavaScript.PdfViewerEnums.ToolbarItems.SignatureTool)))
</div>
{% endhighlight %}

**Enable or Disable handwritten signature**

The adding of handwritten signature feature in the PDF document can be enabled or disabled using the EnableSignture property.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").EnableSignature(true))
{% endhighlight %}

**Providing settings for hand written signature**

You can get or set the settings of the handwritten signature using the signatureSettings property. The signatureSettings property is used to set the color and opacity of the hand written signature.

{% highlight javascript %}
<script type="text/javascript">
    $(function() {
        $(“#pdfviewer”).ejPdfViewer({signatureSettings: { color: “#ff0000”, opacity: “0.5” } })
    });
</script>
{% endhighlight %}

**Adding signature in the PDF document**

The handwritten signature can be added by drawing the signature content in the signature panel and clicking the button labeled ADD. The following screenshots are the pictorial representation of this.

![](Signature_images/Signature_img1.png)

![](Signature_images/Signature_img2.png)

![](Signature_images/Signature_img3.png)

When the handwritten signature is added in the PDF document, the signatureAdd event will be triggered in the control. The event method can be defined using the SignatureAdd property of the control.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").ClientSideEvents(e=>e.SignatureAdd(“signatureAdded”)))
<script type="text/javascript">
        function signatureAdded (args) {
            alert("A hand written signature is added in the PDF document”);
        }
</script>
{% endhighlight %}

**Move, Resize and Delete the Handwritten Signature**

The handwritten signature content can be moved to the specified location within the page bounds by using touch gestures, arrow keys, and mouse. We can also resize the handwritten signature content by maintaining the aspect ratio.

When the handwritten signature is resized in the PDF viewer control, the signatureResize event will be triggered in the control. The event method can be defined using the SignatureResize property of the control.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").ClientSideEvents(e=>e.SignatureResize(“signatureResize”)))
<script type="text/javascript">
        function signatureResize (args) {
            alert("A hand written signature is resized in the PDF viewer control”);
        }
</script>
{% endhighlight %}

The selected handwritten signature content can be deleted using the “Delete” option in the context menu or delete key. The following screenshots are the pictorial representation of this.

![](Signature_images/Signature_img4.png)     

When the handwritten signature is deleted from the PDF document, the signatureDelete event will be triggered in the control. The event method can be defined using the SignatureDelete property of the control.       

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").ClientSideEvents(e=>e.SignatureDelete(“signatureDelete”)))
<script type="text/javascript">
        function signatureDelete (args) {
            alert("A hand written signature is removed from the PDF document”);
        }
</script>
{% endhighlight %}

You can undo and redo the changes made to the handwritten signatures included in the PDF document using the undo() and redo() methods. 

{% highlight javascript %}
<script type="text/javascript">
    function undoChanges() {
        $(“#pdfviewer”).data(“ejPdfViewer”).undo();
    }
    function redoChanges() {
        $(“#pdfviewer”).data(“ejPdfViewer”).redo();
    }
</script>
{% endhighlight %}

**Changing properties of handwritten signature**

The properties that is opacity and color of a handwritten signature can be modified by color palate and opacity slider, which is available in the “Properties” option in context menu. The following screenshots are the pictorial representation of this.

![](Signature_images/Signature_img5.png)      

Select the desired color from the color palette and then click OK button.

![](Signature_images/Signature_img6.png)  

The selected color will be updated on the signature.

![](Signature_images/Signature_img7.png)  

You can also change the opacity of the added signature in the “properties” option.

![](Signature_images/Signature_img8.png)  

When a property of the handwritten signature is changed in the PDF viewer control, the signaturePropertiesChange event will be triggered in the control. The event method can be defined using the SignaturePropertiesChange property of the control.

{% highlight javascript %}
@(Html.EJ().PdfViewer("pdfviewer").ServiceUrl("https://js.syncfusion.com/ejServices/api/PdfViewer").ClientSideEvents(e=>e.SignaturePropertiesChange (“signaturePropertiesChanged”)))
<script type="text/javascript">
        function signaturePropertiesChanged(args) {
            alert("A property of the hand written signature is changed in the PDF viewer control”);
        }
</script>
{% endhighlight %}

**Saving the Signature**

The added signature can be saved to the PDF document and can be downloaded by clicking the download button in the toolbar. This action will not affect the original document.

![](Signature_images/Signature_img9.png) 

**Printing the Signature**

When the print button is clicked in the toolbar, the PDF document will be printed along with the signature added to the pages. This action will not affect the original document.

