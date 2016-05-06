---
title: Customizing Ajax handling functions | FileExplorer | ASP.NET MVC | Syncfusion
description: Customizing Ajax handling function on server side 
platform: ASP.NET MVC
control: FileExplorer
documentation: UG
keywords: FileExplorer,  Syncfusion, ASP.NET MVC FileExplorer, UG document, Customizing Ajax handling function 
---
# Customizing Ajax Handling Functions

In FileExplorer, server side functionalities are necessary to handle the Ajax request of FileExplorer. Here “**Syncfusion.EJ**” assembly contains built-in “[BasicFileOperations](http://help.syncfusion.com/cr/cref_files/aspnetmvc/dociohelper/Syncfusion.EJ~Syncfusion.JavaScript.BasicFileOperations.html#)” abstract class and implementation of “[FileExplorerOperations](http://help.syncfusion.com/cr/cref_files/aspnetmvc/dociohelper/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations.html#)” class for providing the content to FileExplorer and handling Ajax requests**.** If is it necessary, you can customize the server side functionalities of FileExplorer as per your requirement. 

## Override the existing Syncfusion.JavaScript.FileExplorerOperations class

Using “[FileExplorerOperations](http://help.syncfusion.com/cr/cref_files/aspnetmvc/dociohelper/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations.html#)” class, you can manage the underlying machine's physical file system with the help of FileExplorer control. Here you can override the necessary methods that is available in “**FileExplorerOperations**” by sub classing the existing “**FileExplorerOperations**” class.

Below code example shows how to override “[GetDetails](#_GetDetails(string,_string[],_IEnume)” method, which is available in “**FileExplorerOperations**”
    
    {% highlight c# %}
    
        public class FileExplorerCustomOperations : FileExplorerOperations
        {
            FileExplorerOperations operation = new FileExplorerOperations();
            CustomFileExplorerResponse customDetails = new CustomFileExplorerResponse();        
            public override object GetDetails(string path, string[] names, IEnumerable<object> selectedItems = null)
            {
                FileExplorerResponse response = (FileExplorerResponse) operation.GetDetails(path, names);            
                FileDetails fDetails = response.details.ElementAt(0) ;            
                CustomFileDetails cfDetails =new CustomFileDetails() ;
                CustomFileDetails[] responseDetails = new CustomFileDetails[1];
                cfDetails.Name= fDetails.Name;
                cfDetails.Location= fDetails.Location;            
                cfDetails.Size= fDetails.Size;
                cfDetails.Created= fDetails.Created;            
                cfDetails.IsFile = (fDetails.Type == "File Folder"? "false" : "true");
                responseDetails[0] = cfDetails;
                customDetails.details = responseDetails;
                return customDetails;
            }
        }
        public class CustomFileDetails
        {
            public string Name { get; set; }
            public string Location { get; set; }        
            public long Size { get; set; }
            public string Created { get; set; }        
            public string IsFile { get; set; }
        }
        public class CustomFileExplorerResponse
        {
            public IEnumerable<FileExplorerDirectoryContent> files { get; set; }
            public IEnumerable<CustomFileDetails> details { get; set; }
            public object error { get; set; }
        }
    
    
    {% endhighlight %}
    
## Implement a new custom class to handle Ajax request and provide content for FileExplorer

When overriding the particular methods were not enough, you can create a new custom class using “[BasicFileOperations](http://help.syncfusion.com/cr/cref_files/aspnetmvc/dociohelper/Syncfusion.EJ~Syncfusion.JavaScript.BasicFileOperations.html#)” abstract class. It helps to provide different file sources to be used the content for FileExplorer control, such as database system, physical system or online storage system such as Azure. 

### Notes to Implementers

When you implement a derived class of “BasicFileOperations”, you must provide implementations for following methods and its details has been given in this [section](#_Abstract_methods_in)

* Read
* CreateFolder
* Remove
* Rename
* Paste
* Upload
* Download
* GetDetails
* GetImage
* Search

### Abstract methods in BasicFileOperations Class

#### Read(path, string, IEnumerable&lt;object&gt; )

It used to get all immediate files and sub-folders of the given path and it returns the matched type of files only, which are specified in “filter” parameter.

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract object Read(string path, string filter, IEnumerable<object> selectedItems= null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Function Read(path As String, filter As String, Optional selectedItems As IEnumerable(Of Object) = Nothing) As Object
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
path
</td>
<td>
String
</td>
<td>
specifies the path of selected folder
</td>
</tr>
<tr>
<td>
filter
</td>
<td>
String
</td>
<td>
specifies the file types that need to be filter and return 
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about selected folder
</td>
</tr>
</table>

Response data should be in JSON format with key name as ‘files’ and JSON fields should be with following field names *“name, isFile, hasChild”.*

*For example:* 
    
    {% highlight javascript %}
    
    {
    "files":[{"name":"bird.jpg","type":"File","size":102182,"dateModified":"1/9/2016 6:48:42 AM","hasChild":false,"isFile":true,"filterPath":null},
    {"name":"sea.jpg","type":"File","size":97145,"dateModified":"1/9/2016 6:48:42 AM","hasChild":false,"isFile":true,"filterPath":null }],
    "details":null,
    "error":null
    }
    
    {% endhighlight %}
    
N> If needed, customer can also add additional data along with existing properties of “[FileExplorerDirectoryContent](http://help.syncfusion.com/cr/cref_files/aspnetmvc/dociohelper/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerDirectoryContent.html#)” class.

#### CreateFolder(string, string, IEnumerable&lt;object&gt;)

It used to create a new folder in given path with specified name

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract object CreateFolder(string path, string name, IEnumerable<object> selectedItems = null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Function CreateFolder(path As String, name As String, Optional selectedItems As IEnumerable(Of Object) = Nothing) As Object
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
path
</td>
<td>
String
</td>
<td>
specifies the path of selected folder
</td>
</tr>
<tr>
<td>
name
</td>
<td>
String
</td>
<td>
specifies the name for new folder
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about selected folder
</td>
</tr>
</table>

Response data should be in JSON format with key name as ‘files’. In that returning JSON, “**name**” field is necessary.

    
    {% highlight javascript %}
    
    {"files":[{"name":"New folder","type":"Directory","size":0,"dateModified":"2/25/2016 7:31:02 AM","hasChild":true,"isFile":false,"filterPath":null}],"details":null,"error":null}
    
    {% endhighlight %}
    

#### Remove(string[], string path, IEnumerable&lt;object&gt;)

It helps to remove the specified items from given path. Here you may return the removed file details or null.

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract object Remove(string[] names, string path, IEnumerable<object> selectedItems = null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Function Remove(names As String(), path As String, Optional selectedItems As IEnumerable(Of Object) = Nothing) As Object
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
names
</td>
<td>
String[]
</td>
<td>
specifies the selected item names, which is going to be removed
</td>
</tr>
<tr>
<td>
path
</td>
<td>
String
</td>
<td>
specifies the parent folder path of selected items
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about selected items, which is going to be removed
</td>
</tr>
</table>

#### Rename(string, string, string, IEnumerable&lt;CommonFileDetails&gt;, IEnumerable&lt;object&gt;)

This method helps to rename the file/folder, which is available in given path. Here you may return the renamed file details or null.

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract object Rename(string path, string oldName, string newName, IEnumerable<CommonFileDetails> commonFiles, IEnumerable<object> selectedItems = null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Function Rename(path As String, oldName As String, newName As String, commonFiles As IEnumerable(Of CommonFileDetails), Optional selectedItems As IEnumerable(Of Object) = Nothing) As Object
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
path
</td>
<td>
String
</td>
<td>
specifies the parent folder path of renaming item
</td>
</tr>
<tr>
<td>
oldName
</td>
<td>
String
</td>
<td>
specifies the existing file name
</td>
</tr>
<tr>
<td>
newName
</td>
<td>
String
</td>
<td>
specifies the new file name
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about selected items, which is going to be renamed
</td>
</tr>
<tr>
<td>
commonFiles
</td>
<td>
IEnumerable&lt;CommonFileDetails&gt;
</td>
<td>
It contains the details about already existing files, which contains same name and type as given in new file with same parent folder.
</td>
</tr>
</table>

#### Paste(string, string, string[], string, IEnumerable&lt;CommonFileDetails&gt;, IEnumerable&lt;object&gt; , IEnumerable&lt;object&gt;)

This method helps to copy or move files from one location to another location. Here you may return the pasted file details or null.

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract object Paste(string sourceDir, string backupDir, string[] names, string option, IEnumerable<CommonFileDetails> commonFiles, IEnumerable<object> selectedItems = null, IEnumerable<object> targetFolder = null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Function Paste(sourceDir As String, backupDir As String, names As String(), [option] As String, commonFiles As IEnumerable(Of CommonFileDetails), Optional selectedItems As IEnumerable(Of Object) = Nothing, Optional targetFolder As IEnumerable(Of Object) = Nothing) As Object
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
sourceDir
</td>
<td>
String
</td>
<td>
specifies the path of source directory
</td>
</tr>
<tr>
<td>
backupDir
</td>
<td>
String
</td>
<td>
specifies the path of destination directory
</td>
</tr>
<tr>
<td>
names
</td>
<td>
String[]
</td>
<td>
Specifies the name of file/ folders, which are going to be pasted in destination folder.
</td>
</tr>
<tr>
<td>
option
</td>
<td>
String
</td>
<td>
specifies the operation type “move” or “copy”
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about selected items, which is going to be pasted
</td>
</tr>
<tr>
<td>
commonFiles
</td>
<td>
IEnumerable&lt;CommonFileDetails&gt;
</td>
<td>
It contains the details about already existing files in destination folder, which contains the files in same name and type as same as newly copied files.
</td>
</tr>
<tr>
<td>
targetFolder
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about target folder, where the files are going to be pasted.
</td>
</tr>
</table>

#### Upload(IEnumerable&lt;System.Web.HttpPostedFileBase&gt;, string, IEnumerable&lt;object&gt;)

This method helps to upload the specified files to given directory and the return type of this method is “void”. 

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract void Upload(IEnumerable<System.Web.HttpPostedFileBase> files, string path, IEnumerable<object> selectedItems=null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Sub Upload(files As IEnumerable(Of System.Web.HttpPostedFileBase), path As String, Optional selectedItems As IEnumerable(Of Object) = Nothing)
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
files
</td>
<td>
IEnumerable&lt;System.Web.HttpPostedFileBase&gt;
</td>
<td>
Specifies the file details that is going to be uploaded
</td>
</tr>
<tr>
<td>
path
</td>
<td>
String
</td>
<td>
specifies the path of destination directory, where the files need to be uploaded
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about selected items, which is going to be uploaded.
</td>
</tr>
</table>

#### Download(string, string[], IEnumerable&lt;object&gt;)

This method helps to download the specified files and the return type of this method is “void”.

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract void Download(string path, string[] names, IEnumerable<object> selectedItems=null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Sub Download(path As String, names As String(), Optional selectedItems As IEnumerable(Of Object) = Nothing)
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
path
</td>
<td>
String
</td>
<td>
Specifies the parent directory path of selected files, which is going to be download
</td>
</tr>
<tr>
<td>
names
</td>
<td>
String[]
</td>
<td>
specifies the name of files that is need to be downloaded
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about files, which is going to be downloaded.
</td>
</tr>
</table>

#### GetDetails(string, string[], IEnumerable&lt;object&gt;)

This method used to get the details of the specified file or directory.

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract object GetDetails(string path, string[] names, IEnumerable<object> selectedItems=null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Function GetDetails(path As String, names As String(), Optional selectedItems As IEnumerable(Of Object) = Nothing) As Object
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
path
</td>
<td>
String
</td>
<td>
Specifies the parent directory path of selected file
</td>
</tr>
<tr>
<td>
names
</td>
<td>
String[]
</td>
<td>
Specifies the name of files in order to get it’s details
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the basic details about selected files
</td>
</tr>
</table>

Response data should be in JSON format like below


    
    {% highlight javascript %}
    
    {details:[{CreationTime:"4/28/2015 9:44:32 AM", Extension:".png", Format:"Archive", FullName:"F:\All samples\FileExplorer_Custom\FileExplorerContent\human.png", LastAccessTime:"4/28/2015 9:44:32 AM", LastWriteTime:"3/31/2015 3:16:35 PM", Length:11059, Name:"human.png"}]}
    
    {% endhighlight %}
    

    
N> Here you may add additional date fields along with existing JSON data using “FileDetails” class.

#### GetImage(string, IEnumerable&lt;object&gt;)

This method helps to get an image using “HttpResponse” option and the return type of this method is void.

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract void GetImage(string path, IEnumerable<object> selectedItems=null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Sub GetImage(path As String, Optional selectedItems As IEnumerable(Of Object) = Nothing)
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
path
</td>
<td>
String
</td>
<td>
specifies the path of image file
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about selected image
</td>
</tr>
</table>

#### Search(string, string, string, bool, IEnumerable&lt;object&gt;)

It used to search all the matched files and sub-folders in the given folder path also it filters the specified files using it types.

**Syntax**

    {% tabs %}
    
    {% highlight c# %}
    
    public abstract object Search(string path, string filter, string searchString, bool caseSensitive, IEnumerable<object> selectedItems = null)
    
    {% endhighlight %}
    
    {% highlight vb.net %}
    
    Public MustOverride Function Search(path As String, filter As String, searchString As String, caseSensitive As Boolean, Optional selectedItems As IEnumerable(Of Object) = Nothing) As Object
    
    {% endhighlight %}
    
    {% endtabs %}
    
**Parameters**

<table>
<tr>
<td>
{{'**Name**'| markdownify }}
</td>
<td>
{{'**Type**'| markdownify }}
</td>
<td>
{{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
path
</td>
<td>
String
</td>
<td>
specifies the directory path
</td>
</tr>
<tr>
<td>
filter
</td>
<td>
String
</td>
<td>
specifies the file types to filter
</td>
</tr>
<tr>
<td>
searchString
</td>
<td>
String
</td>
<td>
specifies the search string
</td>
</tr>
<tr>
<td>
caseSensitive
</td>
<td>
Bool
</td>
<td>
specifies the case sensitive option
</td>
</tr>
<tr>
<td>
selectedItems
</td>
<td>
IEnumerable&lt;object&gt;
</td>
<td>
It contains the details about selected folder
</td>
</tr>
</table>

It should return data in JSON format with key name as ‘files’ and JSON fields need to be with following field names *“name, isFile, hasChild”.*

*For example:* 
    
    
    
    {% highlight javascript %}
    
    {
    "files":[{"name":"bird.jpg","type":"File","size":102182,"dateModified":"1/9/2016 6:48:42 AM","hasChild":false,"isFile":true,"filterPath":null},
    {"name":"sea.jpg","type":"File","size":97145,"dateModified":"1/9/2016 6:48:42 AM","hasChild":false,"isFile":true,"filterPath":null }],
    "details":null,
    "error":null
    }
    
    {% endhighlight %}
    
    
N> If needed, customer can also add additional data along with existing properties using “FileExplorerDirectoryContent” class.

Here you need to implement new class by sub classing the existing “**BasicFileOperations**” abstract class.

    
    {% highlight c# %}
    
    public class NewClass : BasicFileOperations
        {
    
            public override object CreateFolder(string path, string name, IEnumerable<object> selectedItems = null)
            {
                throw new NotImplementedException();
            }
    
            public override void Download(string path, string[] names, IEnumerable<object> selectedItems = null)
            {
                throw new NotImplementedException();
            }
    
            public override object GetDetails(string path, string[] names, IEnumerable<object> selectedItems = null)
            {
                throw new NotImplementedException();
            }
    
            public override void GetImage(string path, IEnumerable<object> selectedItems = null)
            {
                throw new NotImplementedException();
            }
    
            public override object Paste(string sourceDir, string targetDir, string[] names, string option, IEnumerable<CommonFileDetails> commonFiles, IEnumerable<object> selectedItems = null, IEnumerable<object> targetFolder = null)
            {
                throw new NotImplementedException();
            }
    
            public override object Read(string path, string filter, IEnumerable<object> selectedItems = null)
            {
                throw new NotImplementedException();
            }
    
            public override object Remove(string[] names, string path, IEnumerable<object> selectedItems = null)
            {
                throw new NotImplementedException();
            }
    
            public override object Rename(string path, string oldName, string newName, IEnumerable<CommonFileDetails> commonFiles, IEnumerable<object> selectedItems = null)
            {
                throw new NotImplementedException();
            }
    
            public override object Search(string path, string filter, string searchString, bool caseSensitive, IEnumerable<object> selectedItems = null)
            {
                throw new NotImplementedException();
            }
    
            public override void Upload(IEnumerable<HttpPostedFileBase> files, string path, IEnumerable<object> selectedItems = null)
            {
                throw new NotImplementedException();
            }
        }
    
    {% endhighlight %}
    
Also we have option to configure the Ajax request in client side, please refer link: [http://help.syncfusion.com/js/fileexplorer/behavior-settings#customize-the-ajax-request-settings](http://help.syncfusion.com/js/fileexplorer/behavior-settings#customize-the-ajax-request-settings) 

## Managing files that is available in SQL database

You can manage the files that are available in database using our FileExplorer control. Here you may use this custom “SQLFileExplorerOperations" class for handling file management related operations using SQL database. This class is used to simplify the process on server side. It contains some built-in methods that are used to handle file operations (like read, copy, move, delete, etc.) using SQL database. This class is created by inheriting the abstract class “[BasicFileOperations](http://help.syncfusion.com/cr/cref_files/aspnetmvc/dociohelper/Syncfusion.EJ~Syncfusion.JavaScript.BasicFileOperations.html#)”. If is it necessary, you may override the methods in “SQLFileExplorerOperations” class.

* To make connection with SQL database (FileManager.mdf) services, please specify connection string in "Web.config" file as specified in the following code example. 

    
    {% highlight xml %}
    
    <add name="FileExplorerConnection" connectionString="Data Source=(LocalDB)\v11.0;AttachDbFilename=|DataDirectory|\FileManager.mdf;Integrated Security=True;Trusted_Connection=true" />
    
    {% endhighlight %}
    
* In controller part, you need to create an object of "SQLFileExplorerOperations" class as shown in the following code example.    
    
    
    {% highlight c# %}
    
    //Here "FileExplorerConnection" is a connection string name, which is defined in Web.config file. 
    //"Product" is a table name, which is defined in SQL database
    SQLFileExplorerOperations sqlobj = new SQLFileExplorerOperations("FileExplorerConnection", "Product");
    
    {% endhighlight %}
    
    
After creating the object for “SQLFileExplorerOperations” class in controller part, you have to call the corresponding built-in file operation handling methods available in “SQLFileExplorerOperations” class based on the file operation type.

We have prepared the following sample based on this, [FileExplorer Sample](http://www.syncfusion.com/downloads/support/directtrac/153129/ze/ServerOperations-1702691750#)
