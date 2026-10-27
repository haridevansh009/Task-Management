# Taskflow Frontend

React + Vite + Tailwind CSS + React Router + @dnd-kit + Axios.

    npm install
    npm run dev      # http://localhost:5173 (proxies /api -> http://localhost:5000)
    npm run build

## API contract the frontend expects
- POST /api/auth/signup | login -> { token, user: { id, name, email } }
- POST /api/auth/forgot-password { email } | reset-password { token, password }
- GET /api/tasks?q&status&priority&assignee&dateField&from&to&limit -> { tasks, total }
- GET /api/tasks/stats (same filters) -> { total, byStatus: {TODO,IN_PROGRESS,DONE}, avgSlaMs }
- POST /api/tasks, PATCH /api/tasks/:id, PATCH /api/tasks/:id/status { status }, DELETE /api/tasks/:id
- Task: { id, title, description, status, priority, assignee, dueDate, createdAt, updatedAt,
  sla: { currentMs, totalMs, stageTimeSpentMs: {TODO,IN_PROGRESS,DONE} } }  (all SLA values computed by the server)
- Reset link format: /reset-password?token=<token>
