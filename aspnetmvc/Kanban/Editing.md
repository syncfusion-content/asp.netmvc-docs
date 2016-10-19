---
layout: post
title: Editing | Kanban | ASP.NET MVC | Syncfusion
description: Editing
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

![](Editing_images/editing_img1.png)

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

![](Editing_images/editing_img2.png)

### Dialog Template Form

You can edit any of the fields pertaining to a single card of data and apply it to a template so that the same format is applied to all the other cards that you may edit later. 

Using this template support, you can edit the fields that are not bound to `EditItems`.

To edit the cards using Dialog template form, set `EditMode` as `DialogTemplate` and specify the template id to `DialogTemplate` property of `EditSettings`.

N> 1. `value` attribute is used to bind the corresponding field value while editing.
N> 2. `name` attribute is used to get the changed field values while save the edited card.
N> 3. For `EditMode` property you can assign either `string` value (“DialogTemplate”) or `enum` value (`ej.Kanban.EditMode.DialogTemplate`).

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
                                        <option value="Nancy Davloio">Nancy Davloio</option>
                                        <option value="Andrew Fuller">Andrew Fuller</option>
                                        <option value="Janet Leverling">Janet Leverling</option>
                                        <option value="Margaret hamilt">Margaret hamilt</option>
                                        <option value="Steven walker">Steven walker</option>
                                        <option value="Michael Suyama">Michael Suyama</option>
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

![](Editing_images/editing_img3.png)

### External Form

Set the `EditMode` as `externalform` to open the edit form in outside kanban content.

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

![](Editing_images/editing_img11.png)

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

![](Editing_images/editing_img12.png)

### External Template Form

You can edit any of the fields pertaining to a single card of data and apply it to a template so that the same format is applied to all the other cards that you may edit later. 

Using this template support, you can edit the fields that are not bound to Kanban Edit Items.

To edit the cards using External template form, set `EditMode` as `externalformtemplate` and specify the template id to `ExternalFormTemplate` property of `EditSettings`.

While using template, you can change the elements that are defined in the template, to appropriate Syncfusion JS controls based on the column type. This can be achieved by using `ActionComplete` event of Kanban.

N> 1. `value` attribute is used to bind the corresponding field value while editing. 
N> 2. `name` attribute is used to get the changed field values while save the edited card. 
N> 3. For `EditMode` property you can assign either `string` value ("externalformtemplate") or `enum` value (`ej.Kanban.EditMode.ExternalFormTemplate`).

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
                                        <option value="Nancy Davloio">Nancy Davloio</option>
                                        <option value="Andrew Fuller">Andrew Fuller</option>
                                        <option value="Janet Leverling">Janet Leverling</option>
                                        <option value="Margaret hamilt">Margaret hamilt</option>
                                        <option value="Steven walker">Steven walker</option>
                                        <option value="Michael Suyama">Michael Suyama</option>
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
                .DialogTemplate("#template");
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

![](Editing_images/editing_img13.png)


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

![](Editing_images/editing_img4.png)

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

![](Editing_images/editing_img5.png)

## Persisting data in server

Edited data can be persisted in database using RESTful web services.

All the CRUD operations in Kanban are done through DataManager. DataManager have an option to bind all the CRUD related data in server side. Please refer the [`link`](https://help.syncfusion.com/js/datamanager/overview) to know about the DataManager.

### URL Adaptor

You can use the `UrlAdaptor` of `DataManger` when binding `dataSource` from remote data. At initial load of Kanban, using URL property of DataManager, data are fetched from remote data and bound to Kanban. You can map CRUD operation in Kanban to Server-Side Controller action using the properties `InsertURL`, `RemoveURL`, `UpdateURL` and `CrudURL`.

The following code example describes the above behavior.

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
     .DataSource(ds => ds.URL("Home/DataSource").InsertURL("Home/Insert").UpdateURL("Home/Update").RemoveURL("Home/Remove").Adaptor(AdaptorType.UrlAdaptor))
     .Columns(col =>
     {
         col.HeaderText("Backlog").Key("Open").Add();
         col.HeaderText("In Progress").Key("InProgress").Add();
         col.HeaderText("Done").Key("Close").Add();
     })
     .EditSettings(edit =>
     {
         edit.AllowAdding(true)
             .AllowEditing(true)
             .EditItems(e =>
             {
                 e.Field("Id").Add();
                 e.Field("Status").Add();
                 e.Field("Estimate").Add();
                 e.Field("Text").Add();
             }).EditMode(KanbanEditMode.Dialog);
     })
     .KeyField("Status")
     .Fields(field =>
     {
         field.Content("Text")
             .PrimaryKey("Id");
     })

    )

{% endhighlight  %}

Also when you use `UrlAdaptor`, you need to return the data as JSON and the JSON object must contain a properties result & count. The`result` holds the `dataSource` as its value and `count` holds the total cards count as its value.

The following code example describes the above behavior.

