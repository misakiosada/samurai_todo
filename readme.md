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


## ????????????

https://coxcox.hatenablog.com/entry/2019/03/14/172143
1.homebrew???install - https://brew.sh/index_ja
 (Homebrew???Mac??????????????????????????????????????????)
2.PHP?????????????????????
 brew install php@7.3      #@??????????????????????????????
3.composer (PHP????????????????????????????????????)????????????????????? 
 brew install homebrew/core/composer
4.PATH?????????  https://qiita.com/miya_sho/items/4b79c9a74fecb42768f6
????????????????????????(???????????????????????????)?????????????????????
????????????????????????PATH(??????)????????????????????????????????????????????????????????????composer.phar??????????????????
???????????????????????????~/.composer/vendor/bin????????????????????????????????????
echo $PATH?????????????????????path????????????
vim ~/.bashrc????????????
?????????????????????vim -?????????????????????????????????????????????????????????????????????
export PATH="$PATH:$HOME/.composer/vendor/bin"
???vim???????????????
???composer????????????????????????
source ~/.bash_profile????????????????????????
      *.bash_profile???.zshrc????????????????????????????????????????????????????????????????????????????????????????????????

5.Valet???install
composer global require laravel/valet
valet install
Valet??????????????????????????????Mac??????????????????????????????Laravel???????????????

6.Laravel install
composer global require "laravel/installer"

## Laravel?????????
https://qiita.com/miya_sho/items/6e6635555fcb0af9fa66
laravel??????????????????????????????
composer create-project laravel/laravel=5.8 Laravel_app
???*Laravel_app?????????????????????????????????

cd Laravel_app ????????????
php artisan -V ???????????????????????????

## mysql???????????????????????????????????????????????????
https://qiita.com/miya_sho/items/6e6635555fcb0af9fa66
brew install mysql 
mysql -V??????????????????????????????
mysql.server start????????????????????????
mysql -uroot???root???????????????????????????
mysql> create database macdb;?????????????????????????????????macdb???????????????????????????????????????
mysql> create user mac@localhost identified by 'mo'; ?????????????????????mac?????????????????????mo??????????????????

mysql???????????????????????? mysql -u user-name -p???????????????????????????


## Laravel?????????????????????????????????
.env????????????
DB_CONNECTION=mysql
DB_HOST=localhost?????????127.0.0.1?????????
DB_PORT=3306
DB_DATABASE=macdb
DB_USERNAME=mac
DB_PASSWORD=mo

??????????????????
php artisan config:cache
php artisan cache:clear 
php artisan migrate 

Illuminate\Database\QueryException  : SQLSTATE[HY000] [2002] No such file or directory (SQL: select * from information_schema.tables where table_schema = macdb and table_name = migrations and table_type = 'BASE TABLE')
????????????????????????????????????.env???DB?????????????????????????????????

### npm?????????????????????????????????node ?????????????????????
https://qiita.com/non0311/items/664cf74d9ff4bad9cf46
brew install nodebrew
nodebrew install-binary latest?????????????????????????????????
????????????????????????
mkdir -p ~/.nodebrew/src
nodebrew install-binary latest
???????????????????????????????????????
nodebrew list?????????????????????
nodebrew use v16.0.0??????????????????????????????

*???????????????
echo 'export PATH=$PATH:$HOME/.nodebrew/current/bin' >> ~/.bash_profile
vi ~/.bash_profile????????????????????????
vim -> e: vi ~/.bash_profile -> i????????????->???????????????
if [ -f ~/.bashrc ] ; then
. ~/.bashrc
fi
-> esc?????????????????? -> :wq??????????????????

### Font Awesome
???????????????????????? package.json?????????????????????
}????????????,?????????????????????????????????????????????????????????
    },
        "dependencies": {
                    "font-awesome": "^4.7.0"
            }

###???Sortable?????????????????????
composer require rutorika/sortable
???????????????????????????????????????????????????????????????????????????????????????
composer require rutorika/sortable 7.0.0???????????????????????????????????????????????????
