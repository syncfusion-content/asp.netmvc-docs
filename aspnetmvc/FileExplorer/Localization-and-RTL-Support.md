---
layout: post
title: Localization-and-RTL-Support
description: localization and rtl support
platform: ejmvc
control: FileExplorer
documentation: ug
---

# Localization and RTL Support

## Localization

You can globalize the FileExplorer, so that users of different cultures can make use of it and post their content. For your convenience, you can format the FileExplorer control to your culture. When your blog is in your culture, the viewers of your culture can understand about your company and its products. You can achieve localization using the “Locale” property. 

FileExplorer support all the cultures. Globalize.js is a simple JavaScript library that allows you to use different cultures. Globalize cultures is the open source and you can get all the culture files from [http://cdnjs.com/libraries/globalize/](http://cdnjs.com/libraries/globalize/) link. 

In this example, globalize.min.js file is used that includes all the cultures information. And in this example Spanish culture is used. 

1. Add the following code in your CSHTML page to initialize the FileExplorer with Spanish content.

   ~~~ html

			@Html.EJ().FileExplorer("fileExplorer").Path("~/FileExplorerContent/").AjaxAction(@Url.Content("FileActionDefault")).Locale("es-ES").GridSettings(settings => settings.Column(col =>

                        {

                            col.Add().Field("name").HeaderText("nombre");

                            col.Add().Field("type").HeaderText("tipo");

                            col.Add().Field("size").HeaderText("tamaño");

                            col.Add().Field("dateModified").HeaderText("fecha de modificación");

                        })).Layout(LayoutType.Tile)


   ~~~
   {:.prettyprint }

2. Add the following code in your script section to render FileExplorer with Spanish culture.


   ~~~ html

			<script>

				ej.FileExplorer.Locale["es-ES"] = {

				Back: "hacia atrás",

				Forward: "adelante",

				Refresh: "refrescar",

				Addressbar: "Addressbar",

				Upload: "Subir",

				Rename: "rebautizar",

				Delete: "borrar",

				Download: "Descargar Archivo",

				Cut: "cortada",

				Copy: "copia",

				Paste: "pasta",

				Details: "Obtener detalles",

				Searchbar: "barra de búsqueda",

				Open: "abierto",

				Search: "búsqueda",

				NewFolder: "Agregar carpeta",

				SelectedFileUrl: "dirección Web",

				SelectedFileName: "título",

				ImageWidth: "ancho",

				ImageHeight: "altura",

				Insert: "Insertar",

				Cancel: "cancelar",

				RenameAlert: "Por favor, introduzca el nuevo nombre",

				NewFolderAlert: "Introduzca el nuevo nombre de la carpeta",

				DownloadTitle: "Confirmación ..!",

				DownloadAlert: "¿Seguro que quieres descargar",

				DownloadConfirmation: "Okay, Descargar",

				ContextMenuOpen: "abierto",

				ContextMenuNewFolder: "nueva carpeta",

				ContextMenuDelete: "borrar",

				ContextMenuRename: "rebautizar",

				ContextMenuUpload: "Subir",

				ContextMenuDownload: "descargar",

				ContextMenuCut: "cortada",

				ContextMenuCopy: "copia",

				ContextMenuPaste: "pasta",

				ContextMenuGetinfo: "Obtén información",

				OkButton: "Okay",

				CancelButton: "cancelar",

				YesButton: "sí",

				NoButton: "No",

				Size: "tamaño",

				Item: " artículo",

				Items: " artículos",

				Grid: "Vista de cuadrícula",

				Tile: "vista de mosaicos",

				ErrorOnFolderCreation: "Nombre de la carpeta ya existe en el directorio, por favor, dar un nuevo nombre",

				GeneralError: "Por favor, vea ventana de la consola del navegador para obtener más información",

				ErrorPath: "FileExplorer no puede encontrar '{0}'. Revisa la ortografía y vuelva a intentarlo.",

				InvalidFileUpload: " tipo de archivo seleccionado no es válido. Tipos de archivo admitidos son ",

				Name: "nombre",

				FullName: "Nombre Completo",

				Extension: "extensión",

				Format: "formato",

				Length: "longitud",

				CreationTime: "Hora de creación",

				LastAccessTime: "Última Tiempo de acceso",

				LastWriteTime: "Última Hora Comentario",

				};

				ej.Uploadbox.Locale["es-ES"] = {

				buttonText: {

				upload: "Subir",

				browse: "Explorar",

				cancel: "cancelar"

				},

				dialogText: {

				title: "Subir Box",

				name: "nombre",

				size: "tamaño",

				status: "estado"

					}

				}; 

			</script>

   ~~~
   {:.prettyprint }
   
3. _Figure 13: Showcase of FileExplorer with Spanish culture_
    ![](Localization-and-RTL-Support_images/Localization-and-RTL-Support_img1.png)

	There is no change in the controller part, it is the same controller part used as mentioned above.

## RTL

RTL control supports right-to-left functionality and features for languages that work in a right-to-left way for entering, editing, and displaying text. You can change your display to read right-to-left. Arabic and Hebrew are written from right to left. The customers with writing style from right-to left can use this feature in FileExplorer. You can achieve this in the editing area by using the EnableRTL property. Setting this property to “True” allows you to write in the right-to-left format. Position of the toolbars also changes from right to left.

1. Add the following code to the script section in your CSHTML page to initialize the FileExplorer.


   ~~~ html

		@Html.EJ().FileExplorer("fileExplorer").Path("~/FileExplorerContent/").AjaxAction(@Url.Content("FileActionDefault")).EnableRTL(true).Layout(LayoutType.Tile)
   
   ~~~
   {:.prettyprint }

2. There is no change in the controller part, it is the same controller part used as mentioned above

	_Figure 14:Showcase of FileExplorer with right to left appearance_

	![](Localization-and-RTL-Support_images/Localization-and-RTL-Support_img2.png)