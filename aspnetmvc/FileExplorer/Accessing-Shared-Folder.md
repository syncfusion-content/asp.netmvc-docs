---
title: Accessing shared folder | FileExplorer | ASP.NET MVC | Syncfusion
description: Accessing shared folder in FileExplorer
platform: ejmvc
control: FileExplorer
documentation: UG
keywords: Accessing shared folder option
---

# Access shared folder using FileExplorer

Using “FileExplorer”, you can manage the files that are available in a shared folder of another system which is connected through LAN. Refer following steps, here you will see the details about accessing the shared folder with FileExplorer. 

First you have to specify the shared folder path in any of following formats.

1. “\\Server\SharedFolder”
2. “\\Server”
3. “//Server/SharedFolder”
4. “//Server”

In the view page, add “FileExplorer” helper and specify the shared path as following format.


    {% highlight razor %}

        @(Html.EJ().FileExplorer("fileExplorer")
            .Layout(LayoutType.Tile)
            .Path(@"\\Server\SharedFolder")
            .AjaxAction(@Url.Content("FileActionDefault")))

    {% endhighlight %}

In the controller page, specify the file handling operation as shown below. This handling functions are necessary to perform file operations in FileExplorer.

    {% highlight c# %}

    public ActionResult FileActionDefault(FileExplorerParams args)
            {
                FileExplorerOperations operation = new FileExplorerOperations();
                switch (args.ActionType)
                {
                    case "Read":
                        return Json(operation.Read(args.Path, args.ExtensionsAllow));
                    case "CreateFolder":
                        return Json(operation.CreateFolder(args.Path, args.Name));
                    case "Paste":
                        return Json(operation.Paste(args.LocationFrom, args.LocationTo, args.Names, args.Action, args.CommonFiles));
                    case "Remove":
                        return Json(operation.Remove(args.Names, args.Path));
                    case "Rename":
                        return Json(operation.Rename(args.Path, args.Name, args.NewName, args.CommonFiles));
                    case "GetDetails":
                        return Json(operation.GetDetails(args.Path, args.Names));
                    case "Download":
                        operation.Download(args.Path, args.Names);
                        break;               
                    case "Upload":
                        operation.Upload(args.FileUpload, args.Path);
                        break;
                    case "Search":
                        return Json(operation.Search(args.Path, args.ExtensionsAllow, args.SearchString, args.CaseSensitive));
                }
                return Json("");
            }

    {% endhighlight %}

**Authentication problem in shared folder**

If shared folder is restricted with authentication, that time you are not able to access this folder using our FileExplorer. Here you will get an exception like “**System.UnauthorizedAccessException, Please add your windows credential details to open '\\server\'**”. In order to solve this problem, you have to add the shared folder credential details in the windows credential manager that is available in your service hosted machine.

![](Accessingsharedfolder_images/Accessingsharedfolder_img1.jpeg)

