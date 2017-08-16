---
layout: post
title: Columns | Grid | ASP.NET MVC | Syncfusion
description: columns
platform: ejmvc
control: Grid
documentation: ug
---

# Columns

Column definitions are used as the DataSource schema in grid and it plays vital role in rendering column values in required format and sorting, filtering, editing based on its type. The `Field` property of the columns is necessary to map the datasource values in grid columns.

N> 1. The column with `Field` which are not in the datasource, then the column values will be displayed as empty.
N> 2. If the `Field` name contains "dot" then it is considered as complex binding.


## Auto Generation

The columns are automatically generated when `Columns` declaration is empty or undefined while initializing the grid. Also, all the columns which are in `DataSource` are bound as a grid `Columns`.

{% tabs %}

{% highlight razor %}

     @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            )       
{% endhighlight  %}
{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
                { 
                public class GridController : Controller
                    {        
                        public ActionResult GridFeatures()
                        {    
                                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                                ViewBag.DataSource = DataSource;
                                return View();
                                }
                            }
                        }                 
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img1.png)

### How to set `IsPrimaryKey` for auto generated columns when editing is enabled:

Using `DataBound` event, you can set `IsPrimaryKey` value as `true` by two ways. The following code example demonstrates the above behavior.

1. If primary key "column index" is known then refer the following code example

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .EditSettings(edit =>
                  {
                    edit.AllowEditing(true);
                 })
                .ClientSideEvents(eve => { eve.DataBound("dataBound"); })
               )
    
    <script type="text/javascript">
        function dataBound(args) {
            var column = args.model.columns[0];
            //(or)
            var column = this.getColumnByIndex(0);
            column.isPrimaryKey = true;
            //Here columns method used to update the particular column
            this.columns(column, "update");
        }
    </script>
{% endhighlight  %}
{% highlight c# %}
    
      namespace MVCSampleBrowser.Controllers
       {
        public class GridController : Controller
         { 
           public ActionResult GridFeatures()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.DataSource = DataSource;
                return View();
             }
          }
       }
{% endhighlight  %}
{% endtabs %}  

 2. If primary key "column field name" is known then refer the following code example

{% tabs %}
{% highlight razor %}

      @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit =>
                {
                    edit.AllowEditing(true);
                })
            .ClientSideEvents(eve => { eve.DataBound("dataBound"); })
           )

    <script type="text/javascript">
        function dataBound(args) {
            var column = this.getColumnByField("OrderID");
            column.isPrimaryKey = true;
            //Here columns method used to update the particular column
            this.columns(column, "update");
        }
    </script>
{% endhighlight  %}
{% highlight c# %}

          namespace MVCSampleBrowser.Controllers
              {
                public class GridController : Controller
                   { 
                     public ActionResult GridFeatures()
                       {
                         var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                         ViewBag.DataSource = DataSource;
                         return View();
                        }
                    }
              }          
{% endhighlight  %}
{% highlight js %}
    
        function dataBound(args) {
             var column = this.getColumnByField("OrderID");
             column.isPrimaryKey = true;
             //Here columns method used to update the particular column
             this.columns(column, "update");
          }
 {% endhighlight  %}   
{% endtabs %}  

## Headers

### HeaderText

It represents the title for particular column. To enable header text, set `HeaderText` property of `Columns`. The following code example describes the above behavior.

N> If `HeaderText` is not defined then the `Field` name is considered as header text for that particular column. If `Field` name and `HeaderText` also not defined then the column is rendered with "empty" header text.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

         @(Html.EJ().Grid<Object>("FlatGrid")
              .Datasource((IEnumerable<object>)ViewBag.DataSource)
              .AllowPaging()
              .Columns(col =>
              {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("Freight").HeaderText("Freight").Add();
                col.Field("ShipCountry").HeaderText("Country").Add();
                col.Field("ShipCity").HeaderText("City").Add();
             }))
{% endhighlight  %}
{% highlight c# %}

          namespace MVCSampleBrowser.Controllers
           {
             public class GridController : Controller
              { 
               public ActionResult GridFeatures()
                {
                  var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                  ViewBag.DataSource = DataSource;
                  return View();
                }
              }
            } 
{% endhighlight  %}    
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img2.png)

### Header Text alignment

Align the header text of column header using `HeaderTextAlign` property of the `Columns`. There are four possible ways to align header text, they are

1. Right
2. Left
3. Center
4. Justify

N> For `HeaderTextAlign` property you can assign `enum` value (`TextAlign.Right`).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

       @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").HeaderTextAlign(TextAlign.Right).HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("Freight").HeaderText("Freight").Add();
                col.Field("ShipCountry").HeaderText("Country").Add();
                col.Field("ShipCity").HeaderText("City").Add();
            }))
{% endhighlight  %}
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
        {
          public class GridController : Controller
           { 
            public ActionResult GridFeatures()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.DataSource = DataSource;
                return View();
             }
           }
         }    
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img3.png)

