# 10 - FD4 - Class Notes

## Instructor ToDo Before Class

- Merge 
  - `10-FD4-Activity-Starter`
  - `10-FD4-Activity-Soln`
  - `10-FD4-Application-Starter`
  - `11-OSS1-Tutorials-Starter`

## Questions

Take questions on the Application and Tutorial that are coming in.
- Application 09-FD3
  - Solution is in `modules/farm_fd2_school/src/endpoints/FD4-Application-Starter`
  - HTML elements in the Harvest form have been converted to FarmData2 Components:
    - "Crop" `select` -> `CropSelector`
    - "Quantity" `input` -> `NumericInput`
    - "Comment" `textarea` -> `CommentBox`
    - "Submit" and "Reset" buttons -> `SubmitResetButtons`
- Tutorials 10-FD4
  - Solution is in `modules/farm_fd2_school/10-FD4-Activity-Starter`
  - Tutorial included:
    - Adding `data-cy` to all elements used in tests.
    - Test the initial page state.
    - Test that the "Add item" button shows the full form.

## Test Basics:

- Review of some of the basics of testing just to be sure they are clear.
  - Use the `modules/farm_fd2_school/10-FD4-Activity-Starter` file as example code.
  - Test basics:
    - `.cy.js` extension is a convention
      - FarmData2 conventions.
        - `e2e.cy.js` - End-to-End tests
        - `unit.cy.js` - Unit tests
        - `comp.cy.js ` - Component tests
    - The `describe` function
      ```js
      describe('description', () => { 
        // function body
      });
      ```
      - Arrow Functions
        - `() => {}`
        - A shorthand often used to define an anonymous function in place.
          - There are additional variants of the syntax.
          - Has a different behavior with regard to the implicit `this` parameter, which are not important to us here.
          - See the [MDN Arrow Function Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) for all of the details.
    - The `it` function
      ```js
      describe('description', () => { 
        it('description1', () => {
          // test body 1
        });

        it('description2', () => {
          // test body 2
        });
      });
      ```
      - Keeping the `()` and `{}` straight on these can be the trickiest part.
      - Particularly if there are `()` and `{}` inside the `it`.

## Test Commands, Assertions and Actions

Cypress provides commands, assertions and actions.  These are summarized in the [Cypress Command Reference](../CypressReference.md).

### Commands
- The `get` command attempts to find an element in the page.
  - If the element is not found within a timeout period (4s by default), the test will fail.
- The `visit` command takes the browser to the URL of the page to be tested.

### Assertions
- The `should` function is used to check an assertion.
  - If the assertion becomes `true` during the timeout period, the test passes. 
  - If the assertion remains `false` through the entire timeout period, the test fails.
  - When making multiple assertions about an element, multiple `.should(...)` assertions can be chained together.
    ```js
    cy.get(...)
      .should(...)
      .should(...);
    ```
- Some common areas of confusion in making assertions in Cypress testing include:
  - "Visibility" vs. "Existence"
    - Some tests will check whether elements exists and/or are visible.
    - Elements hidden by a `v-if` are not in the DOM do not exist and thus are not visible.
      - However, because they do not exist the assertion `.should('not.be.visible')` will fail.
      - Instead the assertion `.should('not.exist')` should be used.
  - "Text" vs. "Value"
    - Assertions are made about the `text` contained in page elements (`<div>`, `<span>`, `<p>`, `<h1>`, ...).
      - E.g. `.should('have.text', 'blah')`
    - Assertions are made about the `value` of input elements (`<input>`, `<textarea>`, `<select>`).
      - E.g. `.should('have.value', 'blah')`
  - Radio Buttons and Check Boxes
    - Assertions about the state of a radio button or check box are made using `is.checked` or `is.not.checked`.
      - E.g. `.should('be.checked')`

### Actions
- Cypress provides actions that simulate the user interacting with the page (e.g. clicking, typing, etc.).
  - The actions are all listed in the command summary.

## FarmData2 E2E Tests

Testing within FarmData2 uses all of that but also has a few other details that we'll need to know about.

- Use `modules/farm_fd2_school/src/entrypoints/FD4_Application/harvest.e2e.cy.js` as the example.
- Look at:
  - The `beforeEach` function.
    - Runs before each `it` and is used to factor out code that would be included at the start of every test.
  - The `afterEach` function.
    - Runs after each `it` and has a similar purpose.
  - The `restoreLocalStorage`, `restoreSessionStorage` functions combine with the `saveLocalStorage` and `saveSessionStorage` functions to preserve the browser storage between tests.
    - Cypress clears this storage between tests.
    - But the `farmosUtil` library uses this storage to cache credentials and API responses.
    - So we have to save and restore it to have it persist across tests.
    - Because of the caching, this speeds up the tests significantly!
  - The `login` and `visit` functions are used in `beforeEach` here because all tests in the file use the same page.
    - Could login using the login page and Cypress commands. But that would be much slower.

