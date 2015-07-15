---
layout: post
title: Splitter-Integration
description: splitter integration
platform: ejmvc
control: Splitter
documentation: ug
---

## Splitter Integration

The Splitter allows you to use other Essential ASP.NET MVC products inside the pane. The integrated function of those widgets can be used in other panes of the Splitter.

Configuring other widgets in Splitter

The following steps explain the implementation of Splitter integration.

1. In the View page, add the Splitter helper and configure the elements within the split pane. The first pane has the TreeView content and the next one has some content that is related to TreeView.



<table>
<tr>
<td>
[CSHTML]@{IDictionary<string, object> htmlAttribute = new Dictionary<string, object>();  htmlAttribute.Add("class", "_child");}@{Html.EJ().Splitter("outterSplitter").PaneProperties(p =>    {        p.Add().ContentTemplate(            @&lt;div class="cont"&gt;                &lt;h3 class="h3"&gt;                    ASP.NET MVC                &lt;/h3&gt;           @Html.EJ().TreeView("treeview").Items(items =>                {                    items.Add().Text("Mobile").Expanded(true).Children(child =>                    {                        child.Add().Id("tools").Text("Galaxy").HtmlAttributes(htmlAttribute);                    });                    items.Add().Text("Harddisk").Expanded(true).Children(child =>                   {                       child.Add().Id("chart").Text("Segate").HtmlAttributes(htmlAttribute);                   });                    items.Add().Text("Logo").Expanded(true).Children(child =>                    {                        child.Add().Id("grid").Text("Amazon").HtmlAttributes(htmlAttribute);                    });                }).ClientSideEvents(e=>e.NodeSelect("treeClicked"))            &lt;/div&gt;).PaneSize("200");        p.Add().ContentTemplate(            @&lt;div class="cont"&gt;                &lt;div class="_content"&gt;                  Select any product from the tree to show the description.                &lt;/div&gt;                &lt;div class="tools des"&gt;                    &lt;h3&gt;                        Tools                    &lt;/h3&gt;                    &lt;p&gt;                        Essential Tools is an collection of user interface components used to create interactive                        ASP.NET MVC applications.                    &lt;/p&gt;                &lt;/div&gt;                &lt;div class="chart des"&gt;                    &lt;h3&gt;                        Chart                    &lt;/h3&gt;                    &lt;p&gt; Essential Chart is a business-oriented charting component.&lt;/p&gt;                &lt;/div&gt;                &lt;div class="grid des"&gt;                    &lt;h3&gt;                        Grid                    &lt;/h3&gt;                    &lt;p&gt;                        Essential MVC Grid offers full featured a Grid control with extensive support for                        Grouping and the display of hierarchical data.                    &lt;/p&gt;                &lt;/div&gt;            &lt;/div&gt;).PaneSize("200");    }).Height("400").Width("100%").Render();}[CSS]&lt;style type="text/css"&gt;    #outterSplitter {        margin: 0 auto;    }    .cont #treeView_Container {        margin-bottom: 0;        border: none;    }    .h3, ._content, p {        font-size: 14px;        margin-top: 10px;        text-indent: 10px;    }    .des {        display: none;    }&lt;/style&gt;</td></tr>
<tr>
<td>
[JavaScript]&lt;script type="text/javascript"&gt;    function treeClicked(sender, args) {        if (sender.currentElement.hasClass('_child')) {//nodeSelect event handle            var content = $('.' + sender.currentElement[0].id).html();            $('._content').html(content);        }    }&lt;/script&gt;</td></tr>
</table>




When the node is selected in TreeView, the integrated output is displayed in the second pane.



{ ![](Splitter-Integration_images/Splitter-Integration_img1.png) | markdownify }
{:.image }




{ ![](Splitter-Integration_images/Splitter-Integration_img2.png) | markdownify }
{:.image }


