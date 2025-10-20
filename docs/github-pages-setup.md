# Настройка GitHub Pages для MkDocs

## Пошаговая инструкция по настройке GitHub Pages

### 1. Настройка репозитория

1. Перейдите в настройки репозитория: `Settings` → `Pages`
2. В разделе `Source` выберите `GitHub Actions`
3. Убедитесь, что файл `.github/workflows/docs.yml` присутствует в репозитории

### 2. Настройка защищенных веток

1. Перейдите в `Settings` → `Branches`
2. Нажмите `Add rule` для ветки `main`
3. Настройте правила:
   - ✅ `Require a pull request before merging`
   - ✅ `Require approvals` (количество участников команды - 1)
   - ✅ `Dismiss stale PR approvals when new commits are pushed`
   - ✅ `Require review from code owners`
   - ✅ `Restrict pushes that create files larger than 100 MB`

### 3. Настройка прав доступа

1. Перейдите в `Settings` → `Actions` → `General`
2. В разделе `Workflow permissions` выберите:
   - ✅ `Read and write permissions`
   - ✅ `Allow GitHub Actions to create and approve pull requests`

### 4. Проверка работы CI/CD

После настройки при каждом push в ветку `main` или `gh-pages`:
1. GitHub Actions автоматически запустит сборку документации
2. Документация будет развернута на GitHub Pages
3. URL сайта: `https://username.github.io/repository-name/`

### 5. Локальная разработка

Для локальной разработки документации:

```bash
# Клонирование репозитория
git clone https://github.com/username/repository-name.git
cd repository-name

# Создание виртуального окружения
python -m venv .venv
source .venv/bin/activate  # Linux/Mac
# или
.venv\Scripts\activate     # Windows

# Установка зависимостей
pip install -r requirements.txt

# Запуск локального сервера
mkdocs serve

# Открыть в браузере: http://127.0.0.1:8000
```

### 6. Структура файлов для MkDocs

```
docs/
├── index.md              # Главная страница
├── contribution.md       # Руководство по работе
├── github-pages-setup.md # Данная инструкция
└── content/
    └── questionnaire.md  # Анкета для заказчика
```

### 7. Настройка темы Material

Тема Material уже настроена в `mkdocs.yml` с поддержкой:
- Темной и светлой темы
- Поиска
- Навигации
- Адаптивного дизайна

### 8. Устранение проблем

#### Проблема: Документация не отображается
**Решение:**
1. Проверьте, что в настройках Pages выбран источник `GitHub Actions`
2. Убедитесь, что workflow файл `.github/workflows/docs.yml` присутствует
3. Проверьте логи GitHub Actions в разделе `Actions`

#### Проблема: Ошибки сборки MkDocs
**Решение:**
1. Проверьте синтаксис файлов Markdown
2. Убедитесь, что все ссылки в `mkdocs.yml` корректны
3. Проверьте, что все файлы из навигации существуют

#### Проблема: Не работает поиск
**Решение:**
1. Убедитесь, что в `mkdocs.yml` включен плагин `search`
2. Проверьте, что в навигации указаны все страницы

### 9. Автоматическое обновление

Документация автоматически обновляется при:
- Push в ветку `main`
- Push в ветку `gh-pages`
- Слиянии Pull Request в `main`

### 10. Мониторинг

- Проверяйте статус сборки в разделе `Actions`
- URL сайта: `https://username.github.io/repository-name/`
- Время развертывания: обычно 1-3 минуты

---

*Для получения дополнительной помощи обратитесь к [официальной документации MkDocs](https://www.mkdocs.org/) и [GitHub Pages](https://pages.github.com/).*
