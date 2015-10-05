---
layout: post
title: Multiple files upload | UploadBox | ASP.NET MVC | Syncfusion
description: multiple files upload
platform: ejmvc
control: UploadBox
documentation: ug
---

# Multiple files upload

The UploadBox widget provides support to upload multiple files spontaneously. The MultipleFilesSelection property enables you to select multiple files while browsing.  To achieve this, set the MultipleFilesSelection property to ‘true’. The data type is Boolean.

N> The Multiple file selection supports all the latest versions of browser except Internet Explorer 9 and its previous versions.



The following steps explain the configuration of MultipleFilesSelection property in UploadBox. 

1. In the VIEW page, add the below script to configure the UploadBox element.

{% highlight CSHTML %}

// In the CSHTML page, add the UploadBox element.

@Html.EJ().Uploadbox("uploadbox").SaveUrl("Uploadbox/Save").RemoveUrl("Uploadbox/Remove").MultipleFilesSelection(true)

{% endhighlight %}

The following screenshot displays the output.



![](Multiple-files-upload_images/Multiple-files-upload_img2.png)





![](Multiple-files-upload_images/Multiple-files-upload_img3.png)



