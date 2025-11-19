# 11 - OSS1 - Application

In this application you will take on the role of a **contributor** by creating and testing a solution to the bug report that you have been assigned.

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize your `development` branch with the upstream `development` branch.
3. Rebuild the `school` module.
4. Create and switch to a feature branch for your work on this assignment.
5. Open the "FD2 School" -> "OSS1" page in the browser.
6. Open the `App.vue` and `harvest.e2e.cy.js` files in the `modules/farm_fd2_school/src/entrypoints/OSS1/` directory in VSCodium.
   - All of your work in fixing the bug and testing the solution should be done in these two files.

## Writing Tests First

A common approach in fixing a bug is to begin by writing one or more automated tests. These tests should follow the "Steps to Reproduce" the bug and check for the "Expected Behavior." Because the bug exists, these tests will fail when they are first written. Then later when the implementation code is modified to fix the bug, these tests should pass. This transition from failing tests to passing tests provides a clear indication of when the bug has been fixed.

1. Review the bug report assigned to you and identify each set of "Steps to Reproduce" and "Expected Behavior" that correspond to a test to be written. These may appear in the bug description or in the comments on the issue.
2. For each test that you identified in step 1:
   1. Add a an `it` to the `harvest.e2e.cy.js` that performs the "Steps to Reproduce" the bug and checks that the "Expected Behavior" occurs.
   2. Run the test to ensure that it performs the correct steps and that the test fails (because the bug has not yet been fixed!).
   3. If in the process of writing the test you find that the "Steps to Reproduce" or the "Expected Behavior" are not clear, correct or complete, add a comment to the issue providing clarification.

Note: This practice of fixing bugs by writing test first is sometimes referred to as Test Driven Bug Fixing and it is closely related to the practice of Test Driven Development (TDD). If you are interested you can read a little more about both in this article on [Test-Driven Development (TDD) for bug fixes in Swift](https://www.avanderlee.com/workflow/test-driven-development-tdd-for-bug-fixes-in-swift/) by Antoine van der Lee.

### Only Running Specific Tests

It can become annoying and inefficient to run every test in `harvest.e2e.cy.js` over and over again when fixing a bug.

Cypress provides the `.only` mechanism to allow you to indicate specific `it`s within a file to run. To indicate that tests that should run by appending `.only` to their `it` as shown below.
```js
it.only('this test will run', () => {...});
it('this test will not', () => {...});
it.only('this test will also run', () => {...});
```
1. Add `.only` to the tests that you have written for the bug.

Note: The linter in VSCodium will indicate an issue on lines with the `.only`. Because using `.only` prevents some of the tests from running, we don't want to commit a test file containing `.only`s.  The test file will run fine in Cypress, but the linting issue will cause the pre-commit hook to fail, thus preventing any `.only`s from being committed.

## Fixing the Bug

Now that you have automated tests that demonstrate that the bug exists and that should pass when it is fixed, its time to fix the bug.

1. Study the code in the `App.vue` file to devise **several possible fixes** to the bug.
   - Some fixes will be better than others.
   - So avoid the urge to just start implementing the first thing that you think of.
2. Evaluate each of your fixes to determine which to implement. Consider the following criteria when evaluating each of your possible fixes:
   - It fixes the bug.
   - Only changes addressing the bug are made.
   - The changes should be as simple as possible.
   - The changes should fit with the style and logic of the existing code such that it remains cohesive, readable and understandable to others.
   - Changes do not introduce duplicate code.
   - Changes are as small and localized as possible.
3. Choose what you think is the best fix based on the above criteria.
   - Note you may have to use your judgement as some criteria can conflict. For example:
     - Factoring out a method may avoid duplicate code, but may make the changes less localized.
     - Making a one line change in one place may be simple, but it may not fit best with logic of the existing code.
4. Implement the fix you have chosen.
   - Rebuild the `school` module and test the Harvest form manually as you go.
5. When you believe you have a working fix, run the tests that you have written. If they do not pass:
   - Revisit your solution to ensure it generates the desired behavior.
   - Revisit the tests that you have written to ensure that they are correct.
6. When the bug is fixed and your tests pass:
   1. Remove the `.only`s from `harvest.e2e.cy.js` so that all tests will run.
   2. Run the full suite of tests to ensure that your changes have not broken any other functionality. Continue to adapt and fix the code until all tests pass.
7. Commit your changes to your feature branch.

## Create a High Quality Pull Request

The purpose of the body of a pull request (PR) is to communicate information about the changes that you are proposing to the project maintainers.  

As the pull requests you have made for earlier assignments have been just to turn in work on the tutorials or application assignments the importance of the body of the PR has not been emphasized. However, now that we are transitioning toward making OSS contributions we'll now also start practicing writing good PR bodies.

1. Read the following source that provides some general advice on how to write a quality pull request:
   - [Writing A Great Pull Request Description](https://www.hackerone.com/blog/writing-great-pull-request-description) by Gonzalo Bañuelos for hackerone.
2. Push your feature branch to your origin repo on GitHub.
3. Go to your origin repo on GitHub.
4. Start the process of creating a PR to the `development` branch in the upstream repository and fill in the following sections of the PR template that is used by the FarmData2 project:
    - **Purpose**: Give a concise high-level description of what the PR is trying to accomplish. Focus on the purpose of the PR and avoid discussing implementation details.
    - **Verification Steps**: Give a precise set of steps that the reviewer(s) of your PR can use to manually verify that the proposed changes achieve the purpose.
    - **Approach**: Describe in words the cause(s) each of the "Observed Behavior(s)" and explain how you have addressed each of the causes. This description and explanation should not be a line-by-line description of the code. A competent maintainer will be able to read your code once they know what it is supposed to be doing. The goal of this section is to explain the **purpose** of the code changes that you have made and how they address the causes of the bug at a level of abstraction that is above line-by-line descriptions of the code.
      - As examples, you might find yourself using language similar the following when explaining your approaches:
        - The method `...` is now called from `...` in order to "...", which ensures that "..." when "...".
        - The Vue `data` property `...` is set to `...` in the `...` method, which ensures that "..." when "...".
        - The extra `if` statement was added on line `...`, which ensures that the code that "..." only executes when "...".
        - Etc.
    - **Testing**: Describe the purpose of each automated test that is added or modified by the PR.
    - **Related Issues**: Link to any issues in the issue tracker that are related to this PR.  If the PR full addresses an issue include a line with "- Closes #123" or "- Relates to #123" where "123" is replaced by the number of the issue in the issue tracker. 
      - These lines will be automatically turned into links to the issue in the issue tracker.
      - Using "Closes #123" will ensure that the linked issue is automatically closed if the PR is merged. 
    - **Additional Information**: Include here any additional information that will be helpful to the reviewer(s) of your PR.
      - For this assignment, include here at least an estimate of how long you spend on this assignment.
5. Review the **Licensing Certification* that appears at the bottom of the PR template and ensure that you are in compliance with the Developer Certificate of Origin, which ensures you have the rights necessary to grant license to FarmData2 to use your contribution.
6. Create the pull request.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)
