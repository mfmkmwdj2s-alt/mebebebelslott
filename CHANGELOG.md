# Changelog

## v11-design-polish

Дата: 2026-07-07

### Добавлено

- Новый блок `v11-trust-strip` под hero с короткими сервисными преимуществами.
- Новый блок `slotik-spotlight`, который визуально выделяет Слотика как помощника в каталоге.
- Информационная плашка `v11-catalog-note` перед каталогом.

### Улучшено

- Визуал карточек товаров: тени, скругления, изображение, цена, кнопка “Подробнее”.
- Визуал фильтров, быстрых чипов каталога и основных карточных блоков.
- Лёгкая премиальность первого экрана и секций без изменения структуры магазина.
- Контактный блок: добавлен MAX.

### Не менялось

- Логика Слотика.
- Логика корзины и избранного.
- Формат каталога и данные товаров.

---

# CHANGELOG — mebelslot-v10.1-slotik-bugfix

## Что изменено относительно v10

### Слотик

1. Исправлена выдача ближайших товаров, если точных вариантов в бюджете нет.
   - Пример: «Есть недорогой диван до 30000?» теперь показывает ближайшие диваны по цене, а не оставляет ответ без карточек.

2. Исправлено ложное сравнение по слову «или».
   - Пример: «Доставка до двери или подъезда?» теперь обрабатывается как вопрос о доставке, а не как сравнение товаров.

3. Добавлен отдельный сценарий по повреждениям, царапинам, браку и дефектам.
   - Слотик объясняет, что нужно сделать фото, проверить документы и связаться с менеджером.

4. Исправлена логика избранного.
   - Пример: «Добавь первый в избранное» теперь предлагает сохранить товар в понравившееся, а не добавить в корзину.

5. Доработаны запросы «дешевле» и «дороже» по прошлому контексту.
   - Слотик использует последнюю подборку и последний раздел.

6. Исправлено «что выбрать» для советов.
   - Пример: «Маленькая комната, что выбрать?» теперь получает консультационный ответ, а не попытку сравнить товары.

7. Добавлен нормальный сценарий «покажи похожее на первый».
   - Слотик подбирает похожие товары по relatedIds, разделу, категории, материалу и назначению.

8. Добавлена честная обработка будущих категорий.
   - Кухни, шкафы, комоды, тумбы, прихожие, детская мебель, кресла и пуфы не подменяются случайными товарами текущего демо-каталога.

## Проверка

- `node --check` для всех JS-файлов: синтаксических ошибок нет.
- Добавлен smoke-тест: `tests/run-slotik-smoke.js`.
- Контрольные запросы по 8 исправленным пунктам пройдены.


## v11.1 design fixes
- removed trust strip under hero
- extended product cards so the “Подробнее” button is fully visible
- moved/shrunk favorite button to avoid overlapping rounded image edges


## v12 catalog architecture

- Категории вынесены в `data/categories.js`.
- Добавлено дерево активных и будущих разделов каталога.
- Демо-товары обогащаются расширенными полями для будущих 100+ товаров.
- Добавлены фильтры по механизму/конструкции и наличию.
- Добавлены шаблоны и документация для будущего наполнения товарами.
- Добавлен тест архитектуры каталога.


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

## v14 — legal and launch prep

- Added legal document templates for privacy policy, personal data consent, and purchase/payment terms.
- Added `data/legal.js` as a central place for future legal details and company placeholders.
- Added `js/legal-modals.js` for opening legal documents from the footer and forms.
- Updated consultation and checkout consent text with links to the relevant legal documents.
- Added launch checklist documents in `docs/`.


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
