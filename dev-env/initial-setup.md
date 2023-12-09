# Initial Setup

>
> Установка необходимых инструментов и настройка VS Code
>

1. [Node Js](#1-node-js)
2. [NPM](#2-npm)
3. [VSCode Extentions](#3-vscode-extentions)

## 1. Node JS

 [Установить или обновить][nodejsinstall] Node JS

 Если уже установлен, проверить версию

 ```Shell
 node -v
 ```

 Минимальная версия `v18.12.1`

 *Документация майкрософта <https://code.visualstudio.com/docs/nodejs/nodejs-tutorial>*

## 2. NPM

### Проверить npm

NPM устанавливается вместе с nodejs. Если npm был уже установлен, проверить версию

```Shell
npm -v
```

Минимальная версия `9.6.x`

При необходимости обновления, использовать [установщик nodejs][nodejsinstall] необходимой версии.

### Запустить установку пакетов

```Shell
npm install
```

> Если пакеты были уже установлены и была обновлена версия nodejs, возможно необходимо запустить команду `npm rebuild` для перекомпиляции под новую версию ([более подробно](https://docs.npmjs.com/cli/v9/commands/npm-rebuild))

### Установить gulp глобально

Если ранее была глобально устанавливлена gulp, нужно удалить старую версию.

Чтобы проверить версию, выполните:

```Shell
gulp -v
```

Минимальная проверенная версия:

```Shell
CLI version: 2.x
Local version: 4.0.x
```

Если версия меньше, удалить старую установку, выполнив:

```Shell
npm rm --global gulp
```

Теперь вы можете установить автономный интерфейс командной строки:

```Shell
npm install --global gulp-cli
```

> Подробнее об установке на [оффициальном сайте](https://gulpjs.com/docs/en/getting-started/quick-start/ 'Quick Start')

#### Ошибка запуска скрипта

> gulp : gulp.ps1 cannot be loaded because running scripts is disabled on this system.

PowerShell по умолчанию ограничивает выполнение скриптов, если мы не изменим политики выполнения.

Мы можем изменить политики выполнения, добавив args.

В VSCode вам нужно будет создать профиль оболочки с этими ARG, добавив ниже в settings.json `-ExecutionPolicy Bypass`

> (Ctrl + Shift + P и введите «settings.json»)

```Json
"terminal.integrated.profiles.windows": {
  "PowerShell": {
    "source": "PowerShell",
    "icon": "terminal-powershell",
    "args": ["-ExecutionPolicy", "Bypass"]
  }
},
"terminal.integrated.defaultProfile.windows": "PowerShell",
```

Необходимо перезапустить VS Code и терминал.

## 3. VSCode Extentions

Экстеншены для удобной работы.

### Основные

#### SCSS

* [SCSS Formatter](https://marketplace.visualstudio.com/items?itemName=sibiraj-s.vscode-scss-formatter) - форматирование SCSS
* [SCSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-scss) - автокомплит и рефакторинг SCSS
* [Some Sass: extended support for SCSS and SassDoc](https://marketplace.visualstudio.com/items?itemName=SomewhatStationery.some-sass) - полная поддержка @use и @forward, включая псевдонимы, префиксы и скрытие. Богатая документация через SassDoc. Навигация по коду в масштабах рабочей области и рефакторинг.

#### Vue

* [Vue Language Features (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.volar) - Language support for Vue 3

### Дополнительные

#### Git

* [Git Graph](https://marketplace.visualstudio.com/items?itemName=mhutchie.git-graph) - отображение дерева гита

#### Markdown

* [Markdown Preview Github Styling](https://marketplace.visualstudio.com/items?itemName=bierner.markdown-preview-github-styles) - визуализация
* [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) - разметка и проверка стиля

[nodejsinstall]: https://nodejs.org/en/download

#### Browserslist

[browserslist](https://marketplace.visualstudio.com/items?itemName=webben.browserslist) - подсветка синтаксиса в конфиг файле
