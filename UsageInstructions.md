## HOW TO EMBED sb2.js (simple) ##

sb2.js has a simple one script embed method which is useful for embedding scratch projects into your personal websites. All you have to do is set the properties (minus basedir).

Here's what it looks like with an autoloading project:

```
<script type="text/javascript" src='http://sb2js.tk/sb2.js'></script>

<script>
    autoLoad = "MarioBros.sb2";
</script>

<canvas id='scratch' width='486' height='391' tabindex='1'></canvas>
```

Example: http://dl.dropbox.com/u/12239448/js%20project%20reader/simple.html

For more information on the properties see below. For the canvas you can use any canvas with the id "scratch".

This script will be kept up to date with the latest SVN versions of each of the scripts. The embed code will not change at all through revisions. (some properties may though)

If you're going to run a site that embeds sb2.js as one of its main functions then you should use the method below to not kill my website. :)

## HOW TO EMBED sb2.js (hosting the source files) ##

Include all:
```
    <script type="text/javascript" src='script/ZipFile.complete.js'></script>
    <script type="text/javascript" src="http://canvg.googlecode.com/svn/trunk/rgbcolor.js"></script> 
    <script type="text/javascript" src="http://canvg.googlecode.com/svn/trunk/canvg.js"></script> 
    <script type="text/javascript" src="script/sb2.js"></script>
```

(may be simplified to complete sb2.js as seen above)

"script/" being relative to your base directory, that's where you put the sb2.js files.

Then add a canvas with id "scratch" anywhere on the page, eg:
```
    <canvas id='scratch' width='486' height='391' tabindex='1'></canvas>
```
And you're done! You can load files with the method ReadFile(url);

## PROPERTIES ##

sb2.js has a couple of properties that you can set to change the way the player behaves. Some of these are basedir, framerate, autoLoad, framed, scaledHeight and editorInit().

  * basedir - pretty much required - you set it to where all the sb2.js scripts and images are. This needs to be on the domain you're embedding on.

  * framerate - the target frequency that frames are drawn, and the forever tick rate in non turbo mode. In Scratch 2.0 (and sb2.js) this defaults to 30, however in Scratch 1.4 projects run at 40. You shouldn't set this higher than your refresh rate if you only want smoother animation.

  * autoLoad - the file url loaded upon full loading of the player. If this isn't defined then the player will not load any file.

  * framed - defines whether or not the sb2.js frame is used. Defaults to true.

  * scaledHeight - should be equal to the height of the element when scaled via styles. Scale is assumed to be 1 if not defined.

  * editorInit() - called when the project is loaded. This is mainly for an editor interface, but you can use it for whatever you want.

Here's an example:

```
<script>
    basedir = "/coolstuffthatiembed/sb2js/"; // relative to root directory
    autoLoad = "/scratchstuff/MarioBros.sb2";
    framed = false;
</script>
```

This will load MarioBros.sb2 with no frame at normal scale. The width and height of the canvas should be 480x360 for a non framed project, so make sure to configure the canvas right.

## FUNCTIONS ##

You can call these from anywhere in the page to control the player.

  * execGreenFlag() - executes Green Flag scripts. should always be called after stopAll().
  * stopAll() - stops all scripts.