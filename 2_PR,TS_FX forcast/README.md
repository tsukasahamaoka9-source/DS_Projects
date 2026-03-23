# JPY/USD 為替レート予測プロジェクト

## プロジェクト概要
JPY/USDの為替レートを予測する時系列予測タスクです。過去の為替レート、経済指標、テクニカル指標などを活用して、将来の為替動向を予測します。

**プロジェクトタイプ**: 時系列予測（Time Series Forecasting）  
**ターゲット**: JPY/USD 為替レート  
**実装フェーズ**: 準備中

---

## ファイル構成

```
├── README.md           # このファイル
├── data/               # データセット格納フォルダ（準備中）
└── notebook/           # 実験用ノートブック（準備中）
```

---

## データセット

### 予定しているデータソース
- **為替データ**: Historical FX rates (JPY/USD daily/hourly)
- **経済指標**: 金利、GDP、失業率など
- **テクニカル指標**: 移動平均線、ボリンジャーバンドなど

*注: データセット準備中*

---

## 評価指標

### 主要評価メトリクス
- **Mean Absolute Error (MAE)**: 平均絶対誤差
- **Root Mean Squared Error (RMSE)**: 二乗平均平方根誤差
- **Mean Absolute Percentage Error (MAPE)**: 平均絶対パーセント誤差

---

## 使用予定の手法

### モデル候補
- [ ] ARIMA / SARIMA
- [ ] LSTM / GRU（ディープラーニング）
- [ ] Transformer（時系列用）
- [ ] LightGBM / XGBoost（特徴量ベース）
- [ ] Ensemble手法

### 前処理・特徴量エンジニアリング
- データの正規化・スケーリング
- ラグ特徴量の作成
- 差分（differencing）
- 季節性の分解

---

## セットアップ・実行方法

### 環境構築
```bash
# 必要なライブラリのインストール
pip install pandas numpy scikit-learn matplotlib seaborn
pip install statsmodels  # 時系列分析用
pip install tensorflow   # ディープラーニング用（オプション）
```

### ノートブック実行順序
1. `01_EDA.ipynb` - データ探索・分析
2. `02_Feature_Engineering.ipynb` - 特徴量作成
3. `03_Model_Training.ipynb` - モデル構築・学習
4. `04_Evaluation.ipynb` - 評価・結果分析

*各ノートブックはまだ準備中です*

---

## 進捗状況

- [ ] データセットの取得・準備
- [ ] EDA（探索的データ分析）実施
- [ ] 特徴量エンジニアリング
- [ ] ベースラインモデル構築
- [ ] ハイパーパラメータチューニング
- [ ] 最終評価・予測

---

## 参考リンク

- [statsmodels Time Series](https://www.statsmodels.org/stable/tsa.html)
- [Kaggle Time Series Competitions](https://www.kaggle.com/)

---

## メモ

- 実装開始日: 2026-03-23
- 予測対象: JPY/USD 日足データ
