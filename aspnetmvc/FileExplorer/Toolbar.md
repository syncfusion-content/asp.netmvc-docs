---
title: Toolbar | FileExplorer | ASP.NET MVC | Syncfusion
description: Toolbar support in FileExplorer control
platform: ejmvc
control: FileExplorer
documentation: UG
keywords: FileExplorer,  Syncfusion, EJ MVC FileExplorer, UG document, Toolbar
---
# Toolbar

The toolbar element having the number of tools, and each tool can be configurable.

## Toolbar items

The toolbar having the list of items to perform various operations and grouped into some categorizes.

From below you can see the available toolbar items and its categorization:
    
    {% highlight razor %}
    
        @*all tools grouped under following categories*@
        @{
            List<String> layout = new List<string>() {
                "Layout"
            };
            List<String> creation = new List<string>() {
                "NewFolder"
            };
            List<String> navigation = new List<string>() {
                "Back",
                "Forward",
                "Upward"
            };
            List<String> addressBar = new List<string>() {
                "Addressbar"
            };
            List<String> editing = new List<string>() {
                "Refresh",
                "Upload",
                "Delete",
                "Rename",
                "Download"
            };
            List<String> copyPaste = new List<string>() {
                "Cut",
                "Copy",
                "Paste"
            };
            List<String> getProperties = new List<string>() {
                "Details"
            };
            List<String> searchBar = new List<string>() {
                "Searchbar"
            };
            List<String> sortBy = new List<string>() {
                "SortBy"
            };
        }
        @*all tools categories are placed in the toolbar by the below order*@
        @{
            List<String> toolsList = new List<string>() {
                "layout",
                "creation",
                "navigation",
                "addressBar",
                "editing",
                "copyPaste",
                "getProperties",
                "searchBar",
                "sortBy"
            };
        }
    
    {% endhighlight %}
    
The following table explains the functionality of each toolbar item:

<table>
<tr>
<td>
Tool name
</td>
<td>
Description
</td>
</tr>
<tr>
<td>
Layout
</td>
<td>
In FileExplorer, files have been displayed in 3 types of views “Grid”, “Tile” and “Large Icons”. Using this tool, you can change the view type from one to another.

