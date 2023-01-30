# Стандарты разработки 
Репозиторий с описанием стандартов разработки и обучения кафедры ИУ5

# Требования и стандарты для разработки систем кафедры v0.2


### Требования к проектированию систем
1. Макет интерфейса в Figma для компонентов MUI. [Инструкция](/docs/Tutorial_MUI.pdf) по Figma. [Шаблон](https://www.figma.com/file/ieCIVTZ4Vh10rEajxI2Gic/UI-kit--ИУ5?node-id=0%3A1&t=iahz07OWWtQtEonS-0) с компонентами ИУ5/ГУИМЦ
2. Даталогическая ER диаграмма для базы данных PostgreSQL
3. Описание методов и полей веб-сервисов в процессе проектирования системы. Совместное обсуждение бекендом и фронтендом форм по макету Figma и составление списка методов
4. Минимизация нагрузки на сервер. Сервер только для хранения данных, вычисления нужно переносить на клиент.
5. По причине минимальной нагрузки на сервер требуется использовать `ONNX runtime` для моделей нейронных сетей. И деплой моделей на клиенте
6. При проектировании необходимо соблюдать правило: `1 репозиторий` - `1 контейнер` - `1 сервис`
7. Документирование проекта диаграммами UML. В первую очередь развертывание
8. В документации к проекту требования по нагрузке и количеству пользователей

### Требования к процессу разработки
1. Использование SSO и Redis для авторизации
2. Unit тесты для ключевого функционала приложения, особенно для алгоритмов расчетов
3. Документирование веб-сервисов после реализации в swagger.
4. Для развертывания обязательно наличие проекта в gitlab bmstu.codes
5. Для всех репозиториев должны быть указаны требуемые пакеты (см подробное описание к стеку)
6. Для развертывания новых сервисов в инфрастуктуре кафедры обращаться к Каневу Антону

### Требования к стеку технологий

#### Фронтенд. Подробное [описание](/details/React.md) 
1. React
2. Менеджер состояний Redux
3. Визуальные компоненты MUI
4. Nginx

#### Бекенд, веб-сервисы
1. Первый вариант. Django Rest Framework. Подробное [описание](/details/Python.md)
- DRF используется в сервисах с ML
2. Второй вариант. Golang. Подробное [описание](/details/Golang.md)
- Golang используется в нагруженных сервисах

#### Хранилище. Подробное [описание](/details/store.md) 
- Реляционная СУБД PostgreSQL
- Резидентная БД Redis для сессий, кеширования данных
- Объектное хранилище S3 Ceph
- Очередь Apache Kafka

#### Авторизация
1. Единый подход к авторизации (через JWT)
2. Дополнительно использование SSO Электронного Университета в 2023 [пример](https://bmstu.codes/iu5/infrastructure/examples/-/tree/master/python/oauth-client)

#### Инфраструктура и развертывание. Подробное [описание](/details/sre.md) 
1. ОС Ubuntu 20.04
2. Мониторинг Prometheus + Grafana
3. Пайплайны развертывания CI в GitLab bmstu.codes
4. Контейнеры docker compose в настоящее время, Kubernetes в 2023
5. Ansible
6. Nginx
7. Для деплоя необходимо соблюдать правило: `1 репозиторий` - `1 контейнер` - `1 сервис`

# Стандарты ПО для использования в учебном процессе
### Требования к Linux студентов и компьютеров университета

* [Обсуждение](https://github.com/iu5git/Standards/issues/1)
* [Ссылка для скачивания Linux и требуемые пакеты](/Linux/Linux.md)

1. Ubuntu 20.04 + docker
2. Python 3.9
3. IDE PyCharm, WebStorm, Visual Studio Code (приоритет)
4. Anaconda
5. RStudio
6. СУБД PostgreSQL

