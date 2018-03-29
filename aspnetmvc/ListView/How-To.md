---
title: How To | ListView | ASP.NET MVC | Syncfusion
description: “How to do” section for ListView
platform: ejmvc
control: ListView
documentation: UG
keywords: ListView,  Syncfusion, EJ MVC ListView, UG document, How To
---
# How To

## Get the selected values on post back.  

**Single selection**

Enable the property [PersistSelection](https://help.syncfusion.com/api/js/ejlistview#members:persistselection) in order to use selection in ListView. Then use the [getActiveItemText](https://help.syncfusion.com/api/js/ejlistview#methods:getactiveitemtext) method take the selected active text through javascript and then pass it to the controller via AJAX. 

 
{% highlight html %}

@Html.EJ().ListView("localListView").Width(400).DataSource((IEnumerable<CarsList>)ViewBag.datasource).FieldSettings(sf => sf.Text("text")).PersistSelection(true)

  @Html.EJ().Button("button").ShowRoundedCorner(true).Text("Submit").ClientSideEvents(e => e.Click("click"))
 
 
<script> 
function click(args) { 
  var text = $("#localListView").ejListView("getActiveItemText");      
      $.ajax({ 
                type: "POST", 
                data: { value: text },
                url: "/ListView/Features", 
                success: function (result) {  
                    alert(result); 
                } 
            }); 
 
        }    
    
          
       </script> 


    
{% endhighlight %}

    
    {% highlight c# %}
    
     [HttpPost] 
        public ActionResult Features(string value)
        { 
            string val = value; 
            return Json(val, JsonRequestBehavior.AllowGet); 
        } 

    
    {% endhighlight %}



**Multiple selection**

Multiple items can be selected by using [EnableCheckMark](https://help.syncfusion.com/api/js/ejlistview#members:enablecheckmark) property. Hence we need to use the [getCheckedItemsText](https://help.syncfusion.com/api/js/ejlistview#methods:getcheckeditemstext) method to take all the checked items and then pass it to the controller using javascript AJAX. 


{% highlight html %}

@Html.EJ().ListView("localListView").Width(400).DataSource((IEnumerable<CarsList>)ViewBag.datasource).EnableCheckMark(true).FieldSettings(sf => sf.Text("text"))

@Html.EJ().Button("button").ShowRoundedCorner(true).Text("Submit").ClientSideEvents(e => e.Click("click"))
 
<script> 
 
        function click1(args) { 
              var text = $("#localListView").ejListView("getCheckedItemsText"); 
            $.ajax({ 
                type: "POST", 
                 data: { value: text },
                url: "/ListView/Features", 
                success: function (result) {  
                    alert(result); 
                } 
            }); 
 
        } 
 
    </script> 
    
{% endhighlight %}

{% highlight c# %}
    
      [HttpPost]
         public ActionResult Features(object value)  
         {
             object val = value;
             return Json(val, JsonRequestBehavior.AllowGet);
         }

{% endhighlight %}
    

## Render ListView from Code behind

ListView can be rendered from the code behind by initializing the required properties in controller and passing those properties via **ViewData** or **Model** to the client side

The following code illustrates the initialization of ListView properties in the controller.

{% highlight c# %}

//Namespace to get the JavaScript (ListView) component properties
using Syncfusion.JavaScript.Models;

namespace MvcApplication.Controllers
{
    public class ListViewController: Controller
    {

        public ActionResult ListviewFeatures()
        {

              //Initializing the Listbox model

          ListViewProperties ListviewObj = new ListViewProperties();


            //Initializing the data as items and other properties 

            ListViewProperties ListviewObj = new ListViewProperties();
            ListviewObj.ShowHeader = false;
            ListviewObj.Width = 200;
            List<ListViewItem> obj = new List<ListViewItem>();
            obj.Add(new ListViewItem() { Text = "Home" });
            obj.Add(new ListViewItem() { Text = "Profile" });
            obj.Add(new ListViewItem() { Text = "Photos" });
            obj.Add(new ListViewItem() { Text = "Location" });

            ListviewObj.Items = obj;
            ListviewObj.EnableCheckMark = true;

            //Passing Listview properties using the ViewData

            ViewData["ListModel"] = ListObj;

            return View();
        }
    }
}

{% endhighlight %}

Binding the ListView properties passed via **ViewData** from the controller in the client side as below.

{% highlight CSHTML %}

@{
    Html.EJ().ListView("Listview", (Syncfusion.JavaScript.Models.ListViewProperties)ViewData["ListViewModel"]).Render();
}

{% endhighlight %}