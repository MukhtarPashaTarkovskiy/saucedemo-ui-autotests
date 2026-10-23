# 🧪 SauceDemo — UI Test Automation

Проект автоматизации UI-тестирования учебного интернет-магазина [SauceDemo](https://www.saucedemo.com/) на Java с использованием Selenium WebDriver и TestNG.

## 🛠 Технологический стек

- **Java 17** — язык программирования
- **Selenium WebDriver** — автоматизация браузера
- **TestNG** — запуск тестов, проверки, DataProvider
- **Maven** — управление зависимостями и сборкой
- **Page Object Model** — организация взаимодействия со страницами
- **Allure Report** — отчёты о результатах тестирования
- **GitHub Actions** — CI
- **PostgreSQL / JDBC** — отдельный тест подключения к БД
- **WebDriverManager** — управление драйверами браузеров

## ✅ Реализованные тесты

### Авторизация — `LoginTest`

- Успешная авторизация с разными тестовыми пользователями
- Проверка перехода в каталог товаров
- Авторизация с неверным логином или паролем
- Проверка обязательности заполнения полей
- Проверка сообщения для заблокированного пользователя
- Параметризация сценариев через TestNG DataProvider

### Каталог — `ProductsTest`

- Добавление товаров в корзину
- Проверка отображения корзины
- Проверка количества добавленных товаров
- Проверка оформления счётчика корзины

### Корзина — `CartTest`

- Проверка отображения добавленных товаров
- Проверка количества товаров
- Проверка соответствия названий товаров

### Работа с БД — `DbTest`

- Подключение к PostgreSQL через JDBC
- Выполнение SQL-запроса к тестовой таблице

Тест БД является отдельной демонстрацией работы с JDBC и не проверяет внутреннюю базу SauceDemo.

## 🏗 Архитектура проекта

Проект использует паттерн **Page Object Model**.

- `pages` — классы страниц приложения
- `tests` — тестовые сценарии и базовый тестовый класс
- `user` — модель пользователя и фабрика тестовых пользователей
- `utils` — конфигурация и TestNG Listener
- `database` — подключение к PostgreSQL
- `enums` — перечисления для тестовых данных

## 🚀 Запуск тестов

**Требования:** JDK 17, Maven, установленный Chrome или Firefox.

Клонирование:

```bash
git clone https://github.com/MukhtarPashaTarkovskiy/saucedemo-ui-autotests.git
cd saucedemo-ui-autotests
```

Запуск Maven:

```bash
mvn clean test
```

Для теста `DbTest` необходима переменная окружения `NEON_DB_PASSWORD` с действительными учётными данными тестовой БД.

Запуск отдельных наборов TestNG:

```bash
mvn test -Dsurefire.suiteXmlFiles=src/test/resources/smoke_tests.xml
```

```bash
mvn test -Dsurefire.suiteXmlFiles=src/test/resources/cross_browser.xml
```

## 📊 Отчётность и CI

В проекте используются аннотации Allure (`@Epic`, `@Feature`, `@Story`, `@Severity`, `@Step`).

При падении UI-теста TestNG Listener пытается приложить скриншот страницы к отчёту.

GitHub Actions настроен на запуск Maven-тестов при `push` и `pull_request` в ветку `main`, а также вручную. Секрет для подключения к Neon передаётся через GitHub Actions Secrets.

## 🎯 Цель проекта

Продемонстрировать практические навыки разработки автоматизированных UI-тестов на Java: Page Object, параметризация, проверки пользовательских сценариев, работа с браузерами, отчётность и CI.

---

**Автор:** [MukhtarPashaTarkovskiy](https://github.com/MukhtarPashaTarkovskiy)