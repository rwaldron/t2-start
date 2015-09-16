{::options parse_block_html="true" /}

<div class="row">
<div class="large-12 columns">

## <img class="constrain-sm" src="https://s3.amazonaws.com/technicalmachine-assets/technical-io/modules/camera.png"> Camera

[<i class="fa fa-github"> View source on Github</i>](https://github.com/tcr/node-audiovideo)

### Step 1

Make a directory inside your "tessel-code" folder called "camera", change directory into that folder, and initialize a tessel project:

`mkdir camera; cd camera; t2 init`

### Step 2

</div>
</div>

<div class="row">
<div class="large-6 columns">

Plug any USB camera into either of Tessel's USB ports, then plug Tessel into your computer via USB.

</div>
<div class="large-6 columns">

![](http://i.imgur.com/aaQT2wC.jpg)

</div>
</div>

<div class="row">
<div class="large-12 columns">

### Step 3

</div>
</div>

<div class="row">
<div class="large-12 columns">

Install by typing `npm install audiovideo` into the command line.

Also install `fs` so you can write the file: `npm install fs`.

### Step 4

</div>
</div>

<div class="row">
<div class="large-12 columns">

Rename "index.js" to "camera.js" and replace the file's contents with the following:

{% highlight js %}
// Any copyright is dedicated to the Public Domain.
// http://creativecommons.org/publicdomain/zero/1.0/

/*********************************************
This basic camera example takes a picture and
streams it to a file called "out.jpg".
*********************************************/

var av = require('audiovideo');
var fs = require('fs');

av.acquireCamera(function (err, camera) {
  camera.captureShot('jpeg').pipe(fs.createWriteStream('out.jpg'));
});
{% endhighlight %}

Save the file.

</div>
</div>

<div class="row">
<div class="large-12 columns">

### Step 5

</div>
</div>

<div class="row">
<div class="large-6 columns">

In your command line, `t2 run camera.js`

Watch x, y, and z values appear in your terminal! Move the Tessel module around to see acceleration along different axes.  

**Bonus:** Change the code to make the accelerometer output information once per second (every 1000ms).  

To see what else you can do with the accelerometer module, see the module docs [here](https://github.com/tessel/accel-mma84).

</div>
<div class="large-6 columns">

![](http://i.imgur.com/KnXf6uL.gif)

</div>
</div>

<div class="row">
<div class="large-12 columns">

### Step 6

What else can you do with a accelerometer module? Try a [community-created project.](http://tessel.io/projects)

<div class="row">
<div class="large-6 columns left">
<iframe frameborder="0" height="270" scrolling="no" src="http://tessel.hackster.io/rickyrobinett/a-sleep-tracker-for-your-dog-using-tessel-and-twilio/embed" width="360"></iframe>
</div>
<div class="large-6 columns left">
<iframe frameborder="0" height="270" scrolling="no" src="http://tessel.hackster.io/svdockum/tesselneobullseyelevel/embed" width="360"></iframe>
</div>
</div>

What are you making? [Share your invention!](//tessel.io/projects)

If you run into any issues you can check out the [accelerometer forums](http://forums.tessel.io/category/accelerometer).

</div>
</div>
