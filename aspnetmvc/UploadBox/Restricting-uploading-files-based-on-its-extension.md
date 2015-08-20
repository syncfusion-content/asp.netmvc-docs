---
layout: post
title: Restricting-uploading-files-based-on-its-extension
description: restricting uploading files based on its extension
platform: ejmvc
control: UploadBox
documentation: ug
---

# Restricting uploading files based on its extension

## Allow Extension

Files are filtered before they are uploaded. You can select the files to be filtered by using browse button. The ExtensionsAllow property allows upload of the selected extensions only. You can give multiple extensions by using comma (,).  The data type is string.

> Note: Prepend dot (.) symbol with extension like “.pdf”.



The following steps explain the configuration of ExtensionsAllow property in UploadBox. 

1. In the VIEW page, add the below script to configure the UploadBox element.



{% highlight js %}

// In the CSHTML page, add UploadBox element.

@Html.EJ().Uploadbox("uploadbox").SaveUrl("Uploadbox/Save").RemoveUrl("Uploadbox/Remove").ExtensionsAllow(".docx,.pdf")

{% endhighlight %}

## Deny Extension

Files are filtered before they are uploaded. You can select the files to be filtered by using browse button. The ExtensionsDeny property denies upload of the selected extensions. You can give multiple extensions by using comma (,).  The data type is string.

> Note: Prepend dot (.) symbol with extension like “.pdf”.


The following steps explain the configuration of ExtensionsDeny property in UploadBox

1. In the VIEW page, add the below script to configure the UploadBox element.


{% highlight js %}

// In the CSHTML page, add UploadBox ox element.

@Html.EJ().Uploadbox("uploadbox").SaveUrl("Uploadbox/Save").RemoveUrl("Uploadbox/Remove").ExtensionsDeny(".docx,.pdf")

{% endhighlight %}

