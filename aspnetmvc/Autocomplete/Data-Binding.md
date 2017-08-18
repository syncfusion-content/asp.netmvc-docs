---
layout: post
title: Data Binding | AutoComplete | ASP.NET MVC | Syncfusion
description: data-binding
platform: ejmvc
control: AutoComplete
documentation: ug
---

# Data-Binding

In order to render the AutoComplete control, the data needs to be bound to it in a proper way. The following sub-properties provide a way to bind either the local or remote data to the AutoComplete widget by binding the appropriate data fields to the corresponding options.

## Fields

### DataSource 

This property assigns the List of objects to the AutoComplete control. Either local data or remote data can be specified.  

### Query 

It accepts the data of object type, usually the query string to fetch the required data from a specific table based on certain condition. This property is optional hence when it is not specified the entire records that are initially assigned through DataSource are taken into consideration.

### Key

It maps the corresponding key field name from the data table or the List of objects that is assigned to the DataSource with the Key property of the AutoComplete control. The Key value that is fetched from the table is unique for each records.

### Text

It maps the corresponding Text field name from the data table or the List of Objects that is assigned to the DataSource with the Text property of the AutoComplete control. The text value that is fetched from the table represents the value to be displayed in the AutoComplete textbox.

### GroupBy

It maps the groupBy field name from the data table or JSON data that is assigned to the dataSource. The groupBy value that is fetched from the table is made to group the values in the datasource.

### HtmlAttributes

This allows you to map the CSS styles or classes to the corresponding data from table or the List of Objects data with the AutoComplete items. The HtmlAttributes value customizes the AutoComplete items based on HTML styling or class assigned to it. 

## Local data

AutoComplete provides extensive data binding support to populate AutoComplete items, so that the values are mapped to the AutoComplete fields, namely Key and Text. DataBinding helps you bind a key value pair to AutoComplete textbox. Key field takes the unique id of the dataSource elements. Text field gets the value to be displayed in the AutoComplete textbox.

### Defining the Local data for AutoComplete

The following steps explain local data binding to an AutoComplete textbox.

