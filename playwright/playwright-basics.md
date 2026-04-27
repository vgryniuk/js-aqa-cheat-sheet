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
## UI Mode (запуск тестів)
**UI Mode в Playwright** — це інтерактивний режим запуску тестів із графічним інтерфейсом, відкриває локальний UI, де видно список тестів, їх статуси, логи та кроки виконання. Це по суті “IDE для тестів”: можна запускати окремі тести, фільтрувати їх, дивитися trace, screenshots і мережеві запити. UI Mode показує виконання крок за кроком, включно з DOM-станом і таймлайном. 

Запуск `npx playwright test --ui`.
---

## Playwright + AI (CLI, MCP, skills)
**Playwright MCP (Model Context Protocol server)** — це сервер, який дає LLM-агентам доступ до браузера через Playwright. Його задача, дозволити AI взаємодіяти з вебсторінками через структуровані команди. Як він працює: сторінка перетворюється в accessibility snapshot, елементи отримують ідентифікатори (refs), далі AI працює з refs.

**Playwright CLI** — це командний інтерфейс для браузерної автоматизації, створений спеціально для coding agents (Claude Code, Copilot тощо), які працюють з великими кодовими базами. Playwright CLI дає агенту можливість керувати браузером через компактні команди без перевантаження контексту. CLI працює як послідовність команд у shell.

### Playwright CLI vs Playwright MCP 
| Характеристика | Playwright CLI | Playwright MCP               |
| -------------- | -------------- | ---------------------------- |
| Тип роботи     | shell commands | structured tool calls        |
| Контекст       | мінімальний    | більший (snapshots + schema) |
| Token usage    | низький        | вищий                        |
| Призначення    | coding agents  | exploratory / agentic loops  |
| Mode           | headless       | headed by default            |

### Playwright AI (MCP + CLI) workflow
```
MCP → дослідження UI
↓
AI → генерує тест
↓
CLI → запускає тест
↓
fail?
   ↓
MCP → перевірка UI змін
↓
AI → фікс
↓
CLI → rerun
↓
stable → CI
```









