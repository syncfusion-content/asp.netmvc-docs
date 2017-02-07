---
layout: post
title:  SpellCheck | SpellCheck  | ASP.NET MVC | Syncfusion
description: dictionary
platform: ejmvc
control: SpellCheck 
documentation: ug
keywords: Dictionary, Default Dictionary, Custom Dictionary
---

# Dictionary

Essential ASP.NET MVC SpellCheck uses two different types of dictionary.

 * Default Dictionary
 * Custom Dictionary
 
## Default Dictionary

The default dictionary is a primary dictionary file location to read the dictionary words for comparing it with the input words to identify its erroneous.
The following code example depicts the way to mention the default dictionary path and to read its content.

{% highlight C# %}

SpellCheckController() 

{
 
if (baseDictionary == null) 

{ 

// Here you need to specify the corresponding file name (ex. Default.dic) 

string filePath = HttpContext.Current.Server.MapPath("~/App_Data/SpellCheck/Default.dic"); 

Stream stream = new FileStream(filePath, FileMode.Open, FileAccess.Read); 

baseDictionary = new SpellCheckerBase(stream); 

}
 
this.CustomFileRead(); 

}

{% endhighlight %}


## Custom Dictionary

The custom dictionary is a collection of custom words that are used for spell checking (i.e. technical terms/words, company names, etc.,).
The following code example describes the way to mention the custom dictionary path to read its content.

{% highlight C# %} 

private readonly string _customFilePath = HttpContext.Current.Server.MapPath("~/App_Data/SpellCheck/Custom.dic"); 

// Here you need to specify the corresponding custom dictionary file name 

private void CustomFileRead() 
{ 

Stream stream1 = new FileStream(_customFilePath, FileMode.Open, FileAccess.ReadWrite); 

customDictionary = new SpellCheckerBase(stream1); 

}

{% endhighlight %} 

N> The custom words will be displayed within the custom dictionary file line by line (i.e. one word per line).

### Add a Word to Custom dictionary

You can directly add the necessary words in the custom dictionary file or else by using the SpellCheck control public method addToDictionary to add the custom words one by one.
