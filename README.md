# 🤖 UnicornChess - Reinforcement Learning Chess AI v3.0

My First Hybrid ChessEngine based on reinforcement learning & alpha-beta pruning & minimax — an AI that **grows in real-time** while playing against humans!

## 🌟 Key Features

### 🚀 v3.0 - AlphaZero Style

* **🧠 Dual Head Network**: Outputs both Value + Policy
* **📚 PGN Training**: Supervised Learning from Lichess games
* **🔄 Self-Play**: AI plays against itself to improve
* **🎯 Policy-based Search**: Minimax search filtered by top N moves (8x faster!)
* **🎮 Model Selection**: Choose the model you want at game start
* **🎮 Model Battle**: Compare performance of multiple models
* **💾 Flexible Model Management**: Choose where to save after a game

## 📂 Project Structure

```
UnicornChess/
├── src/                 # Core modules
│   ├── chess_model.py   # Neural network (Value + Policy)
│   ├── chess_ai.py      # AI logic (Minimax)
│   ├── rl_trainer.py    # Reinforcement learning
│   ├── game_manager.py  # Game records
│   └── trainer.py       # Training utilities
├── models/              # Trained models (.pth)
├── data/                # PGN data
├── games/               # Game records
├── docs/                # Documentation
├── main.py              # Main game
├── quick_demo.py        # Quick test
├── pretrain_model.py    # Pretraining
├── train_from_pgn.py    # PGN training
├── self_play.py         # Self-play training
└── model_battle.py      # Model battles
```

## 🚀 Quick Start

### 1. Install

```powershell
pip install torch python-chess numpy tqdm
```

### 2. Pretraining (Recommended, 3-5 min)

```powershell
python pretrain_model.py
```

### 3. PGN Training (Optional, 10-30 min)

```powershell
# 1. Put your PGN files in data/ folder
# 2. Start training
python train_from_pgn.py lichess_games.pgn 1000 10
                                          games evoch
```

### 4. Play the Game!

```powershell
python main.py
```

**At game start:**

```
Choose a model:
1. Self-Play model (learns by playing itself)
2. PGN-trained model (learned from Lichess games)
3. Auto select (priority-based)
4. Random weights (start from scratch)

Selection (1-4, Enter=Auto): 1
✅ Selected: models\self_play_model.pth

Choose learning mode:
1. Learning mode (AI learns automatically after game) ✅
2. Play mode (no learning) 🎮

Selection (1-2, default 1): 1
```

## 🎯 Model Files

| File                         | Description         | Purpose                          |
| ---------------------------- | ------------------- | -------------------------------- |
| `rl_chess_model.pth`         | Live training model | Learns while playing humans      |
| `self_play_model.pth`        | Self-play model     | Learns by playing against itself |
| `pgn_trained_model.pth`      | PGN-trained model   | Learned from Lichess games       |
| `pretrained_chess_model.pth` | Pretrained model    | Heuristic-based initial training |

## 💾 Model Management

### Save options after game

```
Where would you like to save the trained model?
1. Update original model: models\self_play_model.pth
   (accumulate existing training)
2. Save as new file: models\rl_chess_model.pth
   (dedicated for live training, original preserved)
3. Save with custom name
4. Do not save (experiment only)

Selection (1-4, Enter=1): 1
```

## 🎮 Model Battles

Compare multiple models’ performance:

```powershell
python model_battle.py

# Example: PGN-trained vs Self-Play
# Results: win/draw/loss stats, detailed game records
```

## 📊 Performance

* **Depth 3**: ~2-4 sec/move
* **Policy filtering**: ~1 sec/move (8x faster!)
* **Parameters**: 5.7M
* **Model size**: ~66 MB

## 🔧 Advanced Features

### Additional PGN Training

Add new PGN data to an existing model:

```powershell
python train_from_pgn.py new_games.pgn 5000 20

# Select existing model:
1. pgn_trained_model.pth (66 MB)
2. self_play_model.pth (66 MB)
3. Start fresh

Selection: 1  # Continue training existing model
```

### Self-Play Training

```powershell
python self_play.py

# Options:
1. Start from scratch (random)
2. Start from PGN-trained model (recommended) ⭐
3. Continue from existing model

Selection: 2
```

## 📚 Documentation

* `research.md` - Technical documentation and algorithm explanations
* `CHANGELOG.md` - Version history
* `PGN_Training_Guide.md` - Detailed PGN training instructions

## 🤝 Contributing

Issues and PRs are welcome!

## 📄 License

MIT License

