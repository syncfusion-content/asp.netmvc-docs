---
layout: post
title: Editing | Kanban | ASP.NET MVC | Syncfusion
description: This section explains how to enable different editing mode on the Syncfusion ASP.NET MVC Kanban component.
documentation: ug
control: Kanban
platform: ejmvc
---

# Editing

The Kanban control has support for dynamic insertion, updating and deletion of cards. 

Set `AllowEditing` and `AllowAdding` property as true to enable editing/inserting respectively. The primary key for the data source should be defined in `PrimaryKey`, for editing to work properly. 

You can start the edit action by double clicking the particular card. Similarly, you can add new card to Kanban either by double clicking the particular cell or on an external button which is bound to call [`addCard`](https://help.syncfusion.com/js/api/ejkanban#methods:kanbanedit-addcard) method of Kanban. 

Deletion of the card is possible by using [`deleteCard`](https://help.syncfusion.com/js/api/ejkanban#methods:kanbanedit-deletecard) by passing primary key as attribute.

N> In Kanban, the `primary key` column will be automatically set to `read only` while editing the card which is to avoid duplicate entry in the cards.

## Configuring Edit Items

You need to configure the list of data source fields that are allowable in editing state using `EditItems` property. The `Field` property of `EditItems` needs to be mapped with data source fields.

You can map the data source field as title to edit form using `Title` property of `Fields`. By default, it’s mapped with `PrimaryKey`.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .Columns(col =>
        {
            col.HeaderText("Backlog").Key("Open").Add();
            col.HeaderText("In Progress").Key("InProgress").Add();
            col.HeaderText("Done").Key("Close").Add();
        })
        .KeyField("Status")

        .Fields(field =>
        {
            field.Content("Summary")
                .PrimaryKey("Id");
        })
        .EditSettings(edit =>
        {
            edit.AllowAdding(true)
                .AllowEditing(true)
                .EditItems(e =>
                {
                    e.Field("Id").Add();
                    e.Field("Status").EditType(KanbanEditingType.Dropdown).Add();
                    e.Field("Assignee").EditType(KanbanEditingType.Dropdown).Add();
                    e.Field("Estimate").EditType(KanbanEditingType.Numeric).NumericEditOptions(new EditorProperties()
                    {
                        DecimalPlaces = 2
                    }).Add();
                    e.Field("Summary").EditType(KanbanEditingType.TextArea).Add();
                });  
            })           
    )

{% endhighlight  %}
{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            //
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }

{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![Configuring edit items in ASP NET MVC kanban control](Editing_images/editing_img1.png)

## Edit modes

### Dialog

Set `EditMode` as `Dialog` to edit data using a dialog box, which displays the fields associated with the data card being edited. Default value is `Dialog`.

N> For `EditMode` property you can assign either `string` value (“Dialog”) or `enum` value (`ej.Kanban.EditMode.Dialog`).

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .Columns(col =>
        {
            col.HeaderText("Backlog").Key("Open").Add();
            col.HeaderText("In Progress").Key("InProgress").Add();
            col.HeaderText("Done").Key("Close").Add();
        })
        .KeyField("Status")

        .Fields(field =>
        {
            field.Content("Summary")
                .PrimaryKey("Id");
        })
        .EditSettings(edit =>
        {
            edit.AllowAdding(true)
                .AllowEditing(true)
                .EditItems(e =>
                {
                    e.Field("Id").Add();
                    e.Field("Status").EditType(KanbanEditingType.Dropdown).Add();
                    e.Field("Assignee").EditType(KanbanEditingType.Dropdown).Add();
                    e.Field("Estimate").EditType(KanbanEditingType.Numeric).NumericEditOptions(new EditorProperties()
                    {
                        DecimalPlaces = 2
                    }).Add();
                    e.Field("Summary").EditType(KanbanEditingType.TextArea).Add();
                });
        })
    )

{% endhighlight  %}
{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            //
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }
         
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![Dialog in ASP NET MVC kanban control](Editing_images/editing_img2.png)

### Dialog Template Form

You can edit any of the fields pertaining to a single card of data and apply it to a template so that the same format is applied to all the other cards that you may edit later. 

Using this template support, you can edit the fields that are not bound to `EditItems`.

To edit the cards using Dialog template form, set `EditMode` as `DialogTemplate` and specify the template id to `DialogTemplate` property of `EditSettings`.

N> 1. `value` attribute is used to bind the corresponding field value while editing.
N> 2. `name` attribute is used to get the changed field values while save the edited card.
N> 3. For `EditMode` property you can assign `enum` value (`KanbanEditMode.DialogTemplate`).

The following code example describes the above behavior.

{% highlight html %}

    <script id="template" type="text/template">
                        <table cellspacing="10">
                            <tr>
                                <td style="text-align: right;">Id
                                </td>
                                <td style="text-align: left">
                                    <input id="Id" name="Id" value="{{: Id}}" class="e-field e-ejinputtext valid e-disable" style="text-align: right; width: 175px; height: 28px" disabled="disabled" />
                                </td>
                                <td style="text-align: right;">Status
                                </td>
                                <td style="text-align: left">
                                    <select id="Status" name="Status">
                                        <option value="Close">Close</option>
                                        <option value="InProgress">InProgress</option>
                                        <option value="Open">Open</option>
                                    </select>
                                </td>
                            </tr>
                            <tr>
                                <td style="text-align: right;">Estimate
                                </td>
                                <td style="text-align: left">
                                    <input type="text" id="Estimate" name="Estimate" value="{{:Estimate}}" />
                                </td>
                                <td style="text-align: right;">Assignee
                                </td>
                                <td style="text-align: left">
                                    <select id="Assignee" name="Assignee">
                                        <option value="Nancy Davloio">Nancy</option>
                                        <option value="Andrew Fuller">Andrew Fuller</option>
                                        <option value="Janet Leverling">Janet</option>
                                        <option value="Margaret hamilt">Margaret</option>
                                        <option value="Steven walker">Steven walker</option>
                                        <option value="Michael Suyama">Michael</option>
                                        <option value="Robert King">Robert King</option>
                                        <option value="Laura Callahan">Laura Callahan</option>
                                    </select>
                                </td>
                            </tr>
                        </table>
    </script>

{% endhighlight %}

{% tabs %}

{% highlight razor %}
 
    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .ClientSideEvents(eve => eve.ActionComplete("complete"))
        .Columns(col =>
        {
            col.HeaderText("Backlog").Key("Open").Add();
            col.HeaderText("In Progress").Key("InProgress").Add();
            col.HeaderText("Done").Key("Close").Add();
        })
        .KeyField("Status")

        .Fields(field =>
        {
            field.Content("Summary")
                .PrimaryKey("Id");
        })
        .EditSettings(edit =>
        {
            edit.AllowAdding(true)
                .AllowEditing(true)
                .EditMode(KanbanEditMode.DialogTemplate)
                .DialogTemplate("#template");
        })
    )
 
  
{% endhighlight  %}
{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            //
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }

