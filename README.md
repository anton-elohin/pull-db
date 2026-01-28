## История:
Разрабатывался как инструмент, для того, чтобы ddev мог тянуть базу с прода. По мере развития инструмента появилась потребность отвязать от ddev и сделать универсальным, но времени пока нет. Довольствуемся пока тем что есть 🥲

## Как использовать инструмент:

В корне проекта, в папке «.ddev» создать файл «config.remote.yaml» с примерно следующим содержимым
```yaml

environments:
  dev:
    host: dev.mysupersite.com
    ssh_port: 22
    username: cool_user_ssh
#    ssh_password: cool_user_ssh_password
    project_root: /srv/www/supersite/
    database:
      host: localhost
      port: 3306
      name: db_name
      login: db_login
      password: db_password
    ignore_tables:
      - b_event_log
      - b_search_content_stem
      - b_search_content
      - b_search_content_text
      - b_search_content_title
      - b_search_phrase
      - b_perf_error
#    add_tables:
#      - b_event_log
    files:
      - "bitrix/"
    exclude:
      - "*.tmp"
      - "*.log"
      - "cache/*"
      - "bitrix/cache/"
      - "bitrix/managed_cache/"
      - "tmp/*"
      - "local/test/"
 ```
Если не будет указан ssh_password будет использоваться ssh ключ (предпочтительный вариант). database.host и database.port тоже не обязательные
