.. include:: ../../../../Includes.txt

===================
widget.autocomplete
===================


Simple paginate widget
Note: Make sure to include jQuery and jQuery UI in the HTML, like that:
<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.4.2/jquery.min.js"></script>
<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8.4/jquery-ui.min.js"></script>
<link rel="stylesheet" href="http://ajax.googleapis.com/ajax/libs/jqueryui/1.8.3/themes/base/jquery-ui.css" type="text/css" media="all" />
<link rel="stylesheet" href="http://static.jquery.com/ui/css/demo-docs-theme/ui.theme.css" type="text/css" media="all" />
You can include the provided TS template that includes the above snippet to the pages headerData.

= Examples =

<code title="Render lib object">
<input type="text" id="name" />
<f:widget.autocomplete for="name" objects="{posts}" searchProperty="author">
</code>
<output>
<input type="text" id="name" />
the input field and the required JavaScript for the Ajax communication (see Resources/Private/Templates/ViewHelpers/Widget/Autocomplete/Index.html
</output>

Arguments
=========


customWidgetId (string)
-----------------------


extend the widget identifier with a custom widget id

objects (anySimpleType)
-----------------------


Objects to auto-complete

for (string)
------------


Property to fill

searchProperty (string)
-----------------------


Property to search within when filtering list