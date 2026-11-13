---
title: "レッスン 12 - GitHub Pages でサイトをデプロイ"
description: "GitHub Copilot app を使って Pages のワークフローを構成し、pull request を確認して、公開済みのライブ Space Quiz を確認します。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Space Quiz に公開用の場所を用意するため、GitHub Pages でデプロイします。Copilot はワークフローの準備とデプロイの案内を行えますが、変更内容を確認し、サイトが実際に公開されていることを確認するのは開発者の責任です。

このレッスンでは、次の内容を学習します。

- Copilot に GitHub Pages のデプロイを設定させる。
- マージ前にワークフローと pull request を確認する。
- デプロイを追跡して公開サイトを確認する。

## シナリオ

Space Quiz はすでに GitHub リポジトリにありますが、簡単に試せる方法が必要です。単一ファイルのサイトを GitHub Pages で公開すると、サーバーやランタイム依存関係を追加せずに、公開 URL からアクセスできるようになります。

## Copilot にサイトのデプロイを依頼する

Copilot app の `space-quiz` セッションで、次のプロンプトを送信します。

```plaintext
Enable GitHub Pages for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and merge it after required checks pass. Monitor the deployment until it succeeds, then report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![3 段階の図: マージ済みの space-quiz pull request、Build website、Upload artifact、Deploy to Pages の各ステップを含む GitHub Actions Deploy website の成功した実行、yourname.github.io/space-quiz/ で公開された Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

> [!WARNING]
> このプロンプトでは、エージェントに pull request の作成とマージ、およびリポジトリの Pages 設定の変更を依頼します。続行する前に、diff、デプロイ権限、GitHub の承認プロンプトを確認してください。

## ワークフローを確認してデプロイを検証する

1. リポジトリに README がまだない場合に限り、追加されていることを確認します。
2. ワークフローのビルドとデプロイの手順を含め、pull request の変更を確認します。
3. 必須の pull request チェックが成功した後にのみマージします。
4. GitHub Actions のデプロイ実行を追跡し、成功するまで確認します。
5. 報告された URL を開き、Space Quiz が表示されることを確認します。

エージェントが Pages の有効化や pull request のマージを行えない場合は、提示された具体的な手順に従います。デプロイが成功し、公開サイトが読み込まれるまで、タスクを完了と見なさないでください。

## まとめと次のステップ

Space Quiz が公開され、エージェントの報告に頼らずデプロイを確認できました。[レッスン 13: 振り返りと次のステップ][next-lesson]に進みます。

[next-lesson]: ../13-review/
