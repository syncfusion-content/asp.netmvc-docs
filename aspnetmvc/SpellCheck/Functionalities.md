---
layout: post
title:  SpellCheck | SpellCheck  | ASP.NET MVC | Syncfusion
description: Functionalities
platform: ejmvc
control: SpellCheck 
documentation: ug
keywords: Functionalities, Check Spelling, Ignore Words, IgnoreAll, Ignore Settings, Change Words
---

# Functionalities

## Check Spelling

 The main functionality of the SpellCheck control is checking the spelling of a word and returns the suggestions for an error word.
For example, if you pass the sentence that contains misspell words as input, you can know the error words in this sentence and its suggestions (apt words to replace).

## Ignore Words

The SpellCheck control provides the support to ignore the words from an error word consideration and also to ignore an error words whenever needed. Please refer the following options to ignore the words.

## Ignore

The ignore option is used to ignore a specific word once from the given input string.
The following code example describes the above method implementation.

{% highlight CSHTML %}

@section ControlsSection{

   @Html.EJ().SpellCheck("TextArea").DictionarySettings(dictionary => dictionary.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
   @Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("Spell check using dialog").ClientSideEvents(event => event.Click("showDialog"))
 
}
 
@section ScriptSection{ 

    <script type="text/javascript">    
    
        var target = 'The first <span class="errorspan e-errorword">textarea</span> <span class="errorspan e-errorword">sample</span> uses a dialog <span class="errorspan e-errorword">textarea</span> to display the <span class="errorspan e-errorword">sample</span> spell <span class="errorspan e-errorword">textarea</span> errors';
       
	   function showDialog() {
	   
            var spellObj = $("#TextArea").data("ejSpellCheck");
			
            var targetIgnoreContent = spellObj.ignore("textarea", target, null);
			
        }
    </script>
}

{% endhighlight %}

## IgnoreAll

The ignoreAll option is used to ignore all the error word occurrences from the given input string.

The following code example describes the way of using ignore all method.

{% highlight CSHTML %}

@section ControlsSection{

   @Html.EJ().SpellCheck("TextArea").DictionarySettings(dictionary => dictionary.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
   @Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("Spell check using dialog").ClientSideEvents(event => event.Click("showDialog"))
 
}
 
@section ScriptSection{ 

    <script type="text/javascript">        
	
        var target = 'The first <span class="errorspan e-errorword">textarea</span> <span class="errorspan e-errorword">sample</span> uses a dialog <span class="errorspan e-errorword">textarea</span> to display the <span class="errorspan e-errorword">sample</span> spell <span class="errorspan e-errorword">textarea</span> errors';
        
		function showDialog() {
         
		 var spellObj = $("#TextArea").data("ejSpellCheck");

		 var targetIgnoreContent = spellObj.ignoreAll("textarea", target, null);
      
	  }
    </script>
}

{% endhighlight %}

## Word Collection to Ignore

The ignore words option is used to ignore the collection of words from an error word checking. You can pass the technical terms, brand names which is not present in the dictionary file to this property ignoreWords as shown in the following code example and then while checking the spelling these passed words are considered as a correct word.

{% highlight CSHTML %}

@section ControlsSection{ 
<div id="TextArea" contenteditable="true" name="sentence">
    It is a concept vehicle with Liquid Silver body color, 20-inch wheels, fabric folding roof, electrically-controlled hood,
    4-cylinder 2.0 TDI engine rated 204 PS (150 kW; 201 hp) and 400 (295.02 lbf ft), diesel particulate filter and Bluetech emission control system,
    quattro permanent four-wheel drive system, Audi S tronic dual-clutch gearbox, McPherson-strut front axle and a four-link rear axle, Audi drive select system with 3 modes (dynamic, sport, efficiency),
    MMI control panel with touch pad and dual-view technology, sound system with the prominent extending tweeters JavaScript TypeScript .
</div><br />
   
   @Html.EJ().SpellCheck("TextArea").DictionarySettings(dictionary => dictionary.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ContextMenuSettings(context => context.Enable(true)).IgnoreWords(@ViewBag.datasource)
 
 
   @Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("Spell check").ClientSideEvents(event => event.Click("contextMenu"))
}
 
@section ScriptSection{

    <script type="text/javascript">
	
        function contextMenu() {
		
            var spellObj = $("#TextArea").data("ejSpellCheck");
			
            spellObj.validate();
        }
    </script>
}


public ActionResult ContextMenu()
 {
   string[] spellIgnoreWords = { "color", "Liquid", "folding" };
   
   ViewBag.datasource = spellIgnoreWords;
   
   return View();
 }

 {% endhighlight %}
 
Once you have run the above code, you get an output like below.

![](functionalities_images/contextmenu.png) 

## Ignore Settings

The [ignore settings](/api/js/ejspellcheck#members:ignoresettings) helps to ignore the uppercase, mixed case words, alphanumeric words, file path and email addresses from the error word checking. Ignore settings contains the following options to ignore the words based on their category.

* [ignoreAlphaNumericWords](/api/js/ejspellcheck#members:ignoresettings-ignorealphanumericwords) - ignoring the alpha numeric words from an error word consideration.
* [ignoreUpperCase](/api/js/ejspellcheck#members:ignoresettings-ignoreuppercase) - ignoring the upper case words from an error word consideration.
* [ignoreMixedCaseWords](/api/js/ejspellcheck#members:ignoresettings-ignoremixedcasewords) - ignoring the mixed case words from an error word consideration.
* [ignoreFileNames](/api/js/ejspellcheck#members:ignoresettings-ignorefilenames) - ignoring the file address path from an error word consideration.
* [ignoreUrl](/api/js/ejspellcheck#members:ignoresettings-ignoreurl) - ignoring the url links from an error word consideration.
* [ignoreEmailAddress](/api/js/ejspellcheck#members:ignoresettings-ignoreemailaddress) - ignoring the email address from an error word consideration.


The following code example uses to enable the checking of all the words formed with alphanumeric, uppercase, mixed case words and file paths and email addresses.

{% highlight CSHTML %}

@section ControlsSection{
<div id="TextArea" contenteditable="true" name="sentence">
    It is a concept vehicle with Liquid Silver body color, 20-inch wheels, fabric folding roof, electrically-controlled hood,
    4-cylinder 2.0 TDI engine rated 204 PS (150 kW; 201 hp) and 400 (295.02 lbf ft), diesel particulate filter and Bluetech emission control system,
    quattro permanent four-wheel drive system, Audi S tronic dual-clutch gearbox, McPherson-strut front axle and a four-link rear axle, Audi drive select system with 3 modes (dynamic, sport, efficiency),
    MMI control panel with touch pad and dual-view technology, sound system with the prominent extending tweeters.
</div><br />
 
     @Html.EJ().SpellCheck("TextArea").DictionarySettings(dictionary => dictionary.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ContextMenuSettings(context => context.Enable(true)).IgnoreSettings(ignore=>ignore.IgnoreAlphaNumericWords(false).IgnoreEmailAddress(false).IgnoreFileNames(false).IgnoreHtmlTags(false).IgnoreMixedCaseWords(false).IgnoreUpperCase(false).IgnoreUrl(false))
 
 
    @Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("Spell check").ClientSideEvents(event => event.Click("contextMenu"))
}
 
@section ScriptSection{

    <script type="text/javascript">
	
        function contextMenu () {
		
            var spellObj = $("#TextArea").data("ejSpellCheck");
			
            spellObj.validate();
        }
    </script>
}

{% endhighlight %}

## Change Words

The SpellCheck control provides the support to change an error words from its possible suggestions. Please refer the following options to change an error word.

## Change

The change option is used to replace an error word occurrences once from the given input string with the correct word.
The following code example describes the behavior of change method.

{% highlight CSHTML %}

@section ControlsSection{

   @Html.EJ().SpellCheck("TextArea").DictionarySettings(dictionary => dictionary.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
   @Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("Spell check").ClientSideEvents(event => event.Click("showDialog"))
 
}
 
@section ScriptSection{ 

    <script type="text/javascript">     
	
        var target = 'The first <span class="errorspan e-errorword">textarea</span> <span class="errorspan e-errorword">sample</span> uses a dialog <span class="errorspan e-errorword">textarea</span> to display the <span class="errorspan e-errorword">sample</span> spell <span class="errorspan e-errorword">textarea</span> errors';
        function showDialog() {
		
            var spellObj = $("#TextArea").data("ejSpellCheck");
			
            var targetChangeContent = spellObj.change("textarea", target,"text area",null);
        }
    </script>
}

{% endhighlight %}

## ChangeAll

The changeAll option is used to replace all the occurrences of an error word with the correct word(selected from the suggestions list) from the given inputs string.
The following code example uses to change all the error word occurrences.

{% highlight CSHTML %}

@section ControlsSection{

   @Html.EJ().SpellCheck("TextArea").DictionarySettings(dictionary => dictionary.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
   @Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("Spell check").ClientSideEvents(event => event.Click("showDialog"))
 
}
 
@section ScriptSection{ 

    <script type="text/javascript">  
	
        var target = 'The first <span class="errorspan e-errorword">textarea</span> <span class="errorspan e-errorword">sample</span> uses a dialog <span class="errorspan e-errorword">textarea</span> to display the <span class="errorspan e-errorword">sample</span> spell <span class="errorspan e-errorword">textarea</span> errors';
       
	   function showDialog() {

	   var spellObj = $("#TextArea").data("ejSpellCheck");

	   var targetChangeAllContent = spellObj.changeAll("textarea", target,"text area", null);

			}
    </script>
}

{% endhighlight %}


## Custom Words

The SpellCheck control provides the support to add the custom words into the custom dictionary file.
The addToDictionary option is used to add the custom words into the custom dictionary file.
The following code example uses to add the custom word into the custom dictionary file.

{% highlight CSHTML %}

@section ControlsSection{
<div id="TextArea" contenteditable="true" name="sentence">
    It is a concept vehicle with Liquid Silver body color, 20-inch wheels, fabric folding roof, electrically-controlled hood,
    4-cylinder 2.0 TDI engine rated 204 PS (150 kW; 201 hp) and 400 (295.02 lbf ft), diesel particulate filter and Bluetech emission control system,
    quattro permanent four-wheel drive system, Audi S tronic dual-clutch gearbox, McPherson-strut front axle and a four-link rear axle, Audi drive select system with 3 modes (dynamic, sport, efficiency),
    MMI control panel with touch pad and dual-view technology, sound system with the prominent extending tweeters.
</div><br />
 
     @Html.EJ().SpellCheck("TextArea").DictionarySettings(dictionary => dictionary.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ContextMenuSettings(context => context.Enable(true)).IgnoreSettings(ignore=>ignore.IgnoreAlphaNumericWords(false).IgnoreEmailAddress(false).IgnoreFileNames(false).IgnoreHtmlTags(false).IgnoreMixedCaseWords(false).IgnoreUpperCase(false).IgnoreUrl(false))
 
 
    @Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("Spell check").ClientSideEvents(event => event.Click("showDialog"))
}
 
@section ScriptSection{

    <script type="text/javascript">
	
        function showDialog() {
		
            var spellObj = $("#TextArea").data("ejSpellCheck");
			
            spellObj.addToDictionary("Liquid");
        }
    </script>
}

{% endhighlight %}

You can also add the custom words into the custom dictionary file through the dialog mode or context menu mode add to dictionary option.

* Dialog Mode - Add To Dictionary button will be available in the dialog window, while checking the error in the given input string and clicking this button then the word will be added into the custom dictionary file.
* Context Menu Mode - Add To Dictionary option will be available in the context menu while right click on the error word in the target area and clicking this option then the word will be added into the custom dictionary file.

## Checking content on typing

SpellCheck control provides support for checking the content, on pressing the `Enter` and `Space` key. The cursor position will also be properly retained, while processing the SpellCheck operations. If you enable “enableValidateOnType” property, the spellcheck operation will be carried out on typing.

The following code example describes the above behavior.

{% highlight CSHTML %}

@section ControlsSection{
<div id="TextArea" contenteditable="true" name="sentence">
    It is a concept vehicle with Liquid Silver body color, 20-inch wheels, fabric folding roof, electrically-controlled hood,
    4-cylinder 2.0 TDI engine rated 204 PS (150 kW; 201 hp) and 400 (295.02 lbf ft), diesel particulate filter and Bluetech emission control system,
    quattro permanent four-wheel drive system, Audi S tronic dual-clutch gearbox, McPherson-strut front axle and a four-link rear axle, Audi drive select system with 3 modes (dynamic, sport, efficiency),
    MMI control panel with touch pad and dual-view technology, sound system with the prominent extending tweeters.
</div><br />
 
     @Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ContextMenuSettings(context => context.Enable(true)).EnableValidateOnType(true)
}

{% endhighlight %}

The following screenshot displays the output for the above code

![](functionalities_images/validateontype.png)

You can also validate the content within the IFrame element or IFrame element target text, by passing the IFrame element id or class name value to the `controlsToValidate` property. 
Detailed information is given [here](https://help.syncfusion.com/js/spellcheck/multiple-target)

## Suggestion Words

The `getSuggestionWords` option is used to retrieve the possible suggestion words for an error word which is provided to correct that spelling.

The following code example describes the above behavior.

{% highlight CSHTML %}

@section ControlsSection{
<div id="TextArea" contenteditable="true" name="sentence">
    It is a concept vehicle with Liquid Silver body color, 20-inch wheels, fabric folding roof, electrically-controlled hood,
    4-cylinder 2.0 TDI engine rated 204 PS (150 kW; 201 hp) and 400 (295.02 lbf ft), diesel particulate filter and Bluetech emission control system,
    quattro permanent four-wheel drive system, Audi S tronic dual-clutch gearbox, McPherson-strut front axle and a four-link rear axle, Audi drive select system with 3 modes (dynamic, sport, efficiency),
    MMI control panel with touch pad and dual-view technology, sound system with the prominent extending tweeters.
</div><br />
 
     @Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
}
 
@section ScriptSection{

    <script type="text/javascript">
        $( document ).ready(function() {
			var spellObj = $("#SpellCheck").data("ejSpellCheck");
			spellObj.getSuggestionWords("textarea");
			setTimeout(()=>{
				alert(spellObj._suggestedWords);
			},800);
		});
    </script>
}

{% endhighlight %}

N> You can get the suggestion words after some time interval once this method is called. Since, AJAX request processing takes place in the background.

## Synchronous request

On setting `enableAsync` option to false, enables the synchronous request to the server to perform SpellCheck operations.

The following code example describes the above behavior.

{% highlight CSHTML %}

@section ControlsSection{
<div id="TextArea" contenteditable="true" name="sentence">
    It is a concept vehicle with Liquid Silver body color, 20-inch wheels, fabric folding roof, electrically-controlled hood,
    4-cylinder 2.0 TDI engine rated 204 PS (150 kW; 201 hp) and 400 (295.02 lbf ft), diesel particulate filter and Bluetech emission control system,
    quattro permanent four-wheel drive system, Audi S tronic dual-clutch gearbox, McPherson-strut front axle and a four-link rear axle, Audi drive select system with 3 modes (dynamic, sport, efficiency),
    MMI control panel with touch pad and dual-view technology, sound system with the prominent extending tweeters.
</div><br />
 
     @Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).EnableAsync(false).AjaxDataType("json")
}

{% endhighlight %}

N> You need to set the `ajaxDataType` value as `json` to retrieve the synchronous request result properly.

