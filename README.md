# Фреймворк для автоматизации тестирования сайта и мобильного приложения "Pikabu"
> <a target="_blank" href="https://www.pikabu.ru/">pikabu.ru</a>

![main page screenshot](pictures/base_page_web.jpg)

----

### Особенности проекта

* Оповещения о тестовых прогонах в Telegram
* Отчеты с видео, скриншотом, логами, исходной моделью разметки страницы
* Сборка проекта в Jenkins
* Отчеты Allure Report
* Интеграция с Allure TestOps
* Запуск web/UI автотестов в Selenoid
* Запуск mobile автотестов в BrowserStack
* Для запуска mobile автотестов используется Appium

### Список проверок, реализованных в web/UI автотестах

- [x] Проверка фильтрации
- [x] Проверка сортировки
- [x] Проверка функциональности логотипа 
- [x] Проверка регистрации пользователя
- [x] Проверка выполнения поиска
- [x] Проверка функциональности добавления статьи
- [x] Проверка раздела "Блоги"
- [x] Проверка наличия элементов для сторонней авторизации

### Список проверок, реализованных в mobile автотестах

- [x] Проверка фильтрации
- [x] Проверка поиска 
- [x] Проверка регистрации пользователя

----

### Используемый стэк

<img title="Python" src="pictures/icons/python-original.svg" height="40" width="40"/> <img title="Pytest" src="pictures/icons/pytest-original.svg" height="40" width="40"/> <img title="Jira" src="pictures/icons/jira-original.svg" height="40" width="40"/> <img title="Allure Report" src="pictures/icons/Allure_Report.png" height="40" width="40"/> <img title="Allure TestOps" src="pictures/icons/AllureTestOps.png" height="40" width="40"/> <img title="GitHub" src="pictures/icons/github-original.svg" height="40" width="40"/> <img title="Selenoid" src="pictures/icons/selenoid.png" height="40" width="40"/> <img title="Selenium" src="pictures/icons/selenium-original.svg" height="40" width="40"/> <img title="Selene" src="pictures/icons/selene.png" height="40" width="40"/> <img title="Pycharm" src="pictures/icons/pycharm.png" height="40" width="40"/> <img title="Telegram" src="pictures/icons/tg.png" height="40" width="40"/> <img title="Jenkins" src="pictures/icons/jenkins-original.svg" height="40" width="40"/> <img title="Appium" src="pictures/icons/appium.svg" height="40" width="40"/> <img title="BrowserStack" src="pictures/icons/browserstack.svg" height="40" width="40"/>

----

### Локальный запуск автотестов

#### Для запуска web/UI автотестов выполнить в cli:
> [!NOTE]
> Ключ выбора версии `--browser-version` не обязателен
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pytest --browser-version=100 ./tests/web/
```

#### Для запуска mobile автотестов выполнить в cli:
> [!NOTE]
> Ключ `--context` не обязателен, по умолчанию тесты будут запущены на BrowserStack
* Для запуска на реальном устройстве указать ключ `--context=local_real_device`
* Для запуска на виртуальном устройстве указать ключ `--context=local_real_device`
* Для запуска на BrowserStack указать ключ `--context=bstack`

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pytest --context=bstack ./tests/mobile/
```

#### Для запуска всех автотестов выполнить в cli:

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
pytest -s -v
```

#### Получение отчёта:
```bash
allure serve build/allure-results
```

----

### Проект в Jenkins
> <a target="_blank" href="https://jenkins.autotests.cloud/job/jenkins_pikabu_tests/">Ссылка</a>

#### Параметры сборки
> [!NOTE]
> Параметры сборки не обязательны
```python
ENVIRONMENT = ['DEV', 'PROD'] # Окружение
COMMENT = 'comment' # Комментарий
```
#### Запуск автотестов в Jenkins
1. Открыть <a target="_blank" href="https://jenkins.autotests.cloud/job/jenkins_pikabu_tests/">проект</a>

![jenkins project main page](pictures/jenkins_project_main_page.png)

2. Нажать "Build with Parameters"
3. Из списка "ENVIRONMENT" выбрать любое окружение
4. В поле "COMMENT" ввести комментарий
5. Нажать "Build"

![jenkins_build](pictures/jenkins_build.png)

----

### Allure отчет
#### <a target="_blank" href="https://jenkins.autotests.cloud/job/jenkins_pikabu_tests/14/allure/">Общие результаты</a>
![allure_report_overview](pictures/allure_report_overview.png)

#### <a target="_blank" href="https://jenkins.autotests.cloud/job/jenkins_pikabu_tests/14/allure/#suites">Результаты прохождения теста</a>

![allure_reports_behaviors](pictures/allure_reports_suites.png)

#### <a target="_blank" href="https://jenkins.autotests.cloud/job/jenkins_pikabu_tests/14/allure/#graph">Графики</a>


![allure_reports_graphs](pictures/alluere_reports_graphs_2.png)

----

### Интеграция с Allure TestOps
> <a target="_blank" href="https://allure.autotests.cloud/launch/40223">Ссылка на проект</a>

#### <a target="_blank" href="https://allure.autotests.cloud/project/4298/dashboards">Дашборд с общими показателями тестовых прогонов</a>

![allure_test_ops_dashboards](pictures/allure_testops_dashboards.png)

#### <a target="_blank" href="https://allure.autotests.cloud/project/4298/launches">История запуска тестовых наборов</a>

![allure_testops_launches](pictures/allure_testops_launches.png)

#### <a target="_blank" href="https://allure.autotests.cloud/project/4298/test-cases?treeId=0">Тест кейсы</a>

![allure_testops_suites](pictures/allure_testops_suites.png)

----

### Оповещения в Telegram
![telegram_allert](pictures/telegram_allert.png)

----

### Интеграция с Jira
> <a target="_blank" href="https://jira.autotests.cloud/browse/HOMEWORK-1288">Ссылка на проект</a>

![jira_project](pictures/jira_project.png)
----

### Видео прохождения web/UI автотеста
![autotest_gif](/pictures/autotest.gif)


----
### Видео прохождения mobile автотеста
![autotest_gif](/pictures/test_mobile_video.gif)
