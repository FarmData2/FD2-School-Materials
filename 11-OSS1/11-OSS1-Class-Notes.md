# 11 - OSS1 - Class Notes

## Instructor ToDo

- Assign each issue written by a student to one of the other students that has written an issue.
  - If some students uncovered all of the "buggy" behavior (see Demo below) then try to assign them to each other's issues for fairness.

## Questions

- H10-FD4-Application
  - Added tests for:
    - the Initial State of the Harvest form:
    - selecting a Crop with Harvestable Plants.
    - selecting a Crop without Harvestable Plants.
  - Solution is in `modules/farm_fd2_school/src/endpoints/OSS1/harvest.e2e.cy.js`

## The T11 Bug Report

### Discussion

- Have them discuss the bug in small groups and "compare notes" on what they think the bug is.
  - Encourage them to have the Harvest form open from "OSS1".
- Have groups report out on anything new that they discovered collectively.
  - Hopefully someone (but not everyone) has noticed that the submit button **sometimes, but not always** remains enabled.
  - If so, push on that to see if they can more fully characterize it.
    - If not then then guide the discussion using the demo below to reveal the additional "buggy" behavior.
 
### Demonstration 

- Do demos of anything that is suggested while the report out is going on. 
  - The goal being to be sure everyone sees a full characterization of the bug.
- A partial demo of the bug would be:
  1. Select `ARUGULA`
  2. Complete the form picking the plant in "A".
  3. "Submit" button is enabled
     - Do not submit.
  4. Select `ASPARAGUS`
     - No `ASPARAGUS` plants message appears.
     - "Submit" button remains enabled but it should be disabled.
       - Everyone should have discovered and seen this.
- But that doesn't capture all of the "buggy" behavior.
  5. Select `CARROT`
    - No `CARROT` plants message appears.
    - "Submit" button is now disabled as it should be.
      - So the issue is not quite as simple as it might have seemed at first.
        - Unlikely that everyone has seen this.

## The Hands-On Activity

The Hands-On Activity for this topic:
- is required, unlike previous ones.
- has two parts:
  - For both parts assume a reasonably skilled user who has never seen the bug before.
  - Part 1:
    - Take the issue as it is written.
      - It does not need to address the full scope of the issue as we have now come to understand it.
    - Try to follow the "Steps to reproduce"
    - React to the issue if they are good, or add a comment if they can be improved.
  - Part 2:
    - Determine if the issue captures all of the "buggy" behavior.
    - React to the issue if it has, or add a comment with additional information if it has not.

## What does a Good Bug Fix Look Like?

If time permits...
- Ask "What makes a good bug fix?"
  - It is preferable among the possible fixes.
  - What are some things that make a fix "preferable"?
    - It fixes the bug.
    - Only changes addressing the bug are made.
    - Changes do not introduce duplicate code.
    - The changes should be as simple as possible.
    - Changes are as small and localized as possible.
    - The changes should fit with the style and logic of the existing code such that it remains cohesive, readable and understandable to others.

You will want to evaluate a variety of possible fixes to determine which to implement. 
- Some fixes will be better than others. 
- So avoid the urge to start implementing the first thing that you think of.
- Choose what you think is the best solution based on the above criteria.
  - Note you may have to use your judgement as some criteria can conflict:
    - Factoring out a method may avoid duplicate code, but may make the changes less localized.
    - Making a one line change in one place may be simple, but it may not fit best with logic of the existing code.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)
