---
title: How To | FileExplorer | ASP.NET MVC | Syncfusion
description: “How to do” section for FileExplorer component in EJ ASP.NET MVC.
platform: ejmvc
control: FileExplorer
documentation: UG
keywords: FileExplorer,  Syncfusion, EJ MVC FileExplorer, UG document, How To
---
# How To

## File handling operations

In controller page, we have specified some built-in classes at "**FileActionDefault**" action method. It helps to perform the server side operation of FileExplorer and you can find the details about these classes at below.

When you have made AJAX request on client-side, “FileActionDefault” method is triggered in controller part. Here received AJAX data will be stored in “[FileExplorerParams](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerParams.html)” parameter. This “FileActionDefault” method finds out the specific operations using the “ActionType” property and calls the corresponding built-in methods of “[FileExplorerOperations](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations.html)” class.

**BasicFileOperations class**

“BasicFileOperations” is an abstract class and it is useful for handling file operations in server end. By inheriting this class, easily you can implement a new custom class for handling file operations in server end. Refer [class reference](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.BasicFileOperations.html) of “BasicFileOperations”

**FileExplorerOperations class**

This class is useful for handling file operations in server end. This class inherits the “BasicFileOperations” class and its abstract methods has been implemented here for managing files in **underlying machine's physical file system**. Refer [class reference](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations.html) of “FileExplorerOperations”

**FileExplorerParams class**

“FileExplorerParams” class is used to receive the AJAX data in server side. In server side, we have a common method to handle all the AJAX requests, which is raised from client part of FileExplorer. This method contains “FileExplorerParams” object as a parameter and it is used to store the AJAX request data that will be useful for handling file operations. Refer [class reference](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerParams.html) of “FileExplorerParams”

