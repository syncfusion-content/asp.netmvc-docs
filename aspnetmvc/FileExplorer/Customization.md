---
title: Customization | FileExplorer | ASP.NET MVC | Syncfusion
description: Customization support in FileExplorer
platform: ASP.NET MVC
control: FileExplorer
documentation: UG
keywords: FileExplorer,  Syncfusion, EJ MVC FileExplorer, UG document, Customization
---
# Customization

## Dimension Customization

The dimension of the FileExplorer can be customized through “[Height](http://help.syncfusion.com/js/api/ejfileexplorer#members:height)” and “[Width](http://help.syncfusion.com/js/api/ejfileexplorer#members:width)” property. The dimension can be set in percentage (ex; width: “100 %”), so that the control inherits the width from the parent element.

In the view page, add FileExplorer helper with custom height and width
    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            .Height("300px")
            .Width("900px")
        )
        
    {% endhighlight %}
    
## Customizing the Navigation pane

The navigation pane contains the tree view element which displays all the folders from the filesystem in a hierarchical manner. This is useful to a quick navigation of any folder in the filesystem.

The visibility of the navigation pane can be controlled by the “[ShowNavigationPane](http://help.syncfusion.com/js/api/ejfileexplorer#members:shownavigationpane)” property. By disabling this property, you can hide the navigation pane from FileExplorer.

In the view page, add FileExplorer helper and specify the navigation pane as false
    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            .ShowNavigationPane(false)
        )
        
    {% endhighlight %}
    
## Customizing the Content pane

The content pane is the main part of the Fie explorer UI which displays all the files and folders from the filesystem. The content pane supports the following two types of layout views:

* Grid
* Tile
* Large Icons

The **grid view** displays the files and folders in a grid layout with the details in separate columns. By default the grid view having the four columns which displays the file name, type, date modified and size of the file. For more details about grid view customization, refer [here](#customizing-the-grid-view).

The **tile view** display the files and folders like a small size icons in left side and file details in right. It allows the thumbnails for the image files so that you can view the tiny preview of all image files.

The **large icons view** display the files and folders like a large size icons with name. It allows the thumbnails for the image files so that you can view the tiny preview of all image files.

**Changing the Layout views**
You can change the layout of current view by the switcher which displays at right-bottom of footer in the FileExplorer. By clicking the grid and large icons view buttons you can change the layout of current view.

![](Customization_images/Customization_img1.jpeg)

You can change the layout using toolbar option. While clicking this tool, popup opens with different layout types. Here you can choose any options.

![](Customization_images/Customization_img2.jpeg)

Also the layout views can be changed through the “[Layout](http://help.syncfusion.com/js/api/ejfileexplorer#members:layout)” property.

In the view page, add FileExplorer helper and specify the layout type as shown below
    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            // while rendering it displays as tile view
            .Layout(LayoutType.Tile)        
        )
        
    {% endhighlight %}
    
### Customizing the Grid view

By default sorting is enabled in grid view of FileExplorer, it helps you to sort each columns in ascending or descending order by pressing the corresponding column header. The sorting functionality can be disabled by setting “[AllowSorting](http://help.syncfusion.com/js/api/ejfileexplorer#members:gridsettings-allowsorting)” property to false.

The behavior of the columns can be customized through the “[Columns](http://help.syncfusion.com/js/api/ejfileexplorer#members:gridsettings-columns)” property.

In the view page, add FileExplorer helper with custom grid settings
    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            // under gridSettings you can customize the grid view functionalities
            .GridSettings(settings =>
                // disables the sorting functionality in grid view
                settings.AllowSorting(true)
                // it displays 3 columns only, like this you can display your desired columns at here
                .Column(column =>
                    {
                        column.Add()
                            .Field("name")
                            .HeaderText("Name")
                            .Width("150");
                        column.Add()
                            .Field("dateModified")
                            .HeaderText("Date Modified")
                            .Width("150");
                        column.Add()
                            .Field("size")
                            .HeaderText("Size")
                            .Width("90")
                            .TextAlign(TextAlign.Right)
                            .HeaderTextAlign(TextAlign.Left);
                    }
                )
            )
        )
        
    {% endhighlight %}
    
## Footer Customization

The footer displays the details of the current selected files and folders, and the footer contains the switcher to change the layout view. The visibility of the footer can be customized by the “[ShowFooter](http://help.syncfusion.com/js/api/ejfileexplorer#members:showfooter)” property.

In the view page, add FileExplorer helper and hides the footer as shown below.

    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionDefault"))
            // it hides the footer element
            .ShowFooter(false)       
        )
        
    {% endhighlight %}
    
