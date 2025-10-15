# 07 - FD1 - In Class Hands-On Activities

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize the `development` branch in your clone with the upstream `development` branch.
   - After you synchronize a solution to the tutorials that also includes some code that was shown in class will have been added to `development` in the directory `modules/farm_fd2_school/07-FD1-Activity-Starter`.
3. Create and switch to a new feature branch for your work on these activities.
4. Open the `modules/farm_fd2_school/07-FD1-Activity-Starter/index.html` file in the browser and in VS Codium.
   - You will use this file to complete these activities.

## Fetching the new User's Posts

In class we saw the `posts` endpoint and Vue's `watch` feature. Now we need to put those together and use the `watch` to fetch the posts that were made by the selected user.

1. Modify the `watch` so that it uses the `posts` endpoint with a query parameter to fetch the `selectedUser`'s posts.
   - Hints:
     - Recall that the `posts` endpoint can be used as follows to fetch a specific user's posts:
       ```
       `https://jsonplaceholder.typicode.com/posts?userId=1`
       ```
     - Be sure to add `async` to the `watch` on `selectedUser` because you will now be using `await` inside of it.
     - Use the `userId` of the `selectedUser` to build the URL including the query parameter containing the users id that you need to use in `fetch`.
     - Use JavaScript's `fetch` and `json` methods with `await` like we did to fetch the users.


2. Log the object containing the posts to the console.
3. Confirm that when you select a new user the object logged in the console contains only the posts for the user that you selected.
   - Note: The users appear in the "Users" select in order by their `id`.  So if you select the third user in the select (Clementine Bauch), the posts should all have `userID: 3`.
4. Commit the changes to your feature branch with a meaningful commit message. 

## Displaying the User's Posts

Now that we have fetched the posts for the selected user, we need to display those posts in the page.  To keep things simpler, we'll just display the titles of the posts for now.

1. Store the object containing the selected user's posts into a new property in the Vue data.
   - Tip: You can use the Vue Devtools to check that this is working correctly.
2. Add code to the `<template>` to display an ordered list of the selected user's post titles.
   - Hint: Use a `v-for` in a the `<li>` within an `<ol>` element.
3. Verify that now when you select a user, the titles of their posts are displayed.
4. Commit the changes to your feature branch with a meaningful commit message.

## Cleanup

Including `console.log` statements is great for testing and debugging, but they should not be included in production code.

1. Remove the `console.log` statements from the `watch` on `selectedUser`.
2. Verify that your page still works correctly.
3. Commit the changes to your feature branch with a meaningful commit message.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)