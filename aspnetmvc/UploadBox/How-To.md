---
layout: post
title:  How To | UploadBox | ASP.NET MVC | Syncfusion Server-side rendering
description: How to section of UploadBox widget
platform: ejmvc
control: UploadBox
documentation: ug
---

# How To

## Render UploadBox from code behind

UploadBox can be rendered from the code behind by initializing the required properties in controller and passing those properties via ViewData or Model to the client side

The following code illustrates the rendering of UploadBox using UploadBox properties from code behind.

{% tabs %}

{% highlight razor %}
    
    @{ 
        Html.EJ().Uploadbox("UploadDefault", (Syncfusion.JavaScript.Models.UploadboxProperties)ViewData["upload"]).Render();
      }
			
{% endhighlight %}

{% highlight c# %}
	
     public ActionResult Index()
        {
            UploadboxProperties upload = new UploadboxProperties();
            upload.ExtensionsAllow = ".jpg,.png";
            upload.SaveUrl = "SaveDefault";
            upload.RemoveUrl = "RemoveDefault";
            ViewData["upload"] = upload;
            return View();
        }
        public ActionResult SaveDefault(IEnumerable<HttpPostedFileBase> UploadDefault)
        {
            foreach (var file in UploadDefault)
            {
                var fileName = Path.GetFileName(file.FileName);
                var destinationPath = Path.Combine(Server.MapPath("~/App_Data"), fileName);
                file.SaveAs(destinationPath);

            }
            return Content("");
        }
        public ActionResult RemoveDefault(string[] fileNames)
         {
            foreach (var fullName in fileNames)
            {
                var fileName = Path.GetFileName(fullName);
                var physicalPath = Path.Combine(Server.MapPath("~/App_Data"), fileName);
                if (System.IO.File.Exists(physicalPath))
                {
                    System.IO.File.Delete(physicalPath);
                }
            }
            return Content("");
         }
       }
	
{% endhighlight %}

{% endtabs %}

