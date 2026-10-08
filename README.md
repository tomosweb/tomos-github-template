# Tomos GitHub版サイトテンプレート

このRepositoryからTomosの静的サイトを作成できます。GitHub ActionsがTomos Publishing CoreでMarkdownをHTMLへ変換し、GitHub Pagesへ公開します。

## 公開のしくみ

- 記事や固定ページは `content/` にMarkdownで置きます。
- GitHub Actionsが更新を検知して静的サイトを生成します。
- GitHub Pagesが生成ファイルを公開します。
- Tomosの投稿機能から、このRepositoryへ記事を送れます。

このテンプレートは、個人情報や検証用投稿を含まない最小構成です。

## 公開URL

公開URLはRepository名に応じて自動設定されます。

- Repositoryが `ユーザー名.github.io` の場合: `https://ユーザー名.github.io/`
- それ以外の場合: `https://ユーザー名.github.io/Repository名/`

初期のサイト名はRepository名です。Tomosのサイト作成処理から作成すると、指定したサイト名が反映されます。

## 初期構成

- `content/index.md`: トップページ
- `content/about.md`: このサイトについて
- `tomos.config.php`: サイト名、公開URL、Themeの設定
- `.github/workflows/github-pages.yml`: buildとGitHub Pagesへのdeploy

## 公開設定

GitHub Pagesの公開元をGitHub Actionsに設定してから、`main`へ変更をpushしてください。初回セットアップ時はTomosのサイト作成処理がこの設定を行います。

## Tomos Coreのバージョン

WorkflowはTomos Publishing Coreの特定commitを利用します。バージョンを更新するときは互換性を確認して `TOMOS_VERSION` を変更してください。mainへ自動追従はしません。
