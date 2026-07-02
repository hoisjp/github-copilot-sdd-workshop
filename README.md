# GitHub Copilot × 簡略化 SDD ワークショップ

GitHub Copilot の基本操作から、簡略化した SDD（Spec Driven Development）ライフサイクルを使ったハンズオンまでを体験するワークショップの教材一式です。

## フォルダ構成

| パス | 役割 |
|---|---|
| [docs/workshop-timetable.md](docs/workshop-timetable.md) | 当日の時間割・アジェンダ |
| [docs/workshop-instructor-guide-marp.md](docs/workshop-instructor-guide-marp.md) | 講師投影用スライド（Marp形式）。画面に映すマーキー情報のみを抜粋 |
| [docs/participant-guide.md](docs/participant-guide.md) | 参加者が手元で参照する詳細手順ガイド |
| [docs/themes/microsoft-theme.css](docs/themes/microsoft-theme.css) | 講師投影用スライドの Marp テーマ |
| `.github/agents/` | ハンズオンで使う 3 つのカスタムエージェント（`sdd-requirements` / `sdd-design` / `sdd-wireframe`） |
| `.github/copilot-instructions.md` | 本リポジトリ用の最小限の Copilot instruction |
| [samples/meeting-notes-sample.md](samples/meeting-notes-sample.md) | ハンズオン用のサンプル議事録（すぐ試せる題材） |
| `work/` | ハンズオン中に参加者が生成する成果物の置き場（Git 管理対象外） |

## 当日の進め方（概要）

1. [docs/participant-guide.md](docs/participant-guide.md) の「事前準備チェックリスト」を確認する。
2. 講師の説明に沿って GitHub Copilot の基本操作・コンテキストの与え方・Instruction / Skill / Agent の仕組みを学ぶ。
3. 簡略化した SDD ライフサイクル（ヒアリング → 要件定義書 → 設計書 → ワイヤーフレーム）を、`sdd-requirements` → `sdd-design` → `sdd-wireframe` の 3 エージェントで体験する。
4. 生成した成果物は `work/` 配下に保存する（`samples/` は変更しない）。

詳細な時間割は [docs/workshop-timetable.md](docs/workshop-timetable.md) を参照してください。
