# sccout

## 開発環境

- dev(sqlite)
  - `ln -s docker-compose_dev.yml docker-compose.yml`
  - `docker-compose up -d`
  - phpコンテナに入る `docker-compose exec php bash`
  - `find /var/www/storage -type d -print0 | xargs -0 chmod 707`
  - `touch database/database.sqlite`
  - `chmod 707 database`
  - `chmod 707 database/database.sqlite`
  - `npm install`
  - `composer install`
  - `composer run post-root-package-install`
  - `composer run post-create-project-cmd`
  - `php artisan migrate:refresh --seed`
  - `npm run watch-poll`
  - アクセスログの表示 `docker logs nginx -f`
- prod(mysql57)
  - `ln -s docker-compose_prod.yml docker-compose.yml`
  - `docker-compose up -d`
  - phpコンテナに入る `docker-compose exec php bash`
  - `find /var/www/storage -type d -print0 | xargs -0 chmod 707`
  - `npm install`
  - `composer install`
  - `composer run post-root-package-install`
  - `composer run post-create-project-cmd`
  - `php artisan migrate:refresh --seed`
  - `npm run watch-poll`
  - アクセスログの表示 `docker logs nginx -f`

## API reference create

```bash
php artisan apidoc:generate
```
