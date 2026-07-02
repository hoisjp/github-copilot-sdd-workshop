# Copilot Instructions: github-copilot-sdd-workshop

## このリポジトリについて

GitHub Copilot の基本操作と、簡略化した SDD（Spec Driven Development）ライフサイクルを体験するワークショップ用のハンズオン教材リポジトリです。

## 出力言語

- 回答・生成するドキュメントはすべて日本語で出力する。ユーザーから英語を明示的に指定された場合のみ英語を使用する。
- コード（HTML/CSS 等）内のコメント・文字列は英語で記述してよい。

## エージェントの使い分け

以下の依頼が来たら、対応するカスタムエージェントを使う。

| 依頼内容 | 使うエージェント |
|---|---|
| 雑な要望・議事録から要件一覧を作りたい | `sdd-requirements` |
| 要件一覧から設計書（仕様書）を作りたい | `sdd-design` |
| 設計書から画面のワイヤーフレームを作りたい | `sdd-wireframe` |

## 成果物の保存先

- ハンズオンで生成した成果物（`requirements.md` / `design.md` / ワイヤーフレーム HTML など）は `work/` 配下に保存する。
- `samples/` 配下のファイルは参照専用。上書き・変更しない。

## 参照ドキュメント

- 当日の時間割: [docs/workshop-timetable.md](../docs/workshop-timetable.md)
- 参加者向け詳細手順: [docs/participant-guide.md](../docs/participant-guide.md)
