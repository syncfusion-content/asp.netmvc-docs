---
title: Export, import and print the Schedule with its appointments	
description: Export-Import/Print the complete Scheduler or specific appointment alone
platform: ejmvc
control: schedule
documentation: ug
keywords: export, import and print 
---
# Export and Print

## Export Appointments to ICS file

The Appointments can be exported as a whole collection or else a single appointment alone can be exported from the Scheduler. By default, the appointments are exported to .ics format which can then be imported and used in any of the other external calendars.

### Single Appointment Exporting

A single appointment can be exported by making use of its Id. You can achieve this functionality by making use of a client-side `exportSchedule` method by passing the id of an appointment to export as one of its parameter. 

It can also be achieved in another way by enabling the context menu settings and then adding a custom menu option for export appointment functionality. When right clicked on an appointment, and **export Appointment** option is chosen, the exporting functionality can be handled through the `MenuItemClick` event, within which the `exportSchedule` method should be defined with the following parameters,

* Action name (to be called in the server-side)
* Server Event (optional)
* Appointment Id (mandatory for single Appointment exporting)

The following code example shows the way to export single appointment from the Scheduler.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- List of Appointment Menu options -->
    List<Appointment> AppMenu = new List<Appointment>();
    AppMenu.Add(new Appointment { Id = "open", Text = "Open Appointment" });
    AppMenu.Add(new Appointment { Id = "delete", Text = "Delete Appointment" });
    AppMenu.Add(new Appointment { Id = "export", Text = "Export Appointment" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .ContextMenuSettings(cxt => cxt.Enable(true).MenuItems(items => items.Appointment(AppMenu)))
        .ScheduleClientSideEvents(evt => evt.MenuItemClick("onMenuItemClick"))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

{% highlight js %}

function onMenuItemClick(args) {
    if (args.events.ID == "export") {
        var obj = $("#Schedule1").data("ejSchedule");
        obj.exportSchedule("ExportToICS", null, args.targetInfo.Id);
    }
}

{% endhighlight %}

N> The Id value of the appointment passed in the above code example can be retrieved in the server-side action through Request.Form["AppointmentId"], as the id passed from the script is stored as hidden value in the input field of the form under this name internally.

### Exporting all Appointments

To export the entire appointments, the same `exportSchedule` method can be used without passing the id value to its parameter list. To achieve this, keep an individual button to export, and when it is clicked - the Scheduler can be allowed to export all the appointments.

The following code example depicts the way to export all the Scheduler appointments as a whole.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

@(Html.EJ().Button("export").Text("Export").ClientSideEvents(evt => evt.Click("onClick")))


{% endhighlight %}

{% highlight js %}

function onClick() {
    var obj = $("#Schedule1").data("ejSchedule");
    obj.exportSchedule("ExportToICS", null, null);
}

{% endhighlight %}

The server-side action **ExportToICS** contains the following code example to export the Scheduler appointments.

{% highlight c# %}

public void ExportToICS(FormCollection form)
{
	IEnumerable data;
	string JSONModel = Request.Form["ScheduleModel"];
	var model = JsonConvert.DeserializeObject<Dictionary<string, object>>(JSONModel);
	var Id = Request.Form["AppointmentId"];
	if(Id != null)
		// To export single appointment
		data = db.DefaultSchedules.Where(app => app.Id.ToString() == Id.ToString()).ToList();
	else
		// To export all the appointments
		data = db.DefaultSchedules.ToList();
	ScheduleExport obj = new ScheduleExport(model, data);
}

{% endhighlight %}

## PDF Export

Scheduler supports to export the entire schedule control along with its appointments in PDF format, for which the same [exportSchedule](/js/api/ejschedule#methods:exportschedule) method can be used without passing any id value to its parameter list. To achieve this, keep an individual button to export and when it is clicked, the Scheduler with appointments can be allowed to export as PDF.

The following code example depicts the way to export the Scheduler with appointments in PDF format.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
    .Width("100%")
    .Height("525px")
    .CurrentDate(new DateTime(2015, 11, 5))
    .AppointmentSettings(fields => fields.Datasource(Model)
        .Id("Id")
        .Subject("Subject")
        .StartTime("StartTime")
        .EndTime("EndTime")
        .Description("Description")
        .AllDay("AllDay")
        .Recurrence("Recurrence"))
)
@Html.EJ().Button("submit").Text("Export").Width("80px").Height("30px").ClientSideEvents(cli => cli.Click("onPDFExport"))

{% endhighlight %}

{% highlight js %}

function onPDFExport(args) {
    var obj = $("#Schedule1").data("ejSchedule");
    obj.exportSchedule("ExportAsPDF", null, null);
}

{% endhighlight %}

The server-side action **ExportAsPDF** contains the following code example to export the Scheduler.

{% highlight c# %}

public ActionResult ExportAsPDF(string scheduleModel)
{
    JavaScriptSerializer serializer = new JavaScriptSerializer();
    SchedulePDFExport convert = new SchedulePDFExport();
    // Here calling the public method to convert the model values to ScheduleProperties type from string type
    ScheduleProperties scheduleObject = convert.ScheduleSerializeModel(Request.Form["ScheduleModel"]);
    // Here converting the schedule appointments data into enumerable object by deserializing
    IEnumerable scheduleAppointments = (IEnumerable)serializer.Deserialize(Request.Form["ScheduleProcesedApps"], typeof(IEnumerable));
    PdfExport exp = new PdfExport();
    PdfPageSettings pageSettings = new PdfPageSettings(50f);
    pageSettings.Orientation= PdfPageOrientation.Landscape;
    // Here passing the theme values from enum collection
    PdfDocument document = exp.Export(scheduleObject, scheduleAppointments, ExportTheme.FlatSaffron, Request.Form["locale"], pageSettings);
    document.Save("Schedule.pdf", HttpContext.ApplicationInstance.Response, HttpReadType.Save);
    return RedirectToAction("PDFExportController");
}

{% endhighlight %}

N> To pass the theme value as a string instead of the enum value, refer to the following code example of passing the string type theme value.
{% highlight c# %}
    PdfDocument document = exp.Export(scheduleObject, scheduleAppointments, "flat-saffron",Request.Form["locale"]);
{% endhighlight %}

### Setting Page Options:

It is possible to set/change the Pdf page settings such as size, margins (left, right, top and bottom), transition, and rotate angle and header/footer values by passing the page settings and page document template object values into the export method. 

#### Page Settings:

You can set/apply the following page property values to the PDF file before exporting it with the Scheduler by using the `PdfPageSettings` object. 
a)	Page Size
b)	Orientation
c)	Margins ( Left, Right, Top, Bottom)
d)	Transition ( Direction, Dimension, Duration, Motion, PageDuration, Scale, Style)
e)	Rotate ( RotateAngle0, RotateAngle90, RotateAngle180, RotateAngle270)
f)	Height
g)	Width

