# js-powered-css
js-powered-css is a js library that lets you create and inline css rules on the fly to animate your page. for example if you want a to select things on the fly or add selectors to a ruleset etc, this lets you do that. 

## stylings
You can list off your styles in a few different ways. see example-styles.json in src folder for further instructions. you can list a stylesheet with media queries or you can list a style sheet with no media queries.

## API
###Constructor: 
jsonCSS(styleslist [, styleElementID string])

You must give it a stylesList in JSON format or JavaScript Object Literal. You can declare an ID associated with the style element if you want and when you render the element, the ID in the style element will be the ID you set here

Assuming that your declared myStyle somewhere before here in a way similar to the examples

eg: var myJsonStyles = new jsonCSS(myStyle);
alternatively: var myJsonStyles = new jsonCSS(myStyle, "screen-md-styles");

###Renderer:
jsonCSS.render([ styleElementID string])
you can call .render() for functions to output the json CSS as a inline CSS at the bottom of the body. you can also pass a string into this function to make name the output with a spicific ID

eg: myJsonStyles.render();
alternatively: myJsonStyles.render("screen-md-styles-v1");

###Clear:
jsonCSS.clear([elementID string])
You can use this to clear all outputs generated by this variable or clear a spicific ID generated by this styleset. 

eg: myJsonStyles.clear();
alternatively: myJsonStyles.clear("screen-md-styles-v1"); //this will clear just the element with that ID

Note: You can only clear Style elements generated by that instance of jsonCSS so if you have multiple instances of jsonCSS, you cannot clear each other's style elements by calling clear on another style's ID. You also shouldn't be removing style elements via other means (eg with jQuery) but the code will be generally smart enough to notice but edge cases exist.

###getID() and setID(id)
errr do i need to explain these?

###jsonCSS.styleSet
This is a variable that contains an array of your styles. You can just go in and find whatever you want and change whatever rule you want. after you do that, you need to use the .render() function to update the style element associated with this instance of jsonCSS in the DOM

eg: myJsonStyles.styleSet[2].rule["position"] = "relative"; myJsonStyles.render();