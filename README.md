# authorization-app-practice（認可機能の学習プロジェクト）

## 概要
このプロジェクトは、Laravelの「認可（Authorization）」機能を習得するために作成した、シンプルな投稿管理アプリケーションです。
単なるログイン（認証）だけでなく、「どのユーザーが、どの操作を行えるか」という権限管理の実装方法を重点的に学習しました。

## 実装した主な機能
- **ユーザー認証**: Laravel Fortifyを使用したログイン、ログアウト、ユーザー登録機能。
- **認可（Policy）の実装**: `PostPolicy` を作成し、「自分の投稿のみ編集・削除ができる」というルールを定義。
- **アクセス制御**:
    - コントローラー側で `$this->authorize()` を使用し、他人の投稿を不正に編集・削除しようとした場合に403エラーを返す処理。
    - Bladeテンプレート側で `@can` ディレクティブを使用し、権限があるユーザーにのみ「編集」「削除」ボタンを表示する処理。
- **データベース連携**: マイグレーションによるテーブル作成と、Eloquentリレーション（UserとPostの1対多）の活用。

## 学習したキーワード
- **Authentication（認証）**: 「あなたは誰か」を確認する。
- **Authorization（認可）**: 「あなたにその操作を許可するか」を判断する。
- **Policy（ポリシー）**: 特定のモデルに対する認可ロジックをまとめたクラス。
- **Middleware（ミドルウェア）**: リクエストがコントローラーに届く前に「ログイン済みか」などをチェックする門番。

## 使用技術
- PHP 8.x
- Laravel 10.x
- Laravel Fortify (認証バックエンド)
- Docker / Laravel Sail (開発環境)
- Tailwind CSS (スタイリング)

## セットアップ方法
1. コンテナの起動: `sail up -d`
2. データベース構築: `sail artisan migrate --seed`
    - テストユーザーA: usera@example.com / password
    - テストユーザーB: userb@example.com / password