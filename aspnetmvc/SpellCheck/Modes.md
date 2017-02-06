---
layout: post
title:  SpellCheck | SpellCheck  | ASP.NET MVC | Syncfusion
description: modes
platform: ejmvc
control: SpellCheck 
documentation: ug
keywords: Operations, Dialog Mode, Context Menu Mode, Handling Dialog Actions, Context Menu Mode, Handling Menu Actions
---


# Operations

Essential SpellCheck provides two ways to perform the spellcheck operation(error correction). They are,

 * Dialog Mode
 * Context Menu Mode
 
## Dialog Mode

### Description

SpellCheck provides the dialog mode option to perform the following spellcheck operations.

 * Ignore Once
 * IgnoreAll
 * Change
 * ChangeAll
 * Add to Dictionary
 
## Open Dialog Mode

The following code snippet shows how to open the dialog to spell check the content.

{% highlight CSHTML %}

@section ControlsSection{

   @Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords"))
 
    @Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("Spell check using dialog").ClientSideEvents(evet => evet.Click("showDialog"))
 
}
 
@section ScriptSection{
    <script type="text/javascript">
        function showDialog() {
            var spellObj = $("#TextArea").data("ejSpellCheck");
            spellObj.showInDialog();
        }
    </script>
	
{% endhighlight %}
	
## Handling Dialog Actions

To define the specific actions before the dialog window open, the client-side event dialogBeforeOpen can be used as depicted in the below code example.

{% highlight CSHTML %}

@section ControlsSection{

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ClientSideEvents(evt => evt.DialogBeforeOpen("onDialogBeforeOpen"))
 
@Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("spell check using dialog").ClientSideEvents(evet => evet.Click("showDialog"))

}

@section ScriptSection{
    <script type="text/javascript">
        function showDialog() {
            var spellObj = $("#TextArea").data("ejSpellCheck");
            spellObj.showInDialog();
        }
       function onDialogBeforeOpen(args) { 
             if (args.requestType == "dialogBeforeOpen") 
               {
                alert("dialog before open event triggered"); 
               } 
              }
    </script>

{% endhighlight %}
	
The client-side event dialogOpen can be used to define the specific actions after the dialog window open as shown in the following code example.

{% highlight CSHTML %}

@section ControlsSection{

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ClientSideEvents(evt => evt.DialogOpen("onDialogOpen"))
 
@Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("spell check using dialog").ClientSideEvents(evet => evet.Click("showDialog"))

}

@section ScriptSection{
    <script type="text/javascript">
        function showDialog() {
            var spellObj = $("#TextArea").data("ejSpellCheck");
            spellObj.showInDialog();
        }
       function onDialogOpen(args) { 
          if (args.requestType == "dialogOpen") 
              { 
               alert(args.targetText); 
            } }
    </script>

	{% endhighlight %}
	
	
The following code example used to define some actions after the dialog closing by using the client-side event dialogClose.

{% highlight CSHTML %}

@section ControlsSection{

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ClientSideEvents(evt => evt.DialogClose("onDialogClose"))
 
@Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("spell check using dialog").ClientSideEvents(evet => evet.Click("showDialog"))

}

@section ScriptSection{
    <script type="text/javascript">
        function showDialog() {
            var spellObj = $("#TextArea").data("ejSpellCheck");
            spellObj.showInDialog();
        }
       function onDialogClose(args) { 
           if (args.requestType == "dialogClose") 
            { 
             alert(args.updatedText); 
             } }    
        </script>
		
{% endhighlight %}

It is possible to predict the error word details before starting the spellcheck operations through dialog mode by using the client side event start. The below code example describes the above behavior.

{% highlight CSHTML %}

@section ControlsSection{

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ClientSideEvents(evt => evt.Start("onSpellCheckStart"))
 
@Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("spell check using dialog").ClientSideEvents(evet => evet.Click("showDialog"))

}

@section ScriptSection{
    <script type="text/javascript">
        function showDialog() {
            var spellObj = $("#TextArea").data("ejSpellCheck");
            spellObj.showInDialog();
        }
        function onSpellCheckStart(args) { 
             if (args.requestType == "spellCheckDialog") 
             { 
               alert(args.errorWords); 
             } }
        </script>
}

{% endhighlight %}

You can get the corrected text content details before updating it into target element with the help of the client side event complete as mentioned in the below code example.

{% highlight CSHTML %}

@section ControlsSection{

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ClientSideEvents(evt => evt.Complete("onCheckComplete"))
 
@Html.EJ().Button("SpellCheck").Width("200px").Height("25px").Text("spell check using dialog").ClientSideEvents(evet => evet.Click("showDialog"))

}

@section ScriptSection{
    <script type="text/javascript">
        function showDialog() {
            var spellObj = $("#TextArea").data("ejSpellCheck");
            spellObj.showInDialog();
        }
        function onCheckComplete(args) { 
             if (args.requestType == "changeErrorWord") 
              { 
                alert(args.targetText); 
               
              } }
        </script>

{% endhighlight %}

## Context Menu Mode

SpellCheck provides default context menu options to perform the spellcheck operations. It also allows to define additional custom context menu options.

The options that are available under contextMenuSettings are as follows,
 * enable - Enables/disables the context menu option in SpellCheck.
 * menuItems - Contains the options to perform spellcheck operations.

## Default Menu Options

The menu items contains the following options to perform the spellcheck operation.
 * IgnoreAll
 * Add to Dictionary

The following code snippet shows how to enable the context menu settings in SpellCheck and to make use of it with default available options.

{% highlight CSHTML %}

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ContextMenuSettings(items=>items.Enable(true).MenuItems(menuItem=>menuItem.ID("IgnoreAll").Text("Ignore All")))


{% endhighlight %}

N> For default menu items, the id must be defined the same as mentioned in the above code example – as we have processed the menus based on this id within our source.

## Custom Menu Options

Apart from the default available options, it is also possible to add custom menu options to the context-menu list.
The following code example depicts how to add the custom menu items into the context menu settings.

{% highlight CSHTML %}

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ContextMenuSettings(items=>items.Enable(true).MenuItems(menuItem=>menuItem.ID("IgnoreAll").Text("Ignore All")))

{% endhighlight %}

N> The id given for the custom menu items must be unique.

## Handling Menu Actions

The client-side event contextClick can be used to define specific actions when a click made on the custom menu items. The following code example describes the above behavior.

{% highlight CSHTML %}

@section ControlsSection{

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ContextMenuSettings(items => items.Enable(true).MenuItems(menuItem => menuItem.ID("IgnoreAll").Text("Ignore All"))).ClientSideEvents(evts => evts.ContextClick("onCustomMenuClick"))

}

@section ScriptSection{
    <script type="text/javascript">
        function onCustomMenuClick(args) { 
                if (args.selectedOption == "Ignore") 
                   { 
                     alert("Custom menu clicked");
                   } }
        </script>

{% endhighlight %}

It is possible to predict the target (error word) on which the right click is made with the use of the event contextOpen. The below code example shows how to block the display of context menu, when right clicked on the word by setting args.cancel as true.

{% highlight CSHTML %}

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ContextMenuSettings(items => items.Enable(true).MenuItems(menuItem => menuItem.ID("IgnoreAll").Text("Ignore All"))).ClientSideEvents(evts => evts.ContextOpen("onContextOpen"))

@section ScriptSection{
    <script type="text/javascript">
        function onContextOpen (args) { 
                if (args.selectedOption == "Ignore") 
                   { 
                     alert("Custom menu clicked");
                   } }
        </script>

{% endhighlight %}

You can get the current spell check operation arguments details with the client-side event validating. The following code example describes the way to block the ignoreAll operation for the particular word.

{% highlight CSHTML %}

@Html.EJ().SpellCheck("TextArea").DictionarySettings(dic => dic.CustomDictionaryUrl("../api/SpellCheck/AddToDictionary").DictionaryUrl("../api/SpellCheck/CheckWords")).ContextMenuSettings(items => items.Enable(true).MenuItems(menuItem => menuItem.ID("IgnoreAll").Text("Ignore All"))).ClientSideEvents(evts => evts.Validating("onSpellChecking"))
@section ScriptSection{
    <script type="text/javascript">
        function onSpellChecking (args) { 
                if (args.selectedOption == "Ignore") 
                   { 
                     alert("Custom menu clicked");
                   } }
        </script>
		
{% endhighlight %}
