# Mod Support Bot - GitHub Guide (EN)

## Overview

Mod Support Bot provides MOD-specific support channels and relay routing across Discord guilds.
Relay targets are controlled by `/setup` and `/relay_disable`, with optional hub-mode routing.

## Core Commands

- `/help`
- Show supported MODs with pageable embed.

- `/setup mod_no:<number>`
- Create or reuse support channel for selected MOD.
- Auto-register current guild into relay registry.

- `/relay_disable mod_no:<number>`
- Remove current guild from relay registry for selected MOD.

- `/reply mod_no:<number> target_guild_id:<id> message:<text>`
- Hub-only staff reply to spoke guild.

## Relay Design

- Registry file: `relay_registry.json`
- Key: MOD number
- Value: list of guild IDs

Routing behavior:
- No hub mode: registered guilds relay to each other (same MOD channel)
- Hub mode (`GLOBAL_CHAT_HUB_GUILD_ID` set): spoke -> hub only

## Environment Variables

- `DISCORD_BOT_TOKEN` (required)
- `DISCORD_TEST_GUILD_ID` (optional)
- `GLOBAL_CHAT_ALLOWED_GUILD_IDS` (optional hard filter)
- `GLOBAL_CHAT_HUB_GUILD_ID` (optional hub mode)

## Data Files

- `mod_support_config.json`
- `relay_registry.json`

## Permissions

- `/setup`: Manage Channels
- `/relay_disable`: Manage Server
- `/reply`: Manage Server + hub guild context

## Policy Links

- Privacy Policy: [PRIVACY.md](PRIVACY.md)
- Terms of Use: [TERMS.md](TERMS.md)

---

# Mod Support Bot - GitHubガイド (JP)

## 概要

Mod Support Bot は、MOD専用サポートチャンネル作成と、Discordギルド間リレーを提供します。
リレー対象は `/setup` と `/relay_disable` で制御し、任意で hub モード運用が可能です。

## 主要コマンド

- `/help`
- ページ送り付き埋め込みでサポート対象MODを表示。

- `/setup mod_no:<番号>`
- 指定MODのサポートチャンネルを作成または再利用。
- 実行ギルドをリレー登録へ自動追加。

- `/relay_disable mod_no:<番号>`
- 指定MODのリレー登録から現在ギルドを削除。

- `/reply mod_no:<番号> target_guild_id:<ID> message:<テキスト>`
- hub 専用。運営スタッフが spoke ギルドへ返信。

## リレー設計

- 登録ファイル: `relay_registry.json`
- キー: MOD番号
- 値: ギルドID配列

転送挙動:
- hub なし: 登録済みギルド同士で相互転送（同一MODチャンネル）
- hub あり（`GLOBAL_CHAT_HUB_GUILD_ID` 設定）: spoke -> hub のみ

## 環境変数

- `DISCORD_BOT_TOKEN`（必須）
- `DISCORD_TEST_GUILD_ID`（任意）
- `GLOBAL_CHAT_ALLOWED_GUILD_IDS`（任意の上限制限）
- `GLOBAL_CHAT_HUB_GUILD_ID`（任意のhubモード）

## データファイル

- `mod_support_config.json`
- `relay_registry.json`

## 権限

- `/setup`: チャンネルの管理
- `/relay_disable`: サーバーの管理
- `/reply`: サーバーの管理 + hub ギルド内

## ポリシーリンク

- Privacy Policy: [PRIVACY.md](PRIVACY.md)
- Terms of Use: [TERMS.md](TERMS.md)
