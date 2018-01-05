## php7.1 + nginx + percona/postgres + symfony4 docker image

Just clone the repo and run ```docker-compose up```, your symfony aplication should be placed in ```symfony``` directory. All nginx logs will be placed in `logs` directory.

For postgres version run ```docker-compose -f docker-compose-postgres.yml```.

After running the container, page will be available at ```http://symfony.local/```. 

Xdebug is available at `10000` port.

Requires docker-compose 1.6+

DB credentials:
* db name: symfony
* user: root
* password: root
* host: db
