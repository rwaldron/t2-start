{::options parse_block_html="true" /}

<div class="row">
<div class="large-12 columns">

## <img class="constrain-sm" src="https://s3.amazonaws.com/technicalmachine-assets/technical-io/modules/usb.png"> Camera

[<i class="fa fa-github"> View source on Github</i>](https://github.com/tessel/tessel-av)

### Step 1

Make a directory inside your "tessel-code" folder called "camera", change directory into that folder, and initialize a tessel project:

`mkdir camera; cd camera; t2 init`

### Step 2
</div>
</div>

<div class="row">
<div class="large-6 columns">

Plug Tessel into your computer via USB, then plug the camera module into either of Tessel's USB ports. You will also need a UVC compatible USB camera. For this tutorial, either of these is suitable: 

- http://www.amazon.com/Creative-Live-5-7MP-Webcam-Black/dp/B004431UBM/
- http://www.amazon.com/Creative-Live-Sync-720P-Webcam/dp/B0092QJRPC

</div>
<div class="large-6 columns">

![](http://i.imgur.com/uifn1p7.jpg)

</div>
</div>

<div class="row">
<div class="large-12 columns">

### Step 3

Install by typing `npm install tessel-av` into the command line.

### Step 4

Rename "index.js" to "camera.js" and replace the file's contents with the following:

{% highlight js %}
// Any copyright is dedicated to the Public Domain.
// http://creativecommons.org/publicdomain/zero/1.0/

/*********************************************
Create a server that responds to every request by taking a picture and piping it directly to the browser.
*********************************************/

var av = require('tessel-av');
var fs = require('fs');
var os = require('os');
var http = require('http');
var port = 8080;
var camera = new av.Camera();

http.createServer((request, response) => {
  response.writeHead(200, { 'Content-Type': 'image/jpg' });

  camera.capture().pipe(response);

}).listen(port, () => console.log(`http://${os.hostname()}.local:${port}`));

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

Hooray! You should see the following in your terminal: 

```
$ t2 run camera.js
INFO Looking for your Tessel...
INFO Connected to bishop.
INFO Building project.
INFO Writing project to RAM on bishop (314.88 kB)...
INFO Deployed.
INFO Running camera.js...
http://bishop.local:8080
```

> Note: `bishop` is just the name of my Tessel 2 board, yours will display whatever you've named your board!

**Bonus:** EXTRA CHALLENGE FOR VIDEO

To see what else you can do with the USB camera module, read the [tessel-av](https://github.com/tessel-av) documentation.

</div>
<div class="large-6 columns">

![](http://i.imgur.com/Yjvr1Uc.png)

</div>
</div>

<div class="row">
<div class="large-12 columns">

### Step 6

What else can you do with a camera module? Get inspired by a [community-created project.](http://tessel.io/projects)

- Try connecting a button to your Tessel 2 and use it as a shutter. 
- Use an USB storage drive to store many photos.


What are you making? [Share your invention!](//tessel.io/projects)

If you run into any issues you can check out the [module forums](http://forums.tessel.io/c/modules).

</div>
</div>
