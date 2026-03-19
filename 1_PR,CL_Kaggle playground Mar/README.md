# コンペ概要
顧客離脱予測のコンペです。顧客が離脱するかどうかを予測することが目的。

# データの概要
固定回線（家庭用インターネット）＋固定電話のデータセットと考えられる。
ケータイキャリアではない。

- train.csv: 学習用データセット
- test.csv: テスト用データセット
- sample_submission.csv: 提出用のサンプルファイル

train.csvには、顧客の特徴量と離脱フラグが含まれています。

# 各カラムの意味と実務的な解釈

id
   顧客ID。モデルには不要なので削除。

gender
   性別（Male / Female）。Churn との相関は弱い。

SeniorCitizen
   高齢者かどうか（0/1）。だいたい65歳以上が該当。

Partner
   配偶者がいるか（Yes/No）。

Dependents
   扶養家族がいるか（Yes/No）。

tenure
   契約月数（0〜72など）。短いほど離脱しやすい重要特徴。

PhoneService
   電話サービスを契約しているか（Yes/No）。

MultipleLines
   複数の電話回線を契約しているか（No / Yes / No phone service）。

InternetService
   インターネットの種類（DSL / Fiber optic / No）。
   Fiber optic は churn が高い傾向。

OnlineSecurity
   オンラインセキュリティサービス（Yes/No/No internet）。

OnlineBackup
   オンラインバックアップ（Yes/No/No internet）。

DeviceProtection
   デバイス保護サービス（Yes/No/No internet）。

TechSupport
   テクニカルサポート（Yes/No/No internet）。

StreamingTV
   ストリーミングTVサービス（Yes/No/No internet）。

StreamingMovies
   ストリーミング映画サービス（Yes/No/No internet）。

Contract
   契約期間（Month-to-month / One year / Two year）。
   Month-to-month は離脱率が高い。

PaperlessBilling
  紙の請求書かどうか（Yes/No）。

PaymentMethod
   支払い方法（Electronic check など）。
   Electronic check は churn が高い傾向。

MonthlyCharges
   月額料金。高いほど離脱しやすい傾向。

TotalCharges
   総支払額。tenure × MonthlyCharges に近い値。
   文字列で読み込まれることがあるので数値変換が必要。

Churn
   離脱したか（Yes/No）。目的変数。


# 評価指標

# 参考コード
