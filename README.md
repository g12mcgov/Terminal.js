# Terminal.js

A hackable, extendable, utterly-simply, terminal emulator for your browser. 

![demo](http://i1158.photobucket.com/albums/p618/g12mcgov/demo.gif)

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
<div id="terminal">
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
			displayText('/about<br>');
			displayText('/home<br>');
			displayText('/github<br>');
			displayText('.bash_profile<br>');
		}, 
		cd: function(directory) {
			switch (directory[0]) {
				case '/about':
					window.location.href = '/about';
					break;
				case '/github':
					window.location.href = 'http://github.com/g12mcgov';
					break;
				}
			}	
	};
	...
```

That's it!

Of course, you change any of the styling in the `terminal.css` file.