</td>
</tr>
<tr>
<td>
NewFolder <br/><br/></td>
<td>
It creates a new folder on the current directory.<br/><br/>While click on the NewFolder item, the dialog displays to get the folder name. Based on the user input, FileExplorer creates new folder on the current directory.
Also {{'[createFolder](https://help.syncfusion.com/api/js/ejfileexplorer#events:createfolder)'| markdownify}} event will be triggered when new folder is created successfully in the file system.<br/><br/><br/><br/></td></tr>
</tr>
<tr>
<td>
Back <br/><br/></td>
<td>
It navigates to the previous directory from the user history. When the backward history is not available when it is disabled state.<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
Forward <br/><br/></td>
<td>
It navigates to the next directory from the user history. When the forward history is not available when it is disable state.<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
Upward <br/><br/></td>
<td>
It navigates to the parent directory of the current folder.<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
Address bar<br/><br/></td>
<td>
The “address bar” is the textbox which displays the path of the current directory, as a series of its parent directory separated by slash (“/”).<br/><br/>And the address bar is an editable area, so you can enter any directory’s path to a quick navigation.<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
Refresh <br/><br/></td>
<td>
It refreshes the current directory.<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
Upload <br/><br/></td>
<td>
It uploads a file or list of files into the current directory.<br/><br/>And you can customize the upload configurations, for details check {{'[here](https://help.syncfusion.com/js/fileexplorer/toolbar#customizing-the-upload-functionality)'| markdownify }}.
<br/><br/><br/><br/></td></tr>
</tr>
<tr>
<td>
Delete <br/><br/></td>
<td>
It delete the current selected file or folder. The delete icon is enable state if you select any file or folder.<br/><br/>If you selected the multiple files, it deletes all the selected items.<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
Rename <br/><br/></td>
<td>
This is used to rename the current selected file or folder. The rename icon is enable state if you select any file or folder.<br/><br/>Even if you selected multiple files, it renames the last selected file only.<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
Download <br/><br/></td>
<td>
It downloads the selected files. The download icon is enable state if you select any file or folder.<br/><br/>
The {{'[beforeDownload](https://help.syncfusion.com/api/js/ejfileexplorer#events:beforedownload)'| markdownify}} event will be triggered before the files are downloaded.
<br/><br/>If you select multiple files, it downloads all the files in a zip format.<br/><br/><br/><br/></td></tr>
</tr>
<tr>
<td>
Cut <br/><br/></td>
<td>
It makes the copy of the selected files or folders into the clipboard. When the user paste the files in any location, the files are removed from the source location.
The {{'[cut](https://help.syncfusion.com/api/js/ejfileexplorer#events:cut)'| markdownify}} event will be triggered when files or folders are removed from the source.<br/><br/><br/><br/></td></tr>
</tr>
<tr>
<td>
Copy <br/><br/></td>
<td>
It makes the copy of the selected files or folders into the clipboard. When the user paste the files, the copy of the files are pasted in the target location.
The {{'[copy](https://help.syncfusion.com/api/js/ejfileexplorer#events:copy)'| markdownify}} event will be triggered when file or folder is copied.<br/><br/><br/><br/></td></tr>
</tr>
<tr>
<td>
Paste <br/><br/></td>
<td>
It pastes the files from the clipboard into the currently selected folder. <br/><br/>Note: Only when the files are copied into the clipboard it is enabled.
The {{'[paste](https://help.syncfusion.com/api/js/ejfileexplorer#events:paste)'| markdownify}} event will be triggered when file or folder is pasted.<br/><br/><br/><br/></td></tr>
</tr>
<tr>
<td>
Details <br/><br/></td>
<td>
It displays the details of the current selected file or folder.<br/><br/><br/><br/></td>
</tr>
<tr>
<td>
Search bar<br/><br/></td>
<td>
The Search bar is the textbox which is used to search the files from the current directory. It list the files based on the user search.<br/><br/>The search behavior of the “search bar” can be customize, for details check <br/>{{'[here](#_Search_bar)'| markdownify }}.<br/><br/></td>
</tr>
<tr>
<td>
Sort by <br/><br/></td><td>
It's used to sorting the files from the current directory.The sorting can be done based on the columns available from grid,in both ascending and descending order.<br/><br/><br/><br/></td>
</tr>
</table>

## Toolbar Visibility

The visibility of the toolbar can be customized through the “[ShowToolbar](http://help.syncfusion.com/js/api/ejfileexplorer#members:showtoolbar)” property. By disabling this property you can remove the toolbar from FileExplorer. Also you can remove the particular toolbar item by using [removeToolbarItem](https://help.syncfusion.com/api/js/ejfileexplorer#methods:removetoolbaritem) method.

In the view page, add FileExplorer helper and specify “ShowToolbar” as false

    {% highlight razor %}
    
        @*hides the toolbar*@
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            .ShowToolbar(false)
        )
        
    {% endhighlight %}

## Toolbar Configuration

As you can see the available toolbar items from [here](#_Toolbar_items). From the list of available items, you can configure and group your required toolbar items only through the “[Tools](http://help.syncfusion.com/js/api/ejfileexplorer#members:tools)” property. And also you can arrange the toolbar items by the “[ToolsList](http://help.syncfusion.com/js/api/ejfileexplorer#members:toolslist)” property.

In the view page, create the tools list and add FileExplorer helper as shown below
    
    {% highlight razor %}
    
        @{
            List<String> toolsList = new List<string>() {
                "creation",
                "navigation",
                "addressBar",
                "copyPaste",
                "searchBar"
            };
    
            List<String> creation = new List<string>() {
                "NewFolder"
            };
            List<String> navigation = new List<string>() {
                "Back",
                "Forward",
                "Upward"
            };
            List<String> addressBar = new List<string>() {
                "Addressbar"
            };
            List<String> copyPaste = new List<string>() {
                "Cut",
                "Copy",
                "Paste"
            };
            List<String> searchBar = new List<string>() {
                "Searchbar"
            };
        }
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            .Tools(tools =>
                        tools.Creation(creation)
                        .AddressBar(addressBar)
                        .Navigation(navigation)
                        .CopyPaste(copyPaste)
                        .SearchBar(searchBar)
            )
            .ToolsList(toolsList)
        )
        
    {% endhighlight %}
    
