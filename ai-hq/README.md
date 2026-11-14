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
