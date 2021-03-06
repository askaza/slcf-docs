SLCF Docs
=========

SLCF — каркас для верстки по БЭМ-методологии.

Ориентирован на статичную верстку страниц в HTML и CSS. Предоставляет стандартную файловую структура проекта, возможность писать БЭМ-разметку, простую систему шаблонов, сборку CSS раскиданного по файлам блоков, а также настроенные инструменты для оптимизации.

Используемые технологии:
- XSLT-компилятор БЭМ-разметки (BEMXML)
- Grunt для сборки проекта
- LESS-препроцессор (по вкусу)
- CSSO для оптимизации CSS

#### Файловая структура проекта

В корне проекта находятся 4 директории (assets, bundles, code, vendors).

В **assets** лежат исходные материалы для верстки, имеющие смысл в рамках всего проекта. Это может быть техническая документация, гайдлайны, что-либо еще. Обычно сюда не стоит класть PSD-макеты или другие подобные файлы.

В **code** два раздела — dev и production, содержат, соответствующие своим названиям, версии конечных файлов. Реальная работа ведется только с dev-версией проекта, в этой папке находятся как файлы, добавленные вручную, например, картинки, так и скомпилированные (html и css). Production-версия предназначена исключительно для тестирования, в ней находятся конечные (минифицированные и после оптимизаций) файлы, собираемые автоматически.

**vendors** — содержит подключения внешних зависимостей и бандлов (преимущественно), подключаются, как правило, через git submodules.
Изначально содержит:
- [SLCF Compiler](https://github.com/bivihoba/slcf-compiler) — инструмент, предназначенный для организации и написания HTML-страниц в БЭМ-терминах на BEMXML. Синтаксис BEMXML подробно описан ниже.
- [SLCF Docs](https://github.com/bivihoba/slcf-docs)
- [SLCF Nano Core](https://github.com/askaza/slcf-nano-core) – минимальный набор блоков, задекларированный в HTML, который описывает структуру HTML-документа и базовые конструкции.

**bundles** — главная папка, содержит, как это ни странно, бандлы. Бандл — коллекция деклараций блоков, страниц и всего, что относится к какой-либо конкретной части проекта. Бандлов в проекте может быть много — для разных разделов или отдельных страниц, или всего один — на весь проект сайта или приложения. Бандлы могут содержать зависимости от других банлов, в т.ч. внешних, составляя тем самым уровни переопределения для отдельных технологий. Бандлы отличаются по содержанию. По умолчанию в проекте один бандл — main. Рассмотрим его структуру в качестве примера.

### Бандл

Каждый бандл может включать папку _assets_, как правило, там лежат исходники дизайна. Структура этой директории не требует дополнительных пояснений. 

_blocks.less_ — содержит декларации блоков в технологии LESS. Необязательно, чтобы каждой БЭМ-сущности соответствовал отдельный файл. Рекомендуется производить разбиение сущностей по файлам по мере необходимости, исходя из задач проекта. 

_pages_ — содержит описания страниц в BEMXML.

templates — содержит файлы с декларациями общих шаблонов (фрагменты BEMXML), которые можно использовать на страницах.

_utilities, data-sources, i18nd_ в main-бандле приведены для полноты картины, как правило они не используются.

Файлы в корне бандла имеют важное значение, в основном это результирующие файлы технологий.

_styles.less_ — объединяет все подключения стилей бандла

_default-semantic.xml_ — содержит декларации блоков в технологии HTML.

_settings.xml_ — по сути хэлпер. Реализует уровни переопределения для BEMXML-шаблонов и HTML-семантики БЭМ-сущностей.

## BEMXML

TODO

_to be continued_