{% endhighlight  %}

{% endtabs %}  

While using template, you can change the elements that are defined in the `template`, to appropriate Syncfusion JS controls based on the column type. This can be achieved by using [`ActionComplete`](https://help.syncfusion.com/js/api/ejkanban#events:actioncomplete) event of Kanban. Please refer to following code snippets.

{% highlight javascript %}

    function complete(args) {
        if ((args.requestType == "beginedit" || args.requestType == "add") && args.model.editSettings.editMode == "dialogtemplate") {
            $("#Estimate").ejNumericTextbox({ value: parseFloat($("#Estimate").val()), width: "175px", height: "34px", decimalPlaces: 2 });
            $("#Assignee").ejDropDownList({ width: '175px' });
            $("#Status").ejDropDownList({ width: '175px' });
            $("#Priority").ejDropDownList({ width: '175px' });
            if (args.requestType == "beginedit" || args.requestType == "add") {
                $("#Assignee").ejDropDownList("setSelectedValue", args.data['Assignee']);
                $("#Priority").ejDropDownList("setSelectedValue", args.data['Priority']);
                $("#Status").ejDropDownList("setSelectedValue", args.data['Status']);
            }
        
        }
    }

{% endhighlight %}

The following output is displayed as a result of the above code example.

![Dialog template form in ASP NET MVC kanban control](Editing_images/editing_img3.png)

### External Form

Set the `EditMode` as `ExternalForm` to open the edit form in outside kanban content.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .Columns(col =>
        {
            col.HeaderText("Backlog").Key("Open").Add();
            col.HeaderText("In Progress").Key("InProgress").Add();
            col.HeaderText("Done").Key("Close").Add();
        })  
        .KeyField("Status")
        .Fields(field =>
        {
            field.Content("Summary")
                .PrimaryKey("Id");
        })
        .EditSettings(edit =>
        {
            edit.AllowAdding(true)
                .AllowEditing(true)
                .EditItems(e =>
                {
                    e.Field("Id").Add();
                    e.Field("Status").EditType(KanbanEditingType.Dropdown).Add();
                    e.Field("Summary").EditType(KanbanEditingType.TextArea).Add();
                }).EditMode(KanbanEditMode.ExternalForm);
        })
    )

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }
         
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![External form in ASP NET MVC kanban control](Editing_images/editing_img11.png)

