---
layout: post
title: Asynchronous Upload | UploadBox | ASP.NET MVC | Syncfusion
description: asynchronous upload
platform: ejmvc
control: UploadBox
documentation: ug
---

# Asynchronous Upload

The AsyncUpload property is Boolean type, which allow us to upload and remove files asynchronously. To achieve this, set the AsyncUpload property to ‘true’. The default value of AsyncUpload property is ‘true’.

The following steps guide you in uploading the file asynchronously.

1.  In the VIEW page, add the below script to configure the UploadBox element.

{% highlight CSHTML %}

// In the view page, add the UploadBox element.

@Html.EJ().Uploadbox("uploadbox").SaveUrl("Uploadbox/Save").RemoveUrl("Uploadbox/Remove").AsyncUpload(true)

{% endhighlight %}


