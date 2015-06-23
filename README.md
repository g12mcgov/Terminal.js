# Terminal.js

A hackable, extendable, utterly-simply, terminal emulator for your browser. Here's a preview of it running locally, in Chrome:

![demo](http://i1158.photobucket.com/albums/p618/g12mcgov/demo1.gif)

(It doesnt need jQuery either!)

Why?
=======

Because I'm rebuilding my personal site, and I've been inspired by other developers who have embeded a command prompt/something of the like to their site. And I didn't like any of the current options I found on GitHub. 

Currently, it only supports `ls` and `cd` commands, but this was only concieved in approx. 1.5 hours, and I plan on working on this some more. 

Using
=======

`Terminal.js` was built to be extendable and forkable. To include it in your own project, simply add the following to your `html` file:

(Ex: `index.html`):

```html
<!DOCTYPE html>
<html>
<head>
	<link rel="stylesheet" href="terminal.css">
	<!-- Terminal.js -->
	<script type="text/javascript" src="terminal.js"></script>
</head>
...
```

Then, add the following `div`:

```html
<div id="terminal"></div>
```

How-To
=======

Wanna make your own custom commands? Change the styling? Etc... 

First off, change your `root` text to whatever you like. I've set mine to what my machine looks like:

```javascript
var root = 'grantmcgovern@gMAC-2:~/<span style="color:#FF00FF;">Developer</span> $ ';
```

Then, in the `commands` object, simply define your own command (key) and an action (value) via an anonymous function.

**Example:**

```javascript
var commands = {
		ls: function() { 
			displayText('/about<br>');
			displayText('/home<br>');
			displayText('/github<br>');
		},
		ll: function() {
			displayText('.<br>');
			displayText('..<br>');
			displayText('.bash_profile<br>');
			displayText('.bash_history<br>');
			displayText('<span style="color:blue;">about</span><br>');
			displayText('<span style="color:blue;">home</span><br>');
			displayText('<span style="color:yellow;">github</span><br>');
		}, 
		cd: function(directory) {
			// Check if it was called with no args 
			directory = (typeof directory !== 'undefined') ? directory : null;

			if(!directory) {
				displayText("-bash: cd takes [1] argument <br>");
			}
			else {
				switch (directory[0]) {
					case '/about':
						window.location.href = '/about';
						break;
					case '/github':
						window.location.href = 'http://github.com/g12mcgov';
						break;
					default:
						window.location.href = '/';
						break;
				}
			}
		},
		mailx: function(body) {
			window.location.href = 'mailto:grantmcgovern.mcgovern@gmail.com?body=' + body;
		},
		help: function() {
			displayText('Available commands:<br>');
			displayText('ls -- list directory contents ( [ls] [file ...])<br>');
			displayText('cd -- change directory ( [cd] [directory ...])<br>');
		},
	...
```

That's it!

Of course, you change any of the styling in the `terminal.css` file.




