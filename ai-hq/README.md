# AI制作本部 v0.1

## 実際に使う入口
- `ai-hq/index.html`：スマホ用司令塔。GitHub Issuesの公開情報を表示し、新規指示のIssue作成フォームを開く
- `Issues`：5事業共通の正式な仕事台帳
- ChatGPT：指示を解釈し、必要なGitHubファイル・Issue・PRを操作する統括窓口
- Codex：ソフトウェア開発支援。自動割り当ては未接続
- GitHub Actions：既存の動画処理や検証。HQからの自動ディスパッチは未接続

## 組織図
社長（ユーザー）→ 統括マネージャー（ChatGPT）→ 各部署
1. 動画制作：台本、レンダリング、サムネ、公開準備
2. 動画フロー開発：GitHub Actions、Remotion、JSONスキーマ、検証
3. LINEスタンプ：素材、分割、透過、QA、申請準備
4. LINE絵文字：素材、分割、QA、申請準備
5. iOSアプリ：みんなの本棚、UI、ローカルデータ、テスト
横断：QA担当、進捗管理、セキュリティ・公開承認

## 現在のプロジェクト
- YouTube: https://github.com/growth1invest-bot/1- （private）
- LINE管理: https://github.com/growth1invest-bot/line-stamp-manager （public）
- iOSアプリ: https://github.com/growth1invest-bot/minna-no-hondana （public）

## Issue運用ルール
タイトル `[部署] 仕事`。本文に目的、実施内容、成果物、検証、次のアクションを記載。
状態はOPEN=未完了、CLOSED=完了。ラベル `blocked`=障害、`needs-approval`=承認待ち。
上記ラベルの自動付与は未実装。公開Issueには認証情報・非公開リポジトリのコード・個人情報を書かない。

## セキュリティ/品質
- 既存のGitHub Actionsや制作ファイルを無断変更しない
- YouTube投稿・LINE審査申請・課金・本番反映は承認が必要
- 試作の成功と本番投入の成功を区別
- iPhoneのブラウザにGitHubアクセストークンを保存しない
- 自動化できない処理を「完了」と呼ばない

## 将来の統合ステップ
1. HQのGitHub Pages公開（リポジトリの設定が必要）
2. GitHub ActionsによるIssue分類と定期レポート
3. 内部認証つきAPIでGitHub Actions実行とCodex開発依頼を接続
4. LINE Creators Marketの登録フローとの連携、不可操作の切り分け
5. 非公開リポジトリの状況を公開範囲に配慮したサマリー形式で集約

## 管理チャット向け定型指示
「あなたはAI制作本部の統括マネージャーです。5部署のGitHub Issueと関連PRを確認し、作業可能なものは検証まで実行して、Issueに状況・結果・次の一手を残してください。外部公開・申請・課金・本番変更は安全確認を優先してください。根拠のない完了報告はしないでください。」


## v0.2 自動点検ワーカー（2026-11-14）
- `.github/workflows/ai-hq-worker.yml` はIssue作成時にオーナーの指示だけを検査する
- LINEスタンプ：公開管理HTMLの主要要素を静的点検
- iOSアプリ：公開本棚HTMLの主要要素を静的点検
- LINE絵文字：実データ未提供のため品質検査未実施を明記
- 動画系：非公開リポジトリの実行権限がなく、実作業を行わない
- 統括：公開Issueの概況を集計
- 結果をIssueコメントとGitHub Actions Summaryに出力
- 既存Issueにオーナーが `/run-check` とコメントすると再点検
- 手動実行 `workflow_dispatch` から部署を指定可能
- 外部公開、LINE申請、YouTube自動投稿、AIコード修正は未接続

**注意:** GitHubの新規Issueフォームから「Submit new issue」を押して初めて処理が開始されます。この仕組みはChatGPTやCodexを無人で継続稼働させるものではありません。

## v0.3 実行ワーカー（2026-11-14）
- iOS担当の指示は司令塔から `growth1invest-bot/minna-no-hondana` のIssueへ登録する
- `minna-no-hondana/.github/workflows/ai-hq-implement.yml` がIssueを検出して実コードを変更
- 対応済み: 「検索機能を追加」「サンプルJSONを書き出す」。未対応指示では明示的に未実施を報告
- コードは `hq/issue-N-RUN` ブランチへ保存、HTML構造テストを実行、Issueに結果コメント
- 自動PRの作成はリポジトリのActions設定で禁止されていることを確認。GitHub Settings > Actions > General > Workflow permissions > Allow GitHub Actions to create and approve pull requests が必要
- 検証Issue: https://github.com/growth1invest-bot/minna-no-hondana/issues/1
- レビュー用PR: https://github.com/growth1invest-bot/minna-no-hondana/pull/2 （このPRはChatGPT GitHub接続を使って作成）
- 自由文AI推論や任意コード修正、その他部署の実作業は未実装。追加API費用なしにAIが無制限で動くものではない

## v0.4 iPhoneから直接送信（2026-11-14）
- GitHub Pagesの司令塔にfine-grained personal access token（Issues: Read and write）を入力してGitHubへ認証できる
- `/user` でログイン本人 `growth1invest-bot` を確認
- トークンはJSの一時変数だけで保持。localStorage/sessionStorage、URL、HTML、GitHub Issueに保存しない。再読み込みで破棄
- フォームからGitHub REST APIにPOSTして、GitHub新規Issue画面とSubmit操作を省略
- アプリ担当は `minna-no-hondana`、動画担当は非公開の `1-`、LINEと統括は `line-stamp-manager` に送る
- 公開リポジトリのIssue作成時には公開される旨を警告し、確認を要求する
- 台帳は接続時に3リポジトリを読み込み、結果表示ボタンでActionsボットのコメントを表示する
- 失敗時には401/403/404等を表示し、成功を偽装しない
- GitHub REST APIのトークン権限は対象3リポジトリに対するIssues: Read and writeを推奨（Metadata: Readは必須）。Contentsの書込み権限は不要。
- ブラウザに貼ったトークンを保存しないため、ページ再読み込み時は再入力が必要

### 重要な制限
1. **自由文AIは未接続**。自動でコード変更するのは本棚の検索・JSON書き出しという定型タスクのみ。
2. 動画担当は非公開Issue登録まで。YouTube公開や動画生成は自動起動しない。
3. LINE担当は公開Issue登録後の静的点検のみ。スタンプ・絵文字の制作や審査申請は行わない。
4. GitHub Copilot cloud agentで自由文開発を自動実行する場合はGitHub Copilotの有料プランとエージェント権限が別途必要であり、ChatGPT Plusだけでは利用できない。
5. 公開サイトのため、トークンを扱う際はURLが公式のGitHub Pagesドメインであることを確認し、必要最小限の権限を使用する。セキュリティ上の理由でトークンをチャットに貼らない。
