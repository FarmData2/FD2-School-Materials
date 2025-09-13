# 03 - Vue1 - Tutorials

For this activity you will several tutorials from Vue School that introduce you to Vue.js and guide you through the first steps in creating basic shopping list app using Vue. 

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize your `development` branch with the upstream `development` branch.
3. Create and switch to a new feature branch from the FarmData2 `development` branch for this assignment.
   - Be sure to give your feature branch a descriptive name.
4. Create a new directory in the `FarmData2/modules/farm_fd2_school` directory named `03-Vue1` for your work on this assignment.
5. All of the files that you use or create during this assignment should be contained in your `03-Vue1` directory.

## Setting Up for the Tutorials

1. Create a file named `index.html` inside of your `03-Vue1` directory and paste in the following content that is identical to what is shown at the start of the tutorial linked below.
   ```
   <!DOCTYPE html>
     <html lang="en">
     <head>
       <meta charset="UTF-8">
       <title>Shopping List App</title>
       <link rel="stylesheet" href="main.css">
     </head>
     <body>

       <script src=""></script>
     </body>
   </html>
   ```
2. Download the [`main.css` file](https://raw.githubusercontent.com/vueschool/vuejs-3-fundamentals/a3d2b0b43f9e0bd5bc0ea00e238270215efbe40b/main.css) file and place it into your `03-vue` directory.
   - They use this file in the tutorial but do not show it to you in the videos.
3. Open the `index.html` file you just created in Firefox by entering `file:///home/fd2dev/FarmData2` into the URL and then navigating to your `03-Vue1/index.html` file.

## Getting Started with Vue.js 3

1. Log into [Vue School](https://vueschool.io/).  You can create an account or login with using GitHub or Google.
2. Go to the [Vue.js 3 Fundamentals with the Options API](https://vueschool.io/courses/vuejs-3-fundamentals) course.
3. Scroll down to find the list of lessons.
4. Play the first video "Getting Started with Vue.js 3."
5. Follow along with the tutorial, making changes to your code and doing what they do in the videos. Pause and rewind frequently so that you can keep up.
6. Be sure that the code you have at the end of of the video matches what was produced in the video.
7. Autoformat your `index.html` file.
8. Commit your work to your feature branch. 
   - Be sure to use a descriptive commit message.
   - The [Git/GitHub Reference](../GitReference/GitReference.md) may be handy here if you don't remember the commands.

### Checklist

- `<script>` added to import the CDN.
- The `shopping-list` `<div>` has been added.
- `<script>` added to instantiate Vue object.
- `data` method added to the Vue instance.
- `header` data is bound into `<h1>` using "double mustache."
- Uses `v-model` to bind the `header` value to an `<input>`.
- Vue instance is assigned to a variable.
- Your changes have been committed to your feature branch with a descriptive commit message.

## Using Vue Devtools with Vue.js 3

1. Click the "Puzzle piece" in the upper right of the browser.
2. Click the Settings "Gear" beside the "Vue.js devtools."
3. Check "Pin to Toolbar".
   - You should now see a green "V" Vue logo in the toolbar at the top right of the browser.
4. Play the next video "Vue Devtools" and skip ahead to 2:45.
   - Note: The first part of this video shows how to install the Vue Devtools. These tools are already installed in Firefox in the FarmData2 Development Environment, so we can skip that part.
5. Follow along with the video as it demonstrates how to use the Vue Devtools and replicate the things that they demonstrate for yourself.

### Checklist

- There are no code changes in this section of the tutorial so there is nothing to commit.

## Vue.js 3 template Syntax and Expressions

1. Play the next video "Vue.js Fundamentals with the Options API." 
2. Follow along with the tutorial, making changes to your code and doing what they do in the videos. Pause and rewind frequently so that you can keep up.
3. Be sure that the code you have at the end of of the video matches what was produced in the video.
   - Note: The address of the Vue CDN in the video has been changed to `https://unpkg.com/vue@next`. However, that does not seem to work. So you should leave it as `https://unpkg.com/vue@3`.
4. Autoformat your `index.html` file.
5. Commit your work to your feature branch. 
   - Be sure to use a descriptive commit message.

### Checklist

- Default "Welcome" messages added in header using `||` operator.
- `header` data changed to be "Shopping List App"
- `<input>` field has been removed.
- Your changes have been committed to your feature branch with a descriptive commit message.

## List Rendering in Vue 3

1. Play the next video "List Rendering in Vue 3." 
2. Follow along with the tutorial, making changes to your code and doing what they do in the videos. Pause and rewind frequently so that you can keep up.
   - Note: The variable they used for the Vue instance in the earlier video was `shoppingList`, but in this video that has changed to `shoppingListApp`. This matters when they show how to add/remove items from the console.
3. Be sure that the code you have at the end of of the video matches what was produced in the video.
4. Autoformat your `index.html` file.
5. Commit your work to your feature branch. 
   - Be sure to use a descriptive commit message.

### Checklist

- `items` are specified as an array of objects in `data`.
- `v-for` is used to render the list of items.
- Your changes have been committed to your feature branch with a descriptive commit message.

## Turning In Your Work

The [Git/GitHub Reference](../GitReference/GitReference.md) may be handy here if you don't remember the necessary commands.

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have made only the necessary changes in your `03-Vue1` directory.  Make any necessary changes, commit them to your feature branch and push it again to update the PR.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)