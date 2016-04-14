---
layout: post
title: Getting Started | ListBox | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: ListBox
documentation: ug
---

# Getting Started

This section helps to understand the getting started of the ListBox widget with the step-by-step instructions.

## Create ListBox

Create a MVC Project and add the necessary DLL and scripts with the help of the given [MVC Getting Started](http://help.syncfusion.com/aspnetmvc/getting-started) documentation.

Add the following code snippet to the corresponding view page to render the ListBox.

{% highlight razor %}

@Html.EJ().ListBox("listbox").TargetID("carslist")
<div>
    <ul id="carslist">
        <li>Audi A4</li>
        <li>Audi A5</li>
        <li>Audi A6</li>
        <li>Audi A7</li>
        <li>Audi A8</li>
        <li>BMW 501</li>
        <li>BMW 502</li>
        <li>BMW 503</li>
        <li>Batch</li>
        <li>BMW 507</li>
        <li>BMW 3200</li>
        <li>Cut</li>
    </ul>
</div>

{% endhighlight %}


![](Getting-Started_images/Getting-Started_img1.png)

## Data binding

We can populate data in the ListBox widget using `DataSource` and `Fields` properties.

### See Also

[Data Binding](http://help.syncfusion.com/aspnetmvc/listbox/databinding)

In the Model page, define the Class name as Bikes with BikeId and BikeName field property.

In the Controller, create a list of “Bikes” class and add the data.

In the View page, add the ListBox helper and bind the data.

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

![](Getting-Started_images/Getting-Started_img2.png)

## Selection

The ListBox widget supports item selection.

### See Also

[Selection](http://help.syncfusion.com/js/listbox/selection)

{% highlight razor %}

@Html.EJ().ListBox("listbox").TargetID("carslist").SelectedIndex(2)
    <div>
        <ul id="carslist">
            <li>Audi A4</li>
            <li>Audi A5</li>
            <li>Audi A6</li>
            <li>Audi A7</li>
            <li>Audi A8</li>
            <li>BMW 501</li>
            <li>BMW 502</li>
            <li>BMW 503</li>
            <li>Batch</li>
            <li>BMW 507</li>
            <li>BMW 3200</li>
            <li>Cut</li>
        </ul>
    </div>
    
{% endhighlight %}

![](Getting-Started_images/Getting-Started_img3.png)
