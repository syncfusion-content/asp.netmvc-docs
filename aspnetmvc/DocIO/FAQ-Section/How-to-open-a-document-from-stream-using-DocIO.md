---
layout: post
title: How to open a document from stream using DocIO 
description: how to open a document from stream using docio?
platform: ejmvc
control: DocIO
documentation: ug
---

# How to open a document from stream using DocIO?

DocIO provides support for opening documents from stream. It gets the document by using .NET classes, and then passes the stream to DocIO as follows.

{% highlight c# %}
HttpWebRequest request =(HttpWebRequest)WebRequest.Create("http://www.nfpa.org/assets/files//PDF/Forms/EvacuationGuide.doc");
HttpWebResponse response = (HttpWebResponse)request.GetResponse();
Stream stream = response.GetResponseStream();
byte[] buffer = ReadFully(stream, 32768);
//Store bytes into the memory stream.
MemoryStream ms = new MemoryStream();
ms.Write(buffer, 0, buffer.Length);ms.Seek(0, SeekOrigin.Begin);
stream.Close();//Creates a new document.WordDocument doc = new WordDocument();
//Opens the template document from the MemoryStream.
doc.Open(ms, FormatType.Doc);
doc.Save("Sample.doc", FormatType.Doc, Response, HttpContentDisposition.InBrowser);}
public static byte[] ReadFully(Stream stream, int initialLength)
{
	//If an unhelpful initial length has been passed, just//use 32K.
	if (initialLength < 1){initialLength = 32768;}
	byte[] buffer = new byte[initialLength];
	int read = 0;int chunk;
	while ((chunk = stream.Read(buffer, read, buffer.Length - read)) > 0)
	{
		read += chunk;
		//If you have reached the end of our buffer, check to see if there is//any more information.
		if (read == buffer.Length)
		{
			int nextByte = stream.ReadByte();
			//End of stream? If so, we are done.
			if (nextByte == -1)
			{
				return buffer;
			}
			//Nope. Resize the buffer, put in the byte you have just
			//read, and continue.
			byte[] newBuffer = new byte[buffer.Length * 2];
			Array.Copy(buffer, newBuffer, buffer.Length);
			newBuffer[read] = (byte)nextByte;buffer = newBuffer;
			read++;
		}
	}
	//Buffer is now too big. Shrink i
	t.byte[] ret = new byte[read];
	Array.Copy(buffer, ret, read);
	return ret;
}
{% endhighlight  %}
{% highlight vbnet %}
Protected Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) HandlesButton1.Click    
Dim request As HttpWebRequest =CType(WebRequest.Create("http://www.nfpa.org/assets/files//PDF/Forms/EvacuationGuide.doc"), HttpWebRequest)    
Dim response1 As HttpWebResponse = CType(request.GetResponse(), HttpWebResponse)  
  Dim stream As Stream = response1.GetResponseStream()    
Dim buffer As Byte() = ReadFully(stream, 32768)   
 Dim ms As MemoryStream = New MemoryStream()  
  ms.Write(buffer, 0, buffer.Length)  
  ms.Seek(0, SeekOrigin.Begin)   
stream.Close()    
'Creates a new document.   
 Dim doc As WordDocument = New WordDocument()  
  'Opens the template document from the filestream.
    doc.Open(ms, FormatType.Doc)  
  doc.Save("Sample.doc", FormatType.Doc, response, HttpContentDisposition.InBrowser)End SubPublic Shared Method ReadFully(ByVal stream As Stream, ByVal initialLength As Integer) AsByte()  
  ’If an unhelpful initial length has been passed, just    ’use 32K. 
   If initialLength < 1 Then        initialLength = 32768  
  End If    Dim buffer As Byte() = New Byte(initialLength - 1) {} 
   Dim read As Integer = 0  
  Dim chunk As Integer   
chunk = stream.Read(buffer, read, buffer.Length - read)    Do While (chunk > 0)        read += chunk     
   ’If you have reached the end of our buffer, check to see if there is        ’any more information.    
    If read = buffer.Length Then        
    Dim nextByte As Integer = stream.ReadByte()         
   ’End of stream? If so, you are done.     
       If nextByte = -1 Then              
  Return buffer       
     End If           
 ’Nope. Resize the buffer, put in the byte you have just            ’read, and continue.      
      Dim newBuffer As Byte() = New Byte(buffer.Length * 2 - 1) {}    
        Array.Copy(buffer, newBuffer, buffer.Length)       
     newBuffer(read) = CByte(nextByte)          
  buffer = newBuffer            read += 1      
  End If        chunk = stream.Read(buffer, read, buffer.Length - read)    Loop   
 ’Buffer is now too big. Shrink it.   
 Dim ret As Byte() = New Byte(read - 1) {}
    Array.Copy(buffer, ret, read)  
  Return retEnd Method
{% endhighlight  %}


