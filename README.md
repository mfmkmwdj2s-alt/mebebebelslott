# МебельСлот — v11-design-polish

Версия основана на `v10.1-slotik-bugfix`.

Цель версии: аккуратно усилить визуал сайта без смены концепции и без переработки логики Слотика.

## Что изменено

- Добавлена короткая сервисная полоса под первым экраном: подбор, цены, доставка, Слотик.
- Добавлен отдельный блок-презентация Слотика как фишки магазина.
- Улучшены карточки товаров: мягче тени, аккуратнее изображение, цена и кнопки.
- Улучшены фильтры, быстрые чипы каталога и визуальные состояния карточек.
- Добавлены маленькие информационные плашки над каталогом.
- Улучшены карточки преимуществ, доставки, отзывов и форм.
- В контактах добавлен MAX рядом с WhatsApp и Telegram.
- Логика каталога, корзины и Слотика не менялась.

## Проверка

- JS-файлы проверены через `node --check`.
- Проверены локальные пути к CSS, JS и изображениям.
- Прогнан smoke-тест Слотика из `tests/run-slotik-smoke.js`.


## v11.1 design fixes
- removed trust strip under hero
- extended product card action area and fixed details button visibility
- adjusted favorite button size/position


## v12 catalog architecture

Версия готовит каталог к будущему наполнению 100+ реальными товарами.

Добавлено:

- `data/categories.js` — дерево активных и будущих категорий;
- `data/product-template.js` — шаблон нового товара;
- расширенная нормализация товара в `data/products.js`;
- фильтры по механизму/конструкции и наличию;
- документы в `docs/` для будущего наполнения;
- тест `tests/run-catalog-architecture.js`.


## v12.1 content polish
- replaced technical catalog note labels with customer-facing copy
- expanded Slotik promo block with several example questions


## v12.2
- removed the catalog note block above the product grid completely


## v13 secure payment flow
- clarified the main purchase path: cart → checkout → protected payment page
- made email optional and labeled it for receipt/confirmation
- added payment steps and a cleaner pre-payment modal
- kept messengers as support channels, not as a replacement for online payment


## v13.1 cart/payment copy fixes
- removed the 3 payment step pills from the cart
- simplified wording around payment by removing repeated “protected/secure” phrasing
- aligned the delivery row in the cart summary


## v13.2 cart delivery fix
- removed the large delivery/payment hint block from the cart form
- left delivery only as a compact middle row in the cart summary
- aligned cart summary rows consistently

## v14 legal and launch prep

Добавлена подготовка юридического блока к будущему запуску:

- `data/legal.js` — шаблоны правовых документов и реквизитов;
- `js/legal-modals.js` — открытие документов в модальном окне;
- ссылки на документы в футере, форме консультации и корзине;
- `docs/legal-fill-checklist.md` — список данных, которые нужно заполнить перед запуском;
- `docs/legal-documents-template.md` — инструкция по редактированию документов.

Все данные в квадратных скобках нужно заменить на реальные перед публикацией.


## v14.1 modal close fix
- Fixed stray product modal close button appearing on the page in some mobile file viewers.
- Product dialog is now explicitly hidden until it is opened.


## v14.2 modal close hard fix
- removed the permanent product-modal close button from static HTML
- close button is now injected only when a product modal is opened
- product modal body is cleared on close, buy-from-modal, and request-from-modal actions


## v14.3 modal close final fix
- removed the permanent legal-modal close button from HTML
- create the legal close button only while the legal modal is open
- remove the legal close button after closing the modal
- hard-hide all inactive modal close buttons for mobile file viewers


## v15 SEO and meta prep
- Added SEO title/description using “МебельСлот — сайт мебели для дома и офиса…” wording.
- Added Open Graph/Twitter meta tags.
- Added favicon/icon files, site.webmanifest, robots.txt and sitemap.xml.
- Added basic JSON-LD markup for FurnitureStore and WebSite.
- Added SEO launch checklist docs.


## v16 final mobile audit
- changed Slotik mobile layout from bottom sheet to floating window
- added body state for opened Slotik to hide floating buttons behind the assistant
- added safe-area spacing so the input does not overlap the mobile viewer/browser interface


## v16.1 Slotik iOS keyboard fix
- added VisualViewport-based mobile sizing for Slotik
- keeps Slotik input above the iOS keyboard
- compacts the Slotik header and hides quick chips while typing


## v16.2 Slotik full-fit fix
- made Slotik use calculated visible viewport height on iPhone when keyboard is open
- added compact keyboard mode directly on the panel, not only through body class
- reduced the panel height and reserved extra bottom space for the iOS keyboard toolbar


## v16.3 Slotik open-size tweak
- Increased Slotik window height in the normal mobile state before the keyboard opens.
- Kept the compact keyboard mode from v16.2 unchanged.


## v16.4 Slotik open no-autofocus
- removed automatic input focus when Slotik opens on mobile
- Slotik now opens in the larger default state first
- compact keyboard mode starts only after the user taps the input field