1. In the Controller page, define the Class with key and text field. Then create a List of that class and add the data.

   ~~~ csharp
			
			public class CarsList

			{

			  public int UniqueKey { get; set; }

			  public string Text { get; set; }

			}



			public partial class AutocompleteController : Controller

			{

				List<CarsList> cars = new List<CarsList>();

				public ActionResult AutocompleteFeatures()

				{

					cars.Add(new CarsList { UniqueKey = 1, Text = "Audi S6" });

					cars.Add(new CarsList { UniqueKey = 2, Text = "Austin-Healey" });

					cars.Add(new CarsList { UniqueKey = 3, Text = "Alfa Romeo" });

					cars.Add(new CarsList { UniqueKey = 4, Text = "Aston Martin" });

					cars.Add(new CarsList { UniqueKey = 5, Text = "BMW 7" });

					cars.Add(new CarsList { UniqueKey = 6, Text = "Bentley Mulsanne" });

					cars.Add(new CarsList { UniqueKey = 7, Text = "Bugatti Veyron" });

					cars.Add(new CarsList { UniqueKey = 8, Text = "Chevrolet Camaro" });

					cars.Add(new CarsList { UniqueKey = 9, Text = "Cadillac" });

					cars.Add(new CarsList { UniqueKey = 10, Text = "Duesenberg J " });

					cars.Add(new CarsList { UniqueKey = 11, Text = "Dodge Sprinter" });

					cars.Add(new CarsList { UniqueKey = 12, Text = "Elantra" });

					cars.Add(new CarsList { UniqueKey = 13, Text = "Excavator" });

					cars.Add(new CarsList { UniqueKey = 14, Text = "Ford Boss 302" });

					cars.Add(new CarsList { UniqueKey = 15, Text = "Ferrari 360" });

					cars.Add(new CarsList { UniqueKey = 16, Text = "Ford Thunderbird" });

					cars.Add(new CarsList { UniqueKey = 17, Text = "GAZ Siber" });

					cars.Add(new CarsList { UniqueKey = 18, Text = "Honda S2000" });

					cars.Add(new CarsList { UniqueKey = 19, Text = "Hyundai Santro" });

					cars.Add(new CarsList { UniqueKey = 20, Text = "Isuzu Swift" });

					cars.Add(new CarsList { UniqueKey = 21, Text = "Infiniti Skyline" });

					cars.Add(new CarsList { UniqueKey = 22, Text = "Infiniti Skyline" });

					cars.Add(new CarsList { UniqueKey = 23, Text = "Kia Sedona EX" });

					cars.Add(new CarsList { UniqueKey = 24, Text = "Koenigsegg Agera" });

					cars.Add(new CarsList { UniqueKey = 25, Text = "Lotus Esprit" });

					cars.Add(new CarsList { UniqueKey = 26, Text = "Lamborghini Diablo" });

					cars.Add(new CarsList { UniqueKey = 27, Text = "Mercedes-Benz" });

					cars.Add(new CarsList { UniqueKey = 28, Text = "Mercury Coupe" });

					cars.Add(new CarsList { UniqueKey = 29, Text = "Maruti Alto 800" });

					cars.Add(new CarsList { UniqueKey = 30, Text = "Nissan Qashqai" });

					cars.Add(new CarsList { UniqueKey = 31, Text = "Oldsmobile S98" });

					cars.Add(new CarsList { UniqueKey = 32, Text = "Opel Superboss" });

					cars.Add(new CarsList { UniqueKey = 33, Text = "Porsche 356" });

					cars.Add(new CarsList { UniqueKey = 34, Text = "Pontiac Sunbird" });

					cars.Add(new CarsList { UniqueKey = 35, Text = "Scion SRS/SC/SD" });

					cars.Add(new CarsList { UniqueKey = 36, Text = "Saab Sportcombi" });

					cars.Add(new CarsList { UniqueKey = 37, Text = "Subaru Sambar" });

					cars.Add(new CarsList { UniqueKey = 38, Text = "Suzuki Swift" });

					cars.Add(new CarsList { UniqueKey = 39, Text = "Triumph Spitfire" });

					cars.Add(new CarsList { UniqueKey = 40, Text = "Toyota 2000GT" });

					cars.Add(new CarsList { UniqueKey = 41, Text = "Volvo P1800" });

					cars.Add(new CarsList { UniqueKey = 42, Text = "Volkswagen Shirako" });

					cars.Add(new CarsList { UniqueKey = 43, Text = "Ford Boss 302" });

					cars.Add(new CarsList { UniqueKey = 44, Text = "Ferrari 360" });

					cars.Add(new CarsList { UniqueKey = 45, Text = "Ford Thunderbird" });

					ViewBag.datasource = cars;

					return View(); 

				 } 

			}
   ~~~
   

2. In the View page, add Autocomplete helper and map the Local   data list to corresponding DataSource and AutoCompleteFields.


   ~~~ cshtml

	@Html.EJ().Autocomplete("autocomplete")

	.Datasource((IEnumerable<CarsList>)ViewBag.datasource)

	.AutocompleteFields(field => field.Key("UniqueKey").Text("Text"))
   
   ~~~
   


The following image is the output for AutoComplete control with local data binding.



![](Data-Binding_images/Data-Binding_img1.png)

AutoComplete with local data-binding
{:.caption}

## Remote data

AutoComplete provides remote data binding support to populate AutoComplete items, so that the values are mapped to the AutoComplete fields from a remote web service using DataManager and Query. 

DataManager is used to manage relational data. It supports CRUD that is Create, Read, Update, and Destroy, in individual requests and batches. DataManager uses two different classes, ej.DataManager, for processing and ej.Query, for serving data. ej.DataManager communicates with dataSource and ej.Query generates data queries that are read by the DataManager.

### Configuring remote data for AutoComplete

The below following types are used to bind remote datasource to an AutoComplete textbox.


###OData

