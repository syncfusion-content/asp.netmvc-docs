---
layout: post
title: Multiple-files-upload
description: multiple files upload
platform: ejmvc
control: UploadBox
documentation: ug
---

## Multiple files upload

The UploadBox widget provides support to upload multiple files spontaneously. The MultipleFilesSelection property enables you to select multiple files while browsing.  To achieve this, set the MultipleFilesSelection property to ‘true’. The data type is Boolean.

{ ![http://help.syncfusion.com/ug/windows%20forms/pdf/ImagesExt/image517_36.jpg](Multiple-files-upload_images/Multiple-files-upload_img1.jpeg) | markdownify }
{:.image }
_Note: The Multiple file selection supports all the latest versions of browser except Internet Explorer 9 and its previous versions._



The following steps explain the configuration of MultipleFilesSelection property in UploadBox. 

1. In the VIEW page, add the below script to configure the UploadBox element.





[CSHTML]

// In the CSHTML page, add the UploadBox element.

@Html.EJ().Uploadbox("uploadbox").SaveUrl("Uploadbox/Save").RemoveUrl("Uploadbox/Remove").MultipleFilesSelection(true)



The following screenshot displays the output.



{ ![](Multiple-files-upload_images/Multiple-files-upload_img2.png) | markdownify }
{:.image }




{ ![](Multiple-files-upload_images/Multiple-files-upload_img3.png) | markdownify }
{:.image }


