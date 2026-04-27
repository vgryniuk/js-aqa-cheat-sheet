# Playwright + AI (CLI, MCP, skills)
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