OData is a standardized protocol for creating and consuming data. You can provide the [OData service](http://www.odata.org/) URL directly to the Datasource URL property.


{% highlight html %}

    @Html.EJ().Autocomplete("selectCar").Datasource("http://js.syncfusion.com/ejservices/Wcf/Northwind.svc/").Query("ej.Query().from('Customers').take(10)").AutocompleteFields(af => af.Text("CustomerID")).Width("300") 

{% endhighlight %}

Run the code to get the following output

![](Data-Binding_images\odata_img1.png)

###OData Version 4

For OData Version 4 support ODataV4Adaptor should be used. By using URL property of Datasource, you can bind OData Version 4 Service link and specify Adaptor value as enum AdaptorType.ODataV4Adaptor.

For further details about OData service please refer [the link](http://www.odata.org/).

{% highlight html %}


@Html.EJ().Autocomplete("selectData").Datasource(dataSource => dataSource.URL("http://services.odata.org/V4/Northwind/Northwind.svc/Regions/").Adaptor(AdaptorType.ODataV4Adaptor)).AutocompleteFields(af => af.Text("RegionDescription")).Width("300").ShowPopupButton(true) 

{% endhighlight %}


Run the code to get the following output.

![](Data-Binding_images\odataversion4_img1.png)

### URL Adaptor

URL Adaptor of **DataManager** can be used when you are required to use remote service to retrieve data. It interacts with server-side for all **DataManager** Queries and **CRUD** operations.

Now, in the following code example the data is retrieved from **Controller**.

{% highlight html %}

@Html.EJ().Autocomplete("selectCar").Datasource(dataSource => dataSource.URL(Url.Action("DataSource", "Autocomplete")).Adaptor(AdaptorType.UrlAdaptor)).Query("ej.Query()").AutocompleteFields(af => af.Text("text")).Width("300").FilterType(FilterOperatorType.Contains)

{% endhighlight %}


**Controller:**

{% highlight c# %}

public JsonResult DataSource()
        {

            IEnumerable Data = setListSource();
            return Json(Data, JsonRequestBehavior.AllowGet);
        }

        public static List<CarsList> setListSource()
        {
            List<CarsList> cars = new List<CarsList>();

            cars.Add(new CarsList { uniqueKey = 1, text = "Audi S6", company = "Audi" });
            cars.Add(new CarsList { uniqueKey = 2, text = "Austin-žHealey", company = "Austin" });
            cars.Add(new CarsList { uniqueKey = 3, text = "BMW š7", company = "BMW" });
            cars.Add(new CarsList { uniqueKey = 4, text = "Chevrolet Camarož", company = "Chevrolet" });
            cars.Add(new CarsList { uniqueKey = 6, text = "Ferrari š360", company = "Ferrari" });
            cars.Add(new CarsList { uniqueKey = 7, text = "Honda S2000", company = "Honda" });
            cars.Add(new CarsList { uniqueKey = 8, text = "Hyundai Santroš", company = "Hyundai" });
            cars.Add(new CarsList { uniqueKey = 9, text = "Isuzu Swift", company = "Isuzu" });
            cars.Add(new CarsList { uniqueKey = 10, text = "Jaguar XJS", company = "Jaguar" });
            cars.Add(new CarsList { uniqueKey = 11, text = "iLotus Esprit", company = "Lotus" });
            cars.Add(new CarsList { uniqueKey = 12, text = "Mercedes-Benz", company = "Mercedes" });
            cars.Add(new CarsList { uniqueKey = 13, text = "Toyota ž2000GT", company = "Toyota" });
            cars.Add(new CarsList { uniqueKey = 14, text = "Volvo P1800", company = "Volvo" });
            return cars;
        }
{% endhighlight %}


Run the code to get the following output

![](Data-Binding_images\urladaptormvc_img1.png)

### WebAPI

**WebApi** Adaptor, extended from **ODataAdaptor**, of **DataManager** is used for retrieving data from WebApi service. [ASP.NET Web API](https://msdn.microsoft.com/en-us/library/hh833994%28v=vs.108%29.aspx) is a Framework for building HTTP services. You can retrieve data from ASP.NET Web API by using [DataManager](https://help.syncfusion.com/js/datamanager/getting-started). Using WebApiAdaptor, you can bind WebApi service’s data to Autocomplete. The data from WebApi service must be returned as an object that has its value as data source and field property customerID with its value as Datasource total records count.

{% highlight html %}


   @(Html.EJ().Autocomplete("selectAuto").Datasource(dataSource => dataSource.URL(Url.Action("http://js.syncfusion.com/ejservices/Wcf/Northwind.svc/")).Adaptor(AdaptorType.WebApiAdaptor)).Query("ej.Query().from('Customers')").Width("300").AutocompleteFields(fieldSetting => fieldSetting.Text("CustomerID")))


{% endhighlight %}

Run the code to get the following output.

![](Data-Binding_images\webapi_img1.png)

