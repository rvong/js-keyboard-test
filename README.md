Keyboard Test
=============
Show keypress info/stats + heatmap.


Todo
========
- Finish
- Use Angular or some other JS framework to bind data instead of tons of manual (jQuery) updates.
- A more useful version in C# using system hook (https://github.com/rvong/kbdking)


Browser Support
======
Key Codes are sometimes browser specific.
Example: IE/Chrome sends 91 for left-win and 92 for right-win.
But, Firefox sends 91 for both left-win and right-win.

Key location sends 0, 1, 2, 3 on keydown and keyup to indicate the location of the key pressed.
For keys without corresponding pairs, 0 is sent.
For keys with pairs, 1 is sent for the left key and 2 is sent for the right key.
For all numpad keys, 3 is sent.

Key location may not be supported in some browsers.
Firefox added the location property in Gecko 15.0+.
Chrome has a broken keyLocation property that sends the correct key location on keydown, but not keyup.
For all keyup events, 0 is sent.  So, there's no way to find out when a key is released in Chrome, as of Chrome v27.

Keydown and keyup behavior also varies across browsers.
When two keys are pressed down and then released simultaneously, it is not necessarily
the case that two keyup events are triggered.
Example:
Chrome =>
When both SHIFT keys are released simultaneously, only one keyup event is triggered.
Similarly for ALT and WIN.
Firefox behaves similarly to Chrome.
IE is similarl to Chrome, except both ALT keyup events are triggered when simultaneously released.

In Chrome, the context-menu keyup event is not triggered when the context-menu key is released.
IE and Firefox do trigger the keyup event upon context-menu release.

Key press events are determined to be inconsistent
with key press events gathered by low level keyboard hook using the Windows API.
