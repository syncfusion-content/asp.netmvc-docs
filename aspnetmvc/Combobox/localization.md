---
layout: post
title: Localization in ComboBox control for Syncfusion ASP.NET MVC
description: Localization support to ComboBox control for Syncfusion ASP.NET MVC
platform: mvc
control: ComboBox
documentation: ug
keywords: locale, ComboBox
---

# Localization

The Localization library allows you to localize the static text content of the **noRecordsTemplate** and **actionFailureTemplate** &nbsp;properties according to the culture currently assigned to the ComboBox.

| Locale key | en-US (default)  |
|------|------|-------------|
| noRecordsTemplate |  No records found |
| actionFailureTemplate | The request failed |

## Loading translations

To load translation object to your application, use the `load` function of **L10n** class.

In the following sample, French culture is set to the ComboBox and no data is loaded. Hence, the `noRecordsTemplate` property displays its text in French culture initially, and if the sample is run offline, the `actionFailureTemplate` property displays its text appropriately.


{% highlight html %}

<div class="frame">
        <div class="control">
            @{
                Html.EJ()
                    .ComboBox("searchCustomer")
                    .Datasource(d => d.URL("//js.syncfusion.com/ejServices/wcf/NorthWind.svc/").Offline(false).CrossDomain(true))
                    .Query("ej.Query().from('Suppliers').select('SupplierID', 'ContactName').take(0)")
                    .ComboBoxFields(f => f.Text("ContactName").Value("SupplierID"))
                    .Width("100%")
                    .Locale("fr-BE")
                    .Placeholder("Sélectionnez un customer")
                    .Render();
            }
        </div>
    </div>
    <script>
        ej.ComboBox.locale["fr-BE"]={
                'noRecordsTemplate': "Aucun enregistrement trouvé",
                'actionFailureTemplate': "Modèle d'échec d'action"
            }
        
    </script>


{% endhighlight %}

{% highlight c# %}

public ActionResult Databindingremote()
        {
            return View();
        }

{% endhighlight %}

![](Combobox_localization_images/localization.png)