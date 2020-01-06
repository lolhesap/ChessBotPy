# ChessBotPy

ChessBotPy is an interface between certain chess sites, such as Lichess or Chess.com and a chess engine, such as Brainfish (a variation of Stockfish).
The basic operation of this bot is very simple:

1. A browser userscript tracks your chess game, and sends all the moves to the python program through a websocket.
2. The python program converts moves into a format suitable for UCI engines
3. The engine calculates the best moves
4. The data from engine is outputted to the user and sent back to the client

### Caveats:

To be able connect to a websocket, a site must not have restricted content security policy (CSP), specifically connect-src. Fortunately this can be bypassed by opening a new window, which does not have CSP, and communicating through `window` objects in javascript.

## Planned features

**Site support**

-   Support analysis mode properly on lichess
    -   Including variations
-   Support for Chess.com
-   Support for Chess24

**Interface**

-   Read out ponder
-   Read out a move ahead if there is a forced line
-   GUI
    -   Priciple variation lines
        -   Multiple principle variations if they they are within x centipawns of each other
            -   i.e. if no single PV line is clearly better
    -   Centipawn (score)
    -   If currently enabled/searching
    -   Which side you're playing as
    -   Found game / url
    -   FEN
    -   Settings
    -   Console
    -   SVG representation of the board
        -   draw PV lines
            -   Each line is a different color
            -   each move ahead shifts/fades/transparency the color a bit
            -   Settings for SVG stuff

**Configurations**

-   Settings files
    -   Different files for engine and GUI
    -   Generate engine.ini automatically
        -   Base engine setting file off of selected engine
-   Depth / Time
    -   Advanced settings
        -   Stage of game, etc.
-   Output options
    -   Text
    -   Voice
    -   SVG

## Known issues:

-   Lichess parser does not handle interrupts in analysis mode.
-   Should we send full board state from JS every time?
-   Auto managed settings are saved to settings file?

## Todo

-   Create a CSS Grid, 2x2 layout
    -   Main info and buttons
        -   Show PVs, CP, FEN
        -   Start, play as
        -   Open engine settings
        -   Depth / Time setting
    -   SVG Board
    -   Console
    -   Open space for stuff to open to
        -   Engine settings, etc
-   Send in necessary information from server
-   Create a on message parser, that will feed data to vue
