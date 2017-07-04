# AutoToolsWebScreens
Stuff injected into every AutoTools web Screens that you can use in your own Web Screen presets

# How To Use
Look into each file and stuff will be documented :)

If you want to try out the demos you can do so by using the direct raw Github URL as the Source in the **AutoTools Web Screen** action. For example, to use the card list demo, use [this](https://raw.githubusercontent.com/joaomgcd/AutoToolsWebScreens/master/demos/cardlist/cardlist.html) as the source.

# Web Screen Variables
You can create custom variables for a page used as an AutoTools Web Screen.

To do this include a special <meta> tag in the pages head section with the following format:

**&lt;meta name="autotoolswebscreen" type="variablejs" group="Title" id="titleFromTasker" label="Title" description="Title to show at the top."  hint="YouTube" /&gt;**

Let's break it down:

*   **name** - is always **autotoolswebscreen**
*   **type** - can be **variablejs** (will create a JavaScript variable) or **variablehtml** (will replace an html element with the specified ID)
*   **group** - is used to group variables together in the AutoTools Web Screen Tasker configuration screen
*   **id** - the name of the JavaScript variable or HTML element to create/replace
*   **label** - title of the option in the configuration screen
*   **description** - summary of the option in the configuration screen
*   **hint** - placeholder text of the option in the configuration screen

Here are other possible fields for this ***&lt;meta&gt;** tag

*   **subtype** - can be **boolean** to make the option in Tasker a switch instead of a text input. In JavaScript will create a variable with either true or false
*   **defaultValue** - pre-filled value for the field
*   **options** - If set, will create an options field in the AutoTools Web Screen Tasker configuration screen instead of a direct text input field. Set to a comma separated list of values.
*   **isIcon** - if **true** then the input field in the AutoTools Web Screen Tasker configuration screen will prompt the user to browse for an icon
*   **isIcons** - same as above but supports multiple icons
*   **isImage** and **isImages** - same as above but for generic images
*   **isColor** - same as above but to browse for a color
*   **isFile** - same as above but to browse for a file of any type
*   **attribute (HTML Variable Only)** - allows you to specify an attribute to set instead of setting the inner HTML of an element (for example, setting the **href** of an **a** element)

[Here](demos/cardlist/cardlist.html)'s an example of a screen where multiple variables are used. Take a look at the source code of the page for some examples.

# Web Screen Functions
AutoTools automatically creates some convenience JavaScript functions for you so it's easier to do certain things with the data from Web Screen Variables. 

You can check out all of the functions [here](autotoolsfunctions.js).

Here are a few of the main ones:

*   **AutoTools.sendCommand(command, prefix, hapticFeedback)** - Allows you to send an AutoApps command. **prefix** is optional and if present will prepend **=:=** to the command. Example: **&lt;div onclick="AutoTools.sendCommand('hello!')"&gt;Say Hello&lt;/div&gt;** will send the "hello" command when clicked. If you set the third parameter to true it'll perform haptic feedback with the command.
*   **AutoTools.isSet(varName)** - returns true if the Web Screen Variable with the provide name is set, false otherwise
*   **AutoTools.setDefault(varName,value)** - sets the variable with name **varName** to the value **value** if it's not set from Tasker
*   **AutoTools.setDefaultValues(valuesObject)** - accepts an object like **{"var1":"value1","var2":"value2"}** and calls the **AutoTools.setDefault** function for each of the names and values in the object, so you can set all your default values in one call. Check [the source of this page](demos/functions/functiondemo.html) for an example on how to use this.
*   **AutoTools.hide(element)** - hides an element on the page
*   **AutoTools.show(element)** - shows an element on the page
*   **AutoTools.variablesToElements(variableNamesArray, rootElementsId, rootElementClass, itemTransformer)** - converts AutoTools Web Screen variables to HTML elements on a list. **itemTransformer** is optional and if present will be called for every element that's created. Check [the source of this page](demos/functions/functiondemo.html) for an example on how to use this.