### Header Template

The template design that applies on for the column header. To render template, `HeaderTemplateID` property of `Columns`.

You can use JsRender syntax in the template. For more information about JsRender syntax, please refer [the link](http://www.jsviews.com/#jsrapi "the link").

N> It's a standard way to enclose the `template` within the `script` tag with `type` as `text/x-jsrender`.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

       @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderTemplateID("#employeeTemplate").Add();
                col.Field("Freight").HeaderText("Freight").Add();
                col.Field("ShipCountry").HeaderText("Country").Add();
                col.Field("ShipCity").HeaderText("City").Add();
            }))
{% endhighlight  %}
{% highlight c# %}

           namespace MVCSampleBrowser.Controllers
            {
              public class GridController : Controller
               { 
                 public ActionResult GridFeatures()
                        {
                            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                            ViewBag.DataSource = DataSource;
                            return View();
                         }
                     }
                  }        
{% endhighlight  %}
{% highlight js %}

        <script id="employeeTemplate" type="text/x-jsrender">
          Employee ID
          <span class="e-userlogin e-icon employee"></span>
        </script>
{% endhighlight %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img4.png)

## Text alignment

You can align both content and header text of particular column using `TextAlign` property. There are four possible ways to align content and header text of column, they are 

1. Right
2. Left
3. Center
4. Justify

N> 1. For `TextAlign` property you can assign `enum` value (`TextAlign.Right`).
N> 2. The `TextAlign` property will affect both content and header text of the grid.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

       @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").TextAlign(TextAlign.Right).Add();
                col.Field("EmployeeID").TextAlign(TextAlign.Right).Add();
                col.Field("Freight").TextAlign(TextAlign.Right).Add();
                col.Field("ShipCountry").TextAlign(TextAlign.Center).Add();
                col.Field("ShipCity").TextAlign(TextAlign.Justify).Add();
            }))
{% endhighlight  %}
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
       {
         public class GridController : Controller
          { 
            public ActionResult GridFeatures()
             {
               var DataSource = new NorthwindDataContext().OrdersViews.ToList();
               ViewBag.DataSource = DataSource;
               return View();
             }
           }
        }
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img5.png)

## Format

`Format` is the process of customizing the particular column data with specified jQuery recognized globalize formats, such as currency, numeric, decimal, percentage or dates. To specify the globalize format, by using Format property of `Columns`.

The `Format` value should be wrapped within "{0:" and "}". (For ex: "{0:C3}"). The [data format](https://github.com/jquery/globalize/tree/v0.1.1#format "data format") strings available for the `Date` and `Number` types.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("Freight").Format("{0:C2}").Add();
                col.Field("OrderDate").Format("{0:dd/MM/yyyy}").Add();
                col.Field("ShipCity").Add();
            }))
{% endhighlight  %}
{% highlight c# %}

        namespace MVCSampleBrowser.Controllers
         {
           public class GridController : Controller
            { 
              public ActionResult GridFeatures()
               {
                  var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                  ViewBag.DataSource = DataSource;
                  return View();
                }
             }
          }        
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img6.png)

## Width

You can specify the width for particular column by setting `Width` property of `Columns` as in pixel (ex: 100) or in percentage (ex: 40%).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").Width("10%").Add();
                col.Field("EmployeeID").Width("15%").Add();
                col.Field("Freight").Width(100).Add();
                col.Field("ShipCity").Width(150).Add();
                col.Field("ShipCountry").Width(100).Add();
            }))
{% endhighlight  %}
{% highlight c# %}

       namespace MVCSampleBrowser.Controllers
        {
          public class GridController : Controller
           { 
             public ActionResult GridFeatures()
              {
                 var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                 ViewBag.DataSource = DataSource;
                 return View();
              }
          }
       }
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img7.png)

## Resize to fit 

