
Cover structure of a test file.
- .cy.js is convention
  - e2e.cy.js
  - unit.cy.js
  - comp.cy.js 
  - are FarmData2 conventions.
- describe
- it
- "Arrow functions"
  - () => {}
  - shorthand for creating a function.
  - with some limitations that aren't particularly important to us here.
  
- Show the beforeEach? 
  - Move the visit there?
  
Discuss what to test...
- Not every last excruciating detail.
- Not things that are tested by other tests.
  - E.g. Test adding an item, will need to click "Add Item", not necessary to check for all elements again.  Two reasons:
    - Already tested that.
    - Will be using many elements, so if they don't exist the test will fail anyway.
- 

Cover FD2 stuff:
- Show an example.
- Using the login in beforeEach
- saving and restoring local storage (cache and credentials) in beforeEach/afterEach.
- finding data-cy values in the docs.
- accessing component with `get` and element within using `find`.
- Note that pre-commit hook will run any test files that were modified or all test files if page is modified.

- Maybe show Windsurf in VSCodium?
  - Have it generate some of the test lines?

- Running tests with `test.bash` in FD2.
  - with `-gui`
  - headless
  - use `glob`
  