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

初期のサイト名はRepository名です。Tomosのサイト作成処理は `.tomos-site-name` に指定したサイト名を設定します。サイト作成が完了するまでは、Workflowはbuild検証のみを行い、Pagesへdeployしません。

## 初期構成

- `content/index.md`: トップページ
- `content/about.md`: このサイトについて
- `tomos.config.php`: サイト名、公開URL、Themeの設定
- `.github/workflows/github-pages.yml`: buildとGitHub Pagesへのdeploy

## 公開設定

GitHub Pagesの公開元をGitHub Actionsに設定してから、`main`へ変更をpushしてください。Tomosのサイト作成処理はPagesをActionsに設定し、初期設定を完了してからdeployを開始します。

## Tomos Coreのバージョン

WorkflowはTomos Publishing Coreの特定commitを利用します。バージョンを更新するときは互換性を確認して `TOMOS_VERSION` を変更してください。mainへ自動追従はしません。

## テーマの選択と公開

公式追加テーマの Tomos Quiet 1.0.5・Tomos Index 1.0.6・Tomos Wiki 1.0.0 は、サイト管理画面の既存のテーマ選択から利用できます。初期テーマは引き続きTomos Minimalです。

QuietとIndexは固定Publishing Core内のファイルを利用します。Wikiは公式配布ZIPと同じファイルを `themes/wiki/` に同梱しています。テーマの切替で記事、画像、独自ドメインの設定は変わりません。

すでに作成済みのサイトはテンプレートを取り込み直す必要がありません。対応する管理画面でWikiを選択・保存すると、未導入の場合だけ公式ファイルとテーマ設定を一緒に登録します。同名の登録済みテーマを自動更新・上書きすることはありません。

公開テーマは `tomos.config.php` の `theme.name` に指定します。Tomos標準テーマに加え、検証済みの独自テーマをRepositoryの `themes/<テーマ名>/` に登録できます。テーマを変更すると `main` へのpushによってGitHub Actionsが再生成します。

Workflowは固定された対応済みTomos Coreを使用し、選択されているテーマのCSSと静的成果物を確認します。特定の固定ページや記事の存在には依存しません。テーマ名だけを変更してZIP未登録の場合はビルドが失敗します。

> **公開準備中の注意**: 現行のサイト管理画面APIは固定文字列の `site.name`、`site.url`、`site.base_path` などを前提としており、このテンプレートの動的設定形式への対応が未完了です。一般向けのサイト設定画面をリリースする前に互換性を解消します。現段階ではサイト管理画面からの設定変更を正式サポート済みとは扱いません。
