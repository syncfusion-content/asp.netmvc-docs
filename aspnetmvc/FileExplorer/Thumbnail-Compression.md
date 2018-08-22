---
title: Thumbnail Image Compression | FileExplorer | ASP.NET MVC | Syncfusion
description: Thumbnail image compression option in FileExplorer
platform: ejmvc
control: FileExplorer
documentation: UG
keywords: Thumbnail image compression option
---

# Thumbnail Image Compression Support

The “FileExplorer” allows thumbnail images to be compressed on the server side and loaded into the “FileExplorer” layout to improve performance when working with large size images.

You can enable this option using “**EnableThumbnailCompress**” API of FileExplorer. For enabling this API, [showThumbnail](https://help.syncfusion.com/api/js/ejfileexplorer#members:showthumbnail) must be set to true in order to render thumbnail preview of images in Tile and LargeIcons layout.

The [beforeGetImage](https://help.syncfusion.com/api/js/ejfileexplorer#events:beforegetimage) event is triggered before loading a requested image from the server and [getImage](https://help.syncfusion.com/api/js/ejfileexplorer#events:getimage) event is triggered after the requested image is loaded.

Refer following code block that will be helpful to you.

In the view page, add “FileExplorer” helper and specify the thumbnail image compress option as specified below.


    {% highlight razor %}

    @(Html.EJ().FileExplorer("fileExplorer")
            .Layout(LayoutType.Tile)
            .Path("~/FileExplorerContent/")
            .AjaxAction(@Url.Content("FileActionThumbnailCompress"))
            .EnableThumbnailCompress(true)
    )

    {% endhighlight %}

In the controller page, specify the “[GetImage](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations~GetImage.html)” handling operation as shown below. This handling function is necessary to compress and load the images in “FileExplorer”, while “EnableThumbnailCompress” option has been enabled.

    {% highlight c# %}
            public ActionResult FileActionThumbnailCompress(FileExplorerParams args)
            {
                FileExplorerOperations operation  = new FileExplorerOperations();
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
                    case "GetImage":
                        //Helps to reduce thumbnail image size before loading it into FileExplorer
                        operation.GetImage(args.Path, args.CanCompress);
                        break;

                }
                return Json("");
            }

    {% endhighlight %}
