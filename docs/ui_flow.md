# 🧭 UIフロー構成 – SupportFlow利用者向け

SupportFlowは「診断 → 制度提示 → 書類準備 → 予約」までをオンラインで完結できるよう設計されています。

---

## 👤 利用者向け画面フロー

| ステップ | 画面名              | 主な要素                                                                    | 補足                                     |
|----------|---------------------|-----------------------------------------------------------------------------|------------------------------------------|
| ①        | トップ画面          | - サービス概要紹介<br>- 「診断を始める」ボタン                             | 初回訪問者向けの動線                      |
| ②        | 対象者選択画面      | - 「個人」または「法人・事業者」を選択                                     | 質問セット分岐に使用                      |
| ③a       | マイナンバー連携画面 | - 連携同意の確認画面<br>- 説明表示（利用目的／利用範囲）<br>- NFC or ICカード接続開始 | 自動入力・質問省略のための同意確認       |
| ③b       | 質問フロー画面      | - 質問文と選択肢（動的分岐）<br>- [次へ] ボタン                             | 前提情報により質問数を省略可能            |
| ④        | 制度候補提示画面    | - 該当制度の一覧（名称・概要・所管部局）<br>- [詳細を見る] ボタン           | 各制度は「候補」段階（確認後に確定）      |
| ⑤        | 必要書類案内画面    | - 制度ごとの必要書類<br>- チェックリスト形式                               | 印刷・保存対応あり                        |
| ⑥        | 来庁予約画面        | - 日時選択、整理番号発行、QRコード生成                                     | 市民ポータルやLINE連携も想定              |
| ⑦        | 最終確認画面        | - 入力情報確認<br>- 注意事項<br>- [確定して送信] ボタン                    | 修正戻り可能                              |

---

## 🧾 職員向け 引き継ぎ情報一覧

来庁時に自治体職員が活用する情報セットです。

| 引き継ぎ項目     | 利用例                                                           |
|------------------|------------------------------------------------------------------|
| 整理番号         | 来庁順・職員配置の調整                                          |
| 該当制度候補     | 担当課・支援担当者の事前割当                                     |
| 回答概要         | 状況把握・必要説明の簡略化（匿名／本人特定モード切替可能）        |
| 必要書類一覧     | 不備チェック・申請前確認に使用                                    |
| 予約日時         | 時間帯別の応対準備・混雑管理                                     |

---

## 📝 備考

- スマホ／PC／窓口端末共通のUI設計を前提としています
- 法人版の画面は個人版と大枠共通ですが、表示ラベルや設問が異なる仕様です
