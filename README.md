# GitHub Copilot × 簡略化 SDD ワークショップ

GitHub Copilot の基本操作から、簡略化した SDD（Spec Driven Development）ライフサイクルを使ったハンズオンまでを体験するワークショップの教材一式です。

## フォルダ構成

| パス | 役割 |
|---|---|
| [docs/workshop-timetable.md](docs/workshop-timetable.md) | 当日の時間割・アジェンダ |
| [docs/workshop-instructor-guide-marp.md](docs/workshop-instructor-guide-marp.md) | 講師投影用スライド（Marp形式）。画面に映すマーキー情報のみを抜粋 |
| [docs/participant-guide.md](docs/participant-guide.md) | 参加者が手元で参照する詳細手順ガイド |
| [docs/themes/microsoft-theme.css](docs/themes/microsoft-theme.css) | 講師投影用スライドの Marp テーマ |
| `.github/agents/` | ハンズオンで使う 4 つのカスタムエージェント（`sdd-requirements` / `sdd-design` / `sdd-wireframe` / `sdd-pipeline`） |
| `.github/workflows/azure-static-web-apps.yml` | `app/` の変更を Azure Static Web Apps へデプロイする GitHub Actions ワークフロー |
| `.github/copilot-instructions.md` | 本リポジトリ用の最小限の Copilot instruction |
| [samples/meeting-notes-sample.md](samples/meeting-notes-sample.md) | ハンズオン用のサンプル議事録（すぐ試せる題材） |
| `work/` | 要件一覧・設計書など、ハンズオン中に参加者が生成する中間成果物の置き場（Git 管理対象外） |
| `app/` | Azure Static Web Apps へデプロイする静的アプリの置き場（Git 管理対象。初期状態はデプロイ設定のみで、`sdd-wireframe` が `index.html` を生成する） |

## 当日の進め方（概要）

1. [docs/participant-guide.md](docs/participant-guide.md) の「事前準備チェックリスト」を確認する。
2. 講師の説明に沿って GitHub Copilot の基本操作・コンテキストの与え方・Instruction / Skill / Agent の仕組みを学ぶ。
3. 簡略化した SDD ライフサイクル（ヒアリング → 要件定義書 → 設計書 → ワイヤーフレーム → デプロイ）を、`sdd-requirements` → `sdd-design` → `sdd-wireframe` → `sdd-pipeline` の 4 エージェントで体験する。
4. 要件一覧・設計書は `work/` 配下、デプロイするワイヤーフレームは `app/` 配下に保存する（`samples/` は変更しない）。

詳細な時間割は [docs/workshop-timetable.md](docs/workshop-timetable.md) を参照してください。
