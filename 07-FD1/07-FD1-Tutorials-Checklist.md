- `fetchUsers` method:
  - [x] - Is declared as async.
  - [x] - Fetches users from {JSON}Placeholder API using `fetch(...)`.
  - [x] - Converts response to a JavaScript object using `json()` function.
  - [x] - Contains commented out practice accessing properties.
  - [x] - Assigns the retrieved data to the `userList` Vue `data` property.
- `created` lifecycle hook:
  - [x] - `created` is declared as `async`
  - [x] - Calls and `await`s `fetchUsers`
- [x] - Removes the "Fetch Users" and "Clear Users" buttons.
- [x] - Removes the `clearUsers` method.
- [x] - Work is spread across multiple commits.


Common Feedback

- The `created` lifecycle hook calls the `fetchUsers` method which is `async` so the `created` lifecycle hook should also be `async`.
- The `fetchUsers` method is `async` so when it is called you should use `await`.