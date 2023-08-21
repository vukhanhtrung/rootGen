# Suggestions for RootGen v0.2
## 1. Game data Header
### 1.1 What we gain?
For 1 position, header or no header are practically the same thing. 
So what do we gain by grouping game constants to header for multiple turns data encoding?

- Game constants we consider for simplicity: Map-name, map-suit, factions, deck, variant

No header:
```PHP
Turn 1:
    f ep CAPD - FMRRRFMFMRMF - - - v[DI, 3P]
    # Turn 1 Faction data
    # Turn 1 Clearing data
Turn 2:
    f ep CAPD - FMRRRFMFMRMF - - - v[DI, 3P]
    # Turn 2 Faction data
    # Turn 2 Clearing data
Turn 3:
    f ep CAPD - FMRRRFMFMRMF - - - v[DI, 3P]
    # Turn 3 Faction data
    # Turn 3 Clearing data

```
We will have to repeat the game constants with every turn saved.

With header:
```PHP
f ep CAPD - FMRRRFMFMRMF - - - v[DI, 3P]
Turn 1:
    # Turn 1 Faction data
    # Turn 1 Clearing data
Turn 2:
    # Turn 2 Faction data
    # Turn 2 Clearing data
Turn 3:
    # Turn 3 Faction data
    # Turn 3 Clearing data
```

This open room for us to be more verbose with header data
`f ep CAPD - FMRRRFMFMRMF - - - v[DI, 3P]`
can now be 
```PHP
Map:Fall 
MapSuits:FMRRRFMFMRMF 
Deck:EP 
Factions:[Cat, WA, Corvid, Duchy] 
Gamemode[DI,3P]
```



### 1.2 Your concerns:
- Movable landmarks (Ferry)

Honestly reading through the section, I don't see what other concerns you have (beside the concerns you created by your own solutions.)
Also I don't know what your example on Fall map has to do with the Ferry problem.
### 1.3 Movable landmarks (Ferry) Solution:

Encoding the Landmark into 1 addiction column.
You said
> I don't want to add a data column to the clearings (the most logical place to put landmarks) since most landmarks are not movable and we'd be repeating an entire column of data for little gain

But if you're to repeat the whole header, you're repeating the same data all the time too, rather than just repeating the landmark info in clearing. 
Also the info about which Landmark the clearing has would be important for discusion, not much different from how we encoded clearing suit into the data.

A clearing 11, Fox suit, with: **Ferry used, 2 Cats, 1 Ruin, 1 Sawmill, wood** could be encoded
```PHP 
11FRFe C2Sw
```
Symbol | meaning
-|-
11FRFe | 11: clearing 11 <br> F: Fox suit <br> R: Ruin<br> Fe: Ferry used
C2Sw | C: Cat <br> 2: 2 warriors <br> S: Sawmill <br> w: wood token

## 2. Faction grouped data vs Piece-type grouped data:
WIP