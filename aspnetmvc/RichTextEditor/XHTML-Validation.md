---
layout: post
title: XHTML Validation in RichTextEditor widget for Syncfusion Essential ASP.NET MVC
description: XHTML Validation to format the RichTextEditor widget's content
platform: ASP.NET MVC
control: RTE
documentation: ug
keywords: RichTextEditor, XHTML Validation

---
# XHTML Validation

The editor provides option to validate its content through the EnableXHTML property. When you set or modify the content into the editor, it continuously checks whether the HTML source of the content that you are creating is valid. The editor examines the HTML markup and then removes the elements or attributes that are not valid. 

{% highlight razor %}

  @{
    Html.EJ().RTE("rteSample").Width("820px").ContentTemplate(@<div>
          The RichTextEditor (RTE) control enables you to edit the contents with insert table and images
          It also provides a toolbar that helps to apply rich text formats to the content entered in the TextArea
          </div>)
        .EnableXHTML(true)
        .Render();
    }

{% endhighlight %}

The editor checks the following settings on validation:

* **Attributes** 
  * Must be specified in lowercase 
  * Proper use of quotation marks around the attributes
  * Must be valid attributes for corresponding HTML element
  * All the required attributes must be included in the HTML element
  * Accepts the allowed values alone such as true or false.
* **HTML** **Elements** 
  * Must be in lowercase 
  * All opening tags must be closed
  * Allows only the valid HTML elements
