---
layout: post
title: customization
description: customization
platform: asp.net mvc
control: Pager
documentation: ug
---

# Customization

## Show Go To Page

The **ShowGoToPage** property of pager renders a textbox within the pager element.

{% highlight javascript %}

        @Html.EJ().Pager("pager").PageSize(1).PageCount(3).ShowGoToPage(true).TotalRecordsCount(20) 
     
{% endhighlight %}

Run the above code to get the below output.

![](customization_images\showGoToPage.png)
        
## Show Page Info

The **ShowPageInfo** property of the pager control determines whether to show the page related information like total records count, total pages, current page in a pager.


{% highlight javascript %}

        @Html.EJ().Pager("pager").PageSize(1).PageCount(3).ShowPageInfo(false).TotalRecordsCount(20) 

{% endhighlight %}

Run the above code to get the below output.

![](customization_images\pageInfo.png)

## Custom Text

The **CustomText** property of pager allows to add the custom text along with numeric values in the pager numeric elements that are used for navigation in pager control. 

{% highlight javascript %}

        @Html.EJ().Pager("pager").PageSize(1).PageCount(3).CustomText("page").TotalRecordsCount(20)

{% endhighlight %}

Run the above code to get the below output.

![](customization_images\customText.png)

## External Message

The pager control also allows to define a external message using externalMessage API to display an additional information. To use external message, we need to enable it using enableExternalMessage API. In the sample below, the externalMessage of pager is used to show the current active page of the pager control. Whenever the current page value of the pager changes, the externalMessage will be updated with the current page value.


{% highlight javascript %}

<div class="control">  
      @Html.EJ().Pager("pager").PageSize(1).PageCount(3).EnableExternalMessage(true).ExternalMessage("CurrentPage :1").TotalRecordsCount(20).ClientSideEvents(eve => { eve.Change("onChange"); })
</div>
<script type="text/javascript">
            function onChange(e) {
                var a = $("#pager").ejPager("instance");
                a.option("externalMessage", "CurrentPage: " + e.currentPage);
            }
</script>

{% endhighlight %}

Run the above code to get the below output.

![](customization_images\externalMessage.png)

## Custom CSS

Pager control allows you to customize the appearance using user defined CSS and custom skin options such as colors and backgrounds. To apply custom themes, we can make use of cssClass property. Using cssClass property, we can override the existing theme styles. In the following sample, value for cssClass property is set as customCss and this root class is used to customize the pager control theme.


{% highlight javascript %}

<div class="control"> 
       @Html.EJ().Pager("pager").PageSize(1).PageCount(3).TotalRecordsCount(20).CssClass("customCss")
</div>

{% endhighlight %}

Defining custom class.

{% highlight html %}

<style>
        .e-pager.customCss .e-link.e-currentitem{
                background:lightblue;
        }
        .e-pager.customCss .e-numericitem, .e-pager.customCss .e-pagermsg{
            font-family:monospace;
        }
        .e-pager.customCss .e-pagercontainer,.e-pager.customCss .e-link ,.e-pager.customCss .e-icon {
            background-color: rgba(33,33,33,0.35);
        }
        .e-pager.customCss {
            color:white;
            background-color: rgba(33,33,33,0.30);
        }
        .e-pager.customCss :hover {
             color:white
        }
        .e-pager.customCss .e-hover.e-numericitem, .e-pager.customCss .e-hover.e-icon{
            background-color:rgba(173,216,230,0.30);
        }
        .e-pager.customCss .e-hover.e-icon.e-disable {
             background-color: rgba(33,33,33,0.35);
          
        }
        .e-pager.customCss .e-icon, .e-pager.customCss .e-numericitem{
            color:white;
            border-right-color: #777;
        }
</style>

{% endhighlight %}

Run the above code to get the below output.

![](customization_images\cssClass.png)
