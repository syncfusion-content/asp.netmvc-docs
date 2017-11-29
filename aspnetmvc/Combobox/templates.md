---
layout: post
title: Templates in ComboBox control for Syncfusion ASP.NET MVC
description: Template support to ComboBox control for Syncfusion ASP.NET MVC
platform: mvc
control: ComboBox
documentation: ug
keywords: itemTemplate, ComboBox, groupTemplate, headerTemplate, footerTemplate, noRecordsTemplate, actionFailureTemplate
---

# Templates

The ComboBox has been provided with several options to customize each list item, group title, selected value, header, and footer elements. 

## Item template

The content of each list item within the ComboBox can be customized with the help of **ItemTemplate** property.

In the following sample, each list item is splited into two columns to display the relevant data.



{% highlight html %}
<div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("selectCountry")
                    .Width("100%")
                    .Datasource((IEnumerable<empList>)ViewBag.datasource)
                    .ComboBoxFields(h=>h.Text("text"))                    
                    .ItemTemplate("<div><img class=\"eimg\" src=\"../Images/combobox/${eimg}.png\" alt=\"employee\"/><div class=\"ename\"> ${text} </div><div class=\"temp\"> ${country} </div></div>")                    
                    .Placeholder("Select a country")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}

{% highlight css %}

    <style>
        
        .ename {
            font-weight: bold;
            display: block !important;
            opacity: .87;
        }
        
        .tempName {
            padding: 5px 42px;
            opacity: .87;
        }
        
        .temp {
            margin-top: -15px;
            opacity: .54;
        }
        
        .eimg {
            border-radius: 50%;
            padding: 10px 16px;
            width: 40px;
            height: 40px;
            float: left;
        }
        
        .tempImg {
            padding-bottom: 3px;
            border-radius: 50%;
            float: left;
        }
        
        .e-dropdownbase .e-list-item * {
            display: block;
        }
    </style>

{% endhighlight %}

Output for item template combobox control is as follows.


![](Combobox_templates_images/item_template.png)

## Group template

The group header title with appropriate sub-items are categorized that is customized with the help of **GroupTemplate** property. This template is common for both inline and floating group header template.

In the following sample, employees are grouped according to their city.



{%  highlight html %}

<div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("selectCountry")
                    .Width("100%")
                    .Datasource((IEnumerable<empList>)ViewBag.datasource)
                    .ComboBoxFields(h=>h.Text("text").GroupBy("country"))                    
                    .ItemTemplate("<div><img class=\"eimg\" src=\"../Images/combobox/${eimg}.png\" alt=\"employee\"/><div class=\"ename\"> ${text} </div><div class=\"temp\"> ${country} </div></div>")
                    .GroupTemplate("<strong>${country}</strong>")
                    .Placeholder("Select a country")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}

{% highlight css %}

    <style>
        
        .ename {
            font-weight: bold;
            display: block !important;
            opacity: .87;
        }
        
        .tempName {
            padding: 5px 42px;
            opacity: .87;
        }
        
        .temp {
            margin-top: -15px;
            opacity: .54;
        }
        
        .eimg {
            border-radius: 50%;
            padding: 10px 16px;
            width: 40px;
            height: 40px;
            float: left;
        }
        
        .tempImg {
            padding-bottom: 3px;
            border-radius: 50%;
            float: left;
        }
        
        .e-dropdownbase .e-list-item * {
            display: block;
        }
    </style>

{% endhighlight %}

Output for group template combobox control is as follows.


![](Combobox_templates_images/group_template.png)

## Header template

The header element is shown statically at the top of the popup list items within the ComboBox, and any custom element can be placed as a header element using the **HeaderTemplate** property.

In the following sample, the list items and its headers are designed and displayed as two columns similar to multiple columns of the grid.


{% highlight html %}

<div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("selectCountry")
                    .Width("100%")
                    .Datasource((IEnumerable<empList>)ViewBag.datasource)
                    .ComboBoxFields(h=>h.Text("text"))                    
                    .ItemTemplate("<div><img class=\"eimg\" src=\"../Images/combobox/${eimg}.png\" alt=\"employee\"/><div class=\"ename\"> ${text} </div><div class=\"temp\"> ${country} </div></div>")
                    .HeaderTemplate("<div class=\"head\">  Photo  <span style=\"padding-left:42px\"> Contact Info </span></div>")                    
                    .Placeholder("Select a country")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}

