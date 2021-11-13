# Causal-Inference

因果推論に関するexample リポジトリです。

## リポジトリ構成

```
.
├── Dockerfile
├── README.md
├── data
├── docker-compose.yml
├── docs
├── models
├── notebooks
├── pyproject.toml
├── requirements.txt
├── setup.cfg
├── src
│   └── __init__.py
├── tests
│   └── __init__.py
└── work
```

## 環境詳細

- Python : 3.9.6

## 事前準備

- Docker インストール

## 環境構築

- Dockderfileがあるホスト側のフォルダへ移動（例：Desktop/Causal-Inference）

```
cd Desktop/Causal-Inference
```

- Dockerによる環境構築（フォルダをマウント：Desktop/Causal-Inference）

```
docker-compose -f docker-compose-{*構築対象}.yml up --build
```

- ブラウザーを立ち上げてlocalhost:8888へアクセス
- ローカルフォルダがマウントされている

## Conditional Average Treatment Effects Estimationとは

- ある特徴量で条件付けた際の介入の因果効果の期待値を Conditional Average Treatment Effects Estimation (CATE)と呼びます。
- CATEを推定することができれば、例えば、因果効果がプラスであるような特徴量を持つ人だけに広告を打つことで商品の購入確率を最大化したり、投薬計画を最適化することで生存率を改善できる可能性あり。

## 因果推論ライブラリの概要

- EconML
    - Microsoft Research の研究グループが開発中の計量経済学と機械学習を融合した手法が収録されているパッケージ
    - Observational dataからConditional Average Treatment Effect (≒ ITE) を推定する手法が数多く実装されている
    - 安価に手に入るobservational data (過去の介入方策が観測されている特徴量に依存しているようなデータ)から CATEを推定するための手法が豊富に実装されており、低コストに個別化された介入施策を導くための非常に有用なツール

    - CATE推定方法
        - Meta-Learners
            - 既存の機械学習アルゴリズムを内部で用いるMeta的なCATEの推定方法を提供
            - 収録されているMeta-Learnersは5個
                - T-Learner
                - S-Learner
                - X-Learner
                - DA-Learner (Domain Adaptation Learner)
                - DR-Learner (Doubly Robust Learner)

- CausalML
    - Uber Technology のメンバーが開発したパッケージ
    - Uplift Modeling や先導的な機械学習アルゴリズムを用いた因果推論手法を提供

    - CausalML パッケージで提供されているもの
        - Uplift Modeling 手法
            - Uplift Tree
                - KL Divergence
                - Chi-Square
                - Euclidean Distance
                - Contextual Treatment Selection
            - Meta-learner
                - R-learner
                - X-learner
                - T-learner
                - S-learner

- DoWhy
    - 統計的因果推論を行うためのライブラリ

## 動作環境

マシンスペック（Mac)

- MacBook Air (Retina, 13-inch, 2018)
- 1.6 GHz デュアルコアIntel Core i5
- 8 GB 2133 MHz LPDDR3
