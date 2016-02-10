---
layout: post
title: Drag and drop | ListBox | ASP.NET MVC | Syncfusion
description: drag and drop
platform: ejmvc
control: ListBox
documentation: ug
---

# Drag and drop

A list item can be moved from a widget to another ListBox widget. Also the order of list items can be changed. This can be achieved using the drag and drop support.

## Transferring a ListBox data to another ListBox

In some scenarios we might want to transfer a ListBox data to another ListBox. In the below steps we will see how to move skills from a ListBox widget to another.

Enable the drag and drop support through “AllowDrag” and “AllowDrop” properties.

In the Model page, define the Class name as SkillSet with Skill field property.

In the Controller page, to create a List of SkillSet class and add the data.

In the View page, add the ListBox helper as below.

{% tabs %}    
{% highlight c# %}

//define model class with the corresponding property

public class SkillSet
    {
        public string Skill { get; set; }
    }

//specify desired datasource data by using the model class properties

  public partial class ListBoxController : Controller
    {
        List<SkillSet> language = new List<SkillSet>();
        public ActionResult Index()
        {
            language.Add(new SkillSet { Skill = "ASP.NET" });
            language.Add(new SkillSet { Skill = "ActionScript" });
            language.Add(new SkillSet { Skill = "Basic" });
            language.Add(new SkillSet { Skill = "C++" });
            language.Add(new SkillSet { Skill = "C#" });
            language.Add(new SkillSet { Skill = "dBase" });
            language.Add(new SkillSet { Skill = "Delphi" });
            language.Add(new SkillSet { Skill = "ESPOL" });
            language.Add(new SkillSet { Skill = "F#" });
            language.Add(new SkillSet { Skill = "FoxPro" });
            language.Add(new SkillSet { Skill = "Java" });
            language.Add(new SkillSet { Skill = "J#" });
            language.Add(new SkillSet { Skill = "Lisp" });
            language.Add(new SkillSet { Skill = "Logo" });
            language.Add(new SkillSet { Skill = "PHP" });
            ViewBag.datasourcelang = language;
            return View();
        }
    }


{% endhighlight %}

{% highlight razor %}

<div class="control">
    <div> Select your skills </div>
    @{Html.EJ().ListBox("listbox1")
              .AllowDrag(true)
              .Datasource((IEnumerable<SkillSet>)ViewBag.datasourcelang)
              .ListBoxFields(df => df.Text("Skill"))
              .Render();}
</div>
<div class="control">
    <div> Selected skills </div>
    @{Html.EJ().ListBox("listbox2")
              .AllowDrop(true)
              .Render();}
</div>

<style type="text/css" class="cssStyles">
    .control {
        margin-left: 20px;
        float: left;
    }
</style>


{% endhighlight %}

{% endtabs %}



N> The Datasource is not set for the second ListBox widget. In the above example we have restricted listbox1 as draggable element and the listbox2 as droppable element. In this case we can’t drag an item from listbox2 to listbox1. If we want to achieve two way drag and drop, we need to enable both AllowDrag and AllowDrop properties in both ListBox widgets configuration.

![](Drag-and-drop_images\Drag-and-drop_img1.png)

![](Drag-and-drop_images\Drag-and-drop_img2.png)

## Dynamically set data source on drag and drop

While moving the specific item from a ListBox to another only the DOM will be updated. We need to update the data source manually. So for this, we can use “ItemDrop” event to update the Datasource of the second ListBox widget based on the dropped items.

Both the ListBox widgets are bound to a remote data source.

{% highlight razor %}

<div class="control">
    @{Html.EJ().ListBox("listbox1")
          .Datasource("http://mvc.syncfusion.com/Services/Northwnd.svc/")
          .Query("ej.Query().from('Customers')")
          .ListBoxFields(fields => fields.Text("CustomerID"))
          .AllowDrag(true).Render();}
</div>
<div class="control">
    @{Html.EJ().ListBox("listbox2")
          .Datasource("http://mvc.syncfusion.com/Services/Northwnd.svc/")
          .Query("ej.Query().from('Customers').take(10)")
          .ListBoxFields(field => field.Text("CustomerID"))
          .AllowDrop(true)
          .ClientSideEvents(eve => eve.ItemDrop("updateDataSource"))
          .Render();}
</div>

<script>
    function updateDataSource(args) {
        //update the listbox2's datasource
    }

</script>

<style type="text/css" class="cssStyles">
    .control {
        margin-left: 20px;
        float: left;
    }
</style>


{% endhighlight %}



In the “ItemDrop” event, we can implement “updateDataSource” function to update the Datasource of the second ListBox widget. The “ItemDrop” event’s argument contains the details of the dropped item.

## Reordering

Item reordering can be done within a ListBox widget by enabling both “AllowDrag” and “AllowDrop” properties.

{% highlight razor %}

@{Html.EJ().ListBox("listbox")
    .TargetID("carslist")
    .AllowDrag(true)
    .AllowDrop(true)
    .Render();}
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



{% endhighlight %}



![](Drag-and-drop_images\Drag-and-drop_img3.png)

![](Drag-and-drop_images\Drag-and-drop_img4.png)

N> The item reordering can be done dynamically without mouse interaction. For that we have provided two client side methods namely “moveUp” and “moveDown”.



