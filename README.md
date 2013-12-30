templates
=========

Frakture Multimedia Templates

Frakture Templates are directories that contain a template.json file, and any supporting files, that define a multimedia format.


Sample Template:
{
	// The standard Frakture Message type. email, blog, banner_ad, online_video, etc.
	"message_type":"email",
	// A css class indicating the icon to be used.  Font-Awesome icons http://fontawesome.io/3.2.1/icons/ are commonly used
	"icon-class":"icon-at-sign",
	//Public label for this template
	"label":"Standard Email Template",
	// Configuration options for the message, covering all formats
	"configuration":{
		"from_name":{"type":"string"},
		"from_email":{"type":"string"}
	},
	// 1 or more formats this message can be displayed as.  
	// This is NOT to be confused with separate content, or messages different segments, which should be in independent messages.
	// This is the same identical content, targets, and links, etc. optimized for different rendering engines.
	// For example, when reading email, you can read EITHER the text version, OR the HTML version, but not both.  When viewing a video
	// on a smaller device, you might get a smaller copy of the file, which would be a different format.
	//
	"formats":[
		{	
			// Label for the format
			"label":"HTML"
			// (optional) engine to render content
			"render_engine":"hogan",
			// (optional) file to merge content into
			// Content will be merged by the render engine along the lines of 
			// extend(format_config.defaults, bot.configuration, message.format[i].configuration),
			// 
			"render_file":"index.html",
			// Configuration options specific to this format
			"configuration":{
				"html":{"type":"wysiwyg"}
			}
		},
		{
			"label":"Text",
			"help":"Emails are sent with both HTML and text formats, for mobile readers",
			"render_engine":"hogan",
			"render_file":"index.txt",
			"configuration":{
				"text":{"type":"wysiwyg"}
			}
		}
	]
}
