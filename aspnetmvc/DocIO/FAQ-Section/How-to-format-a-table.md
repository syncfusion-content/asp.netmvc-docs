---
layout: post
title: How to format a table 
description: how to format a table?
platform: ejmvc
control: DocIO
documentation: ug
---

# How to format a table?

You can format a table in two ways.

## Method 1:

You can use the TableFormat property of the table instance.

{% highlight c# %}
WTable table= doc.LastSection.AddTable() as WTable;
table.ResetCells(4, 4);
table.TableFormat.Borders.BorderType = Syncfusion.DocIO.DLS.BorderStyle.Double;
table.TableFormat.LeftIndent=20; 
{% endhighlight %}
{% highlight vbnet %}
Dim table As IWTable = sec.body.AddTable()
table.ResetCells(4, 4)table.TableFormat.Borders.BorderType = Syncfusion.DocIO.DLS.BorderStyle.Doubletable.TableFormat.LeftIndent = 20
{% endhighlight  %}
## Method 2:

You can use the ResetCell method of the table instance to format the cell. The following code illustrates this.

{% highlight c# %}
WTable table= doc.LastSection.AddTable() as WTable;
RowFormat rowFormat=new RowFormat();
rowFormat.Borders.BorderType = Syncfusion.DocIO.DLS.BorderStyle.Double;
rowFormat.LeftIndent=20; table.ResetCells(3,3,rowFormat,100);
{% endhighlight  %}
{% highlight vbnet %}
Dim table As IWTable = sec.body.AddTable()
Dim rowFormat As New RowFormat()rowFormat.BackColor = Color.PurplerowFormat.Borders.BorderType = Syncfusion.DocIO.DLS.BorderStyle.[Double]rowFormat.LeftIndent = 20table.ResetCells(3, 3, rowFormat, 100)
{% endhighlight  %}


