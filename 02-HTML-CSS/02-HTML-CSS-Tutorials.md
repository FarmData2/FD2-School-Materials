# 02 - HTML-CSS - Tutorials

For this activity you will complete three tutorials from MDN (Mozilla Developer Network) that lead to the creation of a basic website containing a heading, an image, and a few paragraphs of text.

## Preliminaries

1. [Restart your FarmData2 Development Environment in Codespaces](https://github.com/FarmData2/FarmData2/blob/development/docs/install/codespaces.md#restarting-a-farmdata2-development-environment-in-codespaces)
2. Create a new feature branch from the FarmData2 `development` branch for this assignment.
   - Be sure to give your feature branch a descriptive name.
3. Create a new directory in the `FarmData2/modules/farm_fd2_school` directory for your work. This directory should have the same name as your GitHub username.  
   - For example, if your GitHub username were "octocat" then the new directory will be `modules/farm_fd2_school/octocat`.
   - If you are completing this assignment as part of a course and your GitHub username will not clearly identify you to your instructor, communicate your username to them.
4. Create another new directory inside your directory named `01-HTML-CSS`.
5. All of the files that you use or create during this assignment should be contained in your `01-HTML-CSS` directory.

## Planning 

1. Go to the [Your first website](https://developer.mozilla.org/en-US/docs/Learn_web_development/Getting_started/Your_first_website) tutorial from MDN.
2. Complete the "What will your website look like?" tutorial under "Tutorials."
   - There is nothing to be turned in for this tutorial. The planning that you do will become a part of your submission for the next two tutorials.

## HTML Tutorial

1. Complete the "Creating the content" tutorial under "Tutorials."
   - The `index.html` file you create an be opened in Firefox by entering `file:///home/fd2dev/FarmData2` into the URL and then navigating to your `index.html` file.
2. Commit the result to your feature branch for this assignment. 
   - Be sure to use a descriptive commit message.
   - The [Git/GitHub Reference](../GitReference/GitReference.md) may be handy here if you don't remember the commands.

### HTML Tutorial Checklist:

- Page includes `<img>` element that displays a local image with appropriate `alt` text.
- Page `<title>` element has been customized.
- Page title appear in an `<h1>` element at the top of page.
- One or more `<p>` elements appear below the image.
- An ordered (`<ol>`) or unordered (`<ul>`) list containing multiple list items (`<li>`).
- Some text in one of the paragraphs (`<p>`) has been made into an active link (`<a>`).
- Your changes have been committed to your feature branch with a descriptive commit message.

## CSS Tutorial

1. Complete the "Styling the content" tutorial under "Tutorials."
2. Commit the result to your feature branch for this assignment. 
   - Be sure to use a descriptive commit message.

### CSS Tutorial Checklist

- The `<head>` element in `index.html`:
  - Sets the style sheet to `styles/style.css`
  - Sets the font for the `<html>` element.
- The `styles/style.css` style sheet has CSS rules that use element selectors to style the:
  - `<h1>` element
  - `<p>` and `<li>` elements
  - `<body>` element
  - `<img>` element

## Turning In Your Work

The [Git/GitHub Reference](../GitReference/GitReference.md) may be handy here if you don't remember the necessary commands.

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your team's origin repo.
3. Go to your team's origin repo on GitHub.
4. Make a PR to your team's FarmData2-School upstream to merge your feature branch into the `development` branch.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR and ensure that you have only changed things in your own folder.  If necessary, undo any changes to your branch and push it again to update the PR.