To apply the above page setting values, you need to create an object for the `PdfPageSettings` class. Then, you can assign the values to the available properties within it such as Size = PdfPageSize.A3, Orientation = PdfPageOrientation.Landscape and so on. Once done, pass this object into the export method which will set these page settings values to the PDF file before exporting it. Refer to the following code example (server-side) to set/change the page settings values.

{% highlight c# %}
    public ActionResult ExportAsPDF(string scheduleModel)
        {

            JavaScriptSerializer serializer = new JavaScriptSerializer();
            SchedulePDFExport convert= new SchedulePDFExport();
            ScheduleProperties scheduleObject = convert.ScheduleSerializeModel(scheduleModel); // Here calling the public method to convert the model values to ScheduleProperties type from string type

            IEnumerable scheduleAppointments = (IEnumerable)serializer.Deserialize(Request.Form["ScheduleProcesedApps"], typeof(IEnumerable)); // Here deserialize the appointments to enumerable object

            PdfExport exp = new PdfExport();

            // Here the 50f is the default value for the margins. If you are not assigning any separate values like Margins.Left = 15 means 50f value will be setting to all the Margin properties.
            PdfPageSettings pageSettings = new PdfPageSettings(50f);  

            // Here you can assign the PdfPageSize enum value (ex: A3, A4)
            pageSettings.Size = PdfPageSize.A3;  

            // Here Landscape value assigned to the orientation. You can set either Landscape/Portrait for this Orientation property
            pageSettings.Orientation = PdfPageOrientation.Landscape; 

            // Here assigned different values for the margins 
            pageSettings.Margins.Left = 15;

            pageSettings.Margins.Right = 15;

            pageSettings.Margins.Top = 20;

            pageSettings.Margins.Bottom = 20;

            // Here assigned the Transition Direction as BottomToTop. You can also set any of the Transition values to this property

            pageSettings.Transition.Direction= PdfTransitionDirection.BottomToTop;

            // Here assigned the Rotate Angle as RotateAngle180. You can also set any of the Rotate values to this property
            pageSettings.Rotate = PdfPageRotateAngle.RotateAngle180;

            // Here passing the page settings object value into the export method.

            PdfDocument document = exp.Export(scheduleObject, scheduleAppointments, ExportTheme.FlatSaffron, Request.Form["locale"], pageSettings);
            document.Save("Schedule.pdf", HttpContext.ApplicationInstance.Response, HttpReadType.Save);
            return RedirectToAction("PDFExportController");
        }
{% endhighlight %}

#### Header/Footer Settings:

You can also set the header and footer options to the PDF page before it is being exported, by passing the `PDFDocumentTemplate` object values as mentioned in the following code example. 

{% highlight c# %}
    public ActionResult ExportAsPDF(string scheduleModel)
        {
            JavaScriptSerializer serializer = new JavaScriptSerializer();
            SchedulePDFExport convert= new SchedulePDFExport();
            ScheduleProperties scheduleObject = convert.ScheduleSerializeModel(scheduleModel); // Here calling the public method to convert the model values to ScheduleProperties type from string type

            IEnumerable scheduleAppointments = (IEnumerable)serializer.Deserialize(Request.Form["ScheduleProcesedApps"], typeof(IEnumerable)); // Here deserialize the appointments to enumerable object
            PdfExport exp = new PdfExport();
            PdfDocument document = new PdfDocument();
            PdfPage pdfPage = document.Pages.Add();

            //Create a header and draw the string.
            // Here the bounds value is used to store the position/axis value, where the header and footer content to be displayed
            RectangleF bounds = new RectangleF(0, 0, document.Pages[0].GetClientSize().Width, 50);

            // Creating object for the PdfPageTemplateElement
            PdfPageTemplateElement header = new PdfPageTemplateElement(bounds);

            // Here setting the font style and color to display the header/footer content

            PdfSolidBrush brush = new PdfSolidBrush(Color.Gray);

            PdfFont font = new PdfStandardFont(PdfFontFamily.Helvetica, 6, PdfFontStyle.Bold);

            PdfStringFormat format = new PdfStringFormat();

            format.Alignment = PdfTextAlignment.Center;

            format.LineAlignment = PdfVerticalAlignment.Middle;

            header.Graphics.DrawString("Schedule", font, brush, new RectangleF(0, 18, header.Width, header.Height), format);

            //Create a Page template that can be used as footer (here creating template to display the page number).
            PdfPageTemplateElement footer = new PdfPageTemplateElement(bounds);

            //Create page number field.
            PdfPageNumberField pageNumber = new PdfPageNumberField(font, brush);

            //Create page count field.
            PdfPageCountField count = new PdfPageCountField(font, brush);

            //Add the fields in composite fields.
            PdfCompositeField compositeField = new PdfCompositeField(font, brush, "Page {0} of {1}", pageNumber, count);

            compositeField.Bounds = footer.Bounds;

            //Draw the composite field in footer.
            compositeField.Draw(footer.Graphics, new PointF(470, 40));

            PdfDocumentTemplate headerFooterTemplate = new PdfDocumentTemplate();
            
            //Here assigning the header template value to the PdfDocumentTemplate Object.
            headerFooterTemplate.Top = header; 

            //Here assigning the footer template value to the PdfDocumentTemplate Object.
            headerFooterTemplate.Bottom = footer;

            //Here passing the PdfDocumentTemplate Object value into the export method.

            document = exp.Export(scheduleObject, scheduleAppointments, ExportTheme.FlatSaffron, Request.Form["locale"], headerFooterTemplate);

            document.Save("Schedule.pdf", HttpContext.ApplicationInstance.Response, HttpReadType.Save);

            return RedirectToAction("PDFExportController");
        }

{% endhighlight %}

N>The header and footer values can be passed to the PDF file only through the template option. In the above mentioned code example, the template has been written with the text “Schedule” to display it as the header text and the page number (ex: Page 1 of 2) has been displayed in the footer part. 

It is also possible to pass both the `PageSettings` and header/footer template objects in the export method altogether to apply the page settings as well as the header and footer options to the PDF file which can be referred from the following code example,

{% highlight c# %}
        public ActionResult ExportAsPDF(string scheduleModel)
        {
            //Here add the code example of both the page settings and header/footer values settings.
            
            //Then pass both PdfPageSettings and PdfDocumentTemplate object into the export method.            
            
            document = exp.Export(scheduleObject, scheduleAppointments, ExportTheme.FlatSaffron, Request.Form["locale"], pageSettings, headerFooterTemplate);
            document.Save("Schedule.pdf", HttpContext.ApplicationInstance.Response, HttpReadType.Save);
            return RedirectToAction("PDFExportController");
        }

{% endhighlight %}

## Print

Two types of Print options are available – either to print the entire Scheduler layout including all the appointments in it or else to print any particular appointment alone. The public method `Print` is used to print the entire Scheduler.

### Print the Scheduler

The following code example shows the way to print the entire Scheduler, by keeping an extra button in a page – on which clicking the button will print the entire Scheduler.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

@Html.EJ().Button("print").Text("Print").ClientSideEvents(evt => evt.Click("onClick"))


{% endhighlight %}

{% highlight js %}

function onClick(args) {
    var obj = $("#Schedule1").data("ejSchedule");
    obj.print();
}

{% endhighlight %}

### Printing specific appointments

To print a particular appointment, the context menu **print** option can be used. The print option is handled internally by default, so that when an appointment is right clicked – choosing print option from the context menu that pops-out will automatically print that appointment.

N> To handle this functionality, the context menu settings needs to be enabled with print option added to the appointment items.

The following code example depicts the way to print a particular appointment.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{ 
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- List of Appointment Menu options -->
    List<Appointment> AppMenu = new List<Appointment>();
    AppMenu.Add(new Appointment { Id = "open", Text = "Open Appointment" });
    AppMenu.Add(new Appointment { Id = "delete", Text = "Delete Appointment" });
    AppMenu.Add(new Appointment { Id = "print", Text = "Print Appointment" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .ContextMenuSettings(cxt => cxt.Enable(true).MenuItems(items => items.Appointment(AppMenu)))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .Description("Description")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

## Import Appointments

To import appointments into the Scheduler, server-side method `renderingImportAppointments` can be used, which returns the appointments retrieved from the specified file path.

To Import appointments into the Scheduler, refer the following code example.

{% highlight razor %}

@Html.EJ().Button("submit").Text("Submit").ClientSideEvents(evt => evt.Click("ScheduleImport"))
@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2014, 6, 2))
        .AppointmentSettings(fields => fields
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)


{% endhighlight %}

{% highlight js %}

    function ScheduleImport() {
        var dataManger = ej.DataManager({ url: '@Url.Action("ScheduleImportData", "Schedule")', crossDomain: true });
        $("#Schedule1").ejSchedule({
            appointmentSettings: {
                dataSource: dataManger
            }
        });
    }

{% endhighlight %}

The server-side action `ScheduleImportData` contains the following code example to import the Scheduler appointments.

{% highlight c# %}

public JsonResult ScheduleImportData() {
    var destinationPath = @"Filepath\iCalender.ics";
    ScheduleImport importApps = new ScheduleImport();
    var app = importApps.renderingImportAppointments(destinationPath);
    int intMax = app.Max(a => a.Id);
    List<ScheduleAppointmentsObjData> result = new List<ScheduleAppointmentsObjData>();
    for (var i = 0; i < app.Count; i++) {
        app[i].Id = intMax + 1;
        ScheduleAppointmentsObjData row = new ScheduleAppointmentsObjData(app[i].Id, app[i].Subject, app[i].Location, app[i].StartTime, app[i].EndTime, app[i].Description, null, null, app[i].Recurrence, null, null, app[i].AppointmentCategorize, null, app[i].AllDay, null, null, app[i].RecurrenceRules, null, null);
        result.Add(row);
        intMax = app[i].Id;
    }
    return Json(result, JsonRequestBehavior.AllowGet);
}

{% endhighlight %}