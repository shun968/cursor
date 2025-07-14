# MCP (Model Context Protocol) Servers 設定一覧

このプロジェクトで設定されているMCP (Model Context Protocol) Serversの詳細設定と概要です。

## 参考資料
- [Model Context Protocol Servers 公式リポジトリ](https://github.com/modelcontextprotocol/servers)
- [Model Context Protocol 公式サイト](https://modelcontextprotocol.io)

## 設定済みMCPサーバ一覧

| サーバ名 | ステータス | 概要 | 実行方式 | 関連URL | 設定要件 |
|---------|-----------|------|----------|---------|----------|
| **playwright** | ✅ 有効 | ブラウザ自動化・Webスクレイピング機能 | NPX | [playwright-mcp](https://github.com/modelcontextprotocol/servers/tree/main/src/playwright) | なし |
| **brave-search** | ✅ 有効 | Brave Search APIを使用したWeb検索 | Docker | [brave-search](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/brave-search) | BRAVE_API_KEY |
| **fetch** | ✅ 有効 | Web コンテンツの取得・変換機能 | Docker | [fetch](https://github.com/modelcontextprotocol/servers/tree/main/src/fetch) | なし |
| **sequentialthinking** | ✅ 有効 | 動的・反復的問題解決思考プロセス | Docker | [sequential-thinking](https://github.com/modelcontextprotocol/servers/tree/main/src/sequential-thinking) | なし |

### AWS関連MCPサーバ

| サーバ名 | ステータス | 概要 | AWS リージョン | 関連URL | 機能 |
|---------|-----------|------|---------------|---------|------|
| **awslabs.aws-documentation-mcp-server** | ✅ 有効 | 最新のAWSドキュメント・API参照 | ap-northeast-1 | [aws-documentation](https://github.com/aws-samples/mcp-servers/tree/main/aws-documentation) | ドキュメント検索・参照 |
| **awslabs.cloudwatch-mcp-server** | ✅ 有効 | CloudWatchメトリクス・ログ監視 | ap-northeast-1 | [cloudwatch](https://github.com/aws-samples/mcp-servers/tree/main/cloudwatch) | メトリクス取得・アラーム管理 |
| **awslabs.cost-explorer-mcp-server** | ✅ 有効 | AWS コスト分析・最適化 | ap-northeast-1 | [cost-explorer](https://github.com/aws-samples/mcp-servers/tree/main/cost-explorer) | コスト監視・分析 |
| **awslabs.iam-mcp-server** | ✅ 有効 | IAM ユーザー・ロール・ポリシー管理 | ap-northeast-1 | [iam](https://github.com/aws-samples/mcp-servers/tree/main/iam) | アクセス権限管理 |
| **awslabs.redshift-mcp-server** | ✅ 有効 | Amazon Redshift データウェアハウス操作 | ap-northeast-1 | [redshift](https://github.com/aws-samples/mcp-servers/tree/main/redshift) | データクエリ・分析 |
| **awslabs.ecs-mcp-server** | ✅ 有効 | Amazon ECS コンテナサービス管理 | ap-northeast-1 | [ecs](https://github.com/aws-samples/mcp-servers/tree/main/ecs) | コンテナオーケストレーション |
| **awslabs.cdk-mcp-server** | ✅ 有効 | AWS CDK インフラストラクチャコード支援 | - | [cdk](https://github.com/aws-samples/mcp-servers/tree/main/cdk) | CDK開発・デプロイ |

### GitHub関連MCPサーバ

| サーバ名 | ステータス | 概要 | 関連URL | 設定要件 |
|---------|-----------|------|---------|----------|
| **github** | 🔴 無効 | GitHub API統合・リポジトリ管理 | [github](https://github.com/modelcontextprotocol/servers-archived/tree/main/src/github) | GITHUB_PERSONAL_ACCESS_TOKEN |
| **awslabs.git-repo-research-mcp-server** | 🔴 無効 | GitHubリポジトリの高度分析・研究 | [git-repo-research](https://github.com/aws-samples/mcp-servers/tree/main/git-repo-research) | GITHUB_TOKEN |

## 共通設定

### AWS関連設定
- **AWS_PROFILE**: `default`
- **AWS_REGION**: `ap-northeast-1` (東京リージョン)
- **FASTMCP_LOG_LEVEL**: `ERROR` (本番環境向け)

### 無効化されているサーバの有効化方法

GitHub関連のサーバを有効化するには：

1. **GitHubパーソナルアクセストークンの作成**
   - GitHub → Settings → Developer settings → Personal access tokens → Generate new token
   - 必要なスコープ: `repo`, `read:user`

2. **トークンの設定**
   ```json
   "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_your_actual_token_here"
   "GITHUB_TOKEN": "ghp_your_actual_token_here"  
   ```

3. **サーバの有効化**
   ```json
   "disabled": false
   ```

## MCP設定ファイル

設定ファイルの場所: `~/.cursor/mcp.json`

詳細な設定については、各サーバの公式ドキュメントを参照してください。 