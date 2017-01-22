+++
date = "2016-12-26T16:01:21-08:00"
title = "Swipe to Highlight"
list_item_layout = "list-item-media-left"

media_src = "swipe-to-highlight"
media_title = "Swipe to Highlight"
media_type = "video"
+++

Highlighting text is a core feature of the Logos Bible app. The swipe-to-highlight feature enables quick highlighting without the need to drag selection handles. Simply long press to select a word, then drag outside the word boundary to automatically start highlighting.

For convenience, the selection automatically snaps to word boundaries, but more fine-grained control is still available by creating a standard text selection, then choosing highlight from the context menu.

Utilizing the API's written by our text display team, I implemented the Java and c++ JNI layers necessary for integration of the visual highlight, gestures, and associated preference.<!--more-->
