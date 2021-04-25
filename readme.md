<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 1100 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost you and your team's skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the Laravel [Patreon page](https://patreon.com/taylorotwell).

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Cubet Techno Labs](https://cubettech.com)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[British Software Development](https://www.britishsoftware.co)**
- **[Webdock, Fast VPS Hosting](https://www.webdock.io/en)**
- **[DevSquad](https://devsquad.com)**
- [UserInsights](https://userinsights.com)
- [Fragrantica](https://www.fragrantica.com)
- [SOFTonSOFA](https://softonsofa.com/)
- [User10](https://user10.com)
- [Soumettre.fr](https://soumettre.fr/)
- [CodeBrisk](https://codebrisk.com)
- [1Forge](https://1forge.com)
- [TECPRESSO](https://tecpresso.co.jp/)
- [Runtime Converter](http://runtimeconverter.com/)
- [WebL'Agence](https://weblagence.com/)
- [Invoice Ninja](https://www.invoiceninja.com)
- [iMi digital](https://www.imi-digital.de/)
- [Earthlink](https://www.earthlink.ro/)
- [Steadfast Collective](https://steadfastcollective.com/)
- [We Are The Robots Inc.](https://watr.mx/)
- [Understand.io](https://www.understand.io/)
- [Abdel Elrafa](https://abdelelrafa.com)

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-source software licensed under the [MIT license](https://opensource.org/licenses/MIT).


## 環境構築

https://coxcox.hatenablog.com/entry/2019/03/14/172143
1.homebrewのinstall - https://brew.sh/index_ja
 (HomebrewはMac用のパッケージ管理システム。)
2.PHPをインストール
 brew install php@7.3      #@以下でバージョン指定
3.composer (PHPのパッケージ管理システム)をインストール 
 brew install homebrew/core/composer
4.PATHを通す  https://qiita.com/miya_sho/items/4b79c9a74fecb42768f6
コマンド検索パス(コマンドサーチパス)を追加すること
新たに環境変数のPATH(パス)を追加することでどこのディレクトリからもcomposer.pharを実行できる
コマンド検索パスに~/.composer/vendor/binが追加されているかを確認
echo $PATH　コマンドで、pathの確認。
vim ~/.bashrcを開き、
　　　　　　　vim -テクストエディタ。ターミナル上で、編集が可能。
export PATH="$PATH:$HOME/.composer/vendor/bin"
をvim内に記入。
（composerにパスを通す。）
source ~/.bash_profile　で実行される。
      *.bash_profile（.zshrc）はユーザがターミナルを新規で開いた場合に読み込まれるファイル。

5.Valetのinstall
composer global require laravel/valet
valet install
Valet（ベレット：従者）はMacミニマニストのためのLaravel開発環境。

6.Laravel install
composer global require "laravel/installer"

## Laravelの設定
https://qiita.com/miya_sho/items/6e6635555fcb0af9fa66
laravelのプロジェクトを作成
composer create-project laravel/laravel=5.8 Laravel_app
　*Laravel_appの部分はプロジェクト名

cd Laravel_app で移動し
php artisan -V でバージョンを確認

## mysqlのインストールとデータベースの設定
https://qiita.com/miya_sho/items/6e6635555fcb0af9fa66
brew install mysql 
mysql -V　でバージョンを確認
mysql.server start　で起動をさせる
mysql -uroot　rootユーザーでログイン
mysql> create database macdb;　でデータベースを作成macdbはデータベースのファイル名
mysql> create user mac@localhost identified by 'mo'; ユーザー作成。macがユーザー名でmoがパスワード

mysqlがうごかない時は mysql -u user-name -pでログインしてみる


## Laravelとデータベースの紐付け
.envファイル
DB_CONNECTION=mysql
DB_HOST=localhost　→　127.0.0.1に変更
DB_PORT=3306
DB_DATABASE=macdb
DB_USERNAME=mac
DB_PASSWORD=mo

変更したら、
php artisan config:cache
php artisan cache:clear 
php artisan migrate 

Illuminate\Database\QueryException  : SQLSTATE[HY000] [2002] No such file or directory (SQL: select * from information_schema.tables where table_schema = macdb and table_name = migrations and table_type = 'BASE TABLE')
のエラーが起きた場合は、.envのDBの記載が正しいか確認。

### npmコマンドをするために、node をインストール
https://qiita.com/non0311/items/664cf74d9ff4bad9cf46
brew install nodebrew
nodebrew install-binary latest　最新版のインストール
エラーが出たら、
mkdir -p ~/.nodebrew/src
nodebrew install-binary latest
リストからバージョンを選択
nodebrew list　で確認して、
nodebrew use v16.0.0　でバージョンを入力

*パスを通す
echo 'export PATH=$PATH:$HOME/.nodebrew/current/bin' >> ~/.bash_profile
vi ~/.bash_profile　に以下を入力。
vim -> e: vi ~/.bash_profile -> iで編集　->以下を入力
if [ -f ~/.bashrc ] ; then
. ~/.bashrc
fi
-> escボタン押して -> :wqで保存と終了

### Font Awesome
インストール前に package.jsonに以下を追加。
}のあとの,コンマがないとインストールできません。
    },
        "dependencies": {
                    "font-awesome": "^4.7.0"
            }

###　Sortableのインストール
composer require rutorika/sortable
でエラーが発生した場合、バージョンの不一致の可能性が高い。
composer require rutorika/sortable 7.0.0　でバージョンを指定することが可能
