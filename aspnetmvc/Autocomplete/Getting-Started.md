---
layout: post
title: Getting Started | AutoComplete  | ASP.NET MVC | Syncfusion
description: getting started
platform: ejmvc
control: AutoComplete
documentation: ug
---

# Getting Started

This section explains briefly about how to create an AutoComplete in your ASP.NET MVC application.

## Create your first AutoComplete in MVC

This section helps you to configure the AutoComplete control in your application and also helps you to learn how to pass the required data to it and to customize its various options according to your requirements. 

In this section,  the flat-saffron theme (default) for the Autocomplete is explained.

The following screen shot illustrates the AutoComplete control that searches the list of components available in the database. 

![](Getting-Started_images/Getting-Started_img1.png)

AutoComplete control with search
{:.caption}

### Create an AutoComplete

ASP.NET MVC AutoComplete Textbox widget basically renders with built-in features like keyboard navigation with animations and flexible API’s. You can easily create the AutoCompleteTextbox widget by the following steps.

1. You can create a MVC Project and add necessary Dll’s and Scripts with the help of the given [MVC-Getting Started](/extension/aspnet-mvc-extension/overview) Documentation.
2. Initialize the corresponding AutoComplete widget in the view page.


   ~~~ cshtml

	<div>

		Select Component/s: 

	@Html.EJ().Autocomplete("ComponentList")

	</div>

   ~~~
   


3.  Execute the code to render a AutoComplete widget as follows



![](Getting-Started_images/Getting-Started_img2.png)

Output
{:.caption}

### Populate Data to AutoComplete

You can provide either local data or remote data to the Autocomplete.

#### Local Data Binding

AutoComplete provides extensive data binding support to populate AutoComplete items, so that the values are mapped to the AutoComplete fields, namely Key and Text. DataBinding helps you bind a key value pair to AutoComplete textbox. Key field takes the unique id of the dataSource elements. Text field gets the value to be displayed in the AutoComplete textbox.

##### Defining the Local data for AutoComplete

The following steps explain local data binding to an AutoComplete textbox.

You need to add the class in the Models. Define the Class with key and text field. Then create a List of that class and add the data.

    {% highlight CSHTML %}

        public class CarsList
        {

            public int uniqueKey { get; set; }
            public string text { get; set; }
            public string company { get; set; }
            public static List<CarsList> GetCarList()
            {
                List<CarsList> car = new List<CarsList>();
                car.Add(new CarsList { text = "Audi S6" });
                car.Add(new CarsList { text = "Austin-Healey" });
                car.Add(new CarsList { text = "Alfa Romeo" });
                car.Add(new CarsList { text = "Aston Martin" });
                car.Add(new CarsList { text = "BMW 7" });
                car.Add(new CarsList { text = "Bentley Mulsanne" });
                car.Add(new CarsList { text = "Bugatti Veyron" });
                car.Add(new CarsList { text = "Chevrolet Camaro" });
                car.Add(new CarsList { text = "Cadillac" });
                car.Add(new CarsList { text = "Duesenberg J" });
                car.Add(new CarsList { text = "Dodge Sprinter" });
                car.Add(new CarsList { text = "Elantra" });
                car.Add(new CarsList { text = "Excavator" });
                car.Add(new CarsList { text = "Ford Boss 302" });
                car.Add(new CarsList { text = "Ferrari 360" });
                car.Add(new CarsList { text = "Ford Thunderbird" });
                car.Add(new CarsList { text = "GAZ Siber" });
                car.Add(new CarsList { text = "Honda S2000" });
                car.Add(new CarsList { text = "Hyundai Santro" });
                car.Add(new CarsList { text = "Isuzu Swift" });
                car.Add(new CarsList { text = "Infiniti Skyline" });
                car.Add(new CarsList { text = "Jaguar XJS" });
                car.Add(new CarsList { text = "Kia Sedona EX" });
                car.Add(new CarsList { text = "Koenigsegg Agera" });
                car.Add(new CarsList { text = "Lotus Esprit" });
                car.Add(new CarsList { text = "Lamborghini Diablo" });
                car.Add(new CarsList { text = "Mercedes-Benz" });
                car.Add(new CarsList { text = "Mercury Coupe" });
                car.Add(new CarsList { text = "Maruti Alto 800" });
                car.Add(new CarsList { text = "Nissan Qashqai" });
                car.Add(new CarsList { text = "Oldsmobile S98" });
                car.Add(new CarsList { text = "Opel Superboss" });
                car.Add(new CarsList { text = "Porsche 356" });
                car.Add(new CarsList { text = "Pontiac Sunbird" });
                car.Add(new CarsList { text = "Scion SRS/SC/SD" });
                car.Add(new CarsList { text = "Saab Sportcombi" });
                car.Add(new CarsList { text = "Subaru Sambar" });
                car.Add(new CarsList { text = "Suzuki Swift" });
                car.Add(new CarsList { text = "Triumph Spitfire" });
                car.Add(new CarsList { text = "Toyota 2000GT" });
                car.Add(new CarsList { text = "Volvo P1800" });
                car.Add(new CarsList { text = "Volkswagen Shirako" });
                return car;
            }
        }

    {% endhighlight %}

