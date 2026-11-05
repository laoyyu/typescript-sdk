---
'@modelcontextprotocol/node': patch
---

`toNodeHandler` releases a response stream as soon as the client disconnects, instead of waiting for the next chunk to be written. An idle stream — an SSE stream between keep-alive writes — used to stay registered for up to the whole keep-alive interval, so reconnects were answered `409 Conflict` and a client could miss the rest of the session's notifications.
