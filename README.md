# Connect Four Extension – CS 608 Final Project

This repository contains an advanced, console-based **Connect Four** application developed as the final project for Algorithms and Computing Theory (CS-608). [file:1]  
The system goes beyond standard Connect Four gameplay by adding persistent player accounts, multiple game modes (including AI with scalable difficulty), a tournament system with AVL tree-based standings, and a robust persistence layer for player statistics and profiles. [file:1]

---

## Features

- **Core Connect Four gameplay** with a gravity-based 6x7 board, move validation, win detection in all directions, and draw detection when the board is full. [file:1]  
- **Persistent player accounts** supporting registration, login/logout, profile management, and long-term statistics storage. [file:1]  
- **Multiple game modes**, including:
  - Human vs Human (HvH)
  - Human vs AI (HvAI) with Random, Medium, and Hard difficulty levels [file:1]
- **Advanced AI module**:
  - Random AI: selects a valid move uniformly at random.
  - Medium AI: heuristic-based, blocks immediate threats and pursues simple strategies.
  - Hard AI: minimax/negamax search with alpha–beta pruning, bitboard representation, memoization, and move ordering. [file:1]
- **Tournament system**:
  - Round-robin scheduling so every participant faces every other participant.
  - Match queue for ordered execution of matches.
  - AVL tree-based standings with efficient updates and ranked output. [file:1]
- **Rich statistics and leaderboards**:
  - Total games, wins, losses, draws, win rate, streaks, and AI performance tracked per player.
  - Leaderboard of top N players, sorted by win rate, total wins, and username. [file:1]
- **Persistence layer** using JSON files for player profiles with atomic updates and optional backup/recovery. [file:1]  
- **Robust input handling** with a command-driven UI, validation, and helpful error messages. [file:1]  
- **Testing and quality assurance** via unit tests, integration tests, and basic performance analysis. [file:1][file:2]

---

## System Architecture

The application is decomposed into several main modules. [file:1]

- **User Interface (UI) Module**
  - Parses commands, validates input, and renders outputs (boards, messages, standings). [file:1]
- **Game Engine Module**
  - Manages board state, turn logic, move history, win/draw detection, and undo. [file:1]
- **Player Management Module**
  - Handles account registration, login/logout, profile retrieval, and statistics updates. [file:1]
- **AI Module**
  - Implements Random, Medium (heuristic), and Hard (minimax/negamax with alpha–beta) AI opponents. [file:1]
- **Tournament Module**
  - Manages tournament creation, player registration, round-robin scheduling, match execution, and AVL tree standings. [file:1]
- **Persistence Layer**
  - Serializes/deserializes player profiles to/from JSON files, with atomic writes to avoid corruption. [file:1]
- **Testing and Utilities Module**
  - Provides unit tests, input validation helpers, and shared utilities. [file:1]

The modules interact through clear interfaces so that user commands flow from the UI to the game engine, player management, AI, tournament logic, and persistence services as needed. [file:1]

---

## Data Structures and Algorithms

The project is explicitly designed to demonstrate mastery of data structures and algorithmic concepts. [file:1]

- **Board representation**
  - 2D array (list of lists or equivalent) for a 6x7 grid with gravity-based piece placement. [file:1]
- **Move history and undo**
  - Stack storing moves (player, column, row) to support multi-step undo. [file:1]
- **Turn order and scheduling**
  - Queue for player turns and ordered tournament matches. [file:1]
- **Player directory**
  - Map/dictionary/hash table for fast lookup and update of profiles and aggregate statistics. [file:1]
- **Tournament standings**
  - AVL tree (self-balancing BST) ordered primarily by wins, with secondary ordering as needed. [file:1]
- **AI search**
  - Recursive minimax/negamax search with alpha–beta pruning, bitboards, memoization, and move ordering. [file:1]
- **Recent results**
  - Fixed-size array or circular buffer storing the last 10 game results per profile. [file:1]

Asymptotic complexities (high level): board updates in \(O(1)\), win detection in \(O(n)\) per move, AVL tree operations in \(O(\log n)\), and hard AI search in \(O(b^d)\) before pruning, where \(b\) is branching factor and \(d\) is depth. [file:1]

---

## Command-Line Interface

The application exposes a rich text-based command interface for both gameplay and system management. [file:1]

### Core gameplay commands

- `move N` – Drop a piece into column `N` (0- or 1-based depending on implementation). [file:1]  
- `board` – Display the current board state as ASCII or Unicode art. [file:1]  
- `undo` – Undo the last move using the move history stack. [file:1]  
- `restart` – Reset the current game to a fresh board. [file:1]  
- `help` – Show all available commands and short usage hints. [file:1]  
- `quit` – Exit the application. [file:1]

### Player and profile commands

- `register` – Create a new player account (username, password, display name). [file:1]  
- `login` – Authenticate and start a session for an existing user. [file:1]  
- `logout` – End the current session and persist any changes. [file:1]  
- `whoami` – Display the currently logged-in user. [file:1]  
- `profile` – Show detailed statistics and recent results for the current player. [file:1]  
- `leaderboard` / `leaderboard top N` – Show top players by win rate and related metrics. [file:1]

### Tournament commands

- `tournament create` – Create a new tournament. [file:1]  
- `tournament join <username>` – Add a player to the current tournament. [file:1]  
- `tournament start` – Generate the full round-robin schedule. [file:1]  
- `next` – Run the next scheduled match (supports human vs AI and AI vs AI). [file:1]

The UI also supports helpful error messages and potentially command abbreviations to improve usability. [file:1]

---

## How to Build and Run

> Adjust this section to match your actual implementation language (Python or Java), then keep only the relevant subsection. [file:1]

### If implemented in Python

#### Prerequisites

- Python 3.8+ installed. [file:1]  
- (Optional) `pytest` or `unittest` for running tests. [file:1]

#### Steps

