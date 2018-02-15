---
layout: post
title: Save and Load Report | PivotClient | ASP.NET MVC | Syncfusion
description: save and load report
platform: js
control: PivotClient
documentation: ug
---

# Save and Load Report

Save and load report allows you to save the current report collection of PivotClient and render the control later on loading the same.

We can save and load the report in two ways.

* Database
* Local Storage

## Save Report to Database

We can store the report collection of PivotClient to database, by using the [`SaveReport`](/js/api/ejpivotclient#members:saveReport) event in PivotClient.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotClient("PivotClient1”).ClientSideEvents(events => events.SaveReport("saveReportSettings"))

<script>
    function saveReportSettings(args) {
        if(args.saveReportSettings)
            return args.saveReportSetting.url = "../wcf/OlapClientService.svc";
    }
</script>
{% endhighlight %}

Service method needs to be added in WCF/WebAPI for storing PivotClient report collection in database.

For WebAPI controller, the below method needs to be added.

{% highlight c# %}

[System.Web.Http.ActionName("SaveReportToDB")]
[System.Web.Http.HttpPost]
public Dictionary<string, object> SaveReportToDB(Dictionary<string, object> jsonResult)
{
    string operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString(), reportName = string.Empty;
    bool isDuplicate = true;
    SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
    con.Open();
    reportName = jsonResult["reportName"].ToString() + "##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower();
    SqlCeCommand cmd1 = null;
    foreach (DataRow row in GetDataTable().Rows)
    {
        if ((row.ItemArray[0] as string).Equals(reportName))
        {
            isDuplicate = false;
            cmd1 = new SqlCeCommand("update ReportsTable set Report=@Reports where ReportName like @ReportName", con);
        }
    }
    if (isDuplicate)
    {
        cmd1 = new SqlCeCommand("insert into ReportsTable Values(@ReportName,@Reports)", con);
    }
    cmd1.Parameters.Add("@ReportName", reportName);
    cmd1.Parameters.Add("@Reports", Encoding.UTF8.GetBytes(jsonResult["clientReports"].ToString()).ToArray());
    cmd1.ExecuteNonQuery();
    con.Close();
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    dictionary.Add("CurrentAction", "Save");
    return dictionary;
}

{% endhighlight %}

For WCF controller, the below method needs to be added.

{% highlight c# %}


public Dictionary<string, object> SaveReportToDB(string reportName, string operationalMode, string analysisMode, string olapReport, string clientReports)
{
    reportName = reportName + "##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower();
    bool isDuplicate = true;
    SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
    con.Open();
    SqlCeCommand cmd1 = null;
    foreach (DataRow row in GetDataTable().Rows)
    {
        if ((row.ItemArray[0] as string).Equals(reportName))
        {
            isDuplicate = false;
            cmd1 = new SqlCeCommand("update ReportsTable set Report=@Reports where ReportName like @ReportName", con);
        }
    }
    if (isDuplicate)
    {
        cmd1 = new SqlCeCommand("insert into ReportsTable Values(@ReportName,@Reports)", con);
    }
    cmd1.Parameters.Add("@ReportName", reportName);
    cmd1.Parameters.Add("@Reports", Encoding.UTF8.GetBytes(clientReports).ToArray());
    cmd1.ExecuteNonQuery();
    con.Close();
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    dictionary.Add("CurrentAction", "Save");
    return dictionary;
}

{% endhighlight %}

## Save Report to Local Storage

We can store the report collection of PivotClient to local storage, by setting the [`EnableLocalStorage`](/js/api/ejpivotclient#members:enableLocalStorage) property to true and by defining the [`SaveReport`](/js/api/ejpivotclient#members:saveReport) event of PivotClient.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotClient("PivotClient1”).ClientSideEvents(events => events.SaveReport("saveReportSettings")).EnableLocalStorage(true)

<script>
function saveReportSettings(args) {
    var reportCollection = [];
    if ((localStorage.pivotClientRPTCollection != "" && !ej.isNullOrUndefined(localStorage.pivotClientRPTCollection))) {
        reportCollection = JSON.parse(localStorage.pivotClientRPTCollection);
    }
    if(args.saveReportSettings){
        reportCollection.push(({ reportName: args.saveReportSetting.reportName, reportCol: args.saveReportSetting.reportCollection }));
        localStorage.pivotClientRPTCollection = JSON.stringify(reportCollection);;
    }
}
</script>
{% endhighlight %}

## Load Report from Database

We can load the stored report collection of PivotClient from database, by using the [`FetchReport`](/js/api/ejpivotclient#members:fetchReport)  and [`LoadReport`](/js/api/ejpivotclient#members:loadReport) events in PivotClient.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotClient("PivotClient1”).ClientSideEvents(events => events.LoadReport("reportSettings").FetchReport(”reportSettings”)) 

<script>
    function reportSettings(args) {
        if (args.fetchReportSetting)
            return args.fetchReportSetting.url = "../wcf/OlapClientService.svc";
        else if (args.loadReportSetting)
            return args.loadReportSetting.url = "../wcf/OlapClientService.svc";
    }
</script>
{% endhighlight %}

Service methods need to be added in WCF/WebAPI for storing PivotClient report collection in database.

For WebAPI controller, the below methods need to be added.

{% highlight c# %}


[System.Web.Http.ActionName("FetchReportListFromDB")]
[System.Web.Http.HttpPost]
public Dictionary<string, object> FetchReportListFromDB(Dictionary<string, object> jsonResult)
{
    string reportNames = string.Empty, currentRptName = string.Empty, operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString();
    foreach (System.Data.DataRow row in GetDataTable().Rows)
    {
        currentRptName = (row.ItemArray[0] as string);
        if (currentRptName.IndexOf("##" + operationalMode + "#>>#" + analysisMode) >= 0)
        {
            currentRptName = currentRptName.Replace("##" + operationalMode + "#>>#" + analysisMode, "");
            reportNames = reportNames == "" ? currentRptName : reportNames + "__" + currentRptName;
        }
    }
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    dictionary.Add("ReportNameList", reportNames);
    dictionary.Add("action", jsonResult["action"].ToString());
    return dictionary;
}

[System.Web.Http.ActionName("LoadReportFromDB")]
[System.Web.Http.HttpPost]
public Dictionary<string, object> LoadReportFromDB(Dictionary<string, object> jsonResult)
{
    PivotReport report = new PivotReport();
    string operationalMode = jsonResult["operationalMode"].ToString(), analysisMode = jsonResult["analysisMode"].ToString();
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    string currentRptName = string.Empty;
    foreach (DataRow row in GetDataTable().Rows)
    {
        currentRptName = (row.ItemArray[0] as string).Replace("##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower(), "");
        if (currentRptName.Equals(jsonResult["reportName"].ToString()))
        {                  
            byte[] reportByte = new byte[2 * 1024];
            reportByte = (row.ItemArray[1] as byte[]);
            if (operationalMode.ToLower() == "servermode" && analysisMode == "olap")
            {
                var repCol = Encoding.UTF8.GetString(reportByte);
                OlapDataManager DataManager = new OlapDataManager(connectionString);
                if (repCol.IndexOf("<?xml version") == 0)
                {
                    var reportString = "";
                    reportString = Syncfusion.JavaScript.Olap.Utils.CompressData(row.ItemArray[1] as byte[]);
                    DataManager.Reports = pivotClientHelper.DeserializedReports(reportString);
                    DataManager.SetCurrentReport(DataManager.Reports[0]);
                    return pivotClientHelper.GetJsonData("toolbarOperation", DataManager, "Load Report", jsonResult["reportName"].ToString());
                }
                else
                {
                    dynamic customData = serializer.Deserialize<dynamic>(repCol.ToString());
                    DataManager.Reports = pivotClientHelper.DeserializedReports(customData[customData[customData.Length - 1]["cubeIndex"]]["Reports"]);
                    DataManager.SetCurrentReport(DataManager.Reports[customData[customData[customData.Length - 1]["cubeIndex"]]["ReportIndex"]]);
                    dictionary = pivotClientHelper.GetJsonData("toolbarOperation", DataManager, "Load Report", jsonResult["reportName"].ToString());
                    dictionary.Add("Collection", repCol);
                }
            }
            else
            {
                if (analysisMode.ToLower() == "pivot" && operationalMode.ToLower() == "servermode")
                    dictionary = pivotClientHelper.GetJsonData("LoadReport", ProductSales.GetSalesData(), Encoding.UTF8.GetString(reportByte));
                else
                    dictionary.Add("report", Encoding.UTF8.GetString(reportByte));
                break;
            }
        }
    }
    return dictionary;
}

private DataTable GetDataTable()
{
    SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
    con.Open();
    DataSet dSet = new DataSet();
    new SqlCeDataAdapter("Select * from ReportsTable", con).Fill(dSet);
    con.Close();
    return dSet.Tables[0];
}

{% endhighlight %}

For WCF controller, the below method needs to be added.

{% highlight c# %}

public Dictionary<string, object> FetchReportListFromDB(string action, string operationalMode, string analysisMode)
{
    string reportNames = string.Empty;
    string currentRptName = string.Empty;
    foreach (System.Data.DataRow row in GetDataTable().Rows)
    {
        currentRptName = (row.ItemArray[0] as string);
        if (currentRptName.IndexOf("##" + operationalMode + "#>>#" + analysisMode) >= 0)
        {
            currentRptName = currentRptName.Replace("##" + operationalMode + "#>>#" + analysisMode, "");
            reportNames = reportNames == "" ? currentRptName : reportNames + "__" + currentRptName;
        }
    }
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    dictionary.Add("ReportNameList", reportNames);
    dictionary.Add("action", action);
    return dictionary;
}

public Dictionary<string, object> LoadReportFromDB(string reportName,string operationalMode,string analysisMode, string olapReport, string clientReports)
{
    PivotReport report = new PivotReport();
    Dictionary<string, object> dictionary = new Dictionary<string, object>();
    string currentRptName = string.Empty;
    foreach (DataRow row in GetDataTable().Rows)
    {
        currentRptName = (row.ItemArray[0] as string).Replace("##" + operationalMode.ToLower() + "#>>#" + analysisMode.ToLower(), "");
        if (currentRptName.Equals(reportName))
        {
            byte[] reportByte = new byte[2 * 1024];
            reportByte = (row.ItemArray[1] as byte[]);
            if (operationalMode.ToLower() == "servermode" && analysisMode == "olap")
            {
                var repCol = Encoding.UTF8.GetString(reportByte);
                OlapDataManager DataManager = new OlapDataManager(connectionString);
                if (repCol.IndexOf("<?xml version") == 0)
                {
                    var reportString = "";
                    reportString = Syncfusion.JavaScript.Olap.Utils.CompressData(row.ItemArray[1] as byte[]);
                    DataManager.Reports = pivotClientHelper.DeserializedReports(reportString);
                    DataManager.SetCurrentReport(DataManager.Reports[0]);
                    return pivotClientHelper.GetJsonData("toolbarOperation", DataManager, "Load Report", reportName);
                }
                else
                {
                    dynamic customData = serializer.Deserialize<dynamic>(repCol.ToString());
                    DataManager.Reports = pivotClientHelper.DeserializedReports(customData[customData[customData.Length - 1]["cubeIndex"]]["Reports"]);
                    DataManager.SetCurrentReport(DataManager.Reports[customData[customData[customData.Length - 1]["cubeIndex"]]["ReportIndex"]]);
                    dictionary = pivotClientHelper.GetJsonData("toolbarOperation", DataManager, "Load Report", reportName);
                    dictionary.Add("Collection", repCol);
                }
            }
            else
            {
                if (analysisMode.ToLower() == "pivot" && operationalMode.ToLower() == "servermode")
                    dictionary = pivotClientHelper.GetJsonData("LoadReport", ProductSales.GetSalesData(), Encoding.UTF8.GetString(reportByte));
                else
                    dictionary.Add("report", Encoding.UTF8.GetString(reportByte));
                break;
            }
        }
    }
    return dictionary;
}

private DataTable GetDataTable()
{
    SqlCeConnection con = new SqlCeConnection() { ConnectionString = conStringforDB };
    con.Open();
    DataSet dSet = new DataSet();
    new SqlCeDataAdapter("Select * from ReportsTable", con).Fill(dSet);
    con.Close();
    return dSet.Tables[0];
}

{% endhighlight %}

## Load Report from Local Storage

We can load the stored report collection of PivotClient from local storage, by setting the [`EnableLocalStorage`](/js/api/ejpivotclient#members:enableLocalStorage) property to true and using the [`LoadReport`](/js/api/ejpivotclient#members:loadReport) and [`FetchReport`](/js/api/ejpivotclient#members:fetchReport) events in PivotClient.

{% highlight CSHTML %}

@Html.EJ().Pivot().PivotClient("PivotClient1”).ClientSideEvents(events => events.LoadReport("reportSettings").FetchReport(”reportSettings”)).EnableLocalStorage(true)

<script>
    function reportSettings(args) {
        var reportCollection = [];
        if ((localStorage.pivotClientRPTCollection != "" && !ej.isNullOrUndefined(localStorage.pivotClientRPTCollection))) {
            reportCollection = JSON.parse(localStorage.pivotClientRPTCollection);
        }
        if (args.fetchReportSetting) 
            args.fetchReportSetting.reportList = $.map(reportCollection, function (item, index) { return item.reportName; }).join("__");
        else if (args.loadReportSetting) 
            args.loadReportSetting.reportCollection = $.map(reportCollection, function (item, index) { if (item.reportName == args.loadReportSetting.selectedReport) return item.reportCol; });
    }
</script>
{% endhighlight %}