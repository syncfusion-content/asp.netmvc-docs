---
layout: post
title: Localization | Gantt | ASP.NET MVC | Syncfusion
description: localization
platform: ejmvc
control: Gantt
documentation: ug
---

# Localization

Localization is the process of customizing the User Interface (UI) based on a culture, specific to a particular country or region, in order to display regional data. The culture is represented by a unique string like “en-US” for US English and “fr-FR” for French.

Localization is the key feature that provides solutions to global customers with the help of localized control. 

The following UIs are provided to localize based on culture. The default English Localization UIs are listed as follows:

_Localization_

<table>
<tr>
<th colspan = "2">
Localized string value for en-US culture</th></tr>
<tr>
<td>
Empty Record</td><td>
emptyRecord: "No records to display"</td></tr>
<tr>
<td>
Column Header Texts:<br/>
taskId<br/>
taskName<br/>
startDate<br/>
endDate<br/>
resourceInfo<br/>
duration<br/>
status<br/>
predecessor<br/>
baselineStartDate<br/>
baselineEndDate</td><td>
columnHeaderTexts: {  <br/>  
taskId: "ID",<br/>
taskName: "Task Name", <br/>
startDate: "Start Date",<br/>
endDate: "End Date",<br/>
resourceInfo: "Resources",<br/>
duration: "Duration",<br/>
status: "Progress",<br/>
predecessor: "Predecessor",<br/>
 baselineStartDate: "Baseline Start Date",<br/>
 baselineEndDate: "Baseline End Date"<br/>
 }</td></tr>
<tr>
<td>
Edit Dialog Texts:<br/>
addFormTitle<br/>
editFormTitle<br/>
saveButton<br/>
cancelButton</td><td>
editDialogTexts: {<br/>
addFormTitle: "New Task",<br/>
editFormTitle: "Edit Task",<br/>
saveButton: "Save",<br/>
cancelButton: "Cancel" },</td></tr>
<tr>
<td>
Date Format</td><td>
calendars: {<br/>
     standard: {   <br/>
		days: {  <br/>
			// full name of days  <br/>
			names: ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"],<br/>

			// abbreviated names of days <br/>
            namesAbbr: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],<br/>         }, <br/>
			months: {  <br/>           
				// full name of months  <br/>
				names: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],<br/>

				// abbreviated name of months <br/>
				namesAbbr: ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"]  <br/>     
				}, <br/>
				// set of predefined date and time patterns used by the culture.<br/>
				patterns: {  <br/>
					d: "M/d/yyyy", <br/>
					D: "dddd, MMMM dd, yyyy",<br/>
					F: "dddd, MMMM dd, yyyy h:mm:ss tt", <br/>
					g: "M/d/yyyy h:mm tt",  <br/>
					G: "M/d/yyyy h:mm:ss tt", <br/>
					m: "MMMM dd",  <br/>
					M: "MMMM dd",  <br/>
					s: "yyyy'-'MM'-'ddTHH':'mm':'ss",<br/>
					t: "h:mm tt",  <br/>       
					T: "h:mm:ss tt", <br/>    
					u: "yyyy'-'MM'-'dd HH':'mm':'ss'Z'", <br/> 
					y: "MMMM, yyyy",  <br/>    
					Y: "MMMM, yyyy" <br/>   
					} 
				}
			}</td></tr>
</table>


To localize the Column Header Texts based on French culture, refer to the following code example.


{% highlight CSHTML %}



@(Html.EJ().Gantt("GanttContainer")

//...

.Locale("fr-FR")

.Datasource(ViewBag.datasource)

)



@section ScriptSection{

     <script type="text/javascript">



ej.Gantt.localization["fr-FR"] = {



	//headerText to be displayed in gridtree

	columnHeaderTexts: {

		taskId: "Tâche Ia",

		taskName: "Tâche Tâche",

		startDate: "Démarrer Date",

		endDate: "Fin Date",

		resourceInfo: "Resources",

		duration: "Durée",

		status: "Progrès",

		predecessor: "Prédécesseur",

		baselineStartDate: "Baseline Démarrer Date",

		baselineEndDate: "Baseline Fin Date"

	},



	//string to display in dialog 

	editDialogTexts: {

		addFormTitle: "Nouveau Tâche",

		editFormTitle: "Modifier Tâche",

		saveButton: "Sauver",

		cancelButton: "Annuler"

	},



	calendars: {

		standard: {

			firstDay: 1,

			days: {

				names: ["dimanche", "lundi", "mardi", "mercredi", "jeudi", "vendredi", "samedi"],

				namesAbbr: ["dim.", "lun.", "mar.", "mer.", "jeu.", "ven.", "sam."],

				namesShort: ["di", "lu", "ma", "me", "je", "ve", "sa"]

			},

			months: {

				names: ["janvier", "fÃ©vrier", "mars", "avril", "mai", "juin", "juillet", "aoÃ»t", "septembre", "octobre", "novembre", "dÃ©cembre", ""],

				namesAbbr: ["TEST.", "fÃ©vr.", "mars", "avr.", "mai", "juin", "juil.", "aoÃ»t", "sept.", "oct.", "nov.", "dÃ©c.", ""]

			},

			AM: null,

			PM: null,

			eras: [{ "name": "ap. J.-C.", "start": null, "offset": 0 }],

			patterns: {

				d: "dd/MM/yyyy",

				D: "dddd d MMMM yyyy",

				t: "HH:mm",

				T: "HH:mm:ss",

				f: "dddd d MMMM yyyy HH:mm",

				F: "dddd d MMMM yyyy HH:mm:ss",

				M: "d MMMM",

				Y: "MMMM yyyy"

			}

		}

	}

}

</script>

 }

{% endhighlight %}





The following screenshot shows Gantt with French culture.



![](Localization_images/Localization_img1.png)

Localization
{:.caption}
