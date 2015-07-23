## ADDING YOUR OWN BLOCKS ##

One of the goals of sb2.js is to supply an adaptable player which scratch mod developers can use to showcase their projects on the web. Right now, you can implement your blocks by adding them to either the reporter or non-reporter sections of the blockHandler.
```
    function blockHandler(block, reporter)
```
As you will see, this function is used to interpret a block item in the project's multi-dimensional block array. "reporter" must be set to true if the space in the block is for reporters, so literal values like 1 can be handled correctly.

To add a non-reporter block, add your block definiton under
```
	if (!reporter)
```
To add a reporter block, add your block definition under
```
	} else {
```
### BLOCK DEFINITIONS ###

Blocks are defined as seen in this example:

```

	} else if (block[0] == "createCloneOf") { //this is the block name

		scripttext += "scratchClone(spr, "; //calls the scratchClone method, spr is always the sprite containing the script.
		blockHandler(block[1], true); //handles the reporter (true) inside item 1 of the block (item 0 is always the name).
		scripttext += "); "; //closes the function over it

```

As you can see, sb2.js compiles scratch projects into javascript for maximum performance. The compiled code for this would look something like:

```
scratchClone(spr, "Sprite1"); 
```

### Code Requirements ###

To avoid bugs, all reporters must be wrapped in brackets, eg:

"(1 + 1)" instead of "1+1"

1+1 would break if you were to add a multiplication after it:

"1+1\*3 = 4" vs "((1+1)**3) = 6"**

Main guidelines:
  * Do NOT use i and j in for loops.
  * In functions, keep to undefined names for variables eg. spriten, name, item etc
  * Always end lines with "; ". There are no newlines in generated code.
  * Wrap number-only input with castNumber(number);
  * Make sure you put your block in the right section.

### The future? ###

sb2.js will work with a block plugin system so you can continue using the base engine with blocks simply added. If there are big engine changes then you will have to fork sb2.js anyways. (like in byob)