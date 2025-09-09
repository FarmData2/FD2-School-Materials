
## JSON Introduction

- JSON Intro: https://www.youtube.com/watch?v=KMLOWkGAxVc
  - 5:39
    - Python starts at 4:30 - skip it.
  - covers nested objects and nested arrays too.

## APIs

- quotable: https://github.com/lukePeavey/quotable?tab=readme-ov-file
  - good free api serves quotes.
  - https://api.quotable.io
- mess with it in the browser URL.
  - query parameters
    - https://api.quotable.io/quotes/random?limit=5&author="Winston Churchill"

## Fetching Data


## Reducing Data


## Filtering Data


- in place JS functions for then clauses?

- handling promises
- simple fetch
  - `response.json`
- lifecycle hooks.

- need something with an async function that makes an api call.
  - maybe just use fetch?
- need to call and use then / catch.


- https://jsonplaceholder.typicode.com
  - users - 10 users
  - todos - 200 todo items

  
- Suffers from CORS!!!
- close: https://jsonplaceholder.typicode.com/
  - uses wrong lifecyle hook
  - uses arrow functions - would need to introduce
    - they use just `(param => do something)`
    - or maybe first...  `(function(param) { code here })`
    - then simplify as `((param) => { code here })`
      - subtlety different.
      - How? Give link.





