# AI制作本部｜5事業の現在地
> **第2段階完了（引き継ぎカード）**：[5事業の再開手順・成果物・未完了事項](handoffs/README.md)。2026-11-14のGitHub確認結果と過去チャットの報告を区別した記録です。
> チャット整理（メイン・参照用・アーカイブ候補）の詳細： [CHAT_MAP.md](CHAT_MAP.md)。実際のChatGPTチャットの改名・移動・アーカイブは未実施。

更新日：2026-11-14（GitHubと過去のチャット情報を照合）

> このページは **確認済みの事実・過去チャットの報告・未確認事項を区別** した引き継ぎ台帳です。
> OpenなIssueは必ずしも「作業実行中」を意味しません。GitHubの状態だけでLINE申請や動画完成を断定しません。

## 全体の使い方
- **このChatGPTチャット＝統括窓口**。「全体進捗を確認して」「次はどれを進める？」と依頼する。
- **事業ごとの専用チャット＝制作現場**。そこで詳細に制作し、最後に成果物と残作業を報告する。
- **このファイル＝引き継ぎ台帳**。実際の成果物やGitHub Issue/PRへリンクする。
- **GitHub Actions＝実行記録**。実行成功と納品品質合格を分ける。
- チャットを移動/統合する操作は未実施。過去チャットを削除せず、代表チャットを決めて古いものは参照用とする。

| 領域 | 確認できた進捗 | 次にやること | 主な作業場所 |
|---|---|---|---|
| 1. YouTube動画制作 | JSONアップロードから動画生成へつながる既存ワークフローあり（PR #2はマージ）。台本＋サムネの制作チャットあり。直近動画の完成数と公開状態は未照合 | 作成中の台本・動画・投稿結果をひもづけ、最新成果物を確認 | YouTube制作プロジェクトの「台本制作室」／動画生成Actions |
| 2. YouTube新フロー・スキーマ | 数字強調の試作PR #3がオープン、未本番反映 | 実映像・ナレーション同期・文字の重なりを検証して採否決定 | 動画システム開発チャット／PR #3 |
| 3. LINEスタンプ | 40個作品のZIP品質改善・申請管理が進行。別系列の24個×29セットの引き継ぎIssueも存在。両者は別案件 | 作品単位で生成済み/ZIP QA/下書き/審査/販売を照合。未検査のZIPを審査に送らない | LINEスタンプ「制作」「ZIP品質」「申請」それぞれの代表チャット／管理リポジトリ |
| 4. LINE絵文字 | 40個＋タブ画像の制作と複数作品の登録依頼あり。過去チャットに複数の作品IDが記録。ただし最新のCreators Market状態は未確認 | 各作品のZIP実体・登録ID・下書き/審査状態を照合 | LINE絵文字「制作」「申請」の代表チャット |
| 5. みんなの本棚 | HTML試作あり。検索機能PR #2とサンプルJSON書き出しPR #4がオープン。本番mainへの反映は未確認ではなく、両PR未マージ | PRの競合・動作を確認し、本の追加/保存などMVP機能へ | みんなの本棚開発チャット／GitHub PR |

## 具体的な証拠
### 1. YouTube動画制作
- 本番リポジトリ: https://github.com/growth1invest-bot/1- （非公開。公開Issueに詳細を複製しない）
- 自動動画起動PR #2（マージ済み）: https://github.com/growth1invest-bot/1-/pull/2
- 本部の進捗確認Issue: https://github.com/growth1invest-bot/line-stamp-manager/issues/1
- 直近の台本JSON・公開済み動画の本数・アップロード状況は、この台帳作成時点で網羅検証していない。

### 2. 動画フロー・スキーマ
- 試作PR #3（オープン）: https://github.com/growth1invest-bot/1-/pull/3
- 開発作業台帳: https://github.com/growth1invest-bot/line-stamp-manager/issues/2
- 状況確認のみのIssue（実装作業と混同しない）: https://github.com/growth1invest-bot/line-stamp-manager/issues/8

### 3. LINEスタンプ
- 40個ZIPメーカーのQA: https://github.com/growth1invest-bot/line-stamp-manager/issues/3
- **別案件** 24個×29セットの引き継ぎ: https://github.com/growth1invest-bot/line-stamp-manager/issues/9
- 構造点検のテスト（実制作ではない）: https://github.com/growth1invest-bot/line-stamp-manager/issues/7
- Creators Marketでの最新申請ステータスはログインして照合する必要がある。過去チャットの成功報告と現在状態を同一視しない。

### 4. LINE絵文字
- ZIP/申請工程の台帳: https://github.com/growth1invest-bot/line-stamp-manager/issues/4
- 画像実ファイルとCreators Market最新ステータス未照合。

### 5. iOSアプリ「みんなの本棚」
- 開発リポジトリ: https://github.com/growth1invest-bot/minna-no-hondana
- 検索機能PR #2（オープン、ドラフト）: https://github.com/growth1invest-bot/minna-no-hondana/pull/2
- JSON書き出しPR #4（オープン）: https://github.com/growth1invest-bot/minna-no-hondana/pull/4
- 開発の総合確認Issue: https://github.com/growth1invest-bot/line-stamp-manager/issues/5

## チャットの整理ルール（推奨）
| 専用チャットの役割 | 代表的な名前 |
|---|---|
| 統括・優先順位・進捗報告 | 【本部】5事業進捗管理 |
| YouTube台本・サムネ | 【YT制作】台本制作室 |
| YouTube Actions・Remotion・スキーマ | 【YT開発】動画フロー改善 |
| LINEスタンプの企画・画像生成 | 【スタンプ制作】生成室 |
| LINEスタンプのZIP・品質確認 | 【スタンプQA】ZIPメーカー |
| LINEスタンプのCreators Market登録 | 【スタンプ申請】登録室 |
| LINE絵文字の制作・ZIP | 【絵文字制作】生成・ZIP |
| LINE絵文字の登録・申請 | 【絵文字申請】登録室 |
| みんなの本棚の仕様・実装 | 【本棚開発】アプリ実装 |

上の名前は今後使う整理案であり、**既存ChatGPTチャットの自動移動・改名を実行したわけではない**。
過去チャットは削除しない。各領域の代表チャットを継続し、重複チャットは作業結果を引き継いでからアーカイブ候補にする。

## AI担当者の報告ルール
作業が終わったら常に以下を出す。
1. 何を実施したか（未実施は明記）
2. 完了/進行中/確認待ち/エラーのどれか
3. 成果物、Issue、PR、ZIP、動画などを開けるリンク
4. 次に着手すべき内容と担当チャット
5. 重要な日付と最新確認時点

## 記録上の問題と対策
- 作業Issue・状況確認Issue・接続テストIssueを単純に数えると、実作業の進捗が誤って見える。
- PRの作成は「コードが提案された」段階。マージや動作確認、公開の完了ではない。
- チャットで生成したZIP・画像・台本は、GitHubに登録されていない場合、この台帳からは実体を取得できない。
- 作業完了時に管理台帳への記録を行う運用は今後徹底する。ただし別チャットでの成果が自動同期される機能は未実装。