{% highlight c# %}

    public ActionResult DataSource(DataManager dm)
            {
                IEnumerable DataSource = OrderRepository.GetAllRecords();
                DataResult result = new DataResult();
                DataOperations operation = new DataOperations();
                result1.result = DataSource;
                result1.count = DataSource.AsQueryable().Count();
                if (dm.Take > 0)
                    result1.result = operation.PerformTake(result1.result, dm.Take);
                if (dm.Select != null)
                    return Json(result1.result, JsonRequestBehavior.AllowGet);
                return Json(result1, JsonRequestBehavior.AllowGet);       
            }
            public class DataResult
            {
                public IEnumerable result { get; set; }
                public int count { get; set; }
            }

              
{% endhighlight  %}

Please refer to the below screenshot.

![](Editing_images/editing_img6.png)

Using ‘DataOperations’ helper class you can perform Kanban action at server side. The in-built methods that we have provided in the DataOperations class are listed below.

1.	PerformTake
2.	PerformSelect
3.	Execute

### Accessing CRUD action request details in server side

The `Server-Side` function must be declared with the following parameter name for each editing functionality.

#### Parameters Table

<table>
<tr>
<th>
Action</th><th>
Parameter Name</th><th>
Example</th></tr>
<tr>
<td>
Update, Insert</td><td>value</td>
<td>
public ActionResult Insert(TaskList value){ }, 

public ActionResult Update(TaskList value){ } 
</td>
</tr>
<tr>
<td>
Remove</td><td>key</td>
<td>
public ActionResult Remove(int key){ } 
</td>
</tr>
<tr>
<td>
Crud Update, Crud Remove, Crud Insert </td><td>value, action </td>
<td>
public ActionResult CrudUrl(TaskList value, string action){ } 
</td>
</tr>
</table>

### Insert Card

Using `InsertURL` property, you can specify the controller action mapping URL to perform `insert` operation at server side.

The following code example describes the above behavior.

{% highlight c# %}

    public ActionResult Insert(TaskList value)
    {
        //Insert card in database
    }

{% endhighlight %}

The newly added card details are bound to the `value` parameter. Please refer the below image.

![](Editing_images/editing_img7.png)

### Update Card

Using `UpdateURL` property, you can specify the controller action mapping URL to perform `save/update` operation at server side.
The following code example describes the above behavior.


{% highlight  c# %}

    public ActionResult Update(TaskList value)
    {
        //Update card in database
    }

{% endhighlight %}

The updated card details are bound to the `value` parameter. Please refer the below image.

![](Editing_images/editing_img8.png)

### Delete Card

Using `RemoveURL` property, you can specify the controller action mapping URL to perform `delete` operation at server side.

The following code example describes the above behavior.

{% highlight c# %}

    public ActionResult Remove(int key)
            {
                //Delete record in database
            }

{% endhighlight %}

The deleted card primary key value is bound to the `key` parameter. Please refer the below image.

![](Editing_images/editing_img9.png)

### CRUD URL

Instead of specifying separate controller action method for CRUD (insert, update and delete) operation, using `CrudURL` property you can specify the controller action mapping URL to perform all the CRUD operation at server side using single method.

The action parameter of `CrudURL` is used to get the corresponding CRUD action.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @(Html.EJ().Kanban("Kanban")
        .DataSource(ds => ds.URL("Home/DataSource").CrudURL("Home/CrudUpdate").Adaptor(AdaptorType.UrlAdaptor))
        .Columns(col =>
        {
            col.HeaderText("Backlog").Key("Open").Add();
            col.HeaderText("In Progress").Key("InProgress").Add();
            col.HeaderText("Done").Key("Close").Add();
        })
        .ContextMenuSettings(con=>con.Enable(true))
        .EditSettings(edit =>
        {
            edit.AllowAdding(true)
                .AllowEditing(true)
                .EditItems(e =>
                {
                    e.Field("Id").Add();
                    e.Field("Status").Add();
                    e.Field("Estimate").Add();
                    e.Field("Text").Add();
                }).EditMode(KanbanEditMode.Dialog);
        })
        .KeyField("Status")
        .Fields(field =>
        {
            field.Content("Text")
                .PrimaryKey("Id");
        })

    )

  
{% endhighlight  %}
{% highlight c# %}

    public ActionResult CrudUpdate(TaskList value, string action,int key)
            {
                if (action == "update")
                {
                    //Update record in database
                    OrderRepository.Update(value); 
                    var data = OrderRepository.GetAllRecords(); 
                    return Json(data, JsonRequestBehavior.AllowGet);
                }
                if (action == "insert")
                {
                    //Insert record in database
                    OrderRepository.Add(value); 
                    var data = OrderRepository.GetAllRecords(); 
                    return Json(data, JsonRequestBehavior.AllowGet);
                }

                if (action == "remove")
                {
                    //Delete record in database
                    OrderRepository.Delete(key);
                    var data = OrderRepository.GetAllRecords();
                    return Json(data, JsonRequestBehavior.AllowGet);
                }
                else
                {
                    var data = OrderRepository.GetAllRecords(); 
                    return Json(data, JsonRequestBehavior.AllowGet);
                }
    }
              
{% endhighlight  %}

{% endtabs %}  

Please refer the below image to know about the action parameter

![](Editing_images/editing_img10.png)
	
N> If you specify `InsertURL` along with `CrudURL` then while adding `InsertURL` only called.









