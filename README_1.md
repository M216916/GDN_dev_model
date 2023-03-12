# モデル
### GDN_10 optuna実装
    

# 環境
* README_2.md に記載


# データ
* yfinance_01_10

        時系列属性：2730社 * 日次データ（2614日）

        非時系列属性：40カラム（財務指標14+属性26／標準化あり）

        10社分のデータ（主に動作を確認するために使用）

* yfinance_01_100

        100社分のデータ（実験用のデータ）

* yfinance_01_all

        すべて（2730社分）のデータ（本当はこれで実験したかった）


# 調整事項

* main.py

        データの分割を指定

        時系列属性の平均化（圧縮）の調整

        Pre-training／Fine-tuningどちらのハイパーパラメータの調整をするか指定


* run.sh

        loss_functionの選択（CE_loss / Dice_loss）

        エポック数の調整（pre_EPOCH / fin_EPOCH）


# 実行方法

* 仮想環境を作成（mainの環境を汚さないように）

* GitHub から gitclone

        （例）git clone -b GDN_10 https://github.com/M216916/GDN.git GDN_10

* GDN_10 のディレクトリに入る

* cpu で実行

        （例）@prmir11:~/GDN_10$ bash run.sh cpu yfinance_01_100

        （GPUでも実行できるらしいが、環境設定が分からず断念）

* 実行内容

        所定のエポック数（Pre-trainingおよびFine-tuning）の学習が繰り返される

        上記学習が所定のtrial数だけ繰り返される

        最も良いLossを計測したハイパーパラメータが表示される