In the controller page, you need to pass the model class to the corresponding view.

    {% highlight CSHTML %}

            public ActionResult Index()
            {
            
            return View(CarsList.GetCarList());                
            }

    {% endhighlight %}

In the View page, add Autocomplete helper and map the Local data list to corresponding DataSource and AutoCompleteFields. You need to refer the model class at the top of the page.

    {% highlight CSHTML %}

        @model List<MvcApplication7.Models.CarsList>
        @{
            Html.EJ()
                .Autocomplete("ComponentList")
                .Width("500")
                .Datasource(Model)
                .Render();
        }

    {% endhighlight %}

Run this code to render the AutoComplete with components list.

![](Getting-Started_images/Getting-Started_img3.png)

AutoComplete with Component list
{:.caption}

You can also set some common customization changes to the AutoComplete textbox like enabling multiple-selection, highlight search and add dropdown icon based on your requirement. 

#### Configure Visual Mode with filter option


By default, the AutoComplete is rendered with single-value selection. For multiple-value selection using the property MultiSelectMode that allows you to select multiple Data. There are two types of multiple selection one is ‘delimiter’ and another one is ‘visual mode’. In ‘Delimiter’ mode, the multiple values chosen are separated by using the delimiter character specified. In ‘visual mode’, the values chosen are displayed as box model. Here, the ‘visual mode’ is shown. You can set the FilterType option as StartsWith to sort the suggestion list based on the starting character.


    {% highlight CSHTML %}

        @Html.EJ().Autocomplete("ComponentList").Datasource(Model).AutocompleteFields(field => field.Key("UniqueKey").Text("Text")).Width("500").MultiSelectMode(MultiSelectModeTypes.VisualMode).FilterType(FilterOperatorType.StartsWith).Width("500")

    {% endhighlight %}


The following screen shot displays the AutoComplete textbox with selection visual mode.

![](Getting-Started_images/Getting-Started_img4.png)

AutoComplete textbox with selection visual mode
{:.caption}

#### Configure Highlight Search and Rounded corners

    {% highlight CSHTML %}

        @Html.EJ().Autocomplete("ComponentList").Datasource(Model).AutocompleteFields(field => field.Key("UniqueKey").Text("Text")).Width("500").MultiSelectMode(MultiSelectModeTypes.VisualMode).FilterType(FilterOperatorType.StartsWith).HighlightSearch(true).ShowRoundedCorner(true).Width("500")

    {% endhighlight %}

When you set the HighlightSearch property to ‘true’, the characters typed in textbox gets highlighted in the suggestion list. To display textbox reforms from sharp ends to rounded ends, you can enable the ShowRoundedCorner property.


The following screen shot displays the AutoComplete textbox with highlight search enabled.

![](Getting-Started_images/Getting-Started_img5.png)

AutoComplete text box with highlight search enabled
{:.caption}

#### Configure Popup button

To enable the DropDown button, you can set ShowPopupButton property to ‘true’ that displays the DropDown icon at the end of textbox. By default, search icon replaces other icons and so you need to override the CSS classes and replace the content to DropDown arrow icon available in core CSS file as follows.

    {% tabs %}
    
    {% highlight CSS %}

    <style>.e-icon.e-search:before 
    {                
        content:"\e63b";  
    }
    </style>
    {% endhighlight %}

    {% highlight CSHTML %}

        @Html.EJ().Autocomplete("ComponentList").Datasource(Model).AutocompleteFields(field => field.Key("UniqueKey").Text("Text")).Width("500").MultiSelectMode(MultiSelectModeTypes.VisualMode).FilterType(FilterOperatorType.StartsWith).HighlightSearch(true).ShowRoundedCorner(true).Width("500").ShowPopupButton(true)

    {% endhighlight %}
    {% endtabs %} 

The following screen shot displays the AutoComplete textbox with dropdown icon.

![](Getting-Started_images/Getting-Started_img6.png)

AutoComplete textbox with dropdown icon
{:.caption}
