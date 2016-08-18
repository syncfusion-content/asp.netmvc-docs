---
layout: post
title: Functionalities in the DropDownList control for Syncfusion ASP.NET MVC
description: Functionalities in the DropDownList control for Syncfusion ASP.NET MVC
platform: mvc
control: DropDownList
documentation: ug
keywords: DropDownList, dropdown, Selection, Grouping, Sorting

---
# Functionalities

## Selection

By default only one item can be selected from the popup list. For multiple selection, you have to enable [checkboxes](Checkbox). The selected item consist of active class (“e-active”) to differentiate it from other items.

The following API’s, select the items in the DropDownList via text or value or indices.

<table>
    <tr>
        <th>
            Properties
            <br/>
        </th>
        <th>
            Description
            <br/>
        </th>
    </tr>
    <tr>
        <td>
            {{'[value](http://help.syncfusion.com/js/api/ejdropdownlist#members:value)'| markdownify }} 
            <br/>
        </td>
        <td>
            To select an item initially, you can pass the item’s value via value property.
            <br/>
            Multiple items can select via value property, the given values should be separated by delimiter character.
        </td>
    </tr>
    <tr>
        <td>
            {{'[text](http://help.syncfusion.com/js/api/ejdropdownlist#members:text)'| markdownify }} 
            <br/>
        </td>
        <td>
            To select an item initially, you can pass the item’s text via text property.
            <br/>
            Multiple items can select via text property, the given values should be separated by delimiter character.
        </td>
    </tr>
    <tr>
        <td>
            {{'[selectedIndex](http://help.syncfusion.com/js/api/ejdropdownlist#members:selectedindex)'| markdownify }} 
            <br/>
        </td>
        <td>
            Select a single item by passing an index value to the selectedIndex property.
            <br/>
        </td>
    </tr>
    <tr>
        <td>
             {{'[selectedIndices](http://help.syncfusion.com/js/api/ejdropdownlist#members:selectedindices)'| markdownify }}
            <br/>
        </td>
        <td>
            Select more than one items by passing index values to the selectedIndices property when multi selection enabled. 
            <br/>
        </td>
    </tr>
</table>

N> Index starts from 0 here.
N> To use “selectedIndices” property, you should enable wither ShowCheckbox or MultiSelectMode property.

The following methods, select the items in the DropDownList.

<table>
    <tr>
        <th>
            Methods
            <br/>
        </th>
        <th>
            Description
            <br/>
        </th>
    </tr>
    <tr>
        <td>
            {{'[selectItemByIndices](http://help.syncfusion.com/js/api/ejdropdownlist#methods:selectitembyindices)'| markdownify }}
            <br/>
        </td>
        <td>
            This method is used to select the list of items in the DropDownList through the Index of the items.
        </td>
    </tr>
    <tr>
        <td>
            {{'[selectItemByText](http://help.syncfusion.com/js/api/ejdropdownlist#methods:selectItemByText)'| markdownify }}
            <br/>
        </td>
        <td>
            This method is used to select an item in the DropDownList by using the given text value.
        </td>
    </tr>
    <tr>
        <td>
            {{'[selectItemByValue](http://help.syncfusion.com/js/api/ejdropdownlist#methods:selectitembyvalue)'| markdownify }}
            <br/>
        </td>
        <td>
            This method is used to select an item in the DropDownList by using the given value.
            <br/>
        </td>
    </tr>
</table>

The following methods, used to retrieve the items from the DropDownList.

<table>
    <tr>
        <th>
            Methods
            <br/>
        </th>
        <th>
            Description
            <br/>
        </th>
    </tr>
    <tr>
        <td>
            {{'[getListData](http://help.syncfusion.com/js/api/ejdropdownlist#methods:getlistdata)'| markdownify }}
            <br/>
        </td>
        <td>
            This method is used to retrieve the items that are bound with the DropDownList.
        </td>
    </tr>
    <tr>
        <td>
            {{'[getSelectedItem](http://help.syncfusion.com/js/api/ejdropdownlist#methods:getselecteditem)'| markdownify }}
            <br/>
        </td>
        <td>
            This method is used to get the selected items in the DropDownList.
        </td>
    </tr>
    <tr>
        <td>
            {{'[getSelectedValue](http://help.syncfusion.com/js/api/ejdropdownlist#methods:getSelectedValue)'| markdownify }}
            <br/>
        </td>
        <td>
            This method is used to retrieve the items value that are selected in the DropDownList.
            <br/>
        </td>
    </tr>
