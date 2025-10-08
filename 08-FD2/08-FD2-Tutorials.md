
- Writing data.

- JSON.stringify to create body.

- use {JSON}Placeholder
- create JSON structure
- use fetch to make a post request
  - does it produce errors if wrong JSON?
    - no
  - does it generate error if invalid endpoint
    - yes - 404
  - can send any json at all to any endpoint

- Response on success:
    - responds with 201
    - response.ok = true
- Response on failure:
    - responds with 404
    - response.ok = false

- await response.json()
  - gives id of new resource 
    - But doesn't actually create it...

  - w/o headers 
    ```
    {
      id: 101
    }
    ```
- w/ headers:
  ```
  headers: {
    'Content-type': 'application/json; charset=UTF-8',
  },
  ```
  ```
  {
    id: 101,
    title: 'foo',
    body: 'bar',
    userId: 99,
  }
  ```

## error handling with try/catch


## Putting code into functions and importing

## Using the FD2 Library Functions

- convert the fetching of crops to use a library.

<script>
import * as farmosUtil from '@libs/farmosUtil/farmosUtil';

export default {
    ...
}
</script>



## FD2 Harvest Logs

Move to hands on?

FD2 manually creating log and quantity for harvest.
Understand what a Harvest Log will be.

### Seeing log structures

### Standard Quantities





