---
title: Globalization and Localization
description: Globalizing and localizing Scheduler
platform: ejmvc
control: schedule
documentation: ug
keywords: globalize, localize, localization, globalization 
---
# Globalization and Localization

## Globalization

The Scheduler control is built with default **globalization** support as it format the dates according to the user’s locale automatically and processes it internally without any need for manual conversions. This kind of default handling of Scheduler dates is achieved through the built-in **ej.globalize** library which globalize the date, day and month names accordingly.

## Localization

Scheduler also comes with default localization support which allows it to customize the display of text within the Scheduler in a user-specific culture and locale. The Schedule control can be localized in specific culture using the common API `Locale` along with the collection of localized words defined for that culture using the ej.Schedule.Locale [**culture-code**].

N> By default, the Schedule control is localized in **en-US** culture.

To localize Scheduler into a particular culture, it is necessary to refer the culture-specific script files in your application after the reference of **ej.web.all.min.js** file, which are available under the following location.

_<**Installed location**>\Syncfusion\Essential Studio\{{ site.releaseversion }}\JavaScript\assets\scripts\cultures_

The following code example shows how to localize the Schedule control in **fr-FR** culture.

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
        .Locale("fr-FR")
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

{% highlight html %}
<script src="@Url.Content("~/Scripts/cultures/ej.culture.fr-FR.min.js")"></script>
<script>
    ej.Schedule.Locale["fr-FR"] = {
        ReminderWindowTitle: "Fenêtre de rappel",
        CreateAppointmentTitle: "créer un rendez-",
        RecurrenceEditTitle: "Modifier répétition nomination",
        RecurrenceEditMessage: "Comment voulez-vous changer le cas dans la série?",
        RecurrenceEditOnly: "Seulement cette nomination",
        RecurrenceEditSeries: "La série entière",
        PreviousAppointment: "Nomination précédente",
        NextAppointment: "prochain rendez-vous",
        AppointmentSubject: "sujet",
        StartTime: "Heure de début",
        EndTime: "Heure de fin",
        AllDay: "toute la journée",
        Today: "aujourd'hui",
        Recurrence: "répétition",
        Done: "Terminé",
        Cancel: "annuler",
        Ok: "Ok",
        RepeatBy: "Répétez par",
        RepeatEvery: "répéter chaque",
        RepeatOn: "répéter l'opération sur",
        StartsOn: "démarre sur",
        Ends: "extrémités",
        Summary: "résumé",
        Daily: "quotidien",
        Weekly: "hebdomadaire",
        Monthly: "mensuel",
        Yearly: "annuel",
        Every: "tous",
        EveryWeekDay: "chaque jour de la semaine",
        Never: "jamais",
        After: "après",
        Occurence: "apparition",
        On: "sur",
        Edit: "Modifier",
        RecurrenceDay: "Jour (s)",
        RecurrenceWeek: "Semaine (s)",
        RecurrenceMonth: "Mois (s)",
        RecurrenceYear: "Année (s)",
        The: "la",
        OfEvery: "de chaque",
        First: "première",
        Second: "deuxième",
        Third: "troisième",
        Fourth: "quatrième",
        Last: "dernier",
        WeekDay: "jour de la semaine",
        WeekEndDay: "Jour de week-end",
        Subject: "sujet",
        Categorize: "Catégories",
        DueIn: "En raison",
        DismissAll: "rejeter tout",
        Dismiss: "rejeter",
        OpenItem: "Ouvrir l'élément",
        Snooze: "répétition",
        Day: "jour",
        Week: "semaine",
        WorkWeek: "Semaine de travail",
        Month: "mois",
        AddEvent: "Ajouter événement",
        CustomView: "Vue personnalisée",
        Agenda: "ordre du jour",
        Detailed: "détaillé",
        EventBeginsin: "Nomination commence dans",
        Editevent: "Modifier nomination",
        Editseries: "Modifier série",
        Times: "fois",
        Until: "jusqu'à",
        Eventwas: "rendez-vous était",
        Hours: "hrs",
        Minutes: "minutes",
        Overdue: "en retard",
        Days: "jour (s)",
        Event: "Sujet",
        Select: "sélectionner",
        Previous: "prev",
        Next: "suivant",
        Close: "proche",
        Delete: "effacer",
        Date: "date",
        Showin: "montrer en",
        Gotodate: "Aller à la date",
        Resources: "RESSOURCES",
        RecurrenceDeleteTitle: "Supprimer répétition rendez-",
        Location: "emplacement",
        Priority: "priorité",
        RecurrenceAlert: "alerte",
        WrongPattern: "Le modèle de récurrence est pas valable",
        CreateError: "La durée de la nomination doit être plus courte que la façon dont elle se produit fréquemment. Raccourcir la durée ou changer le modèle de récurrence dans la boîte de dialogue Récurrence de rendez.",
        DragResizeError: "Impossible de replanifier une occurrence du rendez-vous récurrent. si elle saute sur une occurrence ultérieure du même rendez-vous.",
        StartEndError: "L'heure de fin doit être supérieur à l'heure de début",
        MouseOverDeleteTitle: "supprimer un rendez-",
        DeleteConfirmation: "Êtes-vous sûr de vouloir supprimer ce rendez-vous?",
        Time: "Temps"
    };
</script>

{% endhighlight %}

N> Refer the **ej.culture.fr-FR.min.js** file in your HTML application and also define the **Locale** property for the Schedule control with the appropriate **culture-code** [**fr-FR**].

For further information on – how to refer the required culture scripts into your application, refer [here](/aspnetmvc/localization).

### Localizing Specific Words

