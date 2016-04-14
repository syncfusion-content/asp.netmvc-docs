---
layout: post
title: Databinding | ListBox | ASP.NET MVC | Syncfusion
description: data binding 
platform: ejmvc
control: ListBox
documentation: ug
---

# Databinding 

## Field mapping

The ListBox widget has a Field property (object) which holds the properties to map with Datasource fields. For example, the field object has a Text property which is necessary to map with specific field in the Datasource to render the items in the ListBox widget.

The field object contains the following properties.

* text

* toolTipText

* id

* selectBy

* groupBy

* checkBy

* tableName

* imageUrl

* imageAttributes

* spriteCssClass

* htmlAttributes

## Local data

ListBox provides extensive data binding support to populate data items. To achieve this, you need to map the corresponding field with the column names in the data source. Refer the below example.

Here the BikeName and BikeId fields are mapped with text and id properties of the field object respectively. 

In the Model page, define the Class name as Bikes with BikeId and BikeName field property.

In the Controller, create a list of “Bikes” class and add the data.

In the View page, add the ListBox helper and bind the data.

{% tabs %}
{% highlight c# %}

//define model class with the corresponding property

public class Bikes
    {
        public string BikeId { get; set; }
        public string BikeName { get; set; }
    }
    
//specify desired datasource data by using the model class properties

public partial class ListBoxController : Controller
    {
        List<Bikes> bike = new List<Bikes>();
        public ActionResult Index()
        {
            bike.Add(new Bikes { BikeId = "bk1", BikeName = "Apache RTR" });
            bike.Add(new Bikes { BikeId = "bk2", BikeName = "CBR 150-R" });
            bike.Add(new Bikes { BikeId = "bk3", BikeName = "CBZ Xtreme" });
            bike.Add(new Bikes { BikeId = "bk4", BikeName = "Discover" });
            bike.Add(new Bikes { BikeId = "bk5", BikeName = "Dazzler" });
            bike.Add(new Bikes { BikeId = "bk6", BikeName = "Flame" });
            bike.Add(new Bikes { BikeId = "bk7", BikeName = "Fazzer" });
            bike.Add(new Bikes { BikeId = "bk8", BikeName = "FZ-S" });
            bike.Add(new Bikes { BikeId = "bk9", BikeName = "Pulsar" });
            bike.Add(new Bikes { BikeId = "bk10", BikeName = "Shine" });
            bike.Add(new Bikes { BikeId = "bk11", BikeName = "R15" });
            bike.Add(new Bikes { BikeId = "bk12", BikeName = "Unicorn" });
            ViewBag.datasource = bike;
            return View();
        }
    }


{% endhighlight %}

{% highlight razor %}

@{
    Html.EJ().ListBox("bikeList")
        .Datasource((IEnumerable<Bikes>)ViewBag.datasource)
        .ListBoxFields(df => df.ID("BikeId")
        .Text("BikeName")).Render();
}


{% endhighlight %}
{% endtabs %}


![](Databinding_images\Databinding_img1.png)


## Remote data

We can bind the data for the ListBox from any server that is located as a remote web service. By using Query options, you can pass the query string to filter the data that helps to avoid rendering the excessive data. 

Here the CustomerID field is mapped with Text property of the field object. The queries can be created using [ej.Query()](http://help.syncfusion.com/js/datamanager/query).

{% highlight razor %}

@{
    Html.EJ().ListBox("listbox")
        .Datasource("http://mvc.syncfusion.com/Services/Northwnd.svc/")
        .ListBoxFields(fields => fields.Text("CustomerID"))
        .Query("ej.Query().from('Customers').take(10)")
        .Render();
}


{% endhighlight %}

![](Databinding_images\Databinding_img2.png)

### Virtual Scrolling

The ListBox widget provides support to load its data on demand via scrolling behavior to improve the application’s performance. This can be achieved using “AllowVirtualScrolling” property. There are two ways to load data based on the scrolling type.

1. Normal scrolling

2. Continuous Scrolling

The scrolling type can be defined via “VirtualScrollMode” property.

#### Normal Scrolling

This mode allows you to load the list box data while scrolling i.e. each time the scroll bar is scrolled, it will send request to the server to load the data.

{% highlight razor %}

@{
    Html.EJ().ListBox("listbox")
        .Datasource("http://mvc.syncfusion.com/Services/Northwnd.svc/")
        .ListBoxFields(fields => fields.Text("CustomerID"))
        .Query("ej.Query().from('Customers')")
        .AllowVirtualScrolling(true)
        .Render();
}


{% endhighlight %}


N> By default, the value of “VirtualScrollMode” property is normal.

![](Databinding_images\Databinding_img3.png)

![](Databinding_images\Databinding_img4.png)

#### Continuous Scrolling

This mode allows you to load the list box data when the scrollbar reaches the end point. In this mode, we can specify the number of items to be loaded per request.

The number of items to be loaded per request can be specified using the “ItemRequestCount” property.

{% highlight razor %}

@{
    Html.EJ().ListBox("listbox")
        .Datasource("http://mvc.syncfusion.com/Services/Northwnd.svc/")
        .ListBoxFields(fields => fields.Text("CustomerID"))
        .Query("ej.Query().from('Customers')")
        .AllowVirtualScrolling(true)
        .VirtualScrollMode(VirtualScrollMode.Continuous)
        .ItemRequestCount(10)
        .Render();
}


{% endhighlight %}


N> The “ItemRequestCount” property will work only when “VirtualScrollMode” is “Continuous”.

![](Databinding_images\Databinding_img5.png)

![](Databinding_images\Databinding_img6.png)


### Handling errors

In remote binding, the server might not return data sometimes due to various reasons. In such cases we need to handle the error properly. We can handle it using the “ActionFailure” event.

{% highlight razor %}


@{
    Html.EJ().ListBox("listbox")
        .Datasource("http://mvc.syncfusion.com/Services/Northwnd.svc/")
        .ListBoxFields(fields => fields.Text("CustomerID"))
        .Query("ej.Query().from('Customers').take(10)")
        .ClientSideEvents(eve => eve.ActionFailure("onFailure"))
        .Render();
}

<script>
    function onFailure(args) {
        //handle errors
    }
</script>



{% endhighlight %}



![](Databinding_images\Databinding_img7.png)


