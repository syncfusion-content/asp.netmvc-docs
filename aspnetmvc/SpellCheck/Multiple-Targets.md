---
layout: post
title:  SpellCheck | SpellCheck  | ASP.NET MVC | Syncfusion
description: Multiple Targets
platform: ejmvc
control: SpellCheck 
documentation: ug
keywords: multiple targets, dialog mode, contextmenu mode
---

# Multiple Targets

The SpellCheck control has support for multiple target HTML element's texts spelling and correct its error words. This can be achieved by passing the target HTML elements “id” values to the property “ControlsToValidate”.

You can spell check most of the HTML element’s texts such as div, span, textarea, input, address and article by using this property.

The multiple target HTML element supports in both the modes.

 * Dialog Mode
 * Context Menu Mode
 
The following code example describes the above behavior.

{% highlight CSHTML %}

@section ControlsSection{
    <div id="control1">
        London, one of the most popular touist destinations in the world for a reason. A cultural and hisorical hub, London has an excellent public transportation system that allows visitors to see all the fantatic sights without spending a ton of money on a rental car.
        London contains four World Heritage Sites.
    </div><br />
    <textarea id="control2" style="width:940px">
        Paris, the city of lihts and love - this short guide is full of ideas for how to make the most of the romnticism that oozes from every one of its beautiful corners.You couldn't possibly visit Rome, one of the world's most facinating cities. The old adage that Rome was not built in a day - and that you won't see it in one or even in three - is true. For the intrepid traveler who can keep pace, here is a list of must-sees.
        But reember what the Romans say: Even a lifetime isn't enough to see Rome.
    </textarea><br />
    <span id="control3">
        Rome, one of the world's most facinating cities. The old adage that Rome was not built in a day - and that you won't see it in one or even in three - is true. For the intrepid traveler who can keep pace, here is a list of must-sees.
        But reember what the Romans say: Even a lifetime isn't enough to see Rome.
    </span><br /><br />
 
    @Html.EJ().SpellCheck("TextArea").ControlsToValidate("control1,control2,control3").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
    @Html.EJ().Button("SpellCheck").Text("Spell check using dialog").ClientSideEvents(evet => evet.Click("showDialog"))
  }

{% endhighlight %}

N> You need to pass the target HTML element's id value with the comma separator. For example, in the above code example passed id values of div(control1), textarea(control2) and span(control3) element.

## Dialog Mode

If the user specifies multiple targets in ControlsToValidate property, the control must loop through the multiple HTML target elements one by one in the order which they are specified and process of every individual target’ content. 

{% highlight CSHTML %}

@section ControlsSection{
    <div id="control1">
        London, one of the most popular touist destinations in the world for a reason. A cultural and hisorical hub, London has an excellent public transportation system that allows visitors to see all the fantatic sights without spending a ton of money on a rental car.
        London contains four World Heritage Sites.
    </div><br />
    <textarea id="control2" style="width:940px">
        Paris, the city of lihts and love - this short guide is full of ideas for how to make the most of the romnticism that oozes from every one of its beautiful corners.You couldn't possibly visit Rome, one of the world's most facinating cities. The old adage that Rome was not built in a day - and that you won't see it in one or even in three - is true. For the intrepid traveler who can keep pace, here is a list of must-sees.
        But reember what the Romans say: Even a lifetime isn't enough to see Rome.
    </textarea><br />
    <span id="control3">
        Rome, one of the world's most facinating cities. The old adage that Rome was not built in a day - and that you won't see it in one or even in three - is true. For the intrepid traveler who can keep pace, here is a list of must-sees.
        But reember what the Romans say: Even a lifetime isn't enough to see Rome.
    </span><br /><br />
 
    @Html.EJ().SpellCheck("TextArea").ControlsToValidate("control1,control2,control3").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
    @Html.EJ().Button("SpellCheck").Text("Spell check using dialog").ClientSideEvents(evet => evet.Click("showDialog"))
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


## Context Menu Mode

By using ControlsToValidate property, you can spell check Multiple HTML elements at the same time through context menu. You can correct error word by right click on the error word and choose the corresponding context menu option.

{% highlight CSHTML %}

@section ControlsSection{
    <div id="control1">
        London, one of the most popular touist destinations in the world for a reason. A cultural and hisorical hub, London has an excellent public transportation system that allows visitors to see all the fantatic sights without spending a ton of money on a rental car.
         London contains four World Heritage Sites.
  </div><br />
    <textarea id="control2" style="width:940px">
        Paris, the city of lihts and love - this short guide is full of ideas for how to make the most of the romnticism that oozes from every one of its beautiful corners.You couldn't possibly visit Rome, one of the world's most facinating cities. The old adage that Rome was not built in a day - and that you won't see it in one or even in three - is true. For the intrepid traveler who can keep pace, here is a list of must-sees.
        But reember what the Romans say: Even a lifetime isn't enough to see Rome.
    </textarea><br />
    <span id="control3">
        Rome, one of the world's most facinating cities. The old adage that Rome was not built in a day - and that you won't see it in one or even in three - is true. For the intrepid traveler who can keep pace, here is a list of must-sees.
        But reember what the Romans say: Even a lifetime isn't enough to see Rome.
    </span><br /><br />
 
    @Html.EJ().SpellCheck("TextArea").ControlsToValidate("control1,control2,control3").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
    @Html.EJ().Button("SpellCheck").Text("Spell check using context menu").ClientSideEvents(evet => evet.Click("showContextMenu"))
  }
   @section ScriptSection{
    <script type="text/javascript">
        function showContextMenu() {
            var spellObj = $("#TextArea").data("ejSpellCheck");
            spellObj.validate();
        }
    </script>
}

{% endhighlight %}


N> We couldn’t highlight the error word in the target element itself, while checking the elements that doesn’t support the html or innerHTML value.


 



