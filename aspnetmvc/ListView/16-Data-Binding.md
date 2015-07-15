---
layout: post
title: 16-Data-Binding
description: 1.6 data binding
platform: ejmvc
control: ListView
documentation: ug
---

## 1.6 Data Binding

Local Data Binding

Essential Studio WebJS ListView provides support for Data Binding. Data Binding provides a simple and consistent way for applications to present and interact with data. Elements can be bounded to data from a variety of data sources. In local databinding, the data source is written inside the program. Then it is handled by the ListView control. DataSource is used to get the data source that holds the list items.

Please refer the following code examples.





For MVC Wrapper example, you need to create model file for data-binding. Add the following model code to a CS file and save it as ListLocalData.cs.



{% highlight c# %}



   public class ListLocalData

    {

        public string text { get; set; }

    }  

    public static class ListLocalDataModal

    {

        public static List<ListLocalData> listSource = new List<ListLocalData>();      

        public static List<ListLocalData> setListSource()

        {

            listSource.Add(new ListLocalData { text = "Hot Singles"});

            listSource.Add(new ListLocalData { text = "Rising Artists"});

            listSource.Add(new ListLocalData { text = "Live Music"});

            listSource.Add(new ListLocalData { text = "Best of 2013 So Far"});

            listSource.Add(new ListLocalData { text = "100 Albums - $5 Each"});

            listSource.Add(new ListLocalData { text = "Hip-Hop and R&B Sale"});

            listSource.Add(new ListLocalData { text = "CD Deals"});

            listSource.Add(new ListLocalData { text = "Songs"});

            listSource.Add(new ListLocalData { text = "Bestselling Albums"});

            listSource.Add(new ListLocalData { text = "New Releases"});

            listSource.Add(new ListLocalData { text = "Bestselling Songs"});

            listSource.Add(new ListLocalData { text = "Rock"});

            listSource.Add(new ListLocalData { text = "Gospel" });

            listSource.Add(new ListLocalData { text = "Jazz"});

            listSource.Add(new ListLocalData { text = "Music Trade-In"});

            listSource.Add(new ListLocalData { text = "Redeem a Gift Card"});

            listSource.Add(new ListLocalData { text = "Band T-Shirts"});

            listSource.Add(new ListLocalData { text = "Mobile MVC"});

            return listSource;

        }

        public static void clearSource()

        {

            listSource.Clear();

        }       

    }





{% endhighlight %}



You have to modify the controller as the model is added to the sample. You can modify the controller as follows.



{% highlight c# %}



        public ActionResult LocalDataBinding()

        {

            ListLocalDataModal.clearSource();

            return View(ListLocalDataModal.setListSource());

        }





{% endhighlight %}



You can use the following code example to give you the exact output.



{% highlight c# %}



@model List<ListLocalData>

@{

    @Html.EJ().ListView("localListView").Width(400).DataSource(Model)

}





{% endhighlight %}



Screenshot:

{ ![](16-Data-Binding_images/16-Data-Binding_img1.png) | markdownify }
{:.image }


_Local Data Binding_

FieldSettings

The FieldSettings property is used to map the DataSource field with the list item fields. In addition to the list [item specific properties](http://help.syncfusion.com/ug/js/documents/groupedlist.htm), the following fields are available while mapping.

_FieldSettings_

<table>
<tr>
<td>
Properties</td><td>
Definition</td></tr>
<tr>
<td>
ParentPrimaryKey</td><td>
In DB, you can relate any child item to some other item. Set here is ‘PrimaryKey’ for the parent item. Here ‘ParentPrimaryKey’ defines the ‘PrimaryKey’ of some parent item to identify its parent.</td></tr>
<tr>
<td>
Attributes</td><td>
In DB, you can define your desired class name or styles for the list item through the ‘Attributes’ field.</td></tr>
</table>
Please refer the following code examples.

{% highlight html %}



@model List<FieldSettingsData>

@{

    @Html.EJ().ListView("localListView").Width(400).ShowHeader(true).HeaderTitle("Music World").DataBinding(true).DataSource(Model).FieldSettings(f =>

{

    f.Text("texts").PrimaryKey("primaryKeys").ParentPrimaryKey("parentPrimaryKeyss").ChildHeaderTitle("Title").ChildHeaderBackButtonText("BackIconText");

});

}





{% endhighlight %}



Screenshots:

{ ![](16-Data-Binding_images/16-Data-Binding_img2.png) | markdownify }
{:.image }


_Field Settings_

When you click on the parent item, it navigates to its corresponding child list item as follows.



{ ![](16-Data-Binding_images/16-Data-Binding_img3.png) | markdownify }
{:.image }


_Field Settings_