Form Position:

Form Position can be customized by setting the `FormPosition` property of `EditSettings' as "right" or "bottom".

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .Columns(col =>
        {
            col.HeaderText("Backlog").Key("Open").Add();
            col.HeaderText("In Progress").Key("InProgress").Add();
            col.HeaderText("Done").Key("Close").Add();
        })  
        .KeyField("Status")

        .Fields(field =>
        {
            field.Content("Summary")
                .PrimaryKey("Id");
        })
        .EditSettings(edit =>
        {
            edit.AllowAdding(true)
                .AllowEditing(true)
                .FormPosition(KanbanFormPosition.Right)
                .EditItems(e =>
                {
                    e.Field("Id").Add();
                    e.Field("Status").EditType(KanbanEditingType.Dropdown).Add();
                    e.Field("Assignee").EditType(KanbanEditingType.Dropdown).Add();
                    e.Field("Estimate").EditType(KanbanEditingType.Numeric).NumericEditOptions(new EditorProperties()
                    {
                        DecimalPlaces = 2
                    }).Add();
                    e.Field("Summary").EditType(KanbanEditingType.TextArea).Add();
                }).EditMode(KanbanEditMode.ExternalForm);
        })
    )

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }
         
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![Customize external form in ASP NET MVC kanban control](Editing_images/editing_img12.png)

### External Template Form

You can edit any of the fields pertaining to a single card of data and apply it to a template so that the same format is applied to all the other cards that you may edit later. 

Using this template support, you can edit the fields that are not bound to Kanban Edit Items.

To edit the cards using External template form, set `EditMode` as `ExternalFormTemplate` and specify the template id to `ExternalFormTemplate` property of `EditSettings`.

While using template, you can change the elements that are defined in the template, to appropriate Syncfusion JS controls based on the column type. This can be achieved by using `ActionComplete` event of Kanban.

N> 1. `value` attribute is used to bind the corresponding field value while editing. 
N> 2. `name` attribute is used to get the changed field values while save the edited card. 
N> 3. For `EditMode` property you can assign `enum` value (`KanbanEditMode.ExternalFormTemplate`).

The following code example describes the above behavior.

{% highlight html %}

    <script id="template" type="text/template">
                        <table cellspacing="10">
                            <tr>
                                <td style="text-align: right;">Id
                                </td>
                                <td style="text-align: left">
                                    <input id="Id" name="Id" value="{{: Id}}" class="e-field e-ejinputtext valid e-disable" style="text-align: right; width: 175px; height: 28px" disabled="disabled" />
                                </td>
                                <td style="text-align: right;">Status
                                </td>
                                <td style="text-align: left">
                                    <select id="Status" name="Status">
                                        <option value="Close">Close</option>
                                        <option value="InProgress">InProgress</option>
                                        <option value="Open">Open</option>
                                    </select>
                                </td>
                            </tr>
                            <tr>
                                <td style="text-align: right;">Assignee
                                </td>
                                <td style="text-align: left">
                                    <select id="Assignee" name="Assignee">
                                        <option value="Nancy">Nancy</option>
                                        <option value="Andrew Fuller">Andrew Fuller</option>
                                        <option value="Janet">Janet</option>
                                        <option value="Margaret">Margaret</option>
                                        <option value="Steven walker">Steven walker</option>
                                        <option value="Michael">Michael</option>
                                        <option value="Robert King">Robert King</option>
                                        <option value="Laura Callahan">Laura Callahan</option>
                                    </select>
                                </td>
                            </tr>
                        </table>
    </script>

{% endhighlight %}

{% tabs %}

{% highlight razor %}
 
    @(Html.EJ().Kanban("Kanban")
        .DataSource((IEnumerable<object>)ViewBag.datasource)
        .ClientSideEvents(eve => eve.ActionComplete("complete"))
        .Columns(col =>
        {
            col.HeaderText("Backlog").Key("Open").Add();
            col.HeaderText("In Progress").Key("InProgress").Add();
            col.HeaderText("Done").Key("Close").Add();
        })
        .KeyField("Status")

        .Fields(field =>
        {
            field.Content("Summary")
                .PrimaryKey("Id");
        })
        .EditSettings(edit =>
        {
            edit.AllowAdding(true)
                .AllowEditing(true)
                .EditMode(KanbanEditMode.ExternalFormTemplate)
                .ExternalFormTemplate("#template");
        })
    )
 
{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }

{% endhighlight  %}

{% endtabs %}  

{% highlight javascript %}

    function complete(args) {
        if ((args.requestType == "beginedit" || args.requestType == "add") && args.model.editSettings.editMode == "externalformtemplate") {
            $("#Assignee").ejDropDownList({ width: '175px' });
            $("#Status").ejDropDownList({ width: '175px' });
            if (args.requestType == "beginedit" || args.requestType == "add") {
                $("#Assignee").ejDropDownList("setSelectedValue", args.data['Assignee']);
                $("#Status").ejDropDownList("setSelectedValue", args.data['Status']);
            }        
        }
    }

{% endhighlight %}

The following output is displayed as a result of the above code example.

![External template form in ASP NET MVC kanban control](Editing_images/editing_img13.png)


### Cell edit type and its params

The edit type of bound column can be customized using `EditType` property of `Columns`. The following Essential JavaScript controls are supported built-in by `EditType`. You can set the `EditType` based on specific data type of the column.

<table>
<tr>
<th>
EditType</th><th>
EditParams</th>
<th>
Description</th>
<th>
Example</th>
</tr>
<tr>
<td>
Numeric</td><td>
 {{ 'TextBoxes' | markdownify }} </td>
<td>
control for integers, double, and decimal data’s</td>
<td>
NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 })</td>
</tr>
<tr>
<td>
String</td><td>
HTML Textbox</td>
<td>
HTML Textbox</td>
<td>
-</td>
</tr>
<tr>
<td>
DatePicker </td><td>
{{ 'DatePicker'| markdownify }} </td>
<td>
control for date data</td>
<td>
DateEditOptions(new DatePickerProperties() { ButtonText="Now"})</td>
</tr>
<tr>
<td>
DateTimePicker </td><td>
{{ 'DateTimePicker'| markdownify }} </td>
<td>
control for date data-time data</td>
<td>
DateTimeEditOptions(new DateTimePickerProperties() { Enabled=true})</td>
</tr>
<tr>
<td>
DropDown </td><td>
{{ 'DropDownList'| markdownify }} </td>
<td>
control for list of data</td>
<td>
DropdownEditOptions(new DropDownListProperties() { AllowGrouping=true})</td>
</tr>
<tr>
<td>
RTE </td><td>
{{ 'RTE'| markdownify }} </td>
<td>
control for customizing text in RTE format</td>
<td>
RTEEditOptions(new RTEproperties() { EnableResize=true})</td>
</tr>
<tr>
<td>
TextArea </td><td>
HTML TextArea</td>
<td>
Control for multi-line plain-text editing</td>
<td>
</td>
</tr>
</table>

N> 1. If `EditType` is not set, then by default it will display HTML textbox while editing a card.
N> 2. For `EditType` property you can assign either string value (`numericedit`) or `enum` value (`ej.Kanban.EditingType.Numeric`).

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
     .DataSource((IEnumerable<object>)ViewBag.datasource)
     .Columns(col =>
     {
         col.HeaderText("Backlog").Key("Open").Add();
         col.HeaderText("In Progress").Key("InProgress").Add();
         col.HeaderText("Done").Key("Close").Add();
     })
     .KeyField("Status")

     .Fields(field =>
     {
         field.Content("Summary")
             .PrimaryKey("Id");
     })
     .EditSettings(edit =>
     {
         edit.AllowAdding(true)
             .AllowEditing(true)
             .EditItems(e =>
             {
                 e.Field("Id").Add();
                 e.Field("Status").EditType(KanbanEditingType.Dropdown).Add();
                
                 e.Field("Estimate").EditType(KanbanEditingType.Numeric).NumericEditOptions(new EditorProperties()
                 {
                     DecimalPlaces = 2
                 }).Add();
                 e.Field("Summary").EditType(KanbanEditingType.RTE).RTEEditOptions(new RTEproperties() { Height = "150",MinHeight="100"}).Add();
             });
     })

    )


{% endhighlight  %}
{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            //
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }

{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![Cell edit type and its params in ASP NET MVC kanban control](Editing_images/editing_img4.png)

## Column Validation

We can validate the value of the added or edited card cell before saving.
The below validation script files are needed when editing is enabled with validation.

1.	jquery.validate.min.js
2.	jquery.validate.unobtrusive.min.js

N> If you enabled the unobtrusive option, then need to refer the jquery.validate.unobtrusive.min.js

file in your application along with the other script.

### jQuery Validation

You can set validation rules using `ValidationRules` property of `Columns`. The following are jQuery validation methods.


#### List of jQuery validation methods

<table>
<tr>
<th>
Rules</th><th>
Description</th>
</tr>
<tr>
<td>
required</td><td>
Requires an element.</td></tr>
<tr>
<td>
remote</td><td>
Requests a resource to check the element for validity.</td></tr>
<tr>
<td>
minlength</td><td>
Requires the element to be of given minimum length.</td></tr>
<tr>
<td>
maxlength</td><td>
Requires the element to be of given maximum length.</td></tr>
<tr>
<td>
rangelength</td><td>
Requires the element to be in given value range.</td></tr>
<tr>
<td>
min</td><td>
The element requires a given minimum.</td></tr>
<tr>
<td>
max</td><td>
The element requires a given maximum.</td></tr>
<tr>
<td>
range</td><td>
Requires the element to be in a given value range.</td></tr>
<tr>
<td>
email</td><td>
The element requires a valid email.</td></tr>
<tr>
<td>
url</td><td>
The element requires a valid url.</td></tr>
<tr>
<td>
date</td><td>
Requires the element to be a date.</td></tr>
<tr>
<td>
dateISO</td><td>
The element requires an ISO date.</td></tr>
<tr>
<td>
number</td><td>
The element requires a decimal number.</td></tr>
<tr>
<td>
digits</td><td>
The element requires digits only.</td></tr>
<tr>
<td>
creditcard</td><td>
Requires the element to be a credit card number.</td></tr>
<tr>
<td>
equalTo</td><td>
Requires the element to be the same as another.</td></tr>
</table>

Kanban supports all the standard validation methods of jQuery, please refer the jQuery validation documentation [`link`](https://jqueryvalidation.org/) for more information.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
     .DataSource((IEnumerable<object>)ViewBag.datasource)
     .Columns(col =>
     {
         col.HeaderText("Backlog").Key("Open").Add();
         col.HeaderText("In Progress").Key("InProgress").Add();
         col.HeaderText("Done").Key("Close").Add();
     })
     .KeyField("Status")

     .Fields(field =>
     {
         field.Content("Summary")
             .PrimaryKey("Id");
     })
     .EditSettings(edit =>
     {
         edit.AllowAdding(true)
             .AllowEditing(true)
            .EditItems(e =>
            {
                e.Field("Id").Add();
                e.Field("Status").EditType(KanbanEditingType.Dropdown).Add();
                e.Field("Assignee").EditType(KanbanEditingType.Dropdown).Add();
                e.Field("Estimate").EditType(KanbanEditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).ValidationRules(rule => { rule.AddRule("range", "[0,1000]"); }).Add();
                e.Field("Summary").EditType(KanbanEditingType.TextArea).ValidationRules(rule => { rule.AddRule("required", true); }).Add();
            });
     })
    ) 

  
{% endhighlight  %}
{% highlight c# %}

    namespace MVCSampleBrowser
    {
        public partial class KanbanController : Controller
        {
            //
            // GET: /Kanban/
            public ActionResult KanbanFeatures()
            {
                var DataSource = new NorthwindDataContext().Tasks.Take(30).ToList();
                ViewBag.datasource = DataSource;
                return View();
            }
        }
    }
              
{% endhighlight  %}

{% endtabs %}  

The following output is displayed as a result of the above code example.

![Column validation in ASP NET MVC kanban control](Editing_images/editing_img5.png)

## Persisting data in server

Edited data can be persisted in database using RESTful web services.

All the CRUD operations in Kanban are done through DataManager. DataManager have an option to bind all the CRUD related data in server side. Please refer the [`link`](https://help.syncfusion.com/aspnetmvc/datamanager/overview) to know about the DataManager.

### URL Adaptor

You can use the `UrlAdaptor` of `DataManager` when binding `DataSource` from remote data. At initial load of Kanban, using URL property of DataManager, data are fetched from remote data and bound to Kanban. You can map CRUD operation in Kanban to Server-Side Controller action using the property `CrudURL`.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}
 
    @(Html.EJ().Kanban("Kanban")
       .DataSource(data => data.URL("GetData").CrudURL("Crud").Adaptor(AdaptorType.UrlAdaptor))
                   .Columns(col =>
                   {
                       col.HeaderText("Backlog").Key("Open").ShowAddButton(true).Add();
                       col.HeaderText("In Progress").Key("InProgress").Add();
                       col.HeaderText("Done").Key("Close").Add();
                   })
                           .CustomToolbarItems(custom =>
                                       {
                                           custom.Template("#Delete").Add();
                                       })
                  .EditSettings(edit =>
                          {
                              edit.AllowAdding(true)
                                  .AllowEditing(true)
                                  .EditItems(e =>
                                  {
                                      e.Field("Id").Add();
                                      e.Field("Status").Add();
                                      e.Field("Assignee").Add();
                                      e.Field("Estimate").Add();
                                      e.Field("Summary").Add();
                                  }).EditMode(KanbanEditMode.Dialog);
                          })
                  .KeyField("Status")
                  .Fields(field =>
                  {
                      field.Content("Summary")
                           .PrimaryKey("Id")
                           .Priority("RankId");
                  })
                  .ClientSideEvents(eve => eve.ToolBarClick("toolbarClick"))
    )
    
    <script type="text/javascript">
     function toolbarClick(args) {
        if (args.itemName == "Delete" && this.element.find(".e-kanbancard").hasClass("e-cardselection")) {
            var selected = this.element.find(".e-cardselection");
            this.KanbanEdit.deleteCard(selected.attr("id"));
        }

       }
      </script>
     <script id="Delete" type="text/template">
       <a class="e-customdelete  e-icon" />
     </script>
     <style type="text/css" class="cssStyles">
       .e-customdelete:before {
          content: "\e800";
          line-height: 26px;
          min-height: 26px;
          min-width: 14px;
          display: inline-block;
       }
     </style>
 
{% endhighlight  %}

Also when you use `UrlAdaptor`, you need to return the data as JSON and the JSON object must contain a properties result & count. The `result` holds the `dataSource` as its value and `count` holds the total cards count as its value.

The following code example describes the above behavior.

{% highlight c# %}

    public ActionResult GetData(Syncfusion.JavaScript.DataManager value)
       {
           var DataSource = db.Tasks.ToList();
           DataResult result1 = new DataResult();
           DataOperations operation = new DataOperations();
           result1.result = DataSource;
           result1.count = DataSource.AsQueryable().Count();
           if (value.Skip > 0)
               result1.result = operation.PerformSkip(result1.result, value.Skip);
           if (value.Take > 0)
               result1.result = operation.PerformTake(result1.result, value.Take);
           return Json(result1, JsonRequestBehavior.AllowGet);
       }
    public class DataResult
    {
        public IEnumerable result { get; set; }
        public int count { get; set; }
    }
         
{% endhighlight  %}

{% endtabs %} 

Please refer to the below screenshot.

![URL adaptor in ASP NET MVC kanban control](Editing_images/editing_img6.png)

Using `DataOperations` helper class you can perform Kanban action at server side. The in-built methods that we have provided in the `DataOperations` class are listed below.

1.	PerformTake
2.	PerformSelect
3.	Execute

### Accessing CRUD action request details in server side

The Server-Side function must be declared with the following parameter name for each editing functionality.

#### Parameters Table

<table>
<tr>
<th>Action</th>
<th>Parameter Name</th>
<th>Example</th>
</tr>
<tr>
<td>
Update, Insert, Remove, Crud Update(Multiple cards data will be passed to the server when drag and drop enabled with priority.)
</td>
<td>
Changed values,
Added values,
Deleted value
</td>
<td>
public ActionResult Crud(List<Task> `changed`, List<Task> `added`, List<Task> `deleted`)
</td>
</tr>
</table>

### Insert Card

Using `CrudURL` property, you can specify the controller action mapping URL to perform `insert` operation at server side.

The following code example describes the above behavior.

{% highlight c# %}

    public ActionResult Crud(List<Task> changed, List<Task> `added`, List<Task> deleted)
        {
            // Insert card in the database.
            if (added != null && added.Count() > 0)
            {
                foreach (var temp in added)
                {
                    db.Tasks.Add(temp);
                }
            }
            db.SaveChanges();
            var data = db.Tasks.ToList();
            return Json(data, JsonRequestBehavior.AllowGet);
        }

{% endhighlight %}

The newly added card details are bound to the `added` parameter. Please refer the below image.

![Insert card in ASP NET MVC kanban control](Editing_images/editing_img7.png)

### Update Card

Using `CrudURL` property, you can specify the controller action mapping URL to perform `save/update` operation at server side. 

The following code example describes the above behavior.

{% highlight  c# %}

        public ActionResult Crud(List<Task> `changed`, List<Task> added, List<Task> deleted)
        {
            //Update card in the database.
            if (changed != null && changed.Count() > 0)
            {
                foreach (var temp in changed)
                {
                    Task old = db.Tasks.Where(o => o.Id == temp.Id).SingleOrDefault();
                    if (old != null)
                    {
                        db.Entry(old).CurrentValues.SetValues(temp);
                    }
                }
            }
            
            db.SaveChanges();
            var data = db.Tasks.ToList();
            return Json(data, JsonRequestBehavior.AllowGet);
        }

{% endhighlight %}

The updated card details are bound to the `changed` parameter. Please refer the below image.

![Update card in ASP NET MVC kanban control](Editing_images/editing_img8.png)

### Delete Card

Using `CrudURL` property, you can specify the controller action mapping URL to perform `delete`  operation at server side.

The following code example describes the above behavior.

{% highlight c# %}

    public ActionResult Crud(List<Task> changed, List<Task> added, List<Task> deleted)
        {
            //Delete card in the database.
            if (deleted != null && deleted.Count() > 0)
            {
                foreach (var temp in deleted)
                {
                    db.Tasks.Remove(db.Tasks.Where(o => o.Id == temp.Id).SingleOrDefault());
                }
            }

            db.SaveChanges();
            var data = db.Tasks.ToList();
            return Json(data, JsonRequestBehavior.AllowGet);
        }

{% endhighlight %}

The deleted card details are bound to the `deleted` parameter. Please refer the below image.

![Delete card in ASP NET MVC kanban control](Editing_images/editing_img9.png)








