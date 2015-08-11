---
layout: post
title: Appearance-and-styling
description: appearance and styling 
platform: ejmvc
control: UploadBox
documentation: ug
---

# Appearance and styling 

The UploadBox widget provides support to customize the dialog box text and button text. 

## Customizing Button Text

The following table contains the subproperties available under UploadBoxButtonText property. To customize the text, pass the alternate text with corresponding subproperties. 

_Table3: Sub-properties under buttonText property

<table>
<tr>
<th>
Name</th><th>
Description</th><th>
Data Type</th></tr>
<tr>
<td>
Browse</td><td>
Sets the alternative text for browse button. </td><td>
String</td></tr>
<tr>
<td>
Upload</td><td>
Sets the alternative text for upload button. </td><td>
String</td></tr>
<tr>
<td>
Cancel</td><td>
Sets the alternative text for cancel button. </td><td>
String</td></tr>
</table>


The following steps explain the configuration of UploadBoxButtonText property in UploadBox. 

1. In the VIEW page, add the below script to configure the UploadBox element.





{% highlight html %}

// In the CSHTML page, add the UploadBox element.



@Html.EJ().Uploadbox("uploadbox").SaveUrl("Uploadbox/Save").RemoveUrl("Uploadbox/Remove").UploadBoxButtonText(text=>text.Browse("Choose Files").Cancel("Cancel upload").Upload("Upload file"))

{% endhighlight %}


The following screenshot displays the output.



![](Appearance-and-styling_images/Appearance-and-styling_img1.png)



## Customizing Upload Dialog

The following table contains the subproperties available under UploadBoxDialogText property. To customize the text, pass the alternate text with corresponding subproperties. 

_Table4: Subproperties under dialogText property

<table>
<tr>
<th>
Name</th><th>
Description</th></tr>
<tr>
<td>
Title</td><td>
Sets the alternative text for Title of UploadBox dialog. </td></tr>
<tr>
<td>
Name</td><td>
Sets the alternative text for Name column.  </td></tr>
<tr>
<td>
Size</td><td>
Sets the alternative text for Size column. </td></tr>
<tr>
<td>
Status</td><td>
Sets the alternative text for status column.</td></tr>
</table>


The following steps explain the configuration of UploadBoxDialogText property in UploadBox. 

1. In the VIEW page, add the below script to configure the UploadBox element.





{% highlight html %}

// In the CSHTML page, add the UploadBox element.

@Html.EJ().Uploadbox("uploadbox").SaveUrl("Uploadbox/Save").RemoveUrl("Uploadbox/Remove").UploadBoxDialogText(text=>text.Title("Upload File List").Name("File Name").Size("File Size").Status("File Status"))

{% endhighlight %}


The following screenshot displays the output.



![](Appearance-and-styling_images/Appearance-and-styling_img2.png)



## Show or Hide File details 

The ShowFileDetails property is Boolean type, which allow us to show or hidefiledetails in the uploaded file listdialog. To hide the uploaded file details, set ShowFileDetails property is set to ‘false’. By default value of ShowFileDetails property is set to ‘true’.

The following steps explains the configuration of ShowFileDetails property in UploadBox.

1. In the VIEW page, add the below script to configure the UploadBox element.





{% highlight html %}

// In the CSHTML page, add the UploadBox element.

@Html.EJ().Uploadbox("uploadbox").SaveUrl("Uploadbox/Save").RemoveUrl("Uploadbox/Remove").ShowFileDetails(false)

{% endhighlight %}


## Theme

UploadBox control’s style and appearance are controlled based on CSS classes. In order to apply styles to the UploadBox control, you can refer to two files namely, ej.widgets.core.min.css and ej.theme.min.css. When the file ej.widgets.all.min.css is referred, then it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.widgets.all.min.css is the combination of these both files. 

By default, there are 12-theme support available for UploadBox control namely,

* Default-theme
* Flat-azure-dark
* Fat-lime
* Flat-lime-dark
* Flat-saffron
* Flat-saffron-dark
* Gradient-azure
* Gradient-azure-dark
* Gradient-lime
* Gradient-lime-dark
* Gradient-saffron
* Gradient-saffron-dark

## Custom CSS

CSSclass customizes the UploadBox control’s appearance. Define a CSSclass as per the requirement and assign the class name to CssClass property. The data type is string. 

The following steps explain the configuration of CssClass property in UploadBox. 

1. In the View page, add the below script to configure the UploadBox element.





{% highlight html %}

// In the CSHTML page, add the UploadBox element.

@Html.EJ().Uploadbox("uploadbox").SaveUrl("Uploadbox/Save").RemoveUrl("Uploadbox/Remove").CssClass("customcss")


{% endhighlight %}



2. In CSS, configure Custom Styles for the UploadBox.

{% highlight html %}

  <style class="cssStyles">

      .customcss .e-select{

            background-color: #FFFFCC;

            font-weight: bold; 

            font-family: sans-serif;

        }

    </style>

{% endhighlight %}


The following screenshot displays the output.



![](Appearance-and-styling_images/Appearance-and-styling_img3.png)



