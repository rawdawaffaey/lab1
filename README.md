# Practice Assignment 1 — Filter & Search Todos

## What I implemented
- Backend: modified `getTodos` in `controllers/todoController.js` to read
  `req.query.done` and build a conditional filter object, passed into
  `Todo.find(filter)`. No `done` param returns all todos, unchanged from
  the original behavior.
- Frontend: updated `fetchTodos` in `src/api/todos.js` to accept an
  optional filter and pass it as a query param via axios. Added filter
  state in `App.jsx` with `useEffect` re-fetching on change. Added
  All / Active / Done buttons above the todo list.

## Design choice
Implemented server-side filtering (re-fetching with a query param) rather
than client-side filtering, to practice passing query params end to end.
Trade-off: server-side means a network round trip on every filter change,
but keeps the client from holding/filtering the full dataset — better if
the todo list grows large. Client-side would feel snappier for small lists
since there's no re-fetch, but doesn't scale as well.