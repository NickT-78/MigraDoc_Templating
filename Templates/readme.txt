Here we have the MigraDoc templates

Description

A template would be a plain text document using the MigraDoc description. Just like in XML or JSON, it has keywords, groups and other specific items.
When a template is parsed by the MigraDoc document parser, it generates a Document object that contains a hierarchy of items. These items can contain either static text or, in this case, tags that can be replaced.

Running through the given example, there are different types of tags:

 - "<%Author%>" is a simple tag, it would be replaced by the value of the object Author
 - "<%resource(MyDocumentKeywords)%>" is a resource tag, it would be replaced by the value found in the provided resource file matching the given key "MyDocumentKeywords" and the given culture
 - "<%resource(ImageLogo)%>" is a resource tag, but in this case we need special management for the image. The image data must be saved to a file (use a temporary folder) then place the path to the file in the image item
 - "<%Object.Value1%>" is a simple tag, it would be replaced by the value of the sub item of object
 - "<%List{0}%>" and "<%List{1}%>" are table tags, the name must be the same and be the name of a given object. 'List{0} will be used if 'List' is empty and 'List{1}' will be used if List contains entries. The table using the list object will be scoped so all simple tags used are sub items of the 'List' entries.
 - "<%ItemProperty2{C}%>" is a simple tag with formater, in this case we use a currency formater according to the given culture
 - "<%IF(<%BooleanValue%>)%>" is a conditional tag, the complete item will be shown only is the value of the 'BooleanValue' is true
 - "<%SUM(<%Object.CashAfter%>;-<%Object.Amount%>){C}%>" is a math tag, in this case we would sum the 2 given values including the formating for currency
 - "<%template(List2)%>" is a template tag, every item of a single template must contain the same template tag. This will scope the template and all items of the template will be repeated for each entry of 'List2'
 
