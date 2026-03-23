# コンペ概要
顧客離脱予測のコンペです。顧客が離脱するかどうかを予測することが目的。

# データの概要
固定回線（家庭用インターネット）＋固定電話のデータセットと考えられる。
ケータイキャリアではない。

- train.csv: 学習用データセット
- test.csv: テスト用データセット
- sample_submission.csv: 提出用のサンプルファイル

欠損値：なし（TotalCharges は数値変換の際に欠損値が発生する可能性あり？）

# 各カラムの意味と実務的な解釈

id
   顧客ID。モデルには不要なので削除。
gender
   性別['Male', 'Female']。男女はほぼ半々で、Churn との相関や傾向は見られない。
SeniorCitizen
   高齢者かどうか[0, 1]。一般的に65歳以上が該当。11.4%が高齢者で離脱率は50%ほどで高い傾向
Partner
   配偶者がいるか['Yes', 'No']。
   Partner がいる顧客は離脱率が低い傾向。
Dependents
   扶養家族がいるか['Yes', 'No']。
   Partner同様。Dependents がいる顧客は離脱率が低い傾向。差は大きめ。
tenure
   契約月数（0〜72）。
   短いほど離脱しやすい重要特徴。長いほどChurn しにくい傾向。
PhoneService
   電話サービスを契約しているか['Yes', 'No']。
   Noの割合が少なく、決定要因では無さそうだが、No の顧客は離脱率が低い傾向。電話サービスが解約の原因になることもあるのか？
MultipleLines
   複数の電話回線を契約しているか['No', 'Yes', 'No phone service']。
   Yesのほうが離脱率が高い傾向。電話サービス、特に複数回線の契約は、顧客がサービスに不満を持っている可能性があるのかも。
InternetService
   インターネットの種類['DSL', 'Fiber optic', 'No']。
   InternetService が 'No' の顧客は離脱率が低い傾向。DSL より Fiber opticは離脱率が高い傾向。
   Fiber optic は churn が高い傾向。
OnlineSecurity
   オンラインセキュリティサービス['No', 'Yes', 'No internet service']。
   No の顧客は離脱率が高い傾向。オンラインセキュリティサービスを利用していない顧客は、セキュリティに不満を持って解約した可能性があるのかも。
OnlineBackup
   オンラインバックアップ['No', 'Yes', 'No internet service']。
   同じくNo の顧客は離脱率が高い傾向。
DeviceProtection
   デバイス保護サービス['No', 'Yes', 'No internet service']。
   同じくNo の顧客は離脱率が高い傾向。
TechSupport
   テクニカルサポート['No', 'Yes', 'No internet service']。
   同じくNo の顧客は離脱率が高い傾向。
StreamingTV
   ストリーミングTVサービス['No', 'Yes', 'No internet service']。
   若干、Yesのほうが離脱率が低い？とはいえ	No internet service の顧客の方が圧倒的に離脱率が低い傾向。
StreamingMovies
   ストリーミング映画サービス['No', 'Yes', 'No internet service']。
   同じく若干、Yesのほうが離脱率が低い？とはいえ	No internet service の顧客の方が圧倒的に離脱率が低い傾向。
Contract
   契約期間['One year', 'Two year', 'Month-to-month']。
   Month-to-month は離脱率が非常に高い。One year は低め、Two year はかなり低い。最重要クラスの特徴量。
PaperlessBilling
  紙の請求書かどうか['Yes', 'No']。
   PaperlessBilling が 'Yes' の顧客は離脱率が高い傾向。紙の請求書を選択している顧客の内訳は？
PaymentMethod
   支払い方法['Mailed check', 'Credit card (automatic)', 'Electronic check', 'Bank transfer (automatic)']。
   Electronic check は churn が超絶高い傾向。電子的な支払い方法を選択している顧客は、支払い関連に不満を持って解約した可能性があるのかも？Technical support も関連あり？
   でも、Credit card (automatic) や Bank transfer (automatic) は離脱率が低い傾向。自動支払いの方が、支払い関連の不満は少ないのかも。
MonthlyCharges
   月額料金。
   高い層で Churn が増える傾向。
   周期性があるようにも見える。
TotalCharges
   総支払額。tenure × MonthlyCharges に近い値。
   TotalCharges は低〜中で Churn が目立ち、高額帯は Non-Churn が多めです（tenure の影響も強い）？
Churn
   離脱したか['Yes', 'No']。目的変数。data_train では 22.5% が 'Yes'。

# 評価指標
   ROC-AUC (Area Under the ROC Curve)
   ROC曲線とは、真陽性率（TPR）（実際に離脱した顧客）と偽陽性率（FPR）（実際には離脱していないが離脱と予測した顧客）の条件確率をプロットしたもの。AUCはこの曲線の下の面積で、1に近いほど良いモデル。閾値を変えてもモデルの性能が安定していることを示す。
   うまたんさんの動画でわかりやすく解説されている。
   https://www.youtube.com/watch?v=vRV7fJ6JYQY

# 参考コード