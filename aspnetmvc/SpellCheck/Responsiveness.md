---
layout: post
title:  SpellCheck | SpellCheck  | ASP.NET MVC | Syncfusion
description: responsiveness
platform: ejmvc
control: SpellCheck 
documentation: ug
keywords: responsiveness
---

# Responsiveness

The SpellCheck control has support for responsive behavior based on client browser’s width and height. To enable responsive, IsResponsive property should be true.

The following code example describes the above behavior.

{% highlight CSHTML %}

@section ControlsSection{<div id="TextArea" contenteditable="true" name="sentence">
    Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum, Dustin and Chris Hughes.
    The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
</div><br />
 
   @Html.EJ().("TextArea").SpellCheck("TextArea").IsResponsive(true).DictionarySettings(dictionary => dictionary.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
}

{% endhighlight %}

The dialog of spell check control is rendering based on the client browser’s width and height, it can be achieved by IsResponsive property as true.

{% highlight CSHTML %}

@section ControlsSection{<div id="TextArea" contenteditable="true" name="sentence">
    Facebook is a social networking service headquartered in Menlo Park, California. Its website was launched on February 4, 2004, by Mark Zuckerberg with his Harvard College roommates and fellow students Eduardo, Andrew McCollum, Dustin and Chris Hughes.
    The fouders had initially limited the websites membrship to Harvard students, but later expanded it to collges in the Boston area, the Ivy League, and Stanford Univrsity. It graually added support for students at various other universities and later to high-school students.
</div><br />
 
   @Html.EJ().SpellCheck("TextArea").IsResponsive(true).DictionarySettings(dictionary => dictionary.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
    @Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("Spell check using dialog").ClientSideEvents(event => event.Click("showDialog"))
 
}
 
@section ScriptSection{
    <script type="text/javascript">
        function showDialog() {
            var spellObj = $("#TextArea").data("ejSpellCheck");
            spellObj.showInDialog();
        }
    </script>
}

{% endhighlight %}

Mobile Rendering Screenshot

![](responsiveness_images/responsive.png) 