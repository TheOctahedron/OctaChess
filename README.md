**OctaChess – minimalist chess, featuring its own bot, Catfish (coming soon)**

### Architecture

*This architecture represents the planned project structure and may evolve during development.*

```bash
OctaChess/
├── index.html                    ← Main HTML entry point (Vite)
├── package.json                  ← Project metadata, dependencies, and scripts
├── package-lock.json             ← Locked dependency versions
├── vite.config.js                ← Vite configuration with React plugin
├── README.md                     ← Project documentation
├── .gitignore                    ← Git ignore rules (e.g., node_modules, dist)
│
├── public/                       ← Static assets served directly
│   ├── favicon.svg               ← Application icon
│   ├── wasm/                     ← WebAssembly files
│   │   └── sql-wasm.wasm         ← SQL.js WebAssembly module
│   │
│   └── pieces/                   ← Chess piece images
│       ├── white/                ← White chess pieces
│       └── black/                ← Black chess pieces
│
├── src/                          ← Main application source code
│   │
│   ├── main.jsx                  ← React entry point (mounts App into the DOM)
│   │
│   ├── app/                      ← Application initialization and coordination
│   │   ├── App.jsx               ← Root React component
│   │   ├── controller.js         ← Coordinates application and game operations
│   │   ├── state.js              ← Central application state
│   │   └── events.js             ← Application event handling
│   │
│   ├── ui/                       ← React UI components
│   │   ├── Board.jsx             ← Renders the complete 8×8 chessboard
│   │   ├── Square.jsx            ← Renders an individual board square
│   │   ├── Piece.jsx             ← Renders an individual chess piece
│   │   ├── Coordinates.jsx       ← Displays board coordinates (a–h, 1–8)
│   │   ├── Controls.jsx          ← Game controls (undo, restart, etc.)
│   │   ├── Menu.jsx              ← Main application menu
│   │   ├── Promotion.jsx         ← Pawn promotion interface
│   │   ├── GameStatus.jsx        ← Displays check, checkmate, and draw status
│   │   └── Themes.jsx            ← Board and interface theme selection
│   │
│   ├── game/                     ← Chess game logic
│   │   ├── game.js               ← Main game orchestration
│   │   ├── rules.js              ← Legal moves and chess rules
│   │   ├── history.js            ← Move history management
│   │   ├── notation.js           ← Algebraic chess notation (PGN)
│   │   ├── fen.js                ← FEN position parsing and generation
│   │   └── modes.js              ← Game modes (local, vs. bot, etc.)
│   │
│   ├── engine/                   ← Chess engine implementations
│   │   └── catfish/              ← Catfish chess engine
│   │       ├── index.js          ← Public engine interface
│   │       ├── engine.js         ← Main engine orchestration
│   │       ├── search.js         ← Position and move search
│   │       ├── evaluation.js     ← Position evaluation
│   │       ├── move-ordering.js  ← Move ordering optimization
│   │       ├── transposition.js  ← Transposition table
│   │       ├── opening.js        ← Opening logic and book
│   │       ├── config.js         ← Engine configuration
│   │       └── utils.js          ← Engine utility functions
│   │
│   ├── workers/                  ← Background execution
│   │   └── catfish.worker.js     ← Runs Catfish outside the main UI thread
│   │
│   ├── storage/                  ← Data persistence and database layer
│   │   ├── database.js           ← SQL.js initialization and database connection
│   │   ├── schema.js             ← Database table definitions
│   │   ├── migrations.js         ← Database schema migrations
│   │   ├── persistence.js        ← Saving and loading database data
│   │   │
│   │   └── repositories/         ← Database access layer
│   │       ├── games.js          ← Game records repository
│   │       ├── moves.js          ← Move records repository
│   │       └── settings.js       ← User settings repository
│   │
│   ├── styles/                   ← Application stylesheets
│   │   ├── main.css              ← Global styles and layout
│   │   ├── board.css             ← Chessboard styles
│   │   ├── pieces.css            ← Chess piece styles
│   │   ├── controls.css          ← Interface control styles
│   │   └── themes.css            ← Color themes and variables
│   │
│   └── utils/                    ← Shared utility modules
│       ├── constants.js          ← Shared application constants
│       ├── logger.js             ← Logging utilities
│       └── helpers.js             ← General helper functions
│
└── tests/                        ← Automated tests
    │
    ├── game/                     ← Chess logic tests
    │   ├── rules.test.js         ← Tests for chess rules and legal moves
    │   ├── history.test.js       ← Tests for move history
    │   └── notation.test.js      ← Tests for chess notation
    │
    ├── engine/                   ← Catfish engine tests
    │   ├── evaluation.test.js    ← Tests for position evaluation
    │   ├── search.test.js        ← Tests for search algorithms
    │   └── catfish.test.js       ← Engine integration tests
    │
    └── storage/                  ← Database tests
        ├── database.test.js      ← Tests for database initialization
        └── repositories.test.js  ← Tests for database repositories
```