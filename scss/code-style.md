# Соглашения по оформлению кода

При именовании классов нужно придерживаться методологии БЭМ.

## Формат

```css
.prefix-block-name_block-modifier-name, 
.prefix-block-name__element-name_element-modifier-name
```

Дефис разделяет префикс от блока, двойное нижнее подчеркивание отделяет блок от элемента, нижнее подчеркивание отделяет модификатор от блока или элемента.

Пример:

**Неправильно:**

```css
.b-nav-bar, .b-nav-bar-item
```

**Правильно:**

```css
.b-nav__bar, .b-nav__bar-item
.b-menu, .b-menu__item
```

## Виды модификаторов

* `.b-menu_top` – необходим для модифицирования блока или элемента, не зависит от состояния
* `.b-menu__item.m-active` – `m-active` добавляется в зависимости от состояния, может быть добавлено в js или на серверной стороне.

Пример:

**Неправильно:**

```css
.b-menu_top-item_primary
```

**Правильно:**

```css
.b-menu_top, .b-menu__item_primary
```

## Виды префиксов

* `g-` *(global)* префикс для глобальных вспомогательных классов. (Например, для задания невидимых элементов `.g-hidden`, центрирования `.g-align_center`)
* `l-` *(layout)* префикс для блоков разметки страницы. (Например, `.l-body`,`.l-content`)
* `b-` *(block)* префикс для выделения элементов, относящихся к структуре документа. (Например, `.b-menu`, `.b-filter`)
* `m-` *(modifier)* префикс для динамических вспомогательных классов (Например, добавление активности). Не объявляются без привязки блока. (Например, `.m-active`)
* `i-` *(interactive)* используется только для js, не используется в стилях. Именуется по blockName компонента. (Например, `.i-head`, `.i-menu`).
* `di-` *(dynamic-indents)* модификаторы отступов и размера текста по системе динамических отсутпов.

## Общие правила

* Нельзя использовать ID в селекторах.

* Нельзя стилизовать `<span>` и `<div>`

* Каждое CSS свойство/селектор должны начинаться с новой строки.

* Каскадность должна быть минимальной. Рекомендуется использовать не более двух уровней вложенности.

* При написании медиа запросов необходимо придерживаться подхода разделения медиазапросов. Сначала для блока пишутся общие стили. Потом для каждого медиа пишутся уникальные стили.

    ```css
    .b-logo__title {
        font-weight: 700;
        font-size: 20px;
    }

    @media (max-width: 735px) {
        .b-logo__title {
            align-self: center;
        }
    }

    @media (min-width: 736px) {
        .b-logo__title {
            align-self: end;
            letter-spacing: -0.04em;
        }
    }
    ```