# hacking
改造の方法について

# ディレクトリ構成

## ドキュメント
### README.md
このゲームについて
### documents/image1.png
動作時の画面
### documents/hacking.md
ソースのコメント、改造について
### documents/neuralnet_ai.md
4層ニューラルネットワークによるAIモードの例についての説明

## コア
### constants.py
ゲームで利用される定数の一部
### core_object.py
- 画面ピクセルとメートルによる、２つの単位がある
- spliteは表示されうる実物の定義
### physics.py
物理のライブラリ
## util.py
- ユーティリティー関数__
- listのlistを再帰的にを一次元まで展開する

### game_object.py
- ParamArea はゲームの状態を文字として表示するためのユーティリティー
- SystemEvent はゲームを終了させるか否かの判定をしている



## オブジェクト・ゲーム
### maps.py
- ここでステージを定義できる
- 文字列からブロックの配置についてを読み込む
- 文字とブロックとの対応
| 文字 | ブロック |
| `.` | 空間 |
| `#` | 壁 |
| `P` | エージェント |
| `W` | ワープホール |


### character.py
- 各種のオブジェクトの定義を行っている
- Playerが最も多くの相互関係を受けるために、Playerの定義がやたら長くなっている
- オブジェクトとオブジェクトの相互関係を記述する言語があれば、ソースを簡略化できる

### game.py
- create_mapでは、maps.pyのフィールドの情報と、game_dictから、実際の環境を構築している
- Game の *__init系の関数は、各種の初期化を行っている
- Game のgame_loopでは、内部の情報の更新・描写・待機を繰り返している

## AI
### ai_lib.py
- around_terrainは周囲の地形をn次元のベクトルとして、7*7や5*5などで与えている
  - n:オブジェクトの種類
- AIPlayer はAIによるエージェントの定義をしている
- AIParam はAIの情報を表示するためのクラス
  
### neuralnet_ai.py
4層ニューラルネットワークによるAIモードの例。chainerに依存
- AIはモデルの定義をしている
- frame_per_predictは、畳み込み・学習は、何フレームごとに行われるか?を示す
- 実際のモデルはAIクラスだけなので

### neuralnet.model
neuralnet_ai.pyの実行時に、生成された学習モデル



