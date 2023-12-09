# Gulp Build
>
> Сборка стилей, скриптов и шрифтов в бандлы с помощью Gulp
>

Конфиг для сборки расположен в файле `gulpfile.js`.

## Gulp плагины

### gulp-load-plugins

```javascript
const plugins = require('gulp-load-plugins')();`
```

Вместо того, чтобы указывать каждый плагин, **gulp-load-plugins** выполнит поиск файла `packages.json` и автоматически добавит плагины как `plugins.pluginName()`.

Например плагин `gulp-concat` будет доступен по пути `plugins.concat`.

### gulp-sass

```javascript
const sass = plugins.sass(require('sass'));
```

Плагин gulp-sass позволяет использовать компилятор Sass в Gulp task.

Используется компилятор DartSass из пакета `sass`:

```javascript
require('sass');
```

### Остальные

Список остальных плагинов можно найти в файле `packages.json`.

* **gulp-concat** - Объединение файлов - конкатенация
* **gulp-debug** - Показывает какие файлы проходят через конвейер Gulp.
* **gulp-notify** - Выводит ошибки при сборке Gulp в виде системных сообщений
* **gulp-plumber** - Дает возможность продолжить работу gulp при ошибке в коде и формирует вывод об ошибке
* **gulp-postcss** - позволяет использовать PostCss плагины
* **gulp-rename** - Переименование файлов
* **gulp-sass-vars** - Ввод переменных в файлы sass из объекта js
* **gulp-sourcemaps** - Создает карту подключений файлов css и js

## PostCss плагины

```javascript
const postcssPlugins = [
    require('autoprefixer')(),
    require('postcss-sort-media-queries')(),
    require('cssnano')(),
];
```

* **autoprefixer** - Анализ CSS и добавлене префиксов поставщиков в правила CSS, используя значения из Can I Use. Использует `browserslist`.

* **postcss-sort-media-queries** - Плагин для сортировки и объединения медиазапросов CSS с использованием методологий mobile first / desktop first.

    ```javascript
    require('postcss-sort-media-queries')({
        sort: 'mobile-first', // default value
    })
    ```

* **cssnano** - сжатие файла (удаление комментариев, объединение правил и тд.). Использует `browserslist`.

### browserslist

Список целевых браузеров для плагинов задается с помошью **Browserslist** в конфиг файле `.browserslistrc` в корне проекта или путем добавления ключа `browserslist` в ваш `package.json`

Конфиг в файле `.browserslistrc`:

```text
# все браузеры, процент использвоания которых больше 0.5
> 0.5%
# последние 2 версии каждого браузера которые используются
last 2 versions and > 0% 
# последняя версия расширенной поддержки Firefox
Firefox ESR
# браузеры без официальной поддержки или обновлений в течение 24 месяцев (IE 11, IE_Mob 11 и др.)
not dead
```
