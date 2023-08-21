# Suggestions for RootGen
# Game data

>I don't want to add a data column to the clearings (the most logical place to put landmarks) since most landmarks are not movable and we'd be repeating an entire column of data for little gain

But you're ok with repeating the whole game setting header everytime?
The position in your example
```PHP
f ep v[]

C 23 Z[%be %b %h] h[3] 
A 7 Z[[] h[3] w[2] $[4]
P 11 Z[R#t %f %f] h[5] 
D 20 Z[B#b M#l %t %c] h[R#@ R#D R#%c F#f M#b] 0Dw P#f P#y P#m P#r P#a crowns[112]

C day 2 2 - - -
draw[26] 
dis[F#%b R#p M#@ B#@  B#D]

 1F w[1D] b[] t[Per]
 2M w[6D 1C] b[Dc Dc] t[Dt]
 3R w[2C 2P] b[Cr] t[]
 4R w[2A 1P] b[Ar] t[As]

 5R w[3D 1P] b[Dm Dm] t[Dt]
 6F w[5D] b[] t[]
 7M w[1C 1P] b[Cr Cs] t[]
 8F w[4C] b[Cs Cr] t[Cw Ct]

 9M w[3C] b[Cw] t[]
10R w[1P] b[] t[As Dt Pse]
11M w[3D 4C 1P] b[Cw] t[]
12F w[1A] b[Af] t[As]
```
would be encoded
```PHP
# Game Constants
Map: Fall
Deck: E&P

```