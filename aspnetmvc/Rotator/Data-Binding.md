---
layout: post
title: Data Binding | Rotator | ASP.NET MVC | Syncfusion
description: data binding
platform: ejmvc
control: Rotator
documentation: ug
---

# Data Binding

Rotator provides a flexible approach for binding the data from various data sources. There are various properties in Rotator for Data Binding. The value set to this property is object type.

## Data Fields and Configuration

The following sub-properties provide a way to bind the data either locally/remotely to the Rotator control. 

### DataSource

This property specifies the list of data that contains a set of data fields. Each data value is used to render an item for the Rotator. Datasource receives Essential DataManager object and JSON object. The value set to this property is object type.

### Fields

It defines mapping fields for the data items of the Rotator. The value set to this property is object type.

### Text

It specifies the text content of the Image in Rotator control. The value set to this property is string type.

### Url

This property specifies the URL for an image. The value set to this property is string type.

### Query

This property receives query to retrieve data from the table (query is same as SQL).This property is applicable only when a remote data source is used. Each data value is used to render an item for the Rotator. The value set to this property is object type.

## Local data binding

Rotator provides the data binding support for the Rotator item. So you can bind the data from JSONData. For this behavior, you need to map the corresponding filed with their column names. The data can be bound as a list and it is assigned to Datasource property. You can refer the following code example to bind local data.

{% tabs %}
 
{% highlight C# %}

// Add the following data list to be bind in the controller page and define the corresponding data.

// Define local data source elements with  fields            

public class LocalData

{

	public string Text { get; set; }

	public string Url { get; set; }

}


//Refer the Model in the controller 

using <Application name>.Models;



        List<LocalData> localValues = new List<LocalData>();

        public ActionResult Index()

        {

            localValues.Add(new LocalData { Text = "Beautiful Bird", Url = "../Images/rotator/bird.jpg" });

            localValues.Add(new LocalData { Text = "Colorful Night", Url = "../Images/rotator/night.jpg" });

            localValues.Add(new LocalData { Text = "Technology", Url = "../Images/rotator/tablet.jpg" });

            localValues.Add(new LocalData { Text = "Nature", Url = "../Images/rotator/nature.jpg" });

            localValues.Add(new LocalData { Text = "Snow Fall", Url = "../Images/rotator/snowfall.jpg" });

            localValues.Add(new LocalData { Text = "Credit Card", Url = "../Images/rotator/card.jpg" });

            localValues.Add(new LocalData { Text = "Amazing Sculptures", Url = "../Images/rotator/sculpture.jpg" });

            ViewBag.datasource = localValues;

            return View();

        }  

{% endhighlight %}

{% highlight CSHTML %}

@Html.EJ().Rotator("sliderContent").Datasource((IEnumerable<LocalData>)ViewBag.datasource)
.RotatorFields(t => t.Text("Text")
.Url("Url")).SlideWidth("600px")
.SlideHeight("350px")
.ShowPlayButton(true)

{% endhighlight %}
{% endtabs %} 
![](Data-Binding_images/Data-Binding_img1.png)

Rotator control with local data binding
{:.caption}