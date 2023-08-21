# Suggestions for RootGen v0.2
## 1. Game data Header
### 1.1 What we gain?
For 1 position, header or no header are practically the same thing. So what do we gain by grouping game constants to header?

Game constants: Map name, map suit, deck, variant
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

Honestly reading through the section, I don't see what other concerns your have, beside the concerns you created by your own solution(s). 
Also I don't know what the example on Fall map has to do with the ferry problem.
### 1.3 Solution:

Encoding the Landmark into 1 addiction column.
You said
> I don't want to add a data column to the clearings (the most logical place to put landmarks) since most landmarks are not movable and we'd be repeating an entire column of data for little gain

But if you're to repeat the whole header, you're repeating the same data all the time too, rather than just repeating the landmark info in clearing.

A clearing 11 Fox with: **Ferry used, 2 Cats, 1 Ruin, 1 Sawmill, wood** could be encoded
```PHP 
11F C2Sw MRFe
#11F : clearing 11, Fox suit
#C2Sw: Cat Faction: 2 warriors, Sawmill, wood token
#MRFe: Map data: Ruin, Ferry used
```

Here we introduce M as a collum for Map data
symbol| meaning
-|-
M| Map column
R| Ruin
F| Ferry
e| suffix indicate used object.
