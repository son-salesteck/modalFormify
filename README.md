# modalFormify
$.fn.modalFormify is a jQuery plugin to create modal form programmatically



## Description 
Create <a href="https://learn.jquery.com/plugins/basic-plugin-creation/" target="_blank" >jquery plugin</a> for creating or open a modal form and insert revelant form element and a submit handler through ajax. <br>
The plugin must :
<ul>
  <li>Provide plugin debugging</li>
  <li>Provide Public Access to Default Plugin Settings</li>
  <li>Provide Callback Capabilities</li>
  <li>ProProvide Public Access to Secondary Functions as Applicable</li>
  <li>Keep Private Functions Private</li>
  <li>Give Full Control of Elements</li>
</ul>

The purpose of this plugin is to create form programatically through object and function. <br>
When form is submited, apply jqueryValidation Plugin. <br>
Also the plugin must implement bootstrap modal. <br>


## Usage

```javascript
import modalFormify

$(DOM.selector).modalFormify(options); # returns modalFormify api
```

## Requirement 

<ul>
  <li>jquery 3.5.< </li>
  <li>jqueryValidation</li>
  <li>bootstrap 4.< </li>
</ul>


## Todo
Provide Public Access to Default Plugin Settings
```javascript
// Plugin definition.

$.fn.modalFormify= function( options ) {    
    // Extend our default options with those provided.    
    // Note that the first argument to extend is an empty    
    // object – this is to keep from overriding our "defaults" object.
     var _settings = $.extend( {}, $.fn.modalFormify.defaults.option, options );  
    // Our plugin implementation code goes here. 

}; 

// Plugin defaults – added as a property on our plugin function.

var default = $.fn.modalFormify.defaults = {
    option : {
      
    },
   
    // default field option must have those property
    fieldOption : {
        // each field must be unique 
        name : "",
        // label for the input
        label : "", 
         // select, text, radio, checkbox, ... 
        type : "",
        className : "", // this is added to the dom element
        attr : {}, // this is added to the dom element
        // this is used for the jqueryValidation plugin
        validator : function(){
        }
    }
};
```
Define private variable for the plugin's use <br>
exemple : (list all private variable for the api and implement it, this is just an example)
```javascript
// private property must start with _ (underscore)
$.fn.modalFormify= function( options ) {    

    var _data = [];
    var that = this;

}; 

```

Determine the default object property and value for the use of our plugin <br>
example :
```javascript
var pluginDefOption = default.option = {
    // file path to the ajax url
    ajax: "/path/to/ajax-api"
    // or object
    "ajax": {
        "url": "data.json",
        "type": "POST",
        "data": function ( d ) {
            return $.extend( {}, d, {
                "extra_search": $('#extra').val()
            } );
        }
    }
};
```


determine and implement Callback <br>
exemple : (list all event accessible for the api and implement it, this is just an example)
```javascript
$.fn.modalFormify.defaults = {
    event : {

        init: function (modalFormify) {
            if (modalFormify.event.debug) {
                console.log('init(modalFormify) called', {modalFormify: modalFormify});
            }

        },
        preInit: function (modalFormify) {
            if (modalFormify.event.debug) {
                console.log('preInit(modalFormify) called', {modalFormify: modalFormify});
            }
            return true;
        },
        onInit: function (modalFormify) {
            if (modalFormify.event.debug) {
                console.log('onInit(modalFormify) called', {modalFormify: modalFormify});
            }

        },
        postInit: function (modalFormify) {
            if (modalFormify.event.debug) {
                console.log('postInit(modalFormify) called', {modalFormify: modalFormify});
            }
        },
        initDraw: function (modalFormify) {
            if (modalFormify.event.debug) {
                console.log('initDraw(modalFormify) called', {modalFormify: modalFormify});
            }

        },
        preDraw: function (modalFormify) {
            if (modalFormify.event.debug) {
                console.log('preDraw(modalFormify) called', {modalFormify: modalFormify});
            }
            return true;

        },
        onDraw: function (modalFormify) {
            if (modalFormify.event.debug) {
                console.log('onDraw(modalFormify) called', {modalFormify: modalFormify});
            }

        },
        postDraw: function (modalFormify) {
            if (modalFormify.event.debug) {
                console.log('postDraw(modalFormify) called', {modalFormify: modalFormify});
            }

        }
    }
};
```

Provide Public Access to Default Plugin functions (api functions)<br>
exemple : (list all public function for the api and implement it, this is just an example)
```javascript
// Plugin definition.

$.fn.modalFormify= function( options ) {    
    var that = this;
    
    that.data = function (){
        return _data; // Array(object)
    };

}; 

```
