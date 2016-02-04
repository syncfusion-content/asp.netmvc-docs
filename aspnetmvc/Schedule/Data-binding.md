---
title: Data binding with Schedule	
description: Binding local and remote data to Scheduler
platform: ejmvc
control: schedule
documentation: ug
keywords: data binding, local data, remote data 
---
# Data Binding

## Appointment Fields

The below listed names are the appointment fields which holds the appropriate column names from the dataSource.

<table>
<tr>
<th>
Field name<br/><br/></th><th>
Description<br/><br/></th></tr>
<tr>
<td>
Id<br/><br/></td><td>
Binds the <b>Id</b> field name for indexing and performing CRUD operation on the appointments. It’s optional.<br/><br/></td></tr>
<tr>
<td>
StartTime<br/><br/></td><td>
Binds the appointment start time field name which is <b>mandatory</b>.<br/><br/></td></tr>
<tr>
<td>
StartTimeZone<br/><br/></td><td>
Binds the name of the start timezone field in the dataSource. If the <b>StartTimeZone</b> field is not mentioned, then the appointment makes use of the Scheduler timeZone or System timeZone.<br/><br/></td></tr>
<tr>
<td>
SndTime<br/><br/></td><td>
Binds the appointment end time field name which is <b>mandatory</b>.<br/><br/></td></tr>
<tr>
<td>
EndTimeZone<br/><br/></td><td>
Binds the name of the end timezone field in the dataSource. If the <b>EndTimeZone</b> field is not mentioned, then the appointment makes use of the Scheduler timeZone or System timeZone.<br/><br/></td></tr>
<tr>
<td>
Subject<br/><br/></td><td>
Binds the appointment subject field name which holds the summary of the appointment. <br/><br/></td></tr>
<tr>
<td>
Location<br/><br/></td><td>
Binds the name of the location field. It indicates the appointment location/occurrence place. This field needs to be bind to the Scheduler, when an API <b>ShowLocationField</b> is set to true.<br/><br/></td></tr>
<tr>
<td>
Description<br/><br/></td><td>
Binds the appointment description field name.<br/><br/></td></tr>
<tr>
<td>
AllDay<br/><br/></td><td>
Binds the name of the allDay field. It accepts the <b>boolean</b> value and indicates whether the appointment is an allday appointment or not.<br/><br/></td></tr>
<tr>
<td>
Categorize<br/><br/></td><td>
Binds the name of the categorize field. It indicates the category or status value (red categorize, green, yellow and so on). <br/><br/></td></tr>
<tr>
<td>
Priority<br/><br/></td><td>
Binds the name of the priority field and indicates the priority (high, low, medium and none) of the appointments. This field should be bind to the Scheduler, when <b>PrioritySettings.Enable</b> is set to true.<br/><br/></td></tr>
<tr>
<td>
ResourceFields<br/><br/></td><td>
Binds one or more fields in the resource collection. It maps the resource field names with the appointments, denoting to which resource the appointments actually belongs.<br/><br/></td></tr>
<tr>
<td>
Recurrence<br/><br/></td><td>
Binds the name of the recurrence field. It accepts the <b>boolean</b> value and indicates whether the appointment is a recurrence appointment or not.<br/><br/></td></tr>
<tr>
<td>
RecurrenceRule<br/><br/></td><td>
Binds the name of the recurrenceRule field. It holds the recurrence pattern associated with the appointments.<br/><br/></td></tr>
<tr>
<td>
RecurrenceId<br/><br/></td><td>
Binds the recurrence Id field which acts as a parent id for Scheduler recurrence appointments.<br/><br/></td></tr>
<tr>
<td>
RecurrenceExDate<br/><br/></td><td>
Binds the recurrence Exception field which accepts the recurrence Exception date values.<br/><br/></td></tr>
</table>

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{ 
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", AllDay = false, StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Recurrence = false, RecurrenceRule = "", Priority = "high", Categorize = "1", StartTimeZone = "UTC +05:00", EndTimeZone = "UTC +05:00", Location = "US", Description = "Never Giveup on Obstacles", RecurrenceId = "1", RecurrenceExDate = "", ResourceFields = "1" });
    
    <!-- Datasource for Grouping Resources -->
    List<String> Group = new List<String>();
    Group.Add("Owners");
    
    <!-- Datasource for Resources -->
    List<ResourceFields> Resources = new List<ResourceFields>();
    Resources.Add(new ResourceFields { Id = "1", Text = "Nancy", Color = "#f8a398" });
    Resources.Add(new ResourceFields { Id = "3", Text = "Steven", Color = "#56ca85" });
    Resources.Add(new ResourceFields { Id = "5", Text = "Michael", Color = "#51a0ed" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .Group(gr => { gr.Resources(Group); })
        .Resources(res => {
            res.Field("OwnerId").Title("Owner").Name("Owners").AllowMultiple(true).ResourceSettings(flds => flds.Datasource(Resources).Text("Text").Id("Id").Color("Color")).Add();
        })
        .ShowLocationField(true)
        .CategorizeSettings(cat => cat.Enable(true))
        .PrioritySettings(pri => pri.Enable(true))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .StartTimeZone("StartTimeZone")
            .EndTime("EndTime")
            .EndTimeZone("EndTimeZone")
            .Description("Description")
            .Location("Location")
            .AllDay("AllDay")
            .Priority("Priority")
            .Categorize("Categorize")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule")
            .RecurrenceId("RecurrenceId")
            .RecurrenceExDate("RecurrenceExDate")
            .ResourceFields("OwnerId"))
)

{% endhighlight %}


## Binding to Simple List Data Array

Scheduler supports binding the appointment data to it through the list of appointment object collection as depicted in the below code example.

**Example** - Array of List Data Binding

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
        .CurrentDate(new DateTime(2015, 11, 5))
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

## Binding Remote Data Service

The appointment data can be bound to the Scheduler through [Odata](http://www.odata.org) remote services, by configuring the service URL to the Schedule dataSource API.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .AppointmentSettings(fields => fields.Datasource("http://mvc.syncfusion.com/OdataServices/Northwnd.svc/").Query("ej.Query().from('Events').take(10)")
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

## OData V4

The OData v4 is an improved version of OData protocols. Scheduler supports retrieving and consuming appointment data from [OData v4](http://www.odata.org/documentation) services, just similar to the other remote services. 

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .EnableLoadOnDemand(true)
        .AppointmentSettings(fields => fields.Datasource(ds => ds.URL("http://services.odata.org/V4/Northwind/Northwind.svc/Orders/").Adaptor(AdaptorType.ODataV4Adaptor))
            .Id("Id")
            .Subject("ShipName")
            .StartTime("OrderDate")
            .EndTime("RequiredDate")
            .Description("ShipAddress"))
)

{% endhighlight %}

## WebAPI Binding

The appointment data can be bound to the Scheduler through Web API service which serves as a programmatic interface to define the request and response messaging system.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .AppointmentSettings(fields => fields.Datasource(ds => ds.URL("http://mvc.syncfusion.com/OdataServices/api/ScheduleData/").CrossDomain(true))
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

The server-side code to retrieve the appointments are as follows.

{% highlight c# %}

    // To retrieve the appointments from database and bind it to Scheduler
    public IEnumerable<Event> GetData(String CurrentDate, String CurrentView, String CurrentAction)
    {
        return new NORTHWNDEntities().Events.ToList();
    }

{% endhighlight %}

## Controller Action Binding with CRUD operation

Scheduler supports binding appointment data from the controller by using various available options of `DataSource` property like URL, BatchURL, InsertURL, UpdateURL, RemoveURL and Adaptor.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .AppointmentSettings(fields => fields.Datasource(ds => ds.URL("Home/GetData").BatchURL("Home/Crud").InsertURL("Home/add").UpdateURL("Home/update").RemoveURL("Home/remove").Adaptor(AdaptorType.UrlAdaptor))
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

The server-side controller code to handle the CRUD operations are as follows.

{% highlight c# %}

// To initially bind the appointments with Scheduler
public JsonResult GetData()
{
    // ScheduleDataDataContext is a LINQ-to-SQL data class name that is defined in the .dbml file to access the tables from the database 
    IEnumerable data = new ScheduleDataDataContext().Appointments.Take(100); 
    return Json(data, JsonRequestBehavior.AllowGet);
}

// Triggers while saving a new appointment through quick window
public JsonResult add(Appointment value)
{
    ScheduleDataDataContext db = new ScheduleDataDataContext();
    int intMax = db.Appointments.ToList().Count > 0 ? db.Appointments.ToList().Max(p => p.Id) : 1;
    Appointment appoint = new Appointment()
    {
        Id = intMax + 1,
        StartTime = value.StartTime,
        EndTime = value.EndTime,
        Subject = value.Subject,
        Description = value.Description,
        OwnerId = value.OwnerId,
        Recurrence = value.Recurrence,
        AllDay = value.AllDay,
        RecurrenceRule = value.RecurrenceRule
    };
    db.Appointments.InsertOnSubmit(appoint);
    db.SubmitChanges();
    return Json(appoint, JsonRequestBehavior.AllowGet);
}

// Triggers while editing/dragging/resizing the existing appointment
public JsonResult update(Appointment value)
{
    ScheduleDataDataContext db = new ScheduleDataDataContext();
    var filterData = db.Appointments.Where(c => c.Id == Convert.ToInt32(value.Id));
    Appointment appoint = db.Appointments.Single(A => A.Id == Convert.ToInt32(value.Id));
    if (filterData.Count() > 0)
    {
        DateTime startTime = Convert.ToDateTime(value.StartTime);
        DateTime endTime = Convert.ToDateTime(value.EndTime);
        appoint.StartTime = startTime;
        appoint.EndTime = endTime;
        appoint.Subject = value.Subject;
        appoint.Description = value.Description;
        appoint.OwnerId = value.OwnerId;
        appoint.Recurrence = Convert.ToByte(value.Recurrence);
        appoint.AllDay = value.AllDay;
        appoint.RecurrenceRule = value.RecurrenceRule;
    }
    db.SubmitChanges();
    return Json(appoint, JsonRequestBehavior.AllowGet);
}

// Triggers when an appointment is deleted
public JsonResult remove(string key)
{
    ScheduleDataDataContext db = new ScheduleDataDataContext();
    Appointment app = db.Appointments.Where(c => c.Id == Convert.ToInt32(key)).FirstOrDefault();
    if (app != null) db.Appointments.DeleteOnSubmit(app);
    db.SubmitChanges();
    return Json(app, JsonRequestBehavior.AllowGet);
}

// Triggers for any of the Scheduler CRUD operation
public JsonResult Crud(EditParams param)
{
    ScheduleDataDataContext db = new ScheduleDataDataContext();
    if (param.action == "insert" || (param.action == "batch" && param.added != null))  // this block of code will execute while inserting the appointments
    {
        var value = param.action == "insert" ? param.value : param.added[0];
        int intMax = db.Appointments.ToList().Count > 0 ? db.Appointments.ToList().Max(p => p.Id) : 1;
        DateTime startTime = Convert.ToDateTime(value.StartTime);
        DateTime endTime = Convert.ToDateTime(value.EndTime);
        Appointment appoint = new Appointment()
        {
            Id = intMax + 1,
            StartTime = startTime,
            EndTime = endTime,
            Subject = value.Subject,
            Description = value.Description,
            OwnerId = value.OwnerId,
            Recurrence = value.Recurrence,
            AllDay = value.AllDay,
            RecurrenceRule = value.RecurrenceRule
        };
        db.Appointments.InsertOnSubmit(appoint);
        db.SubmitChanges();
    }
    else if (param.action == "remove")  // this block of code will execute while removing the appointment
    {
        Appointment app = db.Appointments.Where(c => c.Id == Convert.ToInt32(param.key)).FirstOrDefault();
        if (app != null) db.Appointments.DeleteOnSubmit(app);
        db.SubmitChanges();
    }
    else if ((param.action == "batch" && param.changed != null) || param.action == "update")   // this block of code will execute while updating the appointment
    {
        var value = param.action == "update" ? param.value : param.changed[0];
        var filterData = db.Appointments.Where(c => c.Id == Convert.ToInt32(value.Id));
        if (filterData.Count() > 0)
        {
            DateTime startTime = Convert.ToDateTime(value.StartTime);
            DateTime endTime = Convert.ToDateTime(value.EndTime);
            Appointment appoint = db.Appointments.Single(A => A.Id == Convert.ToInt32(value.Id));
            appoint.StartTime = startTime;
            appoint.EndTime = endTime;
            appoint.Subject = value.Subject;
            appoint.Description = value.Description;
            appoint.OwnerId = value.OwnerId;
            appoint.Recurrence = Convert.ToByte(value.Recurrence);
            appoint.AllDay = value.AllDay;
            appoint.RecurrenceRule = value.RecurrenceRule;
        }
        db.SubmitChanges();
    }
    IEnumerable data = new ScheduleDataDataContext().Appointments.Take(500); 
    return Json(data, JsonRequestBehavior.AllowGet);
}

// Class definition for EditParams to be used as parameter in the above Crud method for receiving the object value in it.
public class EditParams
{
    public string key { get; set; }
    public string action { get; set; }
    public List<Appointment> added { get; set; }
    public List<Appointment> changed { get; set; }
    public Appointment value { get; set; }
}

{% endhighlight %}


## Loading Data on Demand

Scheduler supports load on demand concept by retrieving only the filtered appointment data (for the current Scheduler date range) from the service/database during **loading** **time**, and that too only for the current Scheduler view**.** There are 3 parameters made accessible on the server-side namely **CurrentDate**, **CurrentView** and **CurrentAction** through which only the necessary appointments are retrieved from the database and then assigned to the Scheduler dataSource. With this kind of action, Scheduler consumes only lesser data and also reduces the usage of network bandwidth size and loading time. 

The **EnableLoadOnDemand** property is used to enable or disable the load on demand functionality of the schedule.

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .EnableLoadOnDemand(true)
        .AppointmentSettings(fields => fields.Datasource(ds => ds.URL("http://mvc.syncfusion.com/OdataServices/api/ScheduleData/").CrossDomain(true))
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

The server-side code to load the Scheduler data on demand is as follows.

{% highlight c# %}

    // retrieve the appointments based on the current date.
    public IEnumerable<Event> GetData(String CurrentDate, String CurrentView, String CurrentAction)
    {
        var dateString = Regex.Match(CurrentDate.ToString(), @"^(\w+\b.*?){4}").ToString(); 
        string format = "ddd MMM dd yyyy"; 
        DateTime dateTimeValue;
        try
        {
            dateTimeValue = DateTime.ParseExact(dateString, format, CultureInfo.InvariantCulture);
        }
        catch(FormatException)
        {
            var dateSplit = CurrentDate.Split(' ');//For IE<=10 Fri Mar 20 11:00:22 UTC+0530 2015
            if (dateSplit[2].Length == 1) dateSplit[2] = string.Concat("0", dateSplit[2]);
            dateString = string.Concat(dateSplit[0], ' ', dateSplit[1], ' ', dateSplit[2], ' ', dateSplit[dateSplit.Length - 1]);
            dateTimeValue = DateTime.ParseExact(dateString, format, CultureInfo.InvariantCulture);
        }
    	// AppointmentReposit is a user-defined class within which the FilterAppointment method is defined. 
        AppointmentReposit rep = new AppointmentReposit();
        var data = rep.FilterAppointment(dateTimeValue, CurrentAction, CurrentView); 
        return data;
    }

    // Method to filter the appointments based on the date range
    public List<Event> FilterAppointment(DateTime CurrentDate, String CurrentAction, String CurrentView)
    {
        DateTime CurrDate = Convert.ToDateTime(CurrentDate);
        DateTime StartDate = FirstWeekDate(CurrDate.Date);
        DateTime EndDate = FirstWeekDate(CurrDate.Date);
        List<Event> appointmentList = new NORTHWNDEntities().Events.ToList();
        switch (CurrentView)
        {
            case "day":
                StartDate = CurrentDate;
                EndDate = CurrentDate;
                break;
            case "week":
                EndDate = EndDate.AddDays(7);
                break;
            case "workweek":
                EndDate = EndDate.AddDays(5);
                break;
            case "month":
                StartDate = CurrDate.Date.AddDays(-CurrDate.Day + 1);
                EndDate = StartDate.AddMonths(1);
                break;
        }
        appointmentList = new NORTHWNDEntities().Events.ToList().Where(app =>
        ((Convert.ToDateTime(app.StartTime).Date >= Convert.ToDateTime(StartDate.Date)) &&
        (Convert.ToDateTime(app.EndTime).Date <= Convert.ToDateTime(EndDate.Date)))).ToList();
        return appointmentList;
    }
    
    internal static DateTime FirstWeekDate(DateTime CurrentDate)
    {
        try
        {
            DateTime FirstDayOfWeek = CurrentDate;
            DayOfWeek WeekDay = FirstDayOfWeek.DayOfWeek;
            switch (WeekDay)
            {
                case DayOfWeek.Sunday:
                    break;
                case DayOfWeek.Monday:
                    FirstDayOfWeek = FirstDayOfWeek.AddDays(-1);
                    break;
                case DayOfWeek.Tuesday:
                    FirstDayOfWeek = FirstDayOfWeek.AddDays(-2);
                    break;
                case DayOfWeek.Wednesday:
                    FirstDayOfWeek = FirstDayOfWeek.AddDays(-3);
                    break;
                case DayOfWeek.Thursday:
                    FirstDayOfWeek = FirstDayOfWeek.AddDays(-4);
                    break;
                case DayOfWeek.Friday:
                    FirstDayOfWeek = FirstDayOfWeek.AddDays(-5);
                    break;
                case DayOfWeek.Saturday:
                    FirstDayOfWeek = FirstDayOfWeek.AddDays(-6);
                    break;
            }
            return (FirstDayOfWeek);
        }
        catch
        {
            return DateTime.Now;
        }
    }

{% endhighlight %}


## Entity Framework Data Binding

The appointment data can be bound to the Scheduler through entity framework which supports Entity Data Model(EDM) defining the data at conceptual level. To know more on how to create and use the entity data model, refer [here.](https://msdn.microsoft.com/en-us/library/bb399182%28v=vs.100%29.aspx)

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
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

{% highlight c# %}

        ScheduleControlDataEntities db = new ScheduleControlDataEntities(); // Create an object of the entity class to access its underlying tables within the controller page.
        public ActionResult Index()
        {
            return View();
        }

        public JsonResult GetData()
        {
            IEnumerable data = new ScheduleControlDataEntities().Appointments.Take(100);
            return Json(data, JsonRequestBehavior.AllowGet);
        }
        public JsonResult Batch(EditParams param)
        {
            // this block of code will execute while inserting the appointments
            if (param.action == "insert" || (param.action == "batch" && param.added != null)) 
            {
                var value = param.action == "insert" ? param.value : param.added[0];
                int intMax = db.Appointments.ToList().Count > 0 ? db.Appointments.ToList().Max(p => p.Id) : 1;
                DateTime startTime = Convert.ToDateTime(value.StartTime);
                DateTime endTime = Convert.ToDateTime(value.EndTime);
                var currentTimeZone = TimeZone.CurrentTimeZone;
                Appointment appoint = new Appointment()
                {
                    Id = value.Id,
                    StartTime = startTime,
                    EndTime = endTime,
                    StartTimeZone=value.StartTimeZone,
                    EndTimeZone=value.EndTimeZone,
                    Subject = value.Subject,                   
                    Description = value.Description,                    
                    Recurrence = value.Recurrence,
                    RoomId = value.RoomId,
                    OwnerId = value.OwnerId,
                    CategoryId = value.CategoryId,
                    AllDay = value.AllDay,                   
                    RecurrenceRule = value.RecurrenceRule,                   
                };
                db.Appointments.Add(appoint);
                db.SaveChanges();
            }
            if (param.action == "remove" || param.deleted != null) 
            // this block of code will execute while removing the appointment 
            {
                if (param.action == "remove")
                {
                    int key = Convert.ToInt32(param.key);
                    Appointment app = db.Appointments.Where(c => c.Id == key).FirstOrDefault();
                    if (app != null) db.Appointments.Remove(app);
                }
                else
                {
                    foreach (var apps in param.deleted)
                    {
                        Appointment app = db.Appointments.Where(c => c.Id == apps.Id).FirstOrDefault();
                        if (apps != null) db.Appointments.Remove(app);
                    }
                }
                db.SaveChanges();
            }
            if ((param.action == "batch" && param.changed != null) || param.action == "update")   
            {
               // this block of code will execute while updating the appointment
                var value = param.action == "update" ? param.value : param.changed[0];
                var filterData = db.Appointments.Where(c => c.Id == Convert.ToInt32(value.Id));

                if (filterData.Count() > 0)
                {
                    DateTime startTime = Convert.ToDateTime(value.StartTime);
                    DateTime endTime = Convert.ToDateTime(value.EndTime);
                    Appointment appoint = db.Appointments.Single(A => A.Id == Convert.ToInt32(value.Id));
                    appoint.StartTime = startTime;
                    appoint.EndTime = endTime;
                    appoint.Subject = value.Subject;
                    appoint.StartTimeZone = value.StartTimeZone;
                    appoint.EndTimeZone = value.EndTimeZone;
                    appoint.Description = value.Description;
                    appoint.OwnerId = value.OwnerId;                  
                    appoint.Recurrence = Convert.ToByte(value.Recurrence);
                    appoint.RoomId = value.RoomId;
                    appoint.AllDay = value.AllDay;
                    appoint.RecurrenceRule = value.RecurrenceRule;
                }
                db.SaveChanges();
            }
            IEnumerable data = new ScheduleControlDataEntities().Appointments.Take(500); // nw.Appointment.Take(5);
            return Json(data, JsonRequestBehavior.AllowGet);
        }

{% endhighlight %}


## SQL Data Binding

Binding SQL data to Scheduler is quite simple and also it supports the complete CRUD operation to be performed on the appointment data easily. 

{% highlight razor %}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .AppointmentSettings(fields => fields.Datasource(ds => ds.URL("/Home/GetData").CrudURL("/Home/Batch").Adaptor("UrlAdaptor"))
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

{% highlight c# %}
        // Mention the correct path of the database to connect. Also ensure, whether the provided database already exists.
        SqlConnection connection = new SqlConnection(@"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=|DataDirectory|\ScheduleDatabase.mdf;Integrated Security=True");

        public ActionResult Index()
        {
            return View();
        }
        
        public JsonResult GetData()
        {
            using (connection)
            {
                connection.Open();
                // To initially bind the Scheduler with data
                SqlDataAdapter data = new SqlDataAdapter("select * from ScheduleData", connection);
                connection.Close();
                return Json(data, JsonRequestBehavior.AllowGet);
            }
        }
        
        // To perform other CRUD operations
        public JsonResult Batch(EditParams param)
        {
            if (param.action == "insert" || (param.action == "batch" && param.added != null))
            {
                var value = param.action == "insert" ? param.value : param.added[0];
                connection.Open();
                SqlCommand add = new SqlCommand("insert into ScheduleData(Id,Subject,StartTime,EndTime,Description,AllDay,Recurrence,RecurrenceRule) values(Id="+ value.Id +",Subject='"+ value.Subject +"', StartTime='"+ value.StartTime +"', EndTime='"+ value.EndTime +"', Description='"+ value.Description +"', AllDay='"+ value.AllDay +"', Recurrence='"+ value.Recurrence +"', RecurrenceRule='"+ value.RecurrenceRule +"')",connection);
                add.ExecuteNonQuery();
                connection.Close();
            }
            if (param.action == "remove" || param.deleted != null)
            {
                connection.Open();
                if (param.action == "remove")
                {
                    int key = Convert.ToInt32(param.key);
                    SqlCommand delete = new SqlCommand("delete from ScheduleData where Id="+ key +"",connection);
                    delete.ExecuteNonQuery();
                }
                else
                {
                    foreach (var apps in param.deleted)
                    {
                        SqlCommand delete = new SqlCommand("delete from ScheduleData where Id=" + apps.Id + "", connection);
                        delete.ExecuteNonQuery();
                    }
                }
                connection.Close();
            }
            if ((param.action == "batch" && param.changed != null) || param.action == "update")
            {
                connection.Open();
                var value = param.action == "update" ? param.value : param.changed[0];
                SqlCommand update = new SqlCommand("update scheduleData set Id = " + value.Id + ", Subject = '" + value.Subject + "', StartTime = '" + value.StartTime + "', EndTime = '" + value.EndTime + "', Description = '" + value.Description + "', AllDay = '" + value.AllDay + "', Recurrence = '" + value.Recurrence + "' where Id = " + value.Id + ",)", connection);
                update.ExecuteNonQuery();
                connection.Close();
            }
            connection.Open();
            SqlDataAdapter data = new SqlDataAdapter("select * from ScheduleData", connection);
            connection.Close();
            return Json(data, JsonRequestBehavior.AllowGet);
        }
        
{% endhighlight %}
