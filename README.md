FoscamView
==========
A lightweight, cross-platform controller and viewer for Foscam HD webcams written entirely in HTML/JavaScript.

Purpose
-------
Foscam provides browser plugins and smartphone apps to control their line of HD webcams. The browser plugins are completely closed-source however (really, ActiveX?!), and don't work on Linux.

Fortunately, Foscam [publishes an SDK](http://foscam.us/forum/new-sdk-cgi-application-t13426.html). The SDK documents CGI commands that you can send to control the camera and view images.

I wanted a lightweight, cross-platform application that could run on a local computer or on a web server. So I created a self-contained HTML page that provides the following functionality:

* Pan and tilt controls.

* Set the camera hostname / IP address, image refresh rate, and length of time a pan/tilt command runs.

* A view pane that displays snapshots from the camera at a user-defined interval.

* A view pane that displays the raw results returned by the camera after each CGI command.

The page sends URLs to the camera by dynamically modifying the 'src' attribute of &lt;img&gt; and &lt;iframe&gt; elements. This removes the need for third-party plugins, XMLHttpRequest() objects (with their associated cross-origin issues), etc.

I developed and tested this using a Foscam FI9821W V2, and it should work with other Foscam HD cameras. (Foscam's non-HD cameras use a different set of CGI commands.)

Usage
-----
Save the FoscamView.html file locally on your computer, or host it on a web server -- it works either way.

You **must** change some of the default parameters in the page's JavaScript section to get the CGI commands to work with your own webcam. Specifically:

* **host**: Although you can change this value through the user interface, by setting it in the code you have a persistent default value every time you reload the page.

* **username**: The webcam account's username ("administrator" level privileges are not necessary; the "operator" level is enough). You can set up users through the regular Foscam web interface.

* **password**: The webcam account's password.

Optionally, you can also change the following values in the code to set persistent default values:

* **viewerRefresh**: How often (in milliseconds) the viewer pane updates with a new snapshot from the webcam.

* **panTiltDuration**: How long a pan or tilt command is allowed to run (in milliseconds). A smaller value means slower webcam movement.

Screenshots
-----------
Here are some screenshots:

![FoscamView with controls visible](/../screenshot/FoscamView-controls-visible.png?raw=true)

![FoscamView with controls hidden](/../screenshot/FoscamView-controls-hidden.png?raw=true)

