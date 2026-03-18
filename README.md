# Mod Support Bot

Discord bot for 7 Days to Die MOD support communities.
This bot creates per-MOD support channels and relays chat between registered guilds.

## 1. Supported MODs

- #1 Action Skills Plus
- #2 Unlock Tracker
- #3 Server Status Bot

The source of truth is `mod_support_config.json`.

## 2. Commands

- `/help`
- Show supported MOD list (one MOD per page, Prev/Next buttons, timeout=None).

- `/setup mod_no:<number>`
- Create or reuse MOD support channel.
- Auto-register current guild to relay registry for that MOD.

- `/relay_disable mod_no:<number>`
- Disable relay registration for this guild and MOD.

- `/reply mod_no:<number> target_guild_id:<id> message:<text>`
- Hub-only command to reply to a specific spoke guild.

## 3. Setup

```bash
cd "/root/Release/Mod Support Bot"
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

Set `DISCORD_BOT_TOKEN` in `.env`.

Start:

```bash
cd "/root/Release/Mod Support Bot"
source .venv/bin/activate
python3 bot.py
```

## 4. Environment Variables

- `DISCORD_BOT_TOKEN`
- Required bot token.

- `DISCORD_TEST_GUILD_ID`
- Optional test guild for startup duplicate-command cleanup.

- `GLOBAL_CHAT_ALLOWED_GUILD_IDS`
- Optional hard filter (comma-separated guild IDs).
- If empty, all guilds registered by `/setup` can relay.

- `GLOBAL_CHAT_HUB_GUILD_ID`
- Optional hub mode target guild ID.
- When set, relay becomes spoke -> hub only.

## 5. Relay Behavior

- `/setup` adds current guild to `relay_registry.json` for selected MOD.
- `/relay_disable` removes current guild from that MOD relay list.
- Hub mode (`GLOBAL_CHAT_HUB_GUILD_ID`) sends spoke messages only to hub.
- In hub mode, relayed messages include `Reply / 返信` button and `/reply` is available in hub guild.

## 6. Data Files

- `mod_support_config.json`
- Command/help labels, category name, MOD metadata, channel names.

- `relay_registry.json`
- Registered guild IDs per MOD for relay routing.

## 7. Permissions

- `/setup`: Manage Channels
- `/relay_disable`: Manage Server
- `/reply`: Manage Server + hub guild context

## 8. systemd

- Service: `mod-support-bot.service`
- Unit: `/etc/systemd/system/mod-support-bot.service`

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now mod-support-bot.service
sudo systemctl restart mod-support-bot.service
sudo systemctl status mod-support-bot.service
sudo journalctl -u mod-support-bot.service -f
```

## 9. Policy Links

- Privacy Policy: [PRIVACY.md](PRIVACY.md)
- Terms of Use: [TERMS.md](TERMS.md)
- Distribution Guide: [GITHUB_GUIDE.md](GITHUB_GUIDE.md)

---

# Mod Support Bot - 日本語

7 Days to Die の MOD サポート向け Discord Bot です。
MODごとのサポートチャンネル作成と、登録ギルド間リレーを提供します。

## 1. 対応MOD

- #1 Action Skills Plus
- #2 Unlock Tracker
- #3 Server Status Bot

正本データは `mod_support_config.json` です。

## 2. コマンド

- `/help`
- サポート対象MOD一覧を表示（1ページ1MOD、Prev/Next、timeout=None）。

- `/setup mod_no:<番号>`
- MODサポートチャンネルを作成または再利用。
- 実行ギルドを対象MODのリレー登録へ自動追加。

- `/relay_disable mod_no:<番号>`
- 実行ギルドの対象MODリレー登録を無効化。

- `/reply mod_no:<番号> target_guild_id:<ID> message:<テキスト>`
- hub 専用。指定 spoke ギルドへ返信。

## 3. セットアップ

```bash
cd "/root/Release/Mod Support Bot"
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp .env.example .env
```

`.env` の `DISCORD_BOT_TOKEN` を設定してください。

起動:

```bash
cd "/root/Release/Mod Support Bot"
source .venv/bin/activate
python3 bot.py
```

## 4. 環境変数

- `DISCORD_BOT_TOKEN`
- 必須のBotトークン。

- `DISCORD_TEST_GUILD_ID`
- 任意。起動時に重複コマンド掃除を行うテストギルドID。

- `GLOBAL_CHAT_ALLOWED_GUILD_IDS`
- 任意。カンマ区切りの許可ギルドID。
- 空欄時は `/setup` で登録されたギルドが転送対象。

- `GLOBAL_CHAT_HUB_GUILD_ID`
- 任意。hub モードの集約先ギルドID。
- 設定時は spoke -> hub のみ転送。

## 5. リレー挙動

- `/setup` は対象MODの `relay_registry.json` へ現在ギルドを追加。
- `/relay_disable` は対象MODの現在ギルド登録を削除。
- hub モード（`GLOBAL_CHAT_HUB_GUILD_ID`）では spoke から hub のみ転送。
- hub モード時は転送メッセージに `Reply / 返信` ボタンが付き、hub で `/reply` が使えます。

## 6. データファイル

- `mod_support_config.json`
- コマンド表示文、カテゴリ名、MOD情報、チャンネル名を定義。

- `relay_registry.json`
- MODごとの登録ギルドIDを保持。

## 7. 権限

- `/setup`: チャンネルの管理
- `/relay_disable`: サーバーの管理
- `/reply`: サーバーの管理 + hub ギルド内

## 8. systemd

- Service: `mod-support-bot.service`
- Unit: `/etc/systemd/system/mod-support-bot.service`

```bash
sudo systemctl daemon-reload
sudo systemctl enable --now mod-support-bot.service
sudo systemctl restart mod-support-bot.service
sudo systemctl status mod-support-bot.service
sudo journalctl -u mod-support-bot.service -f
```

## 9. ポリシーリンク

- Privacy Policy: [PRIVACY.md](PRIVACY.md)
- Terms of Use: [TERMS.md](TERMS.md)
- 配布ガイド: [GITHUB_GUIDE.md](GITHUB_GUIDE.md)
