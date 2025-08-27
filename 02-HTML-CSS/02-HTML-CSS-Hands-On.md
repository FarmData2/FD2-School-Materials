# 02 - HTML/CSS - In Class Hands-On Activities

This set of hands-on activities builds on the basic web site that you created in the tutorials that you completed before class.  In these activities, you'll practice learning about and using some additional HTML elements, attributes and CSS selectors.

## Preliminaries

1. Restart your FarmData2 development environment.
2. Synchronize the `development` branch in your clone with the upstream `development` branch.
   - See the [Git Command Reference](../GitReference/GitReference.md) if you do not remember the commands to synchronize.
   - After you synchronize:
     - Your work on the tutorials that you made a PR for will have been added to `development`.
     - A solution to the tutorials will have been added to `development` in the directory `modules/farm_fd2_school/02-HTMl-CSS-Tutorials-Soln`.
3. Create a new feature branch from `development` for your work on these activities.
   - You may complete the activities using your solution to the tutorials or using the solution.

## HTML Tables

You learned about a number of HTML Elements in the tutorials that you completed.  In this section you will learn about the `<table>` element that allows you to create a table on your page.  

1. Visit the [MDN HTML Element Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements).
2. Find the documentation for the `<table>` element.
3. Find the "Examples" section for the `<table>` element.
4. Create a table below the `<p>` elements in your `index.html` document.
   - Your table can contain what ever information you'd like.
   - But it should have:
     - A row of headings at the top.
     - At at least 3 columns in each row.
     - At least 4 rows. 
     - A border around the full table.
     - A border around each cells.
5. Commit your changes to your feature branch.

## CSS Selectors

In the tutorials that you completed you used some CSS Type Selectors to style some of the HTML elements on your page. In this section you will learn about two additional CSS Selectors that allow you to apply styles to specific elements rather than to all elements of a type.

1. Visit the [MDN CSS Reference](https://developer.mozilla.org/en-US/docs/Web/CSS)
2. Open the "Selectors" section in the left column.
3. The "Type selectors", "Class selectors", and "ID selectors" sections contain example that you may find helpful.
4. Style the table so that:
   a. The text in the table is a different color. (Hint: Use a _type selector_).
   b. The table striped (i.e. change the color of every other row) so that it is easier to read. (Hint: Use a _class selector).
   c. The border of one cell in your table is thicker and a different color than the others (Hint: Use an id selector).
5. Commit your changes to your feature branch.

## HTML Form Elements

In this section you'll learn about some of the HTML elements that can be used to collect input from a user of your page.  

### The `<input>` element

The `<input>` element is used to display different types of user input components (e.g. date, checkbox, button, ...)

1. Visit the [MDN HTML Element Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements). 
2. Find the reference for the "`<input>`" element.
3. Find the "`<input>` types" section in the `<input>` reference and use it to complete the following exercises.
4. Create an `<input>` of type `date` on your page with the label "Date:" and a default date of January 1, 2025.
5. Commit your changes to your feature branch.
6. Create an `<input>` of type `button` on your page that that displays the text "Click Me!".
7. Commit your changes to your feature branch.
8. Create an `<input>` of type `checkbox` on your page labeled "Done:".  The box should be checked initially.
9. Commit your changes to your feature branch.

### The `<select>` element

The `<select>` element is used to create drop down lists from which the user can choose an item.  It seems like this should be just another type of `<input>` element, but it is not.

1. Find the documentation for the `<select>` element.
2. Create a `<select>` element that contains a list of at least three items and make any item other than the first one selected by default.
3. Commit your changes to your feature branch.

## The `<div>` Element & Styling

Sometimes you want to style a collection or elements or one part of the content that appears within another element (e.g. one word or a few sentences in a paragraph.)  The HTML `<div>` element makes this possible.

1. Visit the [MDN HTML Element Reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements). 
2. Find the reference for the "`<dif>`" element.
3. Use a `<div>` and a class selector to place a red border around a few words in one of your paragraphs.
3. Use a `<div>` and a class selector to place a red border around all of the input elements that you created.
4. Commit your changes to your feature branch.