The `AllowResizeToFit` property enable the grid to set width to columns based on maximum width of the particular column's content to facilitate full visibility of data in all the grid rows and this automatic behavior is applicable only for the columns which does not have width specified. 

On columns where "width is defined", double click on the particular column header's resizer symbol to resize the column to show the whole text. For example, refer the "ShipCity" column in the below code snippet and output screen shot. 

The following code example describes the above behavior. 

{% tabs %}
{% highlight razor %}

      @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowResizeToFit()
            .Columns(col =>
            {
                col.Field("OrderID").Width(100).Add();
                col.Field("EmployeeID").Add();
                col.Field("Freight").Width(75).Add();
                col.Field("ShipCity").Width(50).Add();
                col.Field("ShipAddress").Add();
            }))
{% endhighlight  %}
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
       {
         public class GridController : Controller
          { 
            public ActionResult GridFeatures()
             {
               var DataSource = new NorthwindDataContext().OrdersViews.ToList();
               ViewBag.DataSource = DataSource;
               return View();
             }
          }
       }  
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img8.png)


## Reorder

Reordering can be done by drag and drop the particular column header from one index to another index within the grid. Reordering can be enabled by setting `AllowReordering` property as `true`.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

      @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowReordering()
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();               
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("Freight").Add();
            }))
{% endhighlight  %}
{% highlight c# %}

       namespace MVCSampleBrowser.Controllers
         {
           public class GridController : Controller
             { 
               public ActionResult GridFeatures()
                 {
                    var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                    ViewBag.DataSource = DataSource;
                    return View();
                 }
             }
          }    
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img10.png)

## Visibility

You can hide particular column in grid view by setting `Visible` property of it as `false`.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

      @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("EmployeeID").Add();
                col.Field("OrderID").Visible(false).Add();
                col.Field("Freight").Add();         
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add(); 
            }))
{% endhighlight  %}
{% highlight c# %}

       namespace MVCSampleBrowser.Controllers
         {
           public class GridController : Controller
             { 
               public ActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                  }
               }
          }
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img11.png)


## Unbound Column

You can define the unbound columns in grid by not defining `Field` property for that particular. Value for this columns can be populated either manually using `QueryCellInfo` event or by using `ColumnTemplate`.

N> Editing, grouping, filtering, sorting, summary and searching support are not available for unbound columns.

The following code example describes the above behavior. 

{% tabs %}
{% highlight razor %}

         @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .EditSettings(edit => { edit.AllowDeleting(); })
                .Columns(col =>
                  {
                    col.Field("OrderID").IsPrimaryKey(true).Add();
                    col.Field("EmployeeID").Add();
                    col.Field("CustomerID").Add();
                    col.Field("Freight").Add();
                    col.HeaderText("").Format("<a onclick=\"click(this)\" href=#>Delete</a>").Add();
                   })
                 )
{% endhighlight  %}
{% highlight c# %}

         namespace MVCSampleBrowser.Controllers
          {
            public class GridController : Controller
             { 
               public ActionResult GridFeatures()
                 {
                    var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                    ViewBag.DataSource = DataSource;
                    return View();
                  }
              }
           }
{% endhighlight  %}
{% highlight js %}
    
     <script type="text/javascript">
        function click(e) {
            var obj = $("#FlatGrid").data("ejGrid");
            obj.deleteRecord("OrderID", obj.getSelectedRecords()[0]);
        }
    </script>
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img13.png)

## Column Template

HTML templates can be specified in the `Template` property of the particular column as a string (html element) or ID of the template's HTML element.

You can use JsRender syntax in the template. For more information about JsRender syntax, please refer [this link](http://www.jsviews.com/#jsrapi "this link"). 

N> If `Field` is not specified, you will not able to perform editing, grouping, filtering, sorting, search and summary functionalities in particular column.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

       @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .PageSettings(page => { page.PageSize(4); })
                .Columns(col =>
                {
                    col.HeaderText("Photo").Template("<img style='width: 75px; height: 70px' src='/13.2.0.29/themes/web/images/employees/{{"{{"}}:EmployeeID{{}}}}.png' alt='{{"{{"}}:EmployeeID{{}}}}.png' />").Add();
                    col.Field("EmployeeID").Add();
                    col.Field("FirstName").Add();
                    col.Field("LastName").Add();
                    col.Field("Country").Add();
                }))
{% endhighlight  %}
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
        {
           public class GridController : Controller
            { 
              public ActionResult GridFeatures()
                {
                  var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
                  ViewBag.DataSource = DataSource;
                  return View();
                }
              }
          }
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](columns_images/columns_img14.png)

## Controlling Grid actions

You can control the grid actions of a particular column by setting `AllowSorting`,`AllowGrouping`, `AllowFiltering` and `AllowEditing` properties of it as `false`.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

        @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .AllowResizing()
                .AllowSorting()
                .AllowGrouping()
                .AllowFiltering()
                .EditSettings(edit => { edit.AllowEditing(); })
                .Columns(col =>
                {
                    col.Field("OrderID").IsPrimaryKey(true).Add();
                    col.Field("EmployeeID").AllowEditing(false).AllowResizing(false).AllowSorting(false).AllowGrouping(false).AllowFiltering(false).Add();
                    col.Field("Freight").Add();
                    col.Field("ShipCity").Add();
                    col.Field("ShipCountry").Add();
                }) )
{% endhighlight  %}
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
       {
         public class GridController : Controller
           { 
            public ActionResult GridFeatures()
              {
                 var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                 ViewBag.DataSource = DataSource;
                 return View();
                }
            }
        }
{% endhighlight  %}
{% endtabs %} 

## Read only

To make a column as "read-only" then set `AllowEditing` property of `Columns` as `false`.

The following code example describes the above behavior. 

{% tabs %}
{% highlight razor %}

       @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .EditSettings(edit => { edit.AllowEditing(); })
                .Columns(col =>
                {
                    col.Field("OrderID").IsPrimaryKey(true).Add();
                    col.Field("EmployeeID").AllowEditing(false).Add();
                    col.Field("Freight").Add();
                    col.Field("ShipCity").Add();
                    col.Field("ShipCountry").Add();
                })
                )
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
       public class GridController : Controller
        { 
          public ActionResult GridFeatures()
            {
              var DataSource = new NorthwindDataContext().OrdersViews.ToList();
              ViewBag.DataSource = DataSource;
              return View();
            }
         }
      }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](columns_images/columns_img15.png)

## Expression Column

Expression column is possible only for `Template` column. You can use JsRender syntax in the template.

You can use JsRender syntax in the template.For more information about JsRender syntax, please refer [the link](http://www.jsviews.com/#jsrapi "the link"). 

N> This expression column is supported at read only mode.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

        @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .Columns(col =>
                {
                    col.Field("FoodName").Add();
                    col.Field("Protein").Add();
                    col.Field("Fat").Add();
                    col.Field("Carbohydrate").Add();
                    col.HeaderText("Calories In Take").Template("<span>{{"{{"}}:Protein * 4  + Fat * 4 + Carbohydrate * 9 {{}}}}</span>").Add();
                })
                )
{% endhighlight  %}
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
       {
         public class GridController : Controller
          { 
            public ActionResult GridFeatures()
              {
                var DataSource = new NorthwindDataContext().FoodInformation.ToList();
                ViewBag.DataSource = DataSource;
                return View();
              }
          }
      }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](columns_images/columns_img16.png)


## Command Column

### Default action buttons

Using Command column, you can add `CRUD` action buttons as one of the grid column, through `Type` property of `Commands`. The `Type` property supports the below default `UnboundType` buttons.

1. Edit
2. Save
3. Delete
4. Cancel

Through `ButtonOptions` property of `Commands`, you can specify all the button options which are supported by Essential Studio ASP.NET MVC Button control. 

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

        @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .EditSettings(edit => { edit.AllowEditing().AllowDeleting().AllowAdding(); })
                .Columns(col =>
                {
                    col.Field("OrderID").IsPrimaryKey(true).Add();
                    col.Field("EmployeeID").Add();
                    col.Field("Freight").EditType(EditingType.Numeric).Add();
                    col.Field("ShipCountry").Add();
                    col.HeaderText("Manage Records").Commands(command =>
                    {
                        command.Type(UnboundType.Edit)
                            .ButtonOptions(new Syncfusion.JavaScript.Models.ButtonProperties()
                            {
                                Text = "Edit"
                            }).Add();
                        command.Type(UnboundType.Delete)
                            .ButtonOptions(new Syncfusion.JavaScript.Models.ButtonProperties()
                            {
                                Text = "Delete"
                            }).Add();
                        command.Type(UnboundType.Save)
                            .ButtonOptions(new Syncfusion.JavaScript.Models.ButtonProperties()
                            {
                                Text = "Save"
                            }).Add();
                        command.Type(UnboundType.Cancel)
                            .ButtonOptions(new Syncfusion.JavaScript.Models.ButtonProperties()
                            {
                                Text = "Cancel"
                            }).Add();
                    }).Width(150).Add();
                }) )
{% endhighlight  %}
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
       {
         public class GridController : Controller
          { 
            public ActionResult GridFeatures()
              {
                 var DataSource = new NorthwindDataContext().OrdersView.ToList();
                 ViewBag.DataSource = DataSource;
                 return View();
              }
          }
       }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](columns_images/columns_img17.png)

### Custom buttons

You can add custom button in the command column by specifying the `Type` property of `Commands` as `empty` or any other `string` instead of `enum` values.

N> 1. For `Type` property you can assign either `string` value (`edit`).
N> 2. In command column you can add only buttons.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

        @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .Columns(col =>
                {
                    col.Field("EmployeeID").Add();
                    col.HeaderText("Employee Details").Commands(command =>
                     {
                        command.Type("detail")
                            .ButtonOptions(new Syncfusion.JavaScript.Models.ButtonProperties()
                            {
                                Text = "Details",
                                Width = "100px",
                                Click = "onClick"
                            }).Add();
                    })                
                .TextAlign(TextAlign.Center)
                .Width(150)
                .Add();
                })
                )   
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
        public class GridController : Controller
         { 
           public ActionResult GridFeatures()
             {
               var DataSource = new NorthwindDataContext().OrdersView.ToList();
               ViewBag.DataSource = DataSource;
               return View();
             }
         }
      }
{% endhighlight  %}
{% highlight js %}
            <script type="text/javascript">
               function onClick(args) {
                 var grid = $("#FlatGrid").ejGrid("instance");
                 var index = this.element.closest("tr").index();
                 var record = grid.getCurrentViewData()[index];
                 alert("Record Details: " + JSON.stringify(record));
               }
           </script> 
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](columns_images/columns_img18.png)

## Column Chooser

Column chooser contains all the columns which are defined in the `Columns` property, using this you can control the visibility of columns in grid. You can prevent to show the particular column in column chooser by setting `ShowInColumnChooser` property of `Columns` as `false`. It can be shown in the right corner of grid. To enable column chooser, `ShowColumnChooser` property as `true`. 

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

      @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .ShowColumnChooser()
                .Columns(col =>
                {
                    col.Field("OrderID").IsPrimaryKey(true).Add();
                    col.Field("EmployeeID").ShowInColumnChooser(false).Add();
                    col.Field("Freight").Add();
                    col.Field("ShipCity").Add();
                    col.Field("ShipCountry").Add();
                }) )
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
       public class GridController : Controller
        { 
         public ActionResult GridFeatures()
            {
                var DataSource = new NorthwindDataContext().OrdersView.ToList();
                ViewBag.DataSource = DataSource;
                return View();
            }
         }
      }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](columns_images/columns_img19.png)

## Foreign Key Column

Lookup data source can be bound to `DataSource` property of `Columns`. Data `field` and `text` can be set using `ForeignKeyField` and `ForeignKeyValue` property of `Columns`.

In the `DataSource` property, we can bound local and remote data.

I> For foreign key column the sorting and grouping is based on `ForeignKeyField` instead of `ForeignKeyValue`. You can refer [Foreign Key Adaptor](https://help.syncfusion.com/aspnetmvc/grid/data-adaptors#foreign-key-adaptor) to sort and group the foreign key column based on `ForeignKeyField`.

N> In remote data, server should be configured to perform select and filter operations since the Grid will try to fetch required columns using select operation and required data using filter operation.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}
 
         @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource1)
                .AllowPaging()
                .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing(); })
                .Columns(col =>
                {
                    col.Field("OrderID").IsPrimaryKey(true).Add();
                    col.Field("EmployeeID").HeaderText("First Name").ForeignKeyField("EmployeeID").ForeignKeyValue("FirstName").DataSource((IEnumerable<object>)ViewBag.DataSource2).Add();
                          //(or)
                    col.Field("EmployeeID").HeaderText("First Name").ForeignKeyField("EmployeeID").ForeignKeyValue("FirstName").DataSource("http://mvc.syncfusion.com/Services/Northwnd.svc/Employees/").Add();
                    col.Field("CustomerID").Add();
                    col.Field("Freight").Add();
                    col.Field("ShipCity").Add();
                }) )
{% endhighlight  %} 
{% highlight c# %}

       namespace MVCSampleBrowser.Controllers
        {
         public class GridController : Controller
          { 
           public ActionResult GridFeatures()
             {
                var DataSource1 = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.DataSource1 = DataSource1;
                var DataSource2 = new NorthwindDataContext().EmployeeViews.ToList();
                ViewBag.DataSource2 = DataSource2;    
                return View();
            }
        }
      }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](columns_images/columns_img20.png)