## Search bar

The Search bar can be customize through the “[FilterSettings](http://help.syncfusion.com/js/api/ejfileexplorer#members:filtersettings)” property. By default the search doesn’t consider the case sensitivity, and the search works based on “[FilterType](http://help.syncfusion.com/js/api/ejfileexplorer#members:filtersettings-filtertype)”.

The FileExplorer allows the following filter types in the search functionality.

* “FilterOperator.StartsWith” – Supports to search text with starts with

* “FilterOperator.Contains” – Supports to search text with contains with

* “FilterOperator.EndsWith” – Supports to search text with ends with

In the view page, you can configure the filter type with enabling case sensitivity like below:

    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            .FilterSettings(settings =>
                //it changes the search filter type as “startsWith”
                settings.FilterType(FilterOperator.StartsWith)
                //it enables the case sensitive search
                .CaseSensitiveSearch(true)
            )
        )
        
    {% endhighlight %}
    
    
## Custom Tool in Toolbar

From the [toolbar items ](#_Toolbar_items)you can see the list of built-in tools to perform the operations. Along with this built-in tools, you can add your custom tool with the custom functionality.
You can find an online demo sample of FileExplorer with custom tool from [here](http://mvc.syncfusion.com/demos/web/fileexplorer/customtool#). 

In the view page, add FileExplorer helper and specify custom tool as shown below
    
    {% highlight razor %}
    
        @{
            // denotes the order of the tools categories
            List<String> toolsList = new List<string>() {
                "creation",
                "navigation",
                "addressBar",
                "copyPaste",
                "searchBar",
                "customTool"
            };
        }
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            .ToolsList(toolsList)
            //defines the tool items for customTool category
            .Tools(tool =>
                tool.CustomTool(custom =>
                custom.Name("Help")
                .Tooltip("Help")
                .Css("e-fileExplorer-toolbar-icon Help")
                .Action("dialogOpen").Add()
                ))
        )
        <script>
            //click handler of custom tool
            function dialogOpen() {
                alert("custom tool item clicked");
            }
        </script>
        @*Define the CSS that needs to apply for the custom tool.*@
        <style class="cssStyles">
            .e-fileExplorer-toolbar-icon {
                height: 22px;
                width: 22px;
                font-family: 'ej-webfont';
                font-size: 18px;
                margin-top: 2px;
                text-align: center;
            }
    
            .e-fileExplorer-toolbar-icon.Help:before {
                content: "\e72b";
            }
        </style>
        
    {% endhighlight %}
    
## Enable / Disable the Toolbar Item

Each toolbar item can be enabled or disabled through the below client-side public methods.

* [enableToolbarItem](http://help.syncfusion.com/js/api/ejfileexplorer#methods:enabletoolbaritem)

* [disableToolbarItem](http://help.syncfusion.com/js/api/ejfileexplorer#methods:disabletoolbaritem)

These methods accepts the tool name as the parameter. It also allows the parameter as tool item index or the jQuery object of the tool item.
    
    {% highlight javascript %}
    
            $(function () {
                var fileExpObj = $("#fileExplorer").data("ejFileExplorer");
                // this disables the NewFolder item
                fileExpObj.disableToolbarItem("NewFolder");
                // this disables the Layout item (since index of Layout is 0)
                fileExpObj.disableToolbarItem(0);
                // this enables the NewFolder item
                fileExpObj.enableToolbarItem("NewFolder");
            });
    
    {% endhighlight %}

### Enable / Disable the custom added tool in Toolbar Item

If you want to enable / disable the custom added tool in toolbar, you need to pass the corresponding li elements of custom added tool in [enableToolbarItem](https://help.syncfusion.com/api/js/ejfileexplorer#methods:enabletoolbaritem) / [disableToolbarItem](https://help.syncfusion.com/api/js/ejfileexplorer#methods:disabletoolbaritem) method of FileExplorer. Since we have consider this custom tool as a object type.

{% highlight javascript %}
        
        var fileExpObj = $("#fileExplorer").data("ejFileExplorer");
        
        //tool is a cssClass of FileExplorer 
        // this disables the custom tool item 
        
        var li = $(".tool").find(".Help").closest('li'); 
        fileExpObj.disableToolbarItem(li); 
        
        // this enables the custom tool item 
        fileExpObj.enableToolbarItem(li);

{% endhighlight %}

## Customizing the Upload Functionality

FileExplorer helps you to upload the file using “[Upload](http://help.syncfusion.com/js/uploadbox/overview#)” component. File upload can be done through the toolbar item or context menu item. The “[UploadSettings](http://help.syncfusion.com/js/api/ejfileexplorer#members:uploadsettings)” property is used to configure the upload functionalities.

This property has the below sub properties with the default values:
    
    {% highlight razor %}
    
    UploadSettings(settings =>
        settings.AllowMultipleFile(true)
        .FileSize(31457280)
        .AutoUpload(false)
    )
    
    {% endhighlight %}
    
**AllowMultipleFile**: This property used to control the behavior of multiple files upload and this was enabled by default so you can upload multiple files at a time. If you disable this “AllowMultipleFile” property then you can upload only one file at a time.

**MaxFileSize**: The property limits the maximum file size to upload. It accepts the value in bytes.

If you want to upload more than 4 MB files in FileExplorer, you should specify the **maxRequestLength** attribute in webconfig file and specify the **MaxFileSize** property to upload it. Please check the below code block.

{% highlight razor %}

<httpRuntime targetFramework="4.6" maxRequestLength="2147483647"executionTimeout="1600" requestLengthDiskThreshold="2147483647" /> 
     
<system.webServer> 
    <security> 
      <requestFiltering> 
        <requestLimits maxAllowedContentLength="3221225472" /> 
      </requestFiltering> 
    </security> 
… 
</system.webServer> 

{% endhighlight %}

{% highlight razor %}

@(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/Content/images/FileExplorer/")
            .AjaxAction(@Url.Content("/FileExplorer/FileActionDefault"))
            .UploadSettings(settings =>
                settings.MaxFileSize(3221225472)
            )
    )
{% endhighlight %}

To know more details, please check the below reference link and sample.

[Reference Link](https://stackoverflow.com/questions/16287706/how-to-upload-large-files-using-mvc-4?answertab=active#tab-top)

[Sample](http://www.syncfusion.com/downloads/support/directtrac/210600/ze/UploadFileSizeProblem-1398338221.zip)

**AutoUpload**: when you enable this property, the upload action performed automatically after select the files. When you disable this property, it shows a confirmation dialog with the selected file details and perform the upload action on press the “upload” button.

During upload process following events will be triggered, {{'[beforeUploadSend](https://help.syncfusion.com/api/js/ejfileexplorer#events:beforeuploadsend)'| markdownify}}, {{'[beforeUploadDialogOpen](https://help.syncfusion.com/api/js/ejfileexplorer#events:beforeuploaddialogopen)'| markdownify}}, {{'[beforeUpload](https://help.syncfusion.com/api/js/ejfileexplorer#events:beforeupload)'| markdownify}}, {{'[uploadError](https://help.syncfusion.com/api/js/ejfileexplorer#events:uploaderror)'| markdownify}}, {{'[uploadSuccess](https://help.syncfusion.com/api/js/ejfileexplorer#events:uploadsuccess)'| markdownify}} and {{'[uploadComplete](https://help.syncfusion.com/api/js/ejfileexplorer#events:uploadcomplete)'| markdownify}}. You can customize the upload settings with these events.

In the view page, add FileExplorer helper and specify the upload settings as shown below
    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            .UploadSettings(settings =>
                // it disables the multi file upload functionality
                settings.AllowMultipleFile(false)
                // it enables the auto upload functionality
                .AutoUpload(true)
            )
        )
        
    {% endhighlight %}
    