### Running tests in FarmData2

FarmData2 uses the `test.bash` script to run tests. This script handles some extra configuration and details that aren't handled by `npx cypress open`.

Run the tests with the command:
  ```
  test.bash --e2e --school --live --gui
  ```
  - The parts of the command are:
    - `--e2e` indicates End-To-End tests.
    - `--school` indicates we are testing the `school` module.
    - `--live` indicates that the live farmOS server should be used instead of development server.
    - `--gui` indicates that the tests should be run in the Cypress Test Runner.
  - Scroll around to find `FD4_Application/harvest.e2e.cy.js`
    - Click to run that test.
    - It will fail.
- If time seems good can also show:
  - The `--glob` parameter allows us to run only test that match a particular file path pattern.  For example:
    ```
    --glob="**/FD4_Application/*.e2e.cy.js"
    ```
    - Adding this to the command will run only test files that end in `e2e.cy.js` that are within the `FD4_Application` directory.
    - Can save scrolling around.
  - Running headless.
    - If we omit the `--gui` parameter the tests will run without the Cypress Test Runner.
    - This is called running _headless_. 

### Accessing Elements inside of Components

In FarmData2 it is often the case that the elements needed for a test are not in the page itself. Instead they are contained within a Vue component. Thus, we need a way to access elements that are inside of a component.

Let's look at testing the `DateSelector` as an example:
  - add a `data-cy=harvest-date` to the `DateSelector` in `App.vue`
  - change `data-cy` in the test file and add `.should('have.value', '2019-06-15');`
    ```js
    cy.get('[data-cy="harvest-date"]')
      .should('have.value', '2019-06-15');
    ```
    - This test will fail because `DateSelector` is a component and doesn't have a `value`.
  - Instead we actually need to get the date `input` element that is inside the `DateSelector` component.
    - Let's look at the documentation for the `DateSelector` component.
      - This is where that table of `data-cy` values is useful.
      - The table shows the `data-cy` attributes that are defined on the elements inside of the component.
        - e.g. `date-label`, `date-required`, `date-input` ect.
    - We want the `date-input`.
    - To get the `date-input` we will use the `find` function as follows:
      ```js
      cy.get('[data-cy="harvest-date"]')
        .find('[data-cy="date-input"]')
        .should('have.value', '2019-06-15');
      ```
    - This test will now pass.
 - Might also notice that now the Cypress Test Runner has different segments of the output for:
    - `BEFORE EACH`
    - `TEST BODY`
    - `AFTER EACH`

#### Multiply Nested Components

Sometimes FarmData2 components have other components embedded within them.  When this happens you have to use multiple calls to `find`.
- Look at the `CropSelector` documentation.
  - The `data-cy` for `crop-selector` refers to a `SelectorBase` component.
  - `SelectorBase` is also a FarmData2 component.
- Look at the `SelectorBase` documentation.
  - The `data-cy` for `selector-input` is the one we want.
- So the command to check the crop selector might be something like:
  ```js
  cy.get('[data-cy="harvest-crop"]')
    .find('[data-cy="crop-selector"]')
    .find('[data-cy="selector-input"]')
    .should(...);
  ```
  - Assuming the `data-cy` for the `CropSelector` has the value `harvest-crop`.

## Pre-Commit Hook

- Note that pre-commit hook that runs whenever you commit...
  - Now it will run any test files that were modified or all test files if page is modified.
  - If a test fails, the commit will be stopped.
  - If you can't get a test to pass
    - Comment it out then commit so that you can make a PR.

## Why have E2E Tests?

If we test the page manually and already know that it works, why do we need to write the E2E tests?

- They are there to protect us against breaking changes in future commits.
  - extra important in projects where many developers are making changes.
  - no way anyone is going to manually test everything every time there is a change.
  - having test suite makes it possible to have high confidence everything is okay after a change.

## What to Test

- Not every last excruciating detail.
- Not things that are tested by other tests.
  - E.g. Test adding an item, will need to click "Add Item", so it is not necessary for that test to check the visibility of all of the elements again because:
    - we already tested that in the earlier test.
    - we will actually be using Cypress actions on those elements, so if they don't exist the test will fail anyway.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)