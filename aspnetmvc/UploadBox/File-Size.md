---
layout: post
title: File Size | UploadBox | ASP.NET MVC | Syncfusion
description: file size 
platform: ejmvc
control: UploadBox
documentation: ug
---

# File Size 

## Maximum File Size for UploadBox

In the UploadBox control, you can browse files with the size going up to gigabytes. You can restrict the files from being browsed using the FileSize property. When you do not use this property, it takes a default size, 31457280B, that is, 31MB. When this size exceeds, we cannot browse the file. 

1. Add the following code example to the corresponding View page to render the UploadBox control with the customized file size.

{% highlight CSHTML %}

<div class="control"> 
    @Html.EJ().Uploadbox("UploadBox")
	.SaveUrl("Uploadbox/Save")
	.RemoveUrl("UploadBox/Remove")
	.FileSize(848576)
	.ClientSideEvents(e => e.Error("error"))

</div>

<script type="text/javascript">

	function error(e) 
	{

		alert(e.error);

	}
</script>

{% endhighlight %}

To know about file action, we need to refer link:

    <http://help.syncfusion.com/aspnetmvc/uploadbox/file-size>

The following screenshot displays UploadBox control with customized file size.

When you want to browse the file within the fileSize, you can browse and upload the files.

![](File-Size_images/File-Size_img1.png)


When you try to browse the file with exceeded FileSize, an error message will be displayed as an alert.You can customize the error message by converting the file size into mb and display the corresponding value in error message.


{% highlight CSHTML %}

     <script type="text/javascript">

	  function fileUploadError(e) 
	   {
	     alert("The selected file size is too large. Please select a file less than " + Math.round(e.model.fileSize / (1024 * 1024)) + "MB");
       }
    </script>

{% endhighlight %}

Now you will get the error message as shown in the below image

![](File-Size_images/File-Size_img3.png)

N> By default, UploadBox will display the file size as bytes value in error message.