# API Design (Reference)

`POST /ask`
- Request: `{ "question": "..." }`
- Process: retrieve top-k chunks → prompt with citations → generate answer
- Response:
```json
{
  "answer": "text with (Title p.X) citations",
  "citations": [{"title":"Syllabus.pdf","page":3,"url":null}]
}
```
