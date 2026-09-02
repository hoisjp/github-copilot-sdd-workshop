# GitHub Copilot × 簡略化 SDD ワークショップ 時間割

GitHub Copilot の基本操作から、簡略化した SDD（Spec Driven Development）ライフサイクルを使ったハンズオンまでを体験する、合計 3 時間（休憩 10 分 × 2 回）のワークショップ時間割です。

## 1. ワークショップの狙い

- GitHub Copilot の画面操作・コンテキストの与え方・Instruction / Skill / Agent の仕組みを体験する。
- お客様の雑な要望から、いきなり実装に入るのではなく、段階的にアウトプットを育てる進め方（簡略化 SDD ライフサイクル）を体験する。
  - ライフサイクル: `ヒアリング（議事録） → 要件定義書 → 設計書 → ワイヤーフレーム`
  - 各ステップを専用のカスタムエージェント（`sdd-requirements` / `sdd-design` / `sdd-wireframe` / `sdd-pipeline`）に分担させる。
- 総時間: 180 分 = コンテンツ 160 分 + 休憩 20 分（10 分 × 2）。

## 2. 全体アジェンダ（サマリー）

| # | 時間 | 累計 | セクション |
|---|------|------|-----------|
| 0 | 10 min | 0:10 | 事前準備・環境確認 |
| 1 | 15 min | 0:25 | GitHub Copilot 画面操作基礎 |
| 2 | 10 min | 0:35 | コンテキストの与え方 |
| 3 | 15 min | 0:50 | Instruction の仕組み |
| — | 10 min | 1:00 | **休憩①** |
| 4 | 20 min | 1:20 | Skill / Agent の仕組み |
| 5 | 15 min | 1:35 | 簡略化 SDD ライフサイクルの考え方 |
| 6 | 20 min | 1:55 | ハンズオン①: 要件一覧を作る（`sdd-requirements`） |
| — | 10 min | 2:05 | **休憩②** |
| 7 | 20 min | 2:25 | ハンズオン②: 設計書を作る（`sdd-design`） |
| 8 | 15 min | 2:40 | ハンズオン③: ワイヤーフレームを作る（`sdd-wireframe`） |
| 9 | 10 min | 2:50 | 応用トピック駆け足（MCP / Coding Agent / 品質管理） |
| 10 | 10 min | 3:00 | まとめ・Q&A |

> コンテンツ合計 160 分 + 休憩 20 分 = 180 分（3h）。

## 3. 詳細タイムテーブル

### 0. 事前準備・環境確認（10 min）

- GitHub アカウント / Copilot ライセンス / VS Code / Copilot 拡張機能の動作確認。
- 詳細は [参加者ガイド](participant-guide.md) の「事前準備チェックリスト」を参照。

### 1. GitHub Copilot 画面操作基礎（15 min）

- チャットウィンドウ（サイドバー / エディタ内 / インライン）とセッション管理。
- モデル選択（Claude Sonnet / Opus、GPT-5 系、Gemini など）の使い分け。
- 3 つのモード（Agent / Ask / Plan）のデモ。

### 2. コンテキストの与え方（10 min）

- `#file` / `#folder` / `@workspace` / 画像添付 / URL 貼り付けの実演。
- 「何を見せるかで回答品質が決まる」という原則を強調。

### 3. Instruction の仕組み（15 min）

- `.github/copilot-instructions.md`（旧方式）と `.github/instructions/*.instructions.md`（新方式、`applyTo` 指定）の違い。
- 本ワークショップの `.github/copilot-instructions.md` を実例として確認。

### 休憩①（10 min）

### 4. Skill / Agent の仕組み（20 min）

- Skill（`SKILL.md`、`description` による自動マッチ）の仕組みと構成例。
- Agent（`.agent.md`、`@agent名` で明示呼び出し、`tools:` 制限）の仕組みと Skill との違い。
- この後のハンズオンで使う `sdd-` プレフィックス付きエージェント（`sdd-requirements` / `sdd-design` / `sdd-wireframe` / `sdd-pipeline`）の役割を紹介。

### 5. 簡略化 SDD ライフサイクルの考え方（15 min）

- お客様の雑な一言（例:「SNS の反応を分析したい」）から出発する典型的な落とし穴を共有。
- 以下の簡略ライフサイクルで進める理由を説明:

  ```
  ヒアリング（議事録） → 要件定義書 → 設計書 → ワイヤーフレーム
  ```

- 各フェーズを専属エージェントに担当させることで、フェーズ間の役割・出力形式を固定し、認識のズレを防ぐ狙いを説明。

### 6. ハンズオン①: 要件一覧を作る（`sdd-requirements`）（20 min）

- サンプル議事録（[samples/meeting-notes-sample.md](../samples/meeting-notes-sample.md)）を題材に、`@sdd-requirements` で要件一覧を生成。
- 運用・開発・営業など複数ロールを演じさせる壁打ちで抜け漏れを洗い出す体験。
- 実行例:

  ```
  @sdd-requirements #file:samples/meeting-notes-sample.md をもとに要件一覧を作成してください。
  ```

### 休憩②（10 min）

### 7. ハンズオン②: 設計書を作る（`sdd-design`）（20 min）

- ①で作成した `work/requirements.md` を入力に `@sdd-design` で設計書を生成。
- 「要件 → 設計」の変換ルールを Instruction / Agent 定義で固定している点を確認。
- 実行例:

  ```
  @sdd-design #file:work/requirements.md をもとに設計書を作成してください。
  ```

### 8. ハンズオン③: ワイヤーフレームを作る（`sdd-wireframe`）（15 min）

- ②で作成した `work/design.md` を入力に `@sdd-wireframe` で HTML ワイヤーフレームを生成。
- 画面イメージを早期に共有し、関係者との認識合わせに使える点を体験。
- 実行例:

  ```
  @sdd-wireframe #file:work/design.md をもとにワイヤーフレーム（HTML）を生成してください。
  ```

### 9. 応用トピック駆け足（10 min）

- MCP サーバー連携（外部データソースとの接続イメージ）。
- Coding Agent（Issue アサイン → 自動 PR 作成の仕組み）。
- ハルシネーション対策・セキュリティ・ガバナンス上の注意点を簡潔に共有。

### 10. まとめ・Q&A（10 min）

- 簡略化 SDD ライフサイクル × Copilot 技術要素の組み合わせ方を振り返る。
- 実務適用時の次の一歩（Instruction / Skill / Agent の育て方）を案内。

## 4. 使用エージェント（参考）

| エージェント | 役割 | 入力 | 出力 |
|---|---|---|---|
| `sdd-requirements` | ヒアリング内容から要件一覧を作成し、複数ロールの壁打ちで抜け漏れを洗い出す | 議事録ファイル or 雑な要望 | `work/requirements.md` |
| `sdd-design` | 要件一覧から設計書（仕様書）を作成 | `work/requirements.md` | `work/design.md` |
| `sdd-wireframe` | 設計書から画面のワイヤーフレーム（HTML）を作成 | `work/design.md` | `app/index.html` |
| `sdd-pipeline` | `app/` を Azure Static Web Apps へデプロイする CI/CD を作成 | `app/index.html` | `.github/workflows/azure-static-web-apps.yml` |

## 5. 前提条件（事前準備）

- [ ] GitHub アカウント
- [ ] GitHub Copilot ライセンス
- [ ] VS Code + GitHub Copilot 拡張
- [ ] 本リポジトリのクローン

詳細は [参加者ガイド](participant-guide.md) を参照してください。