</table>

I> When multiSelectMode is enabled in a DropDownList and selected items having same text but its value is different means, the items can be selected. Please refer the online link

### Using value or text

To select an item initially you can pass the item’s value via Value property or SelectItemByValue API. To achieve this DropDownList control must be initiated with the associate value. 

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).Value("item3")
		
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropdownData = new List<Data>();
            DropdownData.Add(new Data { Value = "item1", Text = "ListItem 1" });
            DropdownData.Add(new Data { Value = "item2", Text = "ListItem 2" });
            DropdownData.Add(new Data { Value = "item3", Text = "ListItem 3" });
            DropdownData.Add(new Data { Value = "item4", Text = "ListItem 4" });
            DropdownData.Add(new Data { Value = "item5", Text = "ListItem 5" });
            ViewData["DropDownSource"] = DropdownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

![](Functionalities_images/Functionalities_img1.jpeg)

N> To retrieve the selected item’s value in controller page, you can use DropDownList control name in the controller post action.

{% tabs %}
	
    {% highlight html %}
        
        @model MVCApplication.Controllers.HomeController
        
        @using (Html.BeginForm("DropdownlistFeatures", "Dropdownlist", FormMethod.Post, null))
        {
            @Html.EJ().DropDownList("DropDownList1").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).Height("50px").Width("500px").PopupHeight("200px").PopupWidth("300px")
            
            <input type="submit" value="Get Value" />
            
        }
        

	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropdownData = new List<Data>();
            DropdownData.Add(new Data { Value = "item1", Text = "ListItem 1" });
            DropdownData.Add(new Data { Value = "item2", Text = "ListItem 2" });
            DropdownData.Add(new Data { Value = "item3", Text = "ListItem 3" });
            DropdownData.Add(new Data { Value = "item4", Text = "ListItem 4" });
            DropdownData.Add(new Data { Value = "item5", Text = "ListItem 5" });
            ViewData["DropDownSource"] = DropdownData;
            return View();
        }
        [HttpPost]
        public ActionResult DropdownlistFeatures(string DropDownList1)
        {
            //DropDownList1 is ID of DropDownList used in this example. You can get the selected items value in controller using the ID
            string DropDownValue = DropDownList1;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}

{% endtabs %}


### Using indices

You can select a single or more than one item by passing index values to the properties SelectedIndex or SelectedIndices respectively. Index starts from 0 here.

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).SelectedIndex(1)
		
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropdownData = new List<Data>();
            DropdownData.Add(new Data { Value = "item1", Text = "ListItem 1" });
            DropdownData.Add(new Data { Value = "item2", Text = "ListItem 2" });
            DropdownData.Add(new Data { Value = "item3", Text = "ListItem 3" });
            DropdownData.Add(new Data { Value = "item4", Text = "ListItem 4" });
            DropdownData.Add(new Data { Value = "item5", Text = "ListItem 5" });
            ViewData["DropDownSource"] = DropdownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

![](Functionalities_images/Functionalities_img2.jpeg)

I> To use "SelectedIndices" property, you should enable either ShowCheckbox or MultiSelectMode property First.

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).ShowCheckbox(true).SelectedIndices(new List<int> { 1,2 })
		
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropdownData = new List<Data>();
            DropdownData.Add(new Data { Value = "item1", Text = "ListItem 1" });
            DropdownData.Add(new Data { Value = "item2", Text = "ListItem 2" });
            DropdownData.Add(new Data { Value = "item3", Text = "ListItem 3" });
            DropdownData.Add(new Data { Value = "item4", Text = "ListItem 4" });
            DropdownData.Add(new Data { Value = "item5", Text = "ListItem 5" });
            ViewData["DropDownSource"] = DropdownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

### Unselect items

