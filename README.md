# mametsubu VPM Listing

mametsubu が公開している VPM (VRChat Package Manager) パッケージを集約するリポジトリです。GitHub Pages 経由で VCC (VRChat Creator Companion) 向けのパッケージリスティング (`vpm.json`) を配信します。

## 収録パッケージ

| パッケージID | 名前 | 説明 |
|---|---|---|
| `com.mame8.animator-controller-context` | AnimatorController Context | AnimatorController の構造と AnimationClip の内容をテキスト形式に双方向変換する Unity Editor ツール |
| `com.mame8.animator-controller-ma-context` | AnimatorController MA Context | VRChat アバターの構成 (AnimatorController, Modular Avatar, VRC コンポーネント) を AI 向けテキスト形式に一括シリアライズ |

## VCC への追加

以下の URL を VCC の **Settings > Packages > Add Repository** に追加してください。

```
https://mametsubu8.github.io/vpm-listing/vpm.json
```

## 自動ビルド

GitHub Actions により `vpm.json` は自動的に再生成されます。

- **定期実行**: 6 時間ごと (cron)
- **repository_dispatch**: 各パッケージリポジトリからのリリースイベント (`package-released`)
- **手動実行**: Actions タブから workflow_dispatch

ワークフローは各パッケージリポジトリの GitHub Releases から zip をダウンロードし、`package.json` を読み取って `source.json` のテンプレートにバージョン情報をマージします。

## パッケージの追加方法

1. `source.json` の `packages` に新しいパッケージ ID のエントリを追加する
2. `.github/workflows/build-listing.yml` の `PACKAGES` 環境変数に `owner/repo:パッケージID` の形式で追記する
3. プッシュ後、ワークフローを手動実行するか次の定期実行を待つ

## ライセンス

MIT License
