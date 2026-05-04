# SoloptiLinkAI ユーザーサポート AI アシスタント

SoloptiLinkAI v2027.0 のお客様向け AI アシスタント。Streamlit + Claude Haiku 4.5 で動作。

## 役割

- v2027.0 のインストール手順 (Mac 8 ステップ / Win 5 ステップ) を対話で案内
- 「何が作れるか」を PR 視点で回答 (CRM / EC / iOS アプリ等)
- 内部技術 (採用ライブラリ・アーキテクチャ・内部スキル名) は一切回答しない
- プロンプトインジェクション・役割変更要求に耐性

## デプロイ (Streamlit Cloud)

1. https://share.streamlit.io/ に GitHub アカウントでサインイン
2. 「New app」→ Repository: `onukih-design/soloptilinkai-support-bot`、Branch: `main`、Main file: `app.py`
3. Advanced settings → Secrets に以下を追加:
   ```toml
   ANTHROPIC_API_KEY = "sk-ant-api03-xxxxx"
   ```
4. 「Deploy」をクリック → 完了
5. デプロイ後、Settings → Sharing → **Public** に変更

## 環境変数

| 変数 | 必須 | 用途 |
|---|---|---|
| `ANTHROPIC_API_KEY` | ✅ | Claude Haiku 4.5 API 呼び出し |
| `SUPPORT_MODEL` | 任意 | デフォルト: `claude-haiku-4-5-20251001` |

## メールへの埋め込み

デプロイ完了後、Vercel admin-dashboard 側で:
```bash
cd admin-dashboard
vercel env add AI_ASSISTANT_URL production
# 値を貼り付け: https://soloptilinkai-support-bot.streamlit.app/
vercel --prod --yes
```

これでお客様向け配信メールに「🤖 AI アシスタントを開く」ボタンが自動で出現。

## ローカル実行 (開発用)

```bash
pip install -r requirements.txt
export ANTHROPIC_API_KEY=sk-ant-api03-xxxxx
streamlit run app.py
```

## ライセンス

社内利用のみ。再配布禁止。
