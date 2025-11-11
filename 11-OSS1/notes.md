
Prototypical FOSS Roles:
  - Users, Requestors, Contributors, Maintainers and Leaders
  - From GitKit ...

## Before Class: 
- Give them a poor description.
  - Submit button remains enabled when crop with no plants is selected.

Play the role:

- Reporter:
  - Have them write an issue ticket for bug
    - Review readings from 190 on good issues.
      - https://capgemini.github.io/testing/effective-bug-reports/
    - Give bug template???
      - Title
      - Description
      - Reproduction Steps
        - Good advice: https://secure.phabricator.com/book/phabcontrib/article/reproduction_steps/
        - must reliably reproduce bug on clean up-to-date development branch.
        - should be as simple as possible.
          - a minimal example - nothing extra.
        - self-contained.
        - should be able to be followed by an average user of the program.
      - Expected Result
      - Actual Result

- Contributor:
  - Have them comment on their own issue with at least two different approaches to a solution.
    - Describe approach
    - Describe tradeoffs of it.
    - Not just a quick solution, but a good one...
      - Thinking about other readers...
      - Specific criteria???
        - Code quality???
          - Most localized change
          - Simplest logic
          - Consistency
        - Correctness

- Assign issues to others just before class.

## In class let them discuss in small groups 
- What made the issue they read good / less good.
- The merits of different approaches they proposed in their issue.

### Play the role
- Contributor:
  - Comment on assigned issue with:
    - Clarifications
    - Clarified reproduction steps
    - Merits / tradeoffs / clarity of described approaches
    - Proposed approach and justification.
- Reporter:
  - Respond
    - To clarification requests
      - use quoting.
    - to proposed approach on your issue.
      - Accepting it as the way to go.
      - Asking for clarifications.
      - Advocating for a different one.
      - Iterate until consensus.
  
## After Class:

Play the role: Contributor

- Write test, solve issue, make PR.
  - Give improved PR template?
    - Purpose
    - Approach
    - Verification steps

## During Next Class:

Play the role

- Maintainer:
  - Do PR review?
    - Review a PR that I make to all issues?
      - Known issues in the PR?
        - Code issues.
        - Test issues.
    - How to pull PR and run it...
    - Does it implement the intended change?
      - This is a problem since I don't know which approach they want?
      - Maybe just write a branch for each approach and give them what they want with minor issues?
    - Does the test do too much or too little to test the change?
    - Code comments
      - naming?
      - cohesion
      - readability etc...

Turn in for WiD:
- PDF of the original bug report that you wrote.
- PDF of revised bug report with others comments and your replies / edits.
- PDF of the bug report assigned to you with your feedback comments.
- PDF of your PR body - not the code.







Bug Fix and PR

- Maybe do a few issues?
  - One in tutorial, complete in Activity?
    - More guidance here.
  - One in Application?
    - No guidance here?

- I write issue.
  - Bug:
    1. Select ARUGULA
    2. Select plant in "A"
    3. Submit button is enabled correctly.
    4. Select ASPARAGUS
    5. Submit is still enabled even though there are no ASPARAGUS plants to harvest.
- Fix it
- Add a test
- Write PR
  - Find source...
  - What:
    - Descriptive title - not issue #
    - Description of what was done
      - PR Body goes into commit in FD2.
      - Issue has details so need to restate absolutely everything
      - But should stand alone.
    - Link to issue being closed on own line.
      - Closes #123
  - Cause:
    - Describe what caused the problem
  - Solution:
    - Describe the solution.
  - Verification:
    - Describe how to verify manually.
    - Help the reviewer.

- Post requests for assistance in comment if you don't have it done or run into issues.
- Explain what you need.



## PROJECT WORK ISSUES...

Note: You have seen everything you need to know, but that doesn't mean you'll know exactly what to do without learning more / refreshing your memory / extending what you know / etc...
  - Exercise in getting things done.

Give them a workflow...
 - work in pairs? or more?
   - they work from a single fork
   - add collaborator
   - clone that fork
   - Push branch to your fork
   - Make pr for that branch to upstream.
 - Make pr to the upstream
 - Will merge to development later...

What is tutorial? 
  - Nothing? Maybe this is the change to work in the WiD?
Hands on is to get this setup.
Application is fixing issues.


Some things that could be project:

- Convert creation of quantity and harvest log to lib.js using transaction.
- Build a HarvestUnits component
- Augment the ActivePlantAssetPicklist with a crop prop.
- ???

Have them do the below or the more ambitious approach of building / modifying a component as above.
- Set it up as a choose your own adventure...
- Pick the challenge level you want.
  - tag the issues in some way.

And require tests...
- so break things down into smaller chunks and add testing
- Also then add other explicit just testing pieces?

## Optional Additional Improvements

If you would like some additional challenge, there are still a few user interface elements in our Harvest form that are plain HTML elements that can be replaced with nicer FarmData2 components. The sub-sections below give you some guidance on how to replace those HTML elements with FarmDat2 components. Note however, that there are not yet specific components for these elements. So you will use more generic components for now. In the project work you will have the opportunity to modify existing components or build more specific components for these purposes.

### Replace HTML `select` for "Units" with `SelectorBase` Component

1. Replace the HTML `select` input used for the "Units" input in the Harvest form with a FarmData2 `SelectorBase` component.
   - Hints: 
     - Use a computed property to transform the `unitList` that is fetched from farmOS into an array of strings containing just the names of the units.  Ask your favorite AI "in Javascript, given an array of objects with a property name that is a string, how how can I get an array of strings containing just the name."
     - Use a computed property to give you the full `unit` object for the unit that is selected. Then use this computed property in places that need the full `unit` object.
2. Rebuild the `school` module, reload the page.
3. Confirm that the new "Units" component works.
4. Commit the changes to your feature branch.

### Replace HTML `table` with `PicklistBase` Component

1. Replace the HTML `table` input used for the list of the plants that are available for harvest with a FarmData2 `PicklistBase` component.
   - Hints: 
     - Use the `plantList` as it is for the `rows` prop and then set the `columns` and `labels` props as appropriate.
     - Be careful with the payload of the `update:picked` event. Use just the first element of the returned `Map` as the picked plant.
2. Rebuild the `school` module, reload the page.
3. Confirm that the new component works.
4. Commit the changes to your feature branch.

### Styling

- Add some styling to improve the look of the Harvest form. In particular, some of the components would benefit from vertical space either before or after them to separate them from the adjacent components.

Bug Fix

- Bad Submit...
  - Pick a crop with some plants, fill out form, submit button becomes enabled.
  - Pick a crop without plants, submit button remains enabled and can be clicked.  It creates a harvest log???



## Styling

1. Add a rule to the `<style>` element that will create some vertical space between the "Date" and the "Crop" components.
   - Hints:
     - Add an `id` to the component you want to style in the `<template>`.
     - Use a CSS rule with an `id` selector to create some space above or below the component as appropriate.
2. Rebuild the `school` module, reload the page.
3. Confirm that the "Date" and "Crop" now have vertical space between them.
4. Add a rule to the `<style>` element that will create some vertical space between the "Comment" and "SubmitResetButtons" components.
5. Rebuild the `school` module, reload the page.
6. Confirm that the "Date" and "Crop" now have vertical space between them.


Form reset after submit
 - reset with sticky crop.

## Hackathon issues?