## Customize column

You can customize the header and content of that particular column by `CssClass` property of the column.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

        @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .Columns(col =>
                {
                    col.Field("OrderID").Add();
                    col.Field("CustomerID").Add();
                    col.Field("EmployeeID").CssClass("customizes").Add();
                    col.Field("Freight").Add(); 
                })
                )
{% endhighlight  %}
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
       {
         public class GridController : Controller
          { 
            public ActionResult GridFeatures()
             {
                var DataSource1 = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.DataSource = DataSource1;
                return View();
             }
          }
       }
{% endhighlight  %}
{% highlight css %}

    .customizes.e-headercell {
        background-color: #2382c3;
        color: white;
        font-family: 'Bell MT';
        font-size: 20px;
    }
    
    .customizes.e-rowcell {
        background-color: #ecedee;
        font-family: 'Bell MT';
        color: red;
        font-size: 20px;
    }
{% endhighlight %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](columns_images/columns_img23.png)

## Type

Used to define the type of the particular column data. If the `Type` property of `Columns` is not specified then its type is automatically defined based on the first row data of that column.

N> The `Type` is needed for filtering feature when first row of the data is `null` or `empty`.

The available column data type is tabulated as follows.

<table>
<tr>
<th>
Type</th><th>
Description</th>
</tr>
<tr>
<td>
string</td><td>
Gets or sets the type of the column value as string </td>
</tr>
<tr>
<td>
number</td><td>
Gets or sets the type of the column value as number</td>
</tr>
<tr>
<td>
date</td><td>
Gets or sets the type of the column value as date</td>
</tr>
<tr>
<td>
datetime</td><td>
Gets or sets the type of the column value as datetime</td>
</tr>
<tr>
<td>
boolean</td><td>
Gets or sets the type of the column value as true or false </td>
</tr>
<tr>
<td>
guid</td><td>
Gets or sets the type of the column value as guid</td>
</tr>
<tr>
<td>
checkbox </td><td>
Gets or sets the type of the column value as checkbox for row selection </td>
</tr>
</table>

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}
   
        @(Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .Columns(col =>
                {
                    col.Field("OrderID").Add();
                    col.Field("CustomerID").Type("string").Add();
                    col.Field("EmployeeID").Type("number").Add();
                    col.Field("Freight").Add();
                    col.Field("ShipCountry").Add(); 
                }) )
{% endhighlight  %}
{% highlight c# %}

       namespace MVCSampleBrowser.Controllers
        {
          public class GridController : Controller
           { 
             public ActionResult GridFeatures()
              {
                var DataSource1 = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.DataSource = DataSource1;
                return View();
              }
           }
         }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](columns_images/columns_img24.png)

## Column Layout

You can set the Grid's columns layout based on either Grid width or its columns width using `ColumnLayout` property of Grid. There are two ways to set the column layout, they are 

1. Auto
2. Fixed

{% tabs %}
{% highlight razor %}

     @(Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .ColumnLayout(ColumnLayout.Fixed)
            .Columns(col =>
            {
                col.Field("OrderID").Width(80).Add();
                col.Field("EmployeeID").Width(80).Add();
                col.Field("ShipCity").Width(90).Add();
                col.Field("ShipName").Width(110).Add();
                col.Field("ShipCountry").Width(100).Add();
                col.Field("Freight").Width(80).Add();
            }))
{% endhighlight  %}
{% highlight c# %}

       namespace MVCSampleBrowser.Controllers
        {
          public class GridController : Controller
           { 
             public ActionResult GridFeatures()
              {
                 var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                 ViewBag.DataSource = DataSource;
                 return View();
              }
          }
       }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](columns_images/columns_img25.png)