Similarly, you can unselect a single or multiple items by using [unselectItemByValue](http://help.syncfusion.com/js/api/ejdropdownlist#methods:unselectitembyvalue) or [unselectItemByIndices](http://help.syncfusion.com/js/api/ejdropdownlist#methods:unselectitembyindices) or [unselectItemByText](http://help.syncfusion.com/js/api/ejdropdownlist#methods:unselectitembytext) methods. This will remove the selection state of the corresponding data item from the popup list and textbox. 

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).ShowCheckbox(true).SelectedIndices(new List<int> { 1, 2, 3 })
		
        <input type="button" value="Unselect" onclick="unselect()" />
        
	{% endhighlight %}
    
    {% highlight js %}

        var obj;

        $(function() {       
            obj = $('#dropdown1').data("ejDropDownList");
            console.log("Selected Item's Text - " + obj.option("text"));
            console.log("selected Item's Value - " + obj.option("value"));
        });

        function unselect() {
            obj.unselectItemByValue("item2");
            obj.unselectItemByIndices(2);
            obj.unselectItemByText("ListItem 4");
        }			

    {% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropdownData = new List<Data>();
            DropdownData.Add(new Data { Value = "item1", Text = "ListItem 1" });
            DropdownData.Add(new Data { Value = "item2", Text = "ListItem 2" });
            DropdownData.Add(new Data { Value = "item3", Text = "ListItem 3" });
            DropdownData.Add(new Data { Value = "item4", Text = "ListItem 4" });
            DropdownData.Add(new Data { Value = "item5", Text = "ListItem 5" });
            ViewData["DropDownSource"] = DropdownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

## Grouping

The DropDownList items can be categorized by using a specific field in the popup list. This is enabled by using Category field on data source binding. By default grouping is disabled in DropDownList.
The below given example explains the behavior of grouping with List data binding.

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList").Datasource((IEnumerable<VegetableList>)ViewData["VegData"]).DropDownListFields(Df => Df.Text("Name").Category("Category")).Width("150px").PopupHeight("300px").WatermarkText("Select a vegetable")
        
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<VegetableList> VegeList = new List<VegetableList>();
            VegeList.Add(new VegetableList { Name = "Cabbage", Category = "Leafy and Salad" }); 
            VegeList.Add(new VegetableList { Name = "Pea", Category = "Leafy and Salad" }); 
            VegeList.Add(new VegetableList { Name = "Spinach", Category = "Leafy and Salad" }); 
            VegeList.Add(new VegetableList { Name = "Wheatgrass", Category = "Leafy and Salad" }); 
            VegeList.Add(new VegetableList { Name = "Yarrow", Category = "Leafy and Salad" }); 
            VegeList.Add(new VegetableList { Name = "Chickpea", Category = "Beans" }); 
            VegeList.Add(new VegetableList { Name = "Green bean", Category = "Beans" }); 
            VegeList.Add(new VegetableList { Name = "Horse gram", Category = "Beans" }); 
            VegeList.Add(new VegetableList { Name = "Peanut", Category = "Beans" });
            VegeList.Add(new VegetableList { Name = "Pigeon pea", Category = "Beans" }); 
            VegeList.Add(new VegetableList { Name = "Garlic", Category = "Bulb and Stem" }); 
            VegeList.Add(new VegetableList { Name = "Garlic Chives", Category = "Bulb and Stem" }); 
            VegeList.Add(new VegetableList { Name = "Lotus root", Category = "Bulb and Stem" }); 
            VegeList.Add(new VegetableList { Name = "Nopal", Category = "Bulb and Stem" });
            VegeList.Add(new VegetableList { Name = "Onion", Category = "Bulb and Stem" }); 
            VegeList.Add(new VegetableList { Name = "Shallot", Category = "Bulb and Stem" }); 
            VegeList.Add(new VegetableList { Name = "Beetroot", Category = "Root and Tuberous" }); 
            VegeList.Add(new VegetableList { Name = "Carrot", Category = "Root and Tuberous" }); 
            VegeList.Add(new VegetableList { Name = "Ginger", Category = "Root and Tuberous" }); 
            VegeList.Add(new VegetableList { Name = "Potato", Category = "Root and Tuberous" }); 
            VegeList.Add(new VegetableList { Name = "Radish", Category = "Root and Tuberous"}); 
            VegeList.Add(new VegetableList { Name = "Turmeric", Category = "Root and Tuberous" });
            ViewData["VegData"] = VegeList;
            return View();
        }
        public class VegetableList
        {
            public string Name { get; set; }
            public string Category { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

![](Functionalities_images/Functionalities_img3.jpeg)

N> Grouping has restrictions in the following scenarios, <BR>

1.  It is not supported on using HTML "select" element with predefined set of options<BR>
2.  When using UL-LI elements you need to use “e-category” class in LI element to specify it as the grouping header. The following code will explain this behavior,<BR>
3.  The sorting behavior varies when grouping is enabled in the DropDownList, based on browser as we have used browser based stable sorting method when there is multiple level of sorting. <BR>
4.  To overcome this behavior on sorting order with browser, we suggest you to set ej.support.stableSort as false from the script when the page is loaded or in document ready function.<BR>
   
   {% highlight javascript %}
    <script type="text/javascript">
            $(document).ready(function () {
                ej.support.stableSort = false;            
            });
    </script>
   {% endhighlight %}

{% highlight html %}

     @Html.EJ().DropDownList("DropDownList").TargetID("groupinglist").Width("150px").PopupHeight("300px").WatermarkText("Select a vegetable")

        <div id="groupinglist">
            <ul>
                <span class="e-category">Header 1</span>
                <li>Item 1</li>
                <li>Item 2</li>
                <span class="e-category">Header 2</span>
                <li>Item 3</li>
                <li>Item 4</li>
                <li>Item 5</li>
            </ul>
        </div>
    
{% endhighlight %}

![](Functionalities_images/Functionalities_img4.jpeg)

I> Virtual scrolling is not supported with Grouping.

## Sorting

Sorting is enabled in order to display the items alphabetically in either ascending or descending order. By default the items is displayed in the initialized order, use EnableSorting property to automatically sort strings based on text field value. You can assign either SortOrder.Ascending or SortOrder.Descending enum values to the SortOrder property to sort out the list items. By default ascending order is followed when SortOrder property is not specified. 

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).EnableSorting(true).SortOrder(SortOrder.Descending)
		
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropDownData = new List<Data>();
            DropDownData.Add(new Data { Value = "item1", Text = "List Item 1" });
            DropDownData.Add(new Data { Value = "item5", Text = "List Item 5" });
            DropDownData.Add(new Data { Value = "item4", Text = "List Item 4" });
            DropDownData.Add(new Data { Value = "item2", Text = "List Item 2" });
            DropDownData.Add(new Data { Value = "item3", Text = "List Item 3" });
            ViewData["DropDownSource"] = DropDownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

I> Virtual scrolling is not supported with Sorting.

## Cascading

This works for series of DropDownList in which items are filtered based on the previous DropDownList‘s selection. Cascading is performed based on the value field and this field should be bounded with a foreign key. To perform cascading, specify the child DropDownList’s id in CascadeTo property and use delimiter (“,”) to specify more than one child DropDownList.

Configuring the data items for cascading to the series of DropDownList is demonstrated below

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        <div style="width: 400px;">
           <div style="float: left;">
               <span>Select Group</span>
               @Html.EJ().DropDownList("GroupDropDown").Datasource((IEnumerable<Groups>)ViewData["Groups"]).DropDownListFields(Df => Df.Text("Text").ID("ParentId").Value("ParentId")).CascadeTo("CountryDropDown")
           </div>

           <div style="float: right;">
               <span>Select Country</span>
               @Html.EJ().DropDownList("CountryDropDown").Datasource((IEnumerable<Country>)ViewData["CountriesData"]).Enabled(false).DropDownListFields(df=>df.Text("Text"))
           </div>
       </div>
       
	{% endhighlight %}

    {% highlight c# %}
        public ActionResult Index()
        {
            List<Groups> GroupList = new List<Groups>();
            GroupList.Add(new Groups{ ParentId = "a", Text = "Group A" }); 
            GroupList.Add(new Groups{ ParentId = "b", Text = "Group B" }); 
            GroupList.Add(new Groups{ ParentId = "c", Text = "Group C" }); 
            GroupList.Add(new Groups{ ParentId = "d", Text = "Group D" }); 
            GroupList.Add(new Groups { ParentId = "e", Text = "Group E" });
            List<Country> CountryList = new List<Country>();
            CountryList.Add(new Country{ ParentId = "a", Text = "Algeria" }); 
            CountryList.Add(new Country{ ParentId = "a", Text = "Armenia" }); 
            CountryList.Add(new Country{ ParentId = "a", Text = "Bangladesh" }); 
            CountryList.Add(new Country{ ParentId = "a", Text = "Cuba" }); 
            CountryList.Add(new Country{ ParentId = "b", Text = "Denmark" }); 
            CountryList.Add(new Country{ ParentId = "b", Text = "Egypt" }); 
            CountryList.Add(new Country{ ParentId = "c", Text = "Finland" }); 
            CountryList.Add(new Country{ ParentId = "c", Text = "India" }); 
            CountryList.Add(new Country{ ParentId = "c", Text = "Malaysia" }); 
            CountryList.Add(new Country{ ParentId = "d", Text = "New Zealand" }); 
            CountryList.Add(new Country{ ParentId = "d", Text = "Norway" }); 
            CountryList.Add(new Country{ ParentId = "d", Text = "Poland" }); 
            CountryList.Add(new Country{ ParentId = "e", Text = "Romania" }); 
            CountryList.Add(new Country{ ParentId = "e", Text = "Singapore" }); 
            CountryList.Add(new Country{ ParentId = "e", Text = "Thailand" }); 
            CountryList.Add(new Country{ ParentId = "e", Text = "Ukraine" });
            ViewData["Groups"] = GroupList;
            ViewData["CountriesData"] = CountryList;
            return View();
        }
        public class Groups
        {
            public string ParentId { get; set; }
            public string Text { get; set; }
        }
        public class Country
        {
            public string ParentId { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

![](Functionalities_images/Functionalities_img5.jpeg)

![](Functionalities_images/Functionalities_img6.jpeg)

### Binding the data source to the cascading DropDownList using cascade event

Bind the data source to the cascading DropDownList dynamically using ClientSideEvent Cascade as demonstrated below,

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        <div style="width: 530px;">
           <div style="float: left;">
               <span>Select Group</span>
               @Html.EJ().DropDownList("GroupDropDown").Datasource((IEnumerable<Groups>)ViewData["Groups"]).DropDownListFields(Df => Df.Text("Text").ID("ParentId").Value("ParentId")).CascadeTo("CountryDropDown, PlayersDropDown")
           </div>

           <div style="float: left; padding-left: 50px;">
               <span>Select Country</span>
               @Html.EJ().DropDownList("CountryDropDown").Datasource((IEnumerable<Country>)ViewData["CountriesData"]).Enabled(false).DropDownListFields(df => df.Text("Text"))
           </div>

           <div style="float: right;">
               <span>Select Players</span>
               @Html.EJ().DropDownList("PlayersDropDown").Datasource((IEnumerable<Players>)ViewData["PlayersData"]).Enabled(false).DropDownListFields(df => df.Text("Text"))
           </div>
       </div>
       
	{% endhighlight %}

    {% highlight c# %}
        public ActionResult Index()
        {
            List<Groups> GroupList = new List<Groups>();
            GroupList.Add(new Groups{ ParentId = "a", Text = "Group A" }); 
            GroupList.Add(new Groups{ ParentId = "b", Text = "Group B" });
            List<Country> CountryList = new List<Country>();
            CountryList.Add(new Country{ ParentId = "a", Text = "Algeria" }); 
            CountryList.Add(new Country{ ParentId = "a", Text = "Armenia" }); 
            CountryList.Add(new Country{ ParentId = "b", Text = "Denmark" }); 
            CountryList.Add(new Country{ ParentId = "b", Text = "Egypt" }); 
            List<Players> PlayerList = new List<Players>();
            PlayerList.Add(new Players { ParentId = "a", Text = "Adams" });
            PlayerList.Add(new Players { ParentId = "a", Text = "Clarke" });
            PlayerList.Add(new Players { ParentId = "b", Text = "Brett" });
            PlayerList.Add(new Players { ParentId = "b", Text = "James" });
            ViewData["Groups"] = GroupList;
            ViewData["CountriesData"] = CountryList;
            ViewData["PlayersData"] = PlayerList;
            return View();
        }
        public class Groups
        {
            public string ParentId { get; set; }
            public string Text { get; set; }
        }
        public class Country
        {
            public string ParentId { get; set; }
            public string Text { get; set; }
        }
        public class Players
        {
            public string ParentId { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

![](Functionalities_images/Functionalities_img7.jpeg)

### Multi-Level Cascading

The below scenario can be explained with three DropDownList for the multi-level cascading.

{% tabs %}

	{% highlight C# %}
    
    public partial class DropdownlistController: Controller
    {
        List<groups> group = new List<groups>();
        List<Countries> country = new List<Countries>();
        List<Capital> capital = new List<Capital>();
        public ActionResult DropdownlistFeatures()
        {
            group.Add(new groups { parentId = "a", text = "Group A" });
            group.Add(new groups { parentId = "b", text = "Group B" });
            group.Add(new groups { parentId = "c", text = "Group C" });
            group.Add(new groups { parentId = "d", text = "Group D" });
            group.Add(new groups { parentId = "e", text = "Group E" });
            ViewBag.datasource = group;
            country.Add(new Countries { value = 11, parentId = "a", text = "Algeria" });
            country.Add(new Countries { value = 12, parentId = "a", text = "Armenia" });
            country.Add(new Countries { value = 13, parentId = "a", text = "Bangladesh" });
            country.Add(new Countries { value = 14, parentId = "a", text = "Cuba" });
            country.Add(new Countries { value = 15, parentId = "b", text = "Denmark" });
            country.Add(new Countries { value = 16, parentId = "b", text = "Egypt"});
            country.Add(new Countries { value = 17, parentId = "c", text = "Finland"});
            country.Add(new Countries { value = 18, parentId = "c", text = "India" });
            country.Add(new Countries { value = 19, parentId = "c", text = "Malaysia"});
            country.Add(new Countries { value = 20, parentId = "d", text = "New Zealand"});
            country.Add(new Countries { value = 21, parentId = "d", text = "Norway" });
            country.Add(new Countries { value = 22, parentId = "d", text = "Romania" });
            country.Add(new Countries { value = 23, parentId = "e", text = "Singapore"});
            country.Add(new Countries { value = 24, parentId = "e", text = "Thailand" });
            country.Add(new Countries { value = 25, parentId = "e", text = "Ukraine"});
            ViewBag.datasource1 = country;
            capital.Add(new Capital { value = 11, text = "Algiers" });
            capital.Add(new Capital { value = 12, text = "Cairo" });
            capital.Add(new Capital { value = 13, text = "Copenhagen" });
            capital.Add(new Capital { value = 14, text = "Washington" });
            capital.Add(new Capital { value = 15, text = "Denmark" });
            capital.Add(new Capital { value = 16, text = "Yerevan" });
            capital.Add(new Capital { value = 17, text = "Copenhagen" });
            capital.Add(new Capital { value = 18, text = "New Delhi" });
            capital.Add(new Capital { value = 19, text = "Havana" });
            capital.Add(new Capital { value = 20, text = "Brasília" });
            capital.Add(new Capital { value = 21, text = "Lima" });
            capital.Add(new Capital { value = 22, text = "Canberra" });
            capital.Add(new Capital { value = 23, text = "Wellington" });
            capital.Add(new Capital { value = 24, text = "Alfred Faure" });
            capital.Add(new Capital { value = 25, text = "King Edward Point" });
            ViewBag.capital = capital;
              return View();
         } 
    }
    public class groups
    {
        public string text { get; set; }
        public string parentId { get; set; }
      
    }
    public class Countries
    {
        public string text { get; set; }
       
        public int value { get; set; }
        public string parentId { get; set; }
        
    }
    public class Capital
    {
        public string text { get; set; }
        public int value { get; set; }
    }
    {% endhighlight %}
    
    {% highlight html %}
    
    <div class="control" style="float: left;">
        <span class="txt">Select Group</span>
        @Html.EJ().DropDownList("groupsList").Datasource((IEnumerable<groups>)ViewBag.datasource).DropDownListFields(f => f.Value("parentId").Text("text")).CascadeTo("countryList")
    </div>
    <div class="control" style="float: left;">
        <span class="txt">Select Country</span>
        @Html.EJ().DropDownList("countryList").Datasource((IEnumerable<Countries>)ViewBag.datasource1).DropDownListFields(f => f.Value("value").Text("text")).CascadeTo("capitalList").Enabled(false)
    </div>
    <div class="control" style="float: left;">
        <span class="txt">Select Country</span>
        @Html.EJ().DropDownList("capitalList").Datasource((IEnumerable<Capital>)ViewBag.capital).Enabled(false)
    </div>

     {% endhighlight %}
    
{% endtabs %}

First two DropDownList cascaded based on the parentId, and then from second to third, cascading performed based on the value field.

## Search

Items are searched based on the keyed in values to the textbox. There are two types of searches,

* Incremental Search
* Filter Search

### Incremental Search

Selects the item in the popup list based on the keyed in value. If the time taken to type exceeds 1000 milliseconds then filtered items will be reset based on the current input value. By default this mode of search is enabled. Incremental search can be case sensitive or case insensitive. To make case sensitive, you can use CaseSensitiveSearch property.

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).EnableIncrementalSearch(true).CaseSensitiveSearch(true)
		
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropDownData = new List<Data>();
            DropDownData.Add(new Data { Value = "emp1", Text = "Adams", Selected = true });
            DropDownData.Add(new Data { Value = "emp2", Text = "James", Selected = false });
            DropDownData.Add(new Data { Value = "emp3", Text = "Maria", Selected = true });
            DropDownData.Add(new Data { Value = "emp4", Text = "Jessica", Selected = false });
            DropDownData.Add(new Data { Value = "emp5", Text = "Jenneth", Selected = false });
            ViewData["DropDownSource"] = DropDownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

![](Functionalities_images/Functionalities_img8.jpeg)

### Filter search

You can quickly locate specific item within a large data source by filtering matches with a search box. A text box appears in the popup list for searching when EnableFilterSearch property is enabled. By default, filtering returns the matched items list based on text in search textbox. 
You can configure the search filter by using FilterType property that takes SearchFilterType enum values. There is two types of filter options,

* Starts With 
* Contains

N> Items are filtered based on “SearchFilterType.Contains” filter type by default.

{% tabs %}

	{% highlight html %}
        @model MVCApplication.Controllers.HomeController
        
        @Html.EJ().DropDownList("DropDownList").Datasource((IEnumerable<Data>)ViewData["DropDownSource"]).DropDownListFields(Df => Df.Text("Text").Value("Value")).EnableFilterSearch(true).FilterType(SearchFilterType.StartsWith)
		
	{% endhighlight %}
    
    {% highlight c# %}
        public ActionResult Index()
        {
            List<Data> DropDownData = new List<Data>();
            DropDownData.Add(new Data { Value = "emp1", Text = "Adams", Selected = true });
            DropDownData.Add(new Data { Value = "emp2", Text = "James", Selected = false });
            DropDownData.Add(new Data { Value = "emp3", Text = "Maria", Selected = true });
            DropDownData.Add(new Data { Value = "emp4", Text = "Jessica", Selected = false });
            DropDownData.Add(new Data { Value = "emp5", Text = "Jenneth", Selected = false });
            ViewData["DropDownSource"] = DropDownData;
            return View();
        }
        public class Data
        {
            public string Value { get; set; }
            public string Text { get; set; }
        }
    {% endhighlight %}
    
{% endtabs %}

![](Functionalities_images/Functionalities_img9.jpeg)

I> When VirtualScrolling enabled with searching, then filter will be applied only on the DropDownList items available at the moment.