To customize or localize only some specific words in the default `ej.Schedule.Locale["en-US"]` collection, the words to be localized/customized can be defined in a separate variable and then extended to the original collection as depicted in the following code example.

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
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

{% highlight html %}

<script>
var customizationMessage = {
    // customize the appointment window title
    CreateAppointmentTitle: "Create Event",
    // customize the view options text in the Schedule header
    Day: "1 Day",
    Week: "7 Days",
    WorkWeek: "5 Days",
    Month: "Month"
};

// Extend only the required changes to the original locale collection
$.extend(ej.Schedule.Locale["en-US"], customizationMessage);

</script>

{% endhighlight %}

## Time Zone

The Scheduler makes use of the System time zone by default. If it needs to be provided with some other user-specific time zone value, then the API `TimeZone` can be used. Also, the Scheduler can be set to observe the Daylight Saving Time (DST) with its `IsDST` property which is set to **false** by default. 

When `IsDST` property is set to **true**, the Scheduler internally processes the time difference values (for the Start and end time of the appointments) related to the Scheduler time zone that observes daylight savings time. 

The following code example shows the way to set the specific time zone value with the daylight savings time observed in the Scheduler.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });
}

<@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .TimeZone("UTC +05:30")
        .IsDST(true)
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

Apart from the default Scheduler time zone, it is also possible to set the different time zone values for each appointments through the properties **StartTimeZone** and **EndTimeZone** which can be defined as separate fields within the appointment dataSource. When these properties are not explicitly defined for appointments, the appointments Start and End time will be processed based on the Scheduler time zone.

N> The **IsDST** property closely relies on the appointment fields like `StartTimeZone` and `EndTimeZone`, for appropriate time difference calculations. If these two fields are not defined for appointments, then **IsDST** depends on the System **TimeZone** value.

The following code snippet shows how to define isDST and the time zones for specific appointments.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "", StartTimeZone = "UTC +02:00", EndTimeZone = "UTC +02:00" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .IsDST(true)
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule")
            .StartTimeZone("StartTimeZone")
            .EndTimeZone("EndTimeZone"))
)

{% endhighlight %}

It is also possible to define or customize the default time zone collection of the Scheduler, by using the `TimeZoneCollection` API as follows.

{% highlight razor %}

@using Syncfusion.JavaScript.Models;
@{
    <!-- Datasource for Appointments -->
    List<ScheduleFields> Appoint = new List<ScheduleFields>();
    Appoint.Add(new ScheduleFields { Id = "1", Subject = "Meeting", StartTime = new DateTime(2015, 11, 10, 10, 00, 00), EndTime = new DateTime(2015, 11, 10, 11, 00, 00), Description = "", AllDay = false, Recurrence = false, RecurrenceRule = "" });

    <!-- Datasource for TimezoneCollection -->
    List<TimezoneCollection> TimeZone = new List<TimezoneCollection>();
    TimeZone.Add(new TimezoneCollection { Text = "UTC -04:00", Id = "10", Value = "UTC -04:00" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC -03:30", Id = "11", Value = "UTC -03:30" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC -03:00", Id = "12", Value = "UTC -03:00" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC -02:00", Id = "13", Value = "UTC -02:00" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC -01:00", Id = "14", Value = "UTC -01:00" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC +00:00", Id = "15", Value = "UTC +00:00" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC +01:00", Id = "16", Value = "UTC +01:00" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC +02:00", Id = "17", Value = "UTC +02:00" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC +03:00", Id = "18", Value = "UTC +03:00" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC +03:30", Id = "19", Value = "UTC +03:30" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC +04:00", Id = "20", Value = "UTC +04:00" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC +04:30", Id = "21", Value = "UTC +04:30" });
    TimeZone.Add(new TimezoneCollection { Text = "UTC +05:00", Id = "22", Value = "UTC +05:00" });
}

@(Html.EJ().Schedule("Schedule1")
        .Width("100%")
        .Height("525px")
        .CurrentDate(new DateTime(2015, 11, 5))
        .TimeZoneCollection(fields => fields.Datasource(TimeZone).Text("Text").Id("Id").Value("Value"))
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Priority("Priority")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

N> The values defined within the **TimeZoneCollection** dataSource are usually the options displayed at the start and end time zone dropdown fields of the default appointment window.

## Time Mode

The time mode of the Scheduler can be either **12** or **24 hours** format which is based on the `Locale` set to the Scheduler. Since the default locale value of the Scheduler is **en-US**, therefore the time mode will be set to **12 hours** format (by default) automatically based on the culture. 

The user can also set specific time mode for the Scheduler using `TimeMode` property which accepts either **String** or **enum** value. It accepts the following **enum** values,

* TimeMode.Hour12
* TimeMode.Hour24

The following code snippet shows the way to set specific **24 hour format time mode** for the Scheduler.

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
        .TimeMode(TimeMode.Hour24)
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

N> If the **TimeMode** property is not set with specific value, then the value will be taken based on the locale assigned for the Scheduler.

## Date Format

Scheduler can be used with all valid date formats. The default date format used in Scheduler is "MM/dd/yyyy". 

If the `DateFormat` property is not specified particularly, then it will be taken based on the locale that is assigned to the Scheduler. The default locale applied on the Scheduler is “en-US”, which makes it to follow the "MM/dd/yyyy" pattern by default.

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
        .DateFormat("yyyy/MM/dd")
        .AppointmentSettings(fields => fields.Datasource(Appoint)
            .Id("Id")
            .Subject("Subject")
            .StartTime("StartTime")
            .EndTime("EndTime")
            .AllDay("AllDay")
            .Recurrence("Recurrence")
            .RecurrenceRule("RecurrenceRule"))
)

{% endhighlight %}

