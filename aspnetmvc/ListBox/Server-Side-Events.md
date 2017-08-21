---
layout: post
title: Server Side Events | ControlNameundefined | ASP.NET MVC | Syncfusion
description: server side events
platform: aspnet
control: Control Name
documentation: ug
---

# Server Side Events

The following server side event is available in Listbox control.

<table>
<tr>
<th>
Event</th><th>
Event Description</th><th>
Event Description</th></tr>
<tr>
<td>
OnCheckChange</td><td>
Occurs when CheckBox value is changed.</td><td>
Event Argument contains the following parameters.e.IsChecked – Status of Listbox Checkbox.e.Text – Text of Listbox Selected item.e.Value – Value of Listbox Selected item.e.SelectedText –Text of Listbox Selected item.e.ItemId – Index Value of Listbox Selected item.e.EventType – Event Name.Arguments – Contain keys and values for SelectedText and Args.</td></tr>
<tr>
<td>
OnValueSelect</td><td>
Occurs when Listbox Active Node is changed</td><td>
Event Argument contains the following parameters.e.IsChecked – Status of Listbox Checkbox.e.Text – Text of Listbox Selected item.e.Value – Value of Listbox Selected item.e.SelectedText –Text of Listbox Selected item.e.ItemId – Index Value of Listbox Selected item.e.EventType – Event Name.Arguments – Contain keys and values for SelectedText and Args.</td></tr>
<tr>
<td>
OnIndexChanged</td><td>
Occurs when selected list item Index is Change.</td><td>
Event Argument contains the following parameters.e.IsChecked – Status of Listbox Checkbox.e.Text – Text of Listbox Selected item.e.Value – Value of Listbox Selected item.e.SelectedText –Text of Listbox Selected item.e.ItemId – Index Value of Listbox Selected item.e.EventType – Event Name.Arguments – Contain keys and values for SelectedText and Args.</td></tr>
</table>
In an ASPX page, add the Listbox control to configure Listbox events.

{% highlight html %}

<%--Add serverside event for ListBox control as follows--%>

<ej:ListBox ID="listBoxSample" DataTextField="CustomerID" OnValueSelect="listBoxSample_CheckChange" runat="server">

</ej:ListBox>

{% endhighlight %}



The following code example define listbox sample _ValueSelect server side event in behind.

{% highlight c# %}

    // Add the code in C Sharp page



    protected void Page_Load(object sender, EventArgs e)

    {

        this.listBoxSample.DataSource = "http://mvc.syncfusion.com/Services/Northwnd.svc/";

        this.listBoxSample.Query = "ej.Query().from('Customers')";

    }

    protected void listBoxSample_CheckChange(object sender, Syncfusion.JavaScript.Web.ListBoxEventArgs e)

    {

        //e.IsChecked – Status of Checkbox

        //e.EventType – Event Name

        //e.Arguments – Contain keys and values for SelectedText and Args

        //e.Text – Text value of selected node

        //e.Value – Value of selected node

        //e.SelectedText – Text  of selected node

        //e.ItemId – Index value of selected node



    }



{% endhighlight %}



