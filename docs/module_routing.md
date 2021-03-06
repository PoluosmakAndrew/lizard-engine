## Routing.json

Глобальная настройка роутинга вашего приложения конфигурируется модулями.
Все настройки вписываются в файле *routing.json* в следующем формате:

```json
{
    "URL": "controller_name"
}
```

**URL** - поддерживает как обычный указатель вида **directory/page**, так и с указанием параметров **/directory/page/:id**.

**controller_name** -здесь нужно указать ссылку на исполняющий контроллер текущего модуля. Можно указывать вложенность, если ваши контроллеры
находятся не в корне директории controllers.

Например: структура: **MyModule -> controllers -> frontend -> create.js**, ссылка на такой контроллер
будет выглядеть следующим образом **frontend.create**.

По умолчанию контроллеры доступны только в GET запросе. Если вы желаете подключить POST или дать разрешение на любые другие запросы, то
это меняется путем добавления ключевого слова перед ссылкой на контроллер: **post:frontend.create** или **all:frontend.create**.

**Доступные протоколы:** get, post, put, delete, all

### Глобальная замена роутинга (доступно с версии 0.2.1)

Для глобальной замены роутинга в вашем приложении достаточно создать файл **routing.json** в корне вашего проекта.
Формат файла такой же как и routing.json в модулях, только в указании контролера нужно добалять и название модуля к которому он принадлежит.

Пример:
```json
{
    "/catalog": "catalog.list"
}
```

где, /catalog - ссылка для роутера, catalog.list состоит из двух частей: catalog - название модуля и list - название контроллера.

При наличии глобального роутинга - все настройки в модулях будут проигнорированы за исключением системных модулей, которые входят в LizardEngine.
А также остается неизменной настройка роутинга на главную страницу.

### Установка базового контроллера приложения

Главный контроллер приложения (домашней страницы) устанавливается в index.js параметра **main controller**

**Пример:**

```javascript
  var lizard = require('lizard-engine');

  lizard.init({
    'main controller': 'app.index'
  });

  lizard.start();
```

Где app - это название модуля, которому принадлежит контроллер, все остальные парамеры - путь к контроллеру без указание папки controllers.
К примеру если вы хотите указать заглавной страницей контроллер **MyModule -> controllers -> frontend -> create.js**, то следует указывать
 **MyModule.frontend.create**

## Документация

* [Быстрый старт](https://github.com/PoluosmakAndrew/lizard-engine/blob/master/docs/getstarted.md)
* [Архитектура приложения](https://github.com/PoluosmakAndrew/lizard-engine/blob/master/docs/architecture.md)
* [Параметры настройки приложения](https://github.com/PoluosmakAndrew/lizard-engine/blob/master/docs/configuration.md)
* **Структура Модуля:**
 * **роутинг**
 * [контроллеры](https://github.com/PoluosmakAndrew/lizard-engine/blob/master/docs/module_controller.md)
 * [компоненты](https://github.com/PoluosmakAndrew/lizard-engine/blob/master/docs/module_component.md)
 * [модель](https://github.com/PoluosmakAndrew/lizard-engine/blob/master/docs/module_model.md)
 * [шаблоны](https://github.com/PoluosmakAndrew/lizard-engine/blob/master/docs/module_template.md)
* [Плагины](https://github.com/PoluosmakAndrew/lizard-engine/blob/master/docs/plugins.md)