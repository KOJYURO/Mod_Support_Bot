# Privacy Policy / プライバシーポリシー

## EN

### 1. Scope
This policy applies to Mod Support Bot and related relay operation in Discord servers.

### 2. Data Processed
The bot may process and store:
- Discord guild IDs participating in relay
- MOD support channel metadata (category/channel names)
- Relay message content and attachment URLs
- Relay metadata (source guild ID, sender display name, sender user ID, jump URL)
- Optional hub reply data sent by support staff

### 3. Purpose
Data is used only to:
- Create and manage MOD support channels
- Route relay messages between registered guilds
- Enable hub reply workflow
- Troubleshoot operation issues

### 4. Storage
- Relay registry: `relay_registry.json`
- MOD/help configuration: `mod_support_config.json`
- Runtime logs (depending on service configuration)

### 5. Sharing
By design, relay messages are redistributed to registered guild channels for support operations.
Operators are responsible for informing community members that messages in relay channels may be forwarded.

### 6. Retention and Deletion
- `/relay_disable` removes relay registration for selected MOD on current guild.
- Operators can delete local files to remove persisted registry/config data.
- Discord-side message retention follows each server's moderation policy.

### 7. Security Notes
- Restrict access to bot host and runtime files.
- Limit who can run setup/relay admin commands.
- Use least-privilege role design in Discord.

### 8. Contact
Use your support Discord/server operation channel for privacy-related requests.

---

## JP

### 1. 適用範囲
本ポリシーは Mod Support Bot と、Discordサーバー間リレー運用に適用されます。

### 2. 処理・保存する情報
本ボットは運用上、次の情報を処理・保存する場合があります。
- リレー参加ギルドID
- MODサポートチャンネル情報（カテゴリ名・チャンネル名）
- リレー対象メッセージ本文と添付URL
- 転送メタ情報（元ギルドID、送信者表示名、送信者ID、ジャンプURL）
- hub返信で送信される返信メッセージ

### 3. 利用目的
情報は次の目的でのみ利用します。
- MODサポートチャンネルの作成と管理
- 登録ギルド間のメッセージ転送
- hub返信ワークフローの提供
- 障害調査と運用保守

### 4. 保存先
- リレー登録情報: `relay_registry.json`
- MOD表示設定: `mod_support_config.json`
- 実行ログ（サービス設定に依存）

### 5. 共有について
本ボットの仕様上、リレー対象チャンネルのメッセージは登録ギルドへ再配信されます。
運用者は、当該チャンネルのメッセージが転送されることを参加者へ明示してください。

### 6. 保持期間と削除
- `/relay_disable` で、現在ギルドの対象MODリレー登録を削除できます。
- ローカルファイル削除で永続データを消去できます。
- Discord側メッセージ保持は各サーバー運用ルールに従います。

### 7. セキュリティ注意
- Botホストと実行ファイルへのアクセスを制限してください。
- setup/relay管理コマンド実行者を最小限にしてください。
- Discordロール設計は最小権限で運用してください。

### 8. 連絡先
プライバシー関連の問い合わせは、運用中のサポートDiscord窓口で対応してください。
