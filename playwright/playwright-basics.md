# Playwright

**Playwright** — це open-source фреймворк для автоматизації браузерів, який використовується переважно для e2e-тестування вебзастосунків. Playwright випущений Microsoft у 2020-му році, cтворений командою, яка раніше працювала над Puppeteer з Google.

### Особливості:
* **Кросбраузерність з одного API** - один і той самий тест працює в Chromium, Firefox і WebKit.
* **Автоматичне очікування (auto-waiting)** - не потрібно вручну додавати sleep або чекати елементи — Playwright робить це сам.
* **Ізольовані контексти (browser contexts)** - кожен тест запускається в чистому середовищі (аналог incognito).
* **Selector engine** - підтримка CSS, XPath, текстових селекторів, ролей (ARIA).
* **Мережевий контроль** - можливість перехоплювати/мокати HTTP-запити.

**Базова структура тесту:**
```
import { test, expect } from '@playwright/test';

test('example test', async ({ page }) => {
  await page.goto('https://example.com');
  await expect(page).toHaveTitle(/Example/);
});
```
---

### Basic actions

| Дія                       | Опис                               |
| ------------------------- | ---------------------------------- |
| `locator.check()`         | Позначити input checkbox           |
| `locator.click()`         | Натиснути на елемент               |
| `locator.uncheck()`       | Зняти позначку з checkbox          |
| `locator.hover()`         | Навести курсор миші на елемент     |
| `locator.fill()`          | Заповнити поле форми, ввести текст |
| `locator.focus()`         | Перевести фокус на елемент         |
| `locator.press()`         | Натиснути одну клавішу             |
| `locator.setInputFiles()` | Вибрати файли для завантаження     |
| `locator.selectOption()`  | Вибрати опцію у випадаючому списку |

### Basic assertions

| Асерція                             | Опис                                  |
| ----------------------------------- | ------------------------------------- |
| `expect(locator).toBeChecked()`     | Checkbox позначений                   |
| `expect(locator).toBeEnabled()`     | Елемент (контрол) увімкнений          |
| `expect(locator).toBeVisible()`     | Елемент видимий                       |
| `expect(locator).toContainText()`   | Елемент містить текст                 |
| `expect(locator).toHaveAttribute()` | Елемент має атрибут                   |
| `expect(locator).toHaveCount()`     | Список елементів має задану довжину   |
| `expect(locator).toHaveText()`      | Текст елемента відповідає очікуваному |
| `expect(locator).toHaveValue()`     | Input-елемент має значення            |
| `expect(page).toHaveTitle()`        | Сторінка має заголовок                |
| `expect(page).toHaveURL()`          | Сторінка має URL                      |


### Auto-waiting
Playwright виконує набір перевірок “готовності до дії” перед виконанням операцій, щоб гарантувати коректну поведінку. Він автоматично очікує, поки всі необхідні перевірки пройдуть успішно, і лише тоді виконує дію. Якщо перевірки не проходять у межах заданого timeout, дія завершується помилкою TimeoutError.

| Action                                | Visible | Stable | Receives Events |	Enabled | Editable |
| ---------------------------------- | ------- | ---------- | ------------- | ---------- | ----------- |
| `locator.check()`                  | Так     | Так        | Так           | Так        | -           |
| `locator.click()`                  | Так     | Так        | Так           | Так        | -           |
| `locator.dblclick()`               | Так     | Так        | Так           | Так        | -           |
| `locator.setChecked()`             | Так     | Так        | Так           | Так        | -           |
| `locator.tap()`                    | Так     | Так        | Так           | Так        | -           |
| `locator.uncheck()`                | Так     | Так        | Так           | Так        | -           |
| `locator.hover()`                  | Так     | Так        | Так           | -          | -           |
| `locator.dragTo()`                 | Так     | Так        | Так           | -          | -           |
| `locator.screenshot()`             | Так     | Так        | -             | -          | -           |
| `locator.fill()`                   | Так     | -          | -             | Так        | Так         |
| `locator.clear()`                  | Так     | -          | -             | Так        | Так         |
| `locator.selectOption()`           | Так     | -          | -             | Так        | -           |
| `locator.selectText()`             | Так     | -          | -             | -          | -           |
| `locator.scrollIntoViewIfNeeded()` | -       | Так        | -             | -          | -           |
| `locator.blur()`                   | -       | -          | -             | -          | -           |
| `locator.dispatchEvent()`          | -       | -          | -             | -          | -           |
| `locator.focus()`                  | -       | -          | -             | -          | -           |
| `locator.press()`                  | -       | -          | -             | -          | -           |
| `locator.pressSequentially()`      | -       | -          | -             | -          | -           |
| `locator.setInputFiles()`          | -       | -          | -             | -          | -           |

---

### Test annotations

Анотації в Playwright використовуються для керування виконанням тестів без зміни логіки самого тесту. Вони дозволяють позначати тести як повільні, пропускати їх або робити виконання умовним залежно від середовища.

```
test.skip(), test.fail(), test.fixme(), test.slow()
```

`test.slow()` - збільшує timeout тесту в 3 рази.

### Умовні анотації (conditional skip)

Playwright дозволяє пропускати тести на основі умов через test.skip() або test.fixme() з логікою.
```
test('skip this test', async ({ page, browserName }) => {
  test.skip(browserName === 'firefox', 'Still working on it');
});
```


