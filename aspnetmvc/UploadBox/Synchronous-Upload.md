---
layout: post
title: Synchronous-Upload
description: synchronous upload 
platform: ejmvc
control: UploadBox
documentation: ug
---

# Synchronous Upload 

This features allow you to upload and remove the files synchronously. To achieve this, set the AsyncUpload property to ‘false’. The data type is Boolean.

Note: By default, UploadBox widget works with asynchronous upload option only.



The following steps guide you in uploading the file synchronously.

1. In the VIEW page, create a form with action and post method and then add the script into the form to configure the UploadBox element.


{% highlight html %}

// In the CSHTML page, create a form with action and post method and then add the UploadBox element.



@using (Html.BeginForm("Index","Home",FormMethod.Post))

{    

    @Html.EJ().Uploadbox("uploadbox").AsyncUpload(false)

    <input type="submit" value="Submit" />

}

{% endhighlight %}

Once the form is submitted by using Submit button, it triggers the SaveActionResult.  In ActionResult, save the files as usual.

The following screenshot displays the output.



![](Synchronous-Upload_images/Synchronous-Upload_img2.png)



