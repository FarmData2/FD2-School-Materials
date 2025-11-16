
Before class
- Assign an issue to each student for the hands-on part.
- Only those having completed the assignment can complete this part.
- Others will have to exchange later or just solve their own.

After class
- assign a different issue to each student for the bug fix part.
- I don't know if this will work if some don't finish the hands on in class.
- maybe just let them write the solution to the one they were assigned before class?



- The hands-on is required for this assignment.

- Discuss issue in small groups.
- Have report out and whole class discussion.
- Push discussion to full understanding of the issue as a class.
  - Need to be sure they see that the submit button **sometimes, but not always** remains enabled.
    - It depends on the crop that is selected.
Select ASPARAGUS
Complete the form
"Submit" is enabled
Do not submit

Select ARUGULA
No ARUGULA plants
"Submit" is still enabled.

This is because the values are not cleared from the Vue data that is used by the formValid method when the crop is changed.

This part is less obvious.

Select CARROT
No CARROT plants
"Submit" is not enabled.

This is because CARROT has multiple units and when that happens the unit is set to null when the crop changes. 

- First part of Hands-On
- Take the issue as it is written.
- It does not need to address the full scope of the issue as uncovered in the discussion.
Good steps:
- assume a reasonably skilled user who has never seen the bug before.
- be precise: Select "ARUGULA" as opposed to Select a crop. 


Then second part of Hands-on

Add additional information in a comment.



Discuss if time...
- Discuss possible solutions.
  - What makes a good solution?

 Evaluate each of your solutions to determine which to implement. Consider the following criteria when evaluating each of your possible solutions:
   - Only changes addressing the bug are made.
   - The changes should be as simple as possible.
   - The changes should fit with the style and logic of the existing code such that it remains cohesive, readable and understandable to others.
   - Changes do not introduce duplicate code.
   - Changes are as small and localized as possible.
3. Choose what you think is the best solution based on the above criteria.
   - Note you may have to use your judgement as some criteria can conflict:
     - Factoring out a method may avoid duplicate code, but may make the changes less localized.
     - Making a one line change in one place may be simple, but it may not fit best with logic of the existing code.