
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

- Not visible vs not exist.

Cover FD2 stuff:
- Look at starter code.
- Using the login in beforeEach
- saving and restoring local storage (cache and credentials) in beforeEach/afterEach.
- Running tests with `test.bash` in FD2.
  ```
  test.bash --e2e --school --live --glob="**/FD4_Application/*.e2e.cy.js" --gui
  ```
- Show `BEFORE EACH`, `TEST BODY`, `AFTER EACH` segments of the test result.
- accessing component with `get` and element within using `find`.
  - Demo with WindSurf on...
  - Do example with `DateSelector`
    - add a `data-cy`
    - show `data-cy` for component in docs
    - add a `find`
    - check value
      - notice failure...
      - change date format...
      - some trial and error here.
- Look at `CropSelector` because we have to go another level deeper to get to the input we want.
  - data-cy attribute says "component" but not a "B*" component... so have to follow it along...
  - add a .find for each level.

- Note that pre-commit hook will run any test files that were modified or all test files if page is modified.
  - If you can't get a test to pass, comment it out then commit so that you can make a PR.

- Discuss purpose of e2e tests...
  - already know that the features work
    - manually tested them.
  - protect against breaking changes in future commits.
  - extra important in projects where many developers are making changes.
  - no way anyone is going to manually test everything every time there is a change.
  - having test suite makes it possible to have high confidence everything is okay after a change.


