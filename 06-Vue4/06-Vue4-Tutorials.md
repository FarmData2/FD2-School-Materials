# 06 - Vue4 - Tutorials

For this activity you will complete several more tutorials from Vue School that build on your Vue knowledge from the last topic. In these tutorials you'll learn how to dynamically set HTML attributes using Vue's `v-bind` directive and how to use Vue's computed properties to automatically update page content when something changes.

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize your `development` branch with the upstream `development` branch.
3. Create a new feature branch from `development` and switch to it for your work on this assignment.
4. Use the following commands to create the starter code for the tutorials:
   ```
   cd ~/FarmData2/modules/farm_fd2_school
   cp -r 05-Vue3-Tutorials-Soln 06-Vue4
   ```
5. Open the `FarmData2` folder in VSCodium.
6. Open the `index.html` file in the `FarmData2/modules/farm_fd2_school/06-Vue4` directory.
   - This `index.html` file contains the shopping list app as it should be at the start of the tutorials for today.
   - All of your work for this assignment should be with the `06-Vue4` directory.
7. Open the `FarmData2/modules/farm_fd2_school/06-Vue4/index.html` file in the browser.

## HTML Attribute Binding in Vue 3

1. Log into [Vue School](https://vueschool.io/).
3. Go to the [Vue.js 3 Fundamentals with the Options API](https://vueschool.io/courses/vuejs-3-fundamentals) course.
4. Scroll down to find the list of lessons.
5. Play the video "HTML Attribute Binding in Vue 3."
6. Follow along with the tutorial, making changes to the code and doing what they do in the videos. Pause and rewind frequently so that you can keep up.
7. Be sure that the code you have at the end of of the video matches what was produced in the video.
8. Autoformat your `index.html` file.
9. Commit the changes to your feature branch with a meaningful commit message.

### Checklist

- `v-bind` is used to disable the "Save" button when the input contains less than 5 characters.

## Computed Properties in Vue 3

1. Play the video "Computed Properties in Vue 3."
   - NOTE: We are skipping the "Dynamic CSS classes in Vue3." Thus, some of the code and behavior that you see in this video will be slightly different than what you observe in your browser. In particular, you will notice that the items in your shopping list do not appear with ~~strike through~~ or in red as they do in the video. You can ignore these differences as they do not affect the new functionality that is introduced in this video.
2. Follow along with the tutorial, making changes to the code and doing what they do in the videos. Pause and rewind frequently so that you can keep up.
3. Be sure that the code you have at the end of of the video matches what was produced in the video.
4. Autoformat your `index.html` file.
5. Commit the changes to your feature branch with a meaningful commit message.

### Checklist

- The `reversedItems` computed property causes newly added items to appear at the top of the list.

## Turning In Your Work

The [Git/GitHub Reference](../GitReference/GitReference.md) may be handy here if you don't remember the necessary commands.

1. Be sure all changes have been committed to your feature branch.
2. Push your feature branch to your origin repo.
3. Go to your origin repo on GitHub.
4. Make a PR to the `development` branch in the upstream repository.
5. In the body text of the PR include any comments you have on the assignment and an estimate of the amount of time that you spent on it.
6. Examine the "Files Changed" tab on your PR to ensure that you have made only the necessary changes in your `06-Vue4` directory.  Make any necessary changes, commit them to your feature branch and push it again to update the PR.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)