# DivyaOS

DivyaOS is an AI-native operating environment on Linux with chat-first control.

## Completed now
- FastAPI backend with endpoints: chat/workflow/execute/tools/analytics/memory search/health/ready/automation.
- Planner → ModelManager → Executor orchestrated flow.
- Mandatory tool system (file/terminal/app/browser/clipboard/notification).
- DivyaFS + memory + tracking + automation + plugin loading.
- React + Tauri UI shell with Chat, Dashboard, File Explorer, Floating Assistant.

## API
- `GET /healthz`
- `GET /readyz`
- `GET /launch-check`
- `POST /chat`
- `POST /workflow`
- `POST /execute`
- `POST /memory/search`
- `GET /analytics`
- `POST /automation/schedule`
- `POST /automation/trigger`
- `GET /tools`

## Launch
```bash
pip install -r backend/requirements.txt
uvicorn backend.main:app --reload
```

```bash
cd gui
npm install
npm run dev
```

## Safety and behavior
- Structured AI action format: `{"thought":"...","action":"tool_name","args":{}}`
- Dangerous operations require `confirm_dangerous=true`.
- Terminal tool blocks high-risk destructive commands.
- All actions logged to `/divya/logs/actions.jsonl`.

## Next implementation plan
1. Add real semantic embeddings in DivyaFS (currently hook-level index only).
2. Add websocket streaming for chat + action trace updates.
3. Add full permission prompt UX in GUI before dangerous execution.
4. Add richer planner decomposition for multi-step workflows (download cleanup, project bootstrap, backups).
5. Add CI workflow to install deps and run tests automatically.
