# sumikin-support

墨筋の公開ページ（サポート・プライバシーポリシー・利用規約）。

**このフォルダの中身が、そのまま `ogilab-apps/sumikin-support` リポジトリのルートになる。** ほかのアプリの support（`jellim-support` など）と同じ構成に揃えてある。色はアプリの景色に合わせ、端末が明るい表示なら白和紙、暗い表示なら黒和紙で出す。朱は使わない（アプリでは鍛えた筋肉だけの色）。

| ファイル | 公開URL | 用途 |
|---|---|---|
| `index.html` | `https://ogilab-apps.github.io/sumikin-support/` | Support URL（ASC必須）。日本語のあとに英語 |
| `privacy.html` | `.../privacy.html` | Privacy Policy URL（ASC必須・日本語） |
| `terms.html` | `.../terms.html` | 利用規約（日本語） |
| `privacy-en.html` | `.../privacy-en.html` | Privacy Policy（英語） |
| `terms-en.html` | `.../terms-en.html` | Terms of Use（英語） |

アプリからのリンクは `src/constants/links.ts` に定義している（端末の言語で日本語版と英語版を出し分ける）。**URLを変えるときは両方を直す。**

## 公開

2026-11-22 に公開した。`ogilab-apps/sumikin-support`（Public）の `main` のルートを GitHub Pages で出している。

直すときは、まずこのフォルダを直してアプリのリポジトリでコミットし、同じ中身を `ogilab-apps/sumikin-support` に push する。

1. `ogilab-apps/sumikin-support` を clone し、中身をこのフォルダのもので置き換えて commit する
2. `ogilab-apps` のトークンで push する。この PC の git は Git Credential Manager を使うので、`gh auth switch` だけでは push のアカウントが替わらない。その場で gh の資格情報を使う:
   `GH_TOKEN=$(gh auth token --user ogilab-apps) git -c credential.helper= -c 'credential.helper=!gh auth git-credential' push`
3. 1〜2 分で上表のURLに出る

## 問い合わせ先

`ogilab.apps@gmail.com`。ogilab 共通アドレスを使う。アプリ専用のアドレスは作らない。

## 更新のたびに確認すること

- 価格（買い切り ¥1,200。2026-11-22 に決定）が App Store Connect の設定と一致しているか（利用規約の 3）
- App Store Connect で商品のファミリー共有をオンにしたか（サポートと利用規約に「対応しています」と書いている）
- 無料の範囲が実装と一致しているか。無料は履歴の今月と先月、絵姿は侍、景色は白和紙。皆伝版は忍者・力士、黒和紙・自動、ウィジェット、先月より前の履歴、部位ごとの回復時間。絵姿が増えたり替わったりしたら、サポートの「墨筋 皆伝版」と英語の段落、利用規約の 2・3・4 を直す
- 画面の言葉（「トレーニングを記録」「まだ張っている」「記録を書き出す」「購入を復元」など）が `src/i18n/ja.ts`・`en.ts` と一致しているか
- 医療的な表現を使わない（診断・治療・予防をうたわない。「記録から計算した回復の目安」にとどめる）。`__tests__/strings.test.ts` がこのフォルダの HTML も見ている
- 外部と通信しないという説明が実装と一致しているか（購入の確認で Apple と通信するだけ）。書き出すファイルの中身（記録、設定、書いた文字、水面）が `src/features/backup/backup.ts` と一致しているか
- 通知しない時間帯の扱い（その間に回復した分は、終わる時刻に届く。初めは 22:00〜7:30）が実装と一致しているか
