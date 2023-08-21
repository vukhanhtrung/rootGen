# Suggestions for RootGen v0.2
## Game data

### Your concerns:
1. Movable landmarks (Ferry):

Honestly reading through the section, I don't see what other concerns your have, beside the concerns you created by your own solution(s).
### Solution:

Encoding the Landmark into 1 addiction column.
You said
> I don't want to add a data column to the clearings (the most logical place to put landmarks) since most landmarks are not movable and we'd be repeating an entire column of data for little gain

But if you're to repeat the whole header, you're repeating the same data all the time too, rather than just repeating the landmark info in clearing.

A clearing 11 Fox with: **Ferry used, 2 Cats, 1 Ruin, 1 Sawmill, wood** could be encoded
```PHP 
11F C2Sw MR(F)
```

Here we introduce M as a collum for Map data
symbol| meaning
-|-
M| Map column
R| Ruin
F| ferry
(x)| - Indicate x is used, card revealed, plot hidden. <br>-  Meaning different from their default/Initial state