N> Here “ActionType” specifies following operations such as “Read”, “CreateFolder”, “Paste”, “Remove”, “Rename”, “GetDetails”, “Download”, “Upload”, “Search”. Following [section](#abstract-methods-in-basicfileoperations-class) contains the details about each operation.

## Customizing AJAX handling functions

In FileExplorer, server side functionalities are necessary to handle the AJAX request of FileExplorer. Here “Syncfusion.EJ” assembly contains built-in “[BasicFileOperations](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.BasicFileOperations.html)” abstract class and implementation of “[FileExplorerOperations](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations.html)” class for providing the content to FileExplorer and handling AJAX requests. If is it necessary, you can customize the server side functionalities of FileExplorer as per your requirement. 

### Override the existing Syncfusion.JavaScript.FileExplorerOperations class

Using “[FileExplorerOperations](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations.html)” class, you can manage the underlying machine's physical file system with the help of FileExplorer control. Here you can override the necessary methods that is available in “**FileExplorerOperations**” by sub classing the existing “**FileExplorerOperations**” class.

Below code example shows how to override “**GetDetails**” method, which is available in **“FileExplorerOperations**”

    
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
    
### Implement a new custom class to handle AJAX request and provide content for FileExplorer

When overriding the particular methods were not enough, you can create a new custom class using “[BasicFileOperations](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.BasicFileOperations.html)” abstract class. It helps to provide different file sources to be used the content for FileExplorer control, such as database system, physical system or online storage system such as Azure. 

#### Notes to Implementers

When you implement a derived class of “BasicFileOperations”, you must provide implementations for following methods and its details has been given in this [section](#abstract-methods-in-basicfileoperations-class)

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

<br/>

### Abstract methods in BasicFileOperations class

<table>
<tr>
<td>
{{'**Operation and Request Parameter**'| markdownify }}
</td>
<td>
{{'**Response data**'| markdownify }}
</td>
<td>
{{'**Details**'| markdownify }}
</td>
</tr>
<tr>
<td>
{{'**Operation**'| markdownify }}: Read
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name**'| markdownify }}: path
<br/>
{{'**Type  :** '| markdownify }}String
<br/>
{{'**Description:**'| markdownify }}
Specifies the path of selected folder
<br/>
<br/>
{{'**Name**'| markdownify }}: filter
<br/>
{{'**Type  :** '| markdownify }}String
<br/>
{{'**Description:**'| markdownify }}
<br/>
Specifies the file types that need to be filter
<br/>
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
<br/>
It contains the details about selected folder
<br/>
<br/>
</td>
<td>
Response data should be in JSON format with key name as "{{'**files** '| markdownify }}" and JSON fields should be with following field names
<br/>
 {{'*“name,  isFile, hasChild”.*'| markdownify }}
<br/>
<br/>
{{'*For example:*'| markdownify }}
<br/>
{
"{{'**files**'| markdownify }}":[{"{{'**name":"bird.jpg**'| markdownify }}","type":"File","size":102182,"dateModified":"1/9/2016 6:48:42 AM","{{'**hasChild":false,"isFile":true**'| markdownify }},"filterPath":null},
{"{{'**name":"sea.jpg**'| markdownify }}","type":"File","size":97145,"dateModified":"1/9/2016 6:48:42 AM","{{'**hasChild":false,"isFile":true**'| markdownify }},"filterPath":null }],
"details":null,
"error":null
}
<br/>
Note: If needed, customer can also add additional data along with existing properties of “{{'[FileExplorerDirectoryContent](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerDirectoryContent.html)'| markdownify }}” class.
<br/>
</td>
<td>
It used to get all immediate files and sub-folders of the given path and it returns the matched type of files only, which are specified in “filter” parameter.

</td>
</tr>
<tr>
<td>
{{'**Operation**'| markdownify }}: CreateFolder
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name**'| markdownify }}: path<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
Specifies the path of selected folder
<br/>
<br/>
{{'**Name**'| markdownify }}: name<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the name of new folder 
<br/>
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the details about selected folder
<br/>
<br/>
</td>
<td>
Response data should be in JSON format with key name as "{{'**files**'| markdownify }}".
In that returning JSON, “{{'**name**'| markdownify }}” field is necessary.
<br/>
<br/>
{{'*For example:*'| markdownify }}
<br/>
{"files":[{"{{'**name":"New folder**'| markdownify }}","type":"Directory","size":0,"dateModified":"2/25/2016 7:31:02 AM","hasChild":true,"isFile":false,"filterPath":null}],"details":null,"error":null}
<br/>
<br/>
</td>
<td>
It used to create a new folder in given path with specified name

</td>
</tr>
<tr>
<td>
{{'**Operation:**'| markdownify }}Remove
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name:**'| markdownify }}names<br/>
{{'**Type  :** '| markdownify }}String[]<br/>
{{'**Description:**'| markdownify }}
specifies the selected item names, which is going to be removed
<br/> 
<br/>
{{'**Name**'| markdownify }}: path<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the parent folder path of selected items
<br/> 
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the details about selected items, which is going to be removed
<br/>
<br/>
</td>
<td>
Here you may return the removed file details or empty.
<br/>
</td>
<td>
It helps to remove the specified items from given path.
<br/>
</td>
</tr>
<tr>
<td>
{{'**Operation:**'| markdownify }}Rename
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name**'| markdownify }}: path<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the parent folder path of renaming item
<br/> 
<br/>
{{'**Name**'| markdownify }}: oldName<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the existing file name
<br/> 
<br/>
{{'**Name**'| markdownify }}: newName<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the new file name
<br/> 
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the details about selected items, which is going to be renamed
<br/>
<br/>
{{'**Name**'| markdownify }}: commonFiles<br/>
{{'**Type  :** '| markdownify }}IEnumerable<{{'[CommonFileDetails](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.CommonFileDetails.html)'| markdownify }}><br/>
{{'**Description:**'| markdownify }}
It contains the details about already existing files, which contains same name and type as given in new file with same parent folder.
<br/>
<br/>
</td>
<td>
Here you may return the renamed file details or empty.
<br/>
</td>
<td>
This method helps to rename the file/folder, which is available in given path.
</td>
</tr>
<tr>
<td>
{{'**Operation:**'| markdownify }}Paste
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name**'| markdownify }}: sourceDir<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the path of source directory
<br/> 
<br/>
{{'**Name**'| markdownify }}: backupDir<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the path of destination directory
<br/> 
<br/>
{{'**Name**'| markdownify }}: names<br/>
{{'**Type  :** '| markdownify }}String[]<br/>
{{'**Description:**'| markdownify }}
Specifies the name of file/ folders, which are going to be pasted in destination folder.
<br/>
<br/>
{{'**Name**'| markdownify }}: option<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the operation type “move” or “copy”.
<br/>
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the details about selected items, which is going to be pasted
<br/> 
<br/>
{{'**Name**'| markdownify }}: commonFiles<br/>
{{'**Type  :** '| markdownify }}IEnumerable<{{'[CommonFileDetails](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.CommonFileDetails.html)'| markdownify }}><br/>
{{'**Description:**'| markdownify }}
It contains the details about already existing files in destination folder, which contains the files in same name and type as same as newly copied files.
<br/>
<br/>
{{'**Name**'| markdownify }}: targetFolder<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the details about target folder, where the files are going to be pasted.
<br/>
<br/>
</td>
<td>
Here you may return the pasted file details or empty.
<br/>
</td>
<td>
This method helps to copy or move files from one location to another location.
<br/>
</td>
</tr>
<tr>
<td>
{{'**Operation:**'| markdownify }}Upload
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name**'| markdownify }}: files<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;System.Web.HttpPostedFileBase&gt;<br/>
{{'**Description:**'| markdownify }}
Specifies the file details that is going to be uploaded
<br/> 
<br/>
{{'**Name**'| markdownify }}: path<br/>
{{'**Type  :** '| markdownify }}String <br/>
{{'**Description:**'| markdownify }}
specifies the path of destination directory, where the files need to be uploaded
<br/> 
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the details about selected items, which is going to be uploaded.
<br/>
<br/>
</td>
<td>
Return type of this method is “void”
<br/>
</td>
<td>
This method helps to upload the specified files to given directory 
<br/>
</td>
</tr>
<tr>
<td>
{{'**Operation:**'| markdownify }}Download
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name**'| markdownify }}: path<br/>
{{'**Type  :** '| markdownify }}String <br/>
{{'**Description:**'| markdownify }}
Specifies the parent directory path of selected files, which is going to be download
<br/> 
<br/>
{{'**Name**'| markdownify }}: names<br/>
{{'**Type  :** '| markdownify }}String []<br/>
{{'**Description:**'| markdownify }}
specifies the name of files that is need to be downloaded
<br/> 
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the details about files, which is going to be downloaded.
<br/>
<br/>
</td>
<td>
Return type of this method is “void”

</td>
<td>
This method helps to download the specified files.
</td>
</tr>



<tr>
<td>
{{'**Operation:**'| markdownify }}GetDetails
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name**'| markdownify }}: path<br/>
{{'**Type  :** '| markdownify }}String <br/>
{{'**Description:**'| markdownify }}
Specifies the parent directory path of selected file
<br/> 
<br/>
{{'**Name**'| markdownify }}: names<br/>
{{'**Type  :** '| markdownify }}String []<br/>
{{'**Description:**'| markdownify }}
Specifies the name of files in order to get it’s details
<br/> 
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the basic details about selected files
<br/>
<br/>
</td>
<td>
Response data should be in JSON format like below
<br/>
<br/>
{details : [{CreationTime:"4/28/2015 9:44:32 AM", Extension:".png", Format:"Archive", FullName:"F:\All samples\FileExplorer_Custom\FileExplorerContent\human.png", LastAccessTime:"4/28/2015 9:44:32 AM", LastWriteTime:"3/31/2015 3:16:35 PM", Length:11059, Name:"human.png"}]}

<br/>
Note: Here you may add additional date fields along with existing JSON data using “FileDetails” class.
<br/>
</td>
<td>
This method used to get the details of the specified file or directory.

</td>
</tr>


<tr>
<td>
{{'**Operation:**'| markdownify }}GetImage
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name**'| markdownify }}: path<br/>
{{'**Type  :** '| markdownify }}String <br/>
{{'**Description:**'| markdownify }}
specifies the path of image file
<br/> 
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the details about selected image
<br/> 
<br/>
</td>
<td>
Return type of this method is void.
</td>
<td>
This method helps to get an image using “HttpResponse” option 

</td>
</tr>
<tr>
<td>
{{'**Operation:**'| markdownify }}Search
<br/>
<br/>
{{'**Request Parameter**'| markdownify }}
<br/>
{{'**Name**'| markdownify }}: path<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the directory path
<br/> 
<br/>
{{'**Name**'| markdownify }}: filter<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
Specifies the file types that need to be filter
<br/>
<br/>
{{'**Name**'| markdownify }}: searchString<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the search string
<br/> 
<br/>
{{'**Name**'| markdownify }}: caseSensitive<br/>
{{'**Type  :** '| markdownify }}String<br/>
{{'**Description:**'| markdownify }}
specifies the case sensitive option
<br/>
<br/>
{{'**Name**'| markdownify }}: selectedItems<br/>
{{'**Type  :** '| markdownify }}IEnumerable&lt;object&gt;<br/>
{{'**Description:**'| markdownify }}
It contains the details about selected folder
<br/>
<br/>
</td>
<td>
It should return data in JSON format with key name as "{{'**files**'| markdownify }}" and JSON fields need to be with following field names.
<br/>
 {{'*“name,  isFile, hasChild,filterPath”.*'| markdownify }}
 <br/><br/>
 {{'*For example:*'| markdownify }}
 <br/>
{
"{{'**files**'| markdownify }}":[{"{{'**name":"bird.jpg**'| markdownify }}","type":"File","size":102182,"dateModified":"1/9/2016 6:48:42 AM","{{'**hasChild":false,"isFile":true**'| markdownify }},"filterPath":null},
{"{{'**name":"sea.jpg**'| markdownify }}","type":"File","size":97145,"dateModified":"1/9/2016 6:48:42 AM","{{'**hasChild":false,"isFile":true**'| markdownify }},"filterPath":null }],
"details":null,
"error":null
}
<br/>
<br/>
</td>
<td>
It used to search all the matched files and sub-folders in the given folder path also it filters the specified files using it types.

</td>
</tr>
</table>

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
    
Also we have option to configure the AJAX request in client side, please refer link: [https://help.syncfusion.com/js/fileexplorer/behavior-settings#customize-the-ajax-request-settings](https://help.syncfusion.com/js/fileexplorer/behavior-settings#customize-the-ajax-request-settings) 

## Managing files that is available in SQL database

You can manage the files that are available in database using our FileExplorer control. Here you may use this custom “**SQLFileExplorerOperations**" class for handling file management related operations using SQL database. This class is used to simplify the process on server side. It contains some built-in methods that are used to handle file operations (like read, copy, move, delete, etc.) using SQL database. This class is created by inheriting the abstract class “[BasicFileOperations](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.BasicFileOperations.html)”. If is it necessary, you may override the methods in “**SQLFileExplorerOperations**” class.

* To make connection with SQL database (FileManager.mdf) services, please specify connection string in "Web.config" file as specified in the following code example. 

    
    {% highlight c# %}
    
    <add name="FileExplorerConnection" connectionString="Data Source=(LocalDB)\v11.0;AttachDbFilename=|DataDirectory|\FileManager.mdf;Integrated Security=True;Trusted_Connection=true" />
    
    {% endhighlight %}
    

* In controller part, you need to create an object of "SQLFileExplorerOperations" class as shown in the following code example.
    
    {% highlight c# %}
    
    //Here "FileExplorerConnection" is a connection string name, which is defined in Web.config file. 
    
    //"Product" is a table name, which is defined in SQL database
    
    SQLFileExplorerOperations sqlObj = new SQLFileExplorerOperations("FileExplorerConnection", "Product");
    
    {% endhighlight %}
    
After creating the object for “SQLFileExplorerOperations” class in controller part, you have to call the corresponding built-in file operation handling methods available in “SQLFileExplorerOperations” class based on the file operation type.

We have prepared the following sample based on this, [FileExplorer Sample](https://www.syncfusion.com/downloads/support/directtrac/153129/ze/ServerOperations-1702691750#)


### File Access permission for the files that is available in SQL database

The FileExplorer provides method to assign permissions or access rights to specific users and group of users. It allows you to define access permissions for folders and files using a set of access rules to user(s).


* As per the above details, In controller part, you need to create an object of "SQLFileExplorerOperations" class and additionally you need to pass the `access rules` as a constructor parameter.
    
    {% highlight c# %}
    
    //Here "FileExplorerConnection" is a connection string name, which is defined in Web.config file. 
    
    //"Product" is a table name, which is defined in SQL database

    // SQLGetRules() which a function which returns the access rules
    
    SQLFileAccessOperations sqlObj = new SQLFileAccessOperations("FileExplorerConnection", "Product", SQLGetRules());
    
    {% endhighlight %}

For this, we have prepared the sample and you can get it from the below link

[sample](https://www.syncfusion.com/downloads/support/directtrac/general/ze/ServerOperations-291041509.zip)

N> Here we have fetched the file permissions from the SQL table for the files located in SQL database.

To know more details about file access permission, please refer this [link](https://help.syncfusion.com/aspnetmvc/fileexplorer/access-control)

## Cross-origin resource sharing support for FileExplorer

**Cross-origin request**

The “FileExplorer” can browse and manage files on remote servers, which is located in other domains. If a server is located on a different domain, on a different port or using different protocol (HTTP / HTTPS) such requests are considered to be “**cross-origin requests**”. These type requests are prohibited by IE9 and its earlier browsers.

**Enabling cross-origin request in IE8 and IE9**

By default, Internet Explorer 9 and earlier prohibits cross-origin requests for Internet Zone, also it ignores "Access-Control-Allow" headers. To enable cross-origin in IE8 and IE9, we have specified two type of options. As per the requirements, you can use any option that is mentioned below.

**Option 1: Enabling cross-origin in IE through browser settings**

To enable cross-origin access using settings of IE browser, go to Tools->Internet Options->Security tab, click on “Custom Level” button. Find the Miscellaneous and select “Enable” option, which is available under “Access data sources across domains” settings.

If your server is located in Intranet Zone, In IE Browser, confirmation dialog will be popped during first cross-domain request as “*This page is accessing information that is not under its control. This poses a security risk. Do you want to continue*?”

To suppress this warning, you need to specify the "*Access data sources across domains*" setting to “allow”.

![](HowTo_images/HowTo_img1.jpeg)

**Option 2: Using JSONP for cross-origin request**

Using JSONP data type, you can perform cross origin-request. To enable cross-origin request, in your “FileExplorer”, you have to specify “**AjaxDataType”**as “**jsonp**”. And we have provided “**doJSONPAction**” method to handle “jsonp” type AJAX request on server side.  Please refer below code snippet to specify “**AjaxDataType”**as “**jsonp**”.

Code example [CSHTML]:

    
    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("http://js.syncfusion.com/demos/ejServices/Content/FileBrowser/")
            .AjaxAction("http://js.syncfusion.com/demos/ejServices/api/FileExplorer/FileOperations")
            .AjaxDataType("jsonp")
        )
        
    {% endhighlight %}
    
If we specify “AjaxDataType” as “jsonp”, data will be received in string format while calling “doJSONPAction” method of Web API Controller, here you need to deserialize the received “localData” data into “[FileExplorerParams](#_FileExplorerParams_class_1)” object. After performing corresponding operations, you have to specify the response data in serialized format with wrapped callback function. Please refer below code snippet to handle “jsonp” operations on server.

Code example [C#]:

    
    {% highlight c# %}
    
        [HttpGet]
        [ActionName("doJSONPAction")]
        public object doJSONPAction(string callback, string localData)
        {	
            object Data = null;
            var serializer = new JavaScriptSerializer();
            FileExplorerParams args = (FileExplorerParams)serializer.Deserialize(localData, typeof(FileExplorerParams));
            try
            {            
                switch (args.ActionType)
                {
                    case "Read":
                        Data = FileExplorerOperations.ReadData(args.Path, args.ExtensionsAllow);
                        break;
                    case "Search":
                        Data = FileExplorerOperations.Search(args.Path, args.ExtensionsAllow, args.SearchString, args.CaseSensitive);
                        break;
                    case "CreateFolder":
                        Data = FileExplorerOperations.NewFolder(args.Path, args.Name);
                        break;
                    case "Paste":
                        Data = FileExplorerOperations.Paste(args.LocationFrom, args.LocationTo, args.Names, args.Action, args.CommonFiles);
                        break;
                    case "Remove":
                        Data = FileExplorerOperations.Remove(args.Names, args.Path);
                        break;
                    case "Rename":
                        Data = FileExplorerOperations.Rename(args.Path, args.Name, args.NewName, args.CommonFiles);
                        break;
                    case "GetDetails":
                        Data = FileExplorerOperations.GetDetails(args.Path, args.Names);
                        break;
                }
                HttpContext.Current.Response.Write(string.Format("{0}({1});", callback, serializer.Serialize(Data)));
                return "";
            }
            catch (Exception e)
            {
                FileExplorerResponse Response = new FileExplorerResponse();
                Response.error = e.GetType().FullName + ", " + e.Message;
                HttpContext.Current.Response.Write(string.Format("{0}({1});", callback, serializer.Serialize(Response)));
                return "";
            }
        }
            [HttpPost]
            [ActionName("doJSONPAction")]
            public void doJSONPAction()
            {
                if (HttpContext.Current.Request.Files.Count > 0)
                    FileExplorerOperations.Upload(HttpContext.Current.Request.Files,    HttpContext.Current.Request.QueryString.GetValues("Path")[0]);
            }
            [HttpGet]
            [ActionName("doJSONPAction")]
            public void doJSONPAction(string ActionType, string Path, string SelectedItems)
            {
                if (ActionType == "Download")
                FileExplorerOperations.Download(Path, HttpContext.Current.Request.QueryString.GetValues("Names"));
            else if (ActionType == "GetImage")
                FileExplorerOperations.GetImage(Path);
            }
            
    {% endhighlight %}
    
In IE8 and IE9 Browser, These options helps to render our “FileExplorer” control with cross-origin resource support.

## Access static physical path using FileExplorer control

Using “FileExplorer”, also you can manage the files that are available in local file system by referring its physical path. Please refer below example to achieve this.

In the view page, add “FileExplorer” helper and specify the physical path as below shown format.

    {% highlight razor %}
    
        @(Html.EJ().FileExplorer("fileExplorer")
            .Path("C:/Samples/web/FileExplorerContent")
            .AjaxAction(@Url.Content("FileActionDefault"))        
        )
        
    {% endhighlight %}

In the controller page, specify the “[GetImage](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations~GetImage.html)” handling operation as shown below. This handling function is necessary to render the images in FileExplorer, while physical path has been mentioned.
    
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
                    case "GetImage":
                        operation.GetImage(args.Path);
                        break;
                }
                return Json("");
            }
            
    {% endhighlight %}
    
## Adding Custom column in grid view of FileExplorer

You can add custom column in grid view of “FileExplorer”. To achieve this requirement, in controller page you have to add the custom column with existing AJAX response by overriding the “Read” method, which is available in “[FileExplorerOperations](https://help.syncfusion.com/cr/cref_files/aspnetmvc/Syncfusion.EJ~Syncfusion.JavaScript.FileExplorerOperations.html)” class. Please refer following code example.
    
    {% highlight c# %}
    
        public partial class FileExplorerController : Controller
        {
            public ActionResult Default()
            {
                return View();
            }
    
            public ActionResult FileActionDefault(FileExplorerParams args)
            {
                FileExplorerCustomOperations customOperation = new FileExplorerCustomOperations();
                FileExplorerOperations operation = new FileExplorerOperations();
                switch (args.ActionType)
                {
                    case "Read":
                        return Json(customOperation.Read(args.Path, args.ExtensionsAllow));
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
                        operation.GetImage(args.Path);
                        break;
                }
                return Json("");
            }
    
        }
        public class FileExplorerCustomOperations : FileExplorerOperations
        {
            public override object Read(string path, string filter, IEnumerable<object> selectedItems = null)
            {
                CustomFileExplorerResponse ReadResponse = new CustomFileExplorerResponse();
                try
                {
                    var directory = new DirectoryInfo(GetPhysicalPath(ToAbsolute(path)));
                    filter = filter.Replace(" ", "");
                    var extensions = (filter ?? "*").Split(",|;".ToCharArray(), System.StringSplitOptions.RemoveEmptyEntries);
                    var files = extensions.SelectMany(directory.GetFiles)
                        .Select(file => new CustomFileExplorerDirectoryContent
                        {
                            name = file.Name,
                            isFile = true,
                            size = file.Length,
                            type = "File",
                            dateModified = file.LastWriteTime.ToString(),
                            hasChild = false,
                            //assign the value in extension property
                            extension = file.Extension
                        });
    
                    var directories = directory.GetDirectories().Select(subDirectory => new CustomFileExplorerDirectoryContent
                    {
                        name = subDirectory.Name,
                        size = 0,
                        isFile = false,
                        type = "Directory",
                        dateModified = subDirectory.LastWriteTime.ToString(),
                        hasChild = subDirectory.GetDirectories().Length > 0 ? true : false,
                        extension = ""
                    });
    
                    object fileDetails = files.Concat(directories);
                    ReadResponse.files = (IEnumerable<CustomFileExplorerDirectoryContent>)fileDetails;
                    return ReadResponse;
                }
                catch (Exception e)
                {
                    ReadResponse.error = e.GetType().FullName + ", " + e.Message;
                    return ReadResponse;
                }
            }
        }
        public class CustomFileExplorerDirectoryContent
        {
            public string name { get; set; }
            public string type { get; set; }
            public long size { get; set; }
            public string dateModified { get; set; }
            public bool hasChild { get; set; }
            public bool isFile { get; set; }
            //add custom property
            public string extension { get; set; }        
        }
    
        //customize the FileExplorer response
        public class CustomFileExplorerResponse
        {
            public IEnumerable<CustomFileExplorerDirectoryContent> files { get; set; }
            public IEnumerable<FileDetails> details { get; set; }
            public object error { get; set; }
        }
    
    {% endhighlight %}
    
In the view page, add the custom column in grid using “[GridSettings](https://help.syncfusion.com/js/api/ejfileexplorer#members:gridsettings)” API of “FileExplorer”.

    {% highlight razor %}

    @(Html.EJ().FileExplorer("fileExplorer")
        .Path("~/FileExplorerContent/")
        .AjaxAction(@Url.Content("FileActionDefault"))
        .GridSettings(grid => 
            grid.Column(column=>
                {
                    column.Add().Field("name").HeaderText("Name").Width("30%");
                    column.Add().Field("type").HeaderText("Type");
                    //adding new column
                    column.Add().Field("extension").HeaderText("Extension");
                    column.Add().Field("size").HeaderText("Size");
                    column.Add().Field("dateModified").HeaderText("Date Modified");
                }
            )
        )
    )

    {% endhighlight %}

## Create FileExplorer in older version

In older versions (Before 13.3.0.7), you can easily create the FileExplorer widget by using the following steps.

1. Add the following code example to the corresponding view page to render the FileExplorer.

    
    {% highlight razor %}
    
    @Html.EJ().FileExplorer("fileExplorer").Path("~/FileExplorerContent/").AjaxAction(@Url.Content("FileActionDefault"))
    
    {% endhighlight %}
    

In above code block, “Path” denotes the filesystem path that are to be explored and “AjaxAction” specifies the URL of server side AJAX handling method that handles file operations of FileExplorer control. So “[Path](https://help.syncfusion.com/js/api/ejfileexplorer#members:path)” and “[AjaxAction](https://help.syncfusion.com/js/api/ejfileexplorer#members:ajaxaction)” are the mandatory configuration at here.

2. Add the following code example to the corresponding controller page

    
    {% highlight c# %}
    
            public ActionResult FileActionDefault(FileExplorerParams args)
            {
                switch (args.ActionType)
                {
                    case "Read":
                        return Json(FileExplorerOperations.Read(args.Path, args.ExtensionsAllow));
                    case "CreateFolder":
                        return Json(FileExplorerOperations.CreateFolder(args.Path, args.Name));
                    case "Paste":
                        FileExplorerOperations.Paste(args.LocationFrom, args.LocationTo, args.Name.Split(','), args.Action, args.CommonFiles);
                        break;
                    case "Delete":
                        FileExplorerOperations.Delete(args.Name.Split(','), args.Path);
                        break;
                    case "Rename":
                        FileExplorerOperations.Rename(args.Path, args.PreviousName, args.NewName, args.Type, args.CommonFiles);
                        break;
                    case "GetDetails":
                        return Json(FileExplorerOperations.GetDetails(args.Path, args.Name, args.Type));
                    case "Download":
                        FileExplorerOperations.Download(args.Path);
                        break;               
                    case "Upload":
                        FileExplorerOperations.Upload(args.FileUpload, args.Path);
                        break;
                }
                return Json("");
            }
    
    {% endhighlight %}
    
    
Once you have completed the above steps, you will get an output like below.

![](HowTo_images/HowTo_img2.png)

FileExplorerOperations is a predefined class, which is used to perform File Explorer-based operations like read, createFolder, download, upload, rename, paste, getImage. It minimizes the work load on server-side.

By default, we send following parameters in data field of corresponding AJAX request. This helps to handle server side operation. Some Server side action method will only return the response data. This response data and request parameter are explained in following table.

<table>
<tr>
<td>
{{'**Operation**'| markdownify }}
</td>
<td>
{{'**Default Request Parameter**'| markdownify }}
</td>
<td>
{{'**Response data**'| markdownify }}
</td>
<td>
{{'**Details**'| markdownify }}
</td>
</tr>
<tr>
<td>
Read
</td>
<td>
String ActionType,String Path,String ExtensionsAllow
</td>
<td>
Should return data in array of JSON format and JSON fields need to be in following field names.
<br/>
"{{ '**name, size, type, dateModified, hasChild**' | markdownify }}"
<br/>
<br/>
{{ '_For example:_' | markdownify }}[{name: "7.png", type: "File", size: 11439, dateModified: "3/31/2015 3:16:38 PM", hasChild: false},{name: "human.png", type: "File", size: 11059, dateModified: "3/31/2015 3:16:35 PM", hasChild: false}]
<br/>
</td>
<td>
Read the data from the given path
</td>
</tr>
<tr>
<td>
CreateFolder
</td>
<td>
String ActionType,String Path,String Name
</td>
<td>
Should return new folder name in string
</td>
<td>
Create the new folder to given path
</td>
</tr>
<tr>
<td>
Paste
</td>
<td>
String ActionType, String LocationFrom, String LocationTo, String Name,String Type, String Action
</td>
<td>
Void
</td>
<td>
Paste the content from source to target place
</td>
</tr>
<tr>
<td>
Delete
</td>
<td>
String ActionType, String Name,String Path
</td>
<td>
Void
</td>
<td>
Delete the data from the given path
</td>
</tr>
<tr>
<td>
Rename
</td>
<td>
String ActionType, String Path,String PreviousName, String NewName, String Type
</td>
<td>
Void
</td>
<td>
Rename the file or folder from the given path
</td>
</tr>
<tr>
<td>
GetDetails
</td>
<td>
String ActionType, String Path, String Name,String Type
</td>
<td>
Response data should be in JSON format like below 
<br/>
<br/>
{CreationTime:"4/28/2015 9:44:32 AM", Extension:".png", Format:"Archive", FullName:"F:\All samples\FileExplorer_Custom\FileExplorerContent\human.png", LastAccessTime:"4/28/2015 9:44:32 AM", LastWriteTime:"3/31/2015 3:16:35 PM", Length:11059, Name:"human.png"} 
<br/>
<br/>
Here you may add additional date fields with this JSON
<br/>
</td>
<td>
To get the details of the data from the given path
</td>
</tr>
<tr>
<td>
Download
</td>
<td>
String ActionType,String Path
</td>
<td>
Void
</td>
<td>
To download the data from the given path
</td>
</tr>
<tr>
<td>
Upload
</td>
<td>
String ActionType, IEnumerable&lt;HttpPostedFileBase&gt; FileUpload, String Path
</td>
<td>
Void 
</td>
<td>
To upload the data from the given path
</td>
</tr>
</table>

## Customize the Root Folder name in FileExplorer

You can set the alias name to the root folder of FileExplorer by using `rootFolderName` API. It is used to replace the actual root folder name in the FileExplorer UI. Refer to the below code to set the alias name for the root folder of FileExplorer.

 {% highlight razor %}
    
    @(Html.EJ().FileExplorer("fileExplorer")
        .Path("~/FileExplorerContent/")
        .RootFolderName ("This PC")
        .AjaxAction(@Url.Content("FileActionDefault"))
    )
    
{% endhighlight %}

## Use the FTP connection using FileExplorer

You can access your FTP service using our FileExplorer component and can manage your files easily.

### FTP Login

First you will need the FTP account login information. You can connect with the primary username and password or an FTP account. The FTP server is open to the public, using anonymous access. But most of the FTP servers are password protected. 
Username: username or user@example.com
Password: The password that was created for the user you are using.

### FTP with FileExplorer server

In this FTP application, we have provided “FTPFileOperationController” file, which contains “FileActionDefault” action method. When you make AJAX request to this controller part, “FileActionDefault” method will be called after based on ActionType” parameter value, then it calls the corresponding built-in FTP file handling methods such as ‘Read’, ‘Search’, ‘Download’, ‘Upload’, ‘Remove’, ‘Rename’ which are available in our “FTPFileExplorerOperations” class.

### Steps to create FileExplorer application to access FTP server

**Step 1:** Create a new ASP.NET MVC project using Visual Studio.

**Step 2:** Include **“FTPFileExplorerOperations”** file in that application. This file contains built-in file handling methods which helps to connect our FileExplorer with FTP service.

[https://www.syncfusion.com/downloads/support/directtrac/general/ze/FTPFileExplorerOperations901960089.zip](https://www.syncfusion.com/downloads/support/directtrac/general/ze/FTPFileExplorerOperations901960089.zip#)

**Step 3:** Add **“FileExplorerController.cs”** file in the controller part of FTP project.

This file, contains action handler methods. Based on the request parameters, it helps to call the built-in file handling methods of **FTPFileExplorerOperations** and perform corresponding actions.

{% highlight c# %}

public ActionResult FileActionDefault(FileExplorerParams args)
        {
FTPFileExplorerOperations operation= new FTPFileExplorerOperations();
        // FTP Operations
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
            case "GetImage":
                operation.GetImage(args.Path, args.Names);
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

**Step 4:** Add FTP Storage path that is viewed by FileExplorer.
You will create FTP URL like “ftp://localhost/FileBrowser/” (Port number may vary).
After that, you need to specify the FTP folder path and AJAX action handler name as shown in below code block.

{% highlight razor %}

@Html.EJ().FileExplorer("fileexplorer").Path("ftp://localhost/FileBrowser/").AjaxAction(@Url.Content("/FileExplorer/FileActionDefault"))

{% endhighlight %}

We have prepared a demo based on above steps, please refer this.

[https://www.syncfusion.com/downloads/support/directtrac/general/ze/FTPMVC1739148525.zip](https://www.syncfusion.com/downloads/support/directtrac/general/ze/FTPMVC1739148525.zip#)
