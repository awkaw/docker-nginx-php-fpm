# Пресеты

Пресеты в Docker образе `spaceonfire/nginx-php-fpm` позволяют менять конфигурации Nginx, PHP-FPM и supervisor
для работы различных веб-приложений, а также выполнять дополнительные параметры.

## Default

Пресет по-умолчанию. Применяется еще на этапе сборки образа `spaceonfire/nginx-php-fpm` и задает базовые настройки,
как то:

-   включение отправки почты через ssmtp
-   включение директив безопасности в PHP
-   настройка базового роутинга статических файлов и PHP-скриптов
-   настройка стандартных страниц ошибок Nginx
-   запрет прямого доступа из браузера к скрытым файлам, конфигам и пакетам composer,
    скриптам выполняющимся перед запуском веб-сервера

## WordPress

Данный пресет направляет все запросы на `index.php` для работы динамических страниц,
запрещает вызывать PHP-скрипты из директории загрузок, а так же устанавливает WP CLI.
Для использования данного пресета передайте в контейнера переменную окружения `SOF_PRESET=wordpress`.

## Laravel

Данный пресет доустанавливает отсутствующие расширения PHP, необходимые для работы Laravel,
и направляет все запросы на `index.php` для работы внутреннего роутинга приложения.
Для использования данного пресета передайте в контейнера переменную окружения `SOF_PRESET=laravel`.

## 1С-Битрикс

Данный пресет делает следующее:

-   настраивает PHP для соответствия требованиям системы 1С-Битрикс
-   настраивает роутинг в Nginx как для прямого вызова PHP скриптов,
    так и для работы динамических страниц через `urlrewrite.php`
-   запрещает прямой доступ к файлам ядра
-   расширяет конфигурацию supervisor для запуска процесса cron
-   настраивает вызов "Агентов" по расписанию через cron

Для использования данного пресета передайте в контейнера переменную окружения `SOF_PRESET=bitrix`.