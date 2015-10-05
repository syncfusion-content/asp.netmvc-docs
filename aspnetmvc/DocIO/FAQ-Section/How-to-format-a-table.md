---
layout: post
title: How to format a table | DocIo | ASP.NET MVC | Syncfusion
description: how to format a table?
platform: ejmvc
control: DocIO
documentation: ug
---

# How to format a table?

You can format a table in two ways.

### Method 1:

You can use the TableFormat property of the table instance.
{% tabs %}

{% highlight C# %}
WTable table= doc.LastSection.AddTable() as WTable;
table.ResetCells(4, 4);
table.TableFormat.Borders.BorderType = Syncfusion.DocIO.DLS.BorderStyle.Double;
table.TableFormat.LeftIndent=20; 
{% endhighlight %}
{% highlight VB %}
Dim table As IWTable = sec.body.AddTable()
table.ResetCells(4, 4)
table.TableFormat.Borders.BorderType = Syncfusion.DocIO.DLS.BorderStyle.Double
table.TableFormat.LeftIndent = 20
{% endhighlight %}
{% endtabs %} 
### Method 2:

You can use the ResetCell method of the table instance to format the cell. The following code illustrates this.
{% tabs %}

{% highlight C# %}
WTable table= doc.LastSection.AddTable() as WTable;
RowFormat rowFormat=new RowFormat();
rowFormat.Borders.BorderType = Syncfusion.DocIO.DLS.BorderStyle.Double;
rowFormat.LeftIndent=20; table.ResetCells(3,3,rowFormat,100);
{% endhighlight %}
{% highlight VB %}
Dim table As IWTable = sec.body.AddTable()
Dim rowFormat As New RowFormat()
rowFormat.BackColor = Color.Purplerow
Format.Borders.BorderType = Syncfusion.DocIO.DLS.BorderStyle.[Double]
rowFormat.LeftIndent = 20table.ResetCells(3, 3, rowFormat, 100)
{% endhighlight %}

{% endtabs %} 
