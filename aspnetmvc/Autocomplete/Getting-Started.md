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

ASP.NET MVC AutoComplete textbox widget basically renders with built-in features like keyboard navigation with animations and flexible API’s. You can easily create the AutoCompleteTextbox widget by the following steps.

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

    {% highlight c# %}

        public class ComponentsList
        {

            public int ComponentId { get; set; }
            public string ComponentName { get; set; }          
            public static List<ComponentsList> GetComponentsList()
            {
                List<ComponentsList> component = new List<ComponentsList>();
                component.Add(new ComponentsList { ComponentName = "Autocomplete" });
                component.Add(new ComponentsList { ComponentName = "Accordion" });
                component.Add(new ComponentsList { ComponentName = "BulletGraph" });
                component.Add(new ComponentsList { ComponentName = "Chart" });
                component.Add(new ComponentsList { ComponentName = "DatePicker" });
                component.Add(new ComponentsList { ComponentName = "Dialog" });
                component.Add(new ComponentsList { ComponentName = "Diagram" });
                component.Add(new ComponentsList { ComponentName = "DropDown" });
                component.Add(new ComponentsList { ComponentName = "Gauge" });
                component.Add(new ComponentsList { ComponentName = "Schedule" });
                component.Add(new ComponentsList { ComponentName = "Scrollbar" });
                component.Add(new ComponentsList { ComponentName = "Slider" });
                component.Add(new ComponentsList { ComponentName = "RangeNavigatior" });
                component.Add(new ComponentsList { ComponentName = "Rating" });
                component.Add(new ComponentsList { ComponentName = "RichTextEditor" });
                component.Add(new ComponentsList { ComponentName = "Tab" });
                component.Add(new ComponentsList { ComponentName = "TagCloud" });
                component.Add(new ComponentsList { ComponentName = "Toolbar" });
                component.Add(new ComponentsList { ComponentName = "TreeView" });               
                return component;
            }
        }

    {% endhighlight %}

In the controller page, you need to pass the model class to the corresponding view.

    {% highlight c# %}

            public ActionResult Index()
            {
            
            return View(ComponentsList.GetComponentsList()); 
                           
            }

    {% endhighlight %}

In the View page, add Autocomplete helper and map the local data list to corresponding DataSource and AutoCompleteFields. You need to refer the model class at the top of the page.

    {% highlight CSHTML %}

        @model List<MvcApplication7.Models.ComponentsList>
       
        <div>

        Select Component/s: 

        @Html.EJ().Autocomplete("ComponentList").Datasource(Model).AutocompleteFields(f=> f.Text("ComponentName").Key("ComponentId")).Width("500")

        </div>

    {% endhighlight %}

Run this code to render the AutoComplete with components list.

![](Getting-Started_images/Getting-Started_img3.png)

AutoComplete with Component list
{:.caption}

You can also set some common customization changes to the AutoComplete textbox like enabling multiple-selection, highlight search and add dropdown icon based on your requirement. 

#### Configure Visual Mode with filter option


By default, the AutoComplete is rendered with single-value selection. For multiple-value selection using the property MultiSelectMode that allows you to select multiple Data. There are two types of multiple selection one is ‘delimiter’ and another one is ‘visual mode’. In ‘Delimiter’ mode, the multiple values chosen are separated by using the delimiter character specified. In ‘visual mode’, the values chosen are displayed as box model. Here, the ‘visual mode’ is shown. You can set the FilterType option as StartsWith to sort the suggestion list based on the starting character.


    {% highlight CSHTML %}

        <div>

        Select Component/s: 

        @Html.EJ().Autocomplete("ComponentList").Datasource(Model).AutocompleteFields(f=> f.Text("ComponentName").Key("ComponentId")).Width("500").MultiSelectMode(MultiSelectModeTypes.VisualMode).FilterType(FilterOperatorType.StartsWith).Width("500")

        </div>

    {% endhighlight %}


The following screen shot displays the AutoComplete textbox with selection visual mode.

![](Getting-Started_images/Getting-Started_img4.png)

AutoComplete textbox with selection visual mode
{:.caption}

#### Configure Highlight Search and Rounded corners

When you set the HighlightSearch property to ‘true’, the characters typed in textbox gets highlighted in the suggestion list. To display textbox reforms from sharp ends to rounded ends, you can enable the ShowRoundedCorner property.

    {% highlight CSHTML %}

        <div>

        Select Component/s: 

        @Html.EJ().Autocomplete("ComponentList").Datasource(Model).AutocompleteFields(f=> f.Text("ComponentName").Key("ComponentId")).Width("500").MultiSelectMode(MultiSelectModeTypes.VisualMode).FilterType(FilterOperatorType.StartsWith).HighlightSearch(true).ShowRoundedCorner(true).Width("500")

        </div>

    {% endhighlight %}


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

         <div>

        Select Component/s: 

        @Html.EJ().Autocomplete("ComponentList").Datasource(Model).AutocompleteFields(f=> f.Text("ComponentName").Key("ComponentId")).Width("500").MultiSelectMode(MultiSelectModeTypes.VisualMode).FilterType(FilterOperatorType.StartsWith).HighlightSearch(true).ShowRoundedCorner(true).Width("500").ShowPopupButton(true)

        </div>

    {% endhighlight %}
    {% endtabs %} 

The following screen shot displays the AutoComplete textbox with dropdown icon.

![](Getting-Started_images/Getting-Started_img6.png)

AutoComplete textbox with dropdown icon
{:.caption}