{% highlight css %}

    <style>
         .head {
            background-color: #a9a9a9;
            height: 30px;
            font-weight: bold;
            padding: 14px 0 0 20px;
        }
        
        
        .ename {
            font-weight: bold;
            display: block !important;
            opacity: .87;
        }
        
        .tempName {
            padding: 5px 42px;
            opacity: .87;
        }
        
        .temp {
            margin-top: -15px;
            opacity: .54;
        }
        
        .eimg {
            border-radius: 50%;
            padding: 10px 16px;
            width: 40px;
            height: 40px;
            float: left;
        }
        
        .tempImg {
            padding-bottom: 3px;
            border-radius: 50%;
            float: left;
        }
        
        .e-dropdownbase .e-list-item * {
            display: block;
        }
    </style>
{% endhighlight %}


Output for item template combobox control is as follows.


![](Combobox_templates_images/header_template.png)

## Footer template

The ComboBox has an option to show a footer element at the bottom of the list items in the popup list. Here, you can place any custom element as a footer element using the **FooterTemplate** property.

In the following sample, footer element displays the total number of list items present in the ComboBox.

{% highlight html %}

<div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("selectCountry")
                    .Width("100%")
                    .Datasource((IEnumerable<empList>)ViewBag.datasource)
                    .ComboBoxFields(h=>h.Text("text"))                    
                    .ItemTemplate("<div><img class=\"eimg\" src=\"../Images/combobox/${eimg}.png\" alt=\"employee\"/><div class=\"ename\"> ${text} </div><div class=\"temp\"> ${country} </div></div>")
                     .FooterTemplate("<div class=\"Foot\"> Total Items Count: 5 </div>")                    
                    .Placeholder("Select a country")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}

{% highlight css %}

    <style>
        
        .Foot {
            background-color: #dadada;
            vertical-align: middle;
            padding: 16px;
            font-weight: bold;
        }

        .ename {
            font-weight: bold;
            display: block !important;
            opacity: .87;
        }
        
        .tempName {
            padding: 5px 42px;
            opacity: .87;
        }
        
        .temp {
            margin-top: -15px;
            opacity: .54;
        }
        
        .eimg {
            border-radius: 50%;
            padding: 10px 16px;
            width: 40px;
            height: 40px;
            float: left;
        }
        
        .tempImg {
            padding-bottom: 3px;
            border-radius: 50%;
            float: left;
        }
        
        .e-dropdownbase .e-list-item * {
            display: block;
        }
    </style>

{% endhighlight %}

Output for footer template combobox control is as follows.


![](Combobox_templates_images/footer_template.png)

## No records template

The ComboBox is provided with the support to custom design the popup list content when no data is found and no matches found on search with the help of **NoRecordsTemplate** property.

In the following sample, popup list content displays the notification of no data available.



{%  highlight html %}
<div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("searchCustomer")
                    .Datasource(d => d.URL("//js.syncfusion.com/ej/ejServices/wcf/NorthWind.svc/").Offline(false).CrossDomain(true))
                    .Query("ej.Query().from('Suppliers').select('SupplierID', 'ContactName').take(0)")
                    .ComboBoxFields(f => f.Text("ContactName").Value("SupplierID"))
                    .Width("100%")
                    .NoRecordsTemplate("<span class='norecord'> NO DATA AVAILABLE</span>")
                    .Placeholder("Search a customer")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}

{% highlight c# %}

public ActionResult Databinding()
        {
            return View();
        }

{% endhighlight %}


Output for no records template combobox control is as follows.


![](Combobox_templates_images/no_records_template.png)

## Action failure template

There is also an option to custom design the popup list content when the data fetch request fails at the remote server. This can be achieved by using the **ActionFailureTemplate** property.

In the following sample, when the data fetch request fails, the ComboBox displays the notification.



{%  highlight html %}
<div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("searchCustomer")
                    .Datasource(d => d.URL("//js.syncfusion.com/ej/ejServices/wcf/NorthWind.svc/").Offline(false).CrossDomain(true))
                    .Query("ej.Query().from('Suppliers').select('SupplierID', 'ContactName')")
                    .ComboBoxFields(f => f.Text("ContactName").Value("SupplierID"))
                    .Width("100%")
                    .ActionFailureTemplate("<span class='action-failure'>Data fetch get fails</span>")
                    .Placeholder("Search a customer")
                    .Render();
            }
        </div>
    </div>

{% endhighlight %}

{% highlight c# %}

public ActionResult Databinding()
        {
            return View();
        }

{% endhighlight %}
