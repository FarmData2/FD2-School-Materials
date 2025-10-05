# 07 - FD1 - In Class Hands-On Activities

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize the `development` branch in your clone with the upstream `development` branch.
   - After you synchronize a solution to the tutorials will have been added to `development` in the directory `modules/farm_fd2_school/07-FD1-Tutorials-Soln`.
3. Create and switch to a new feature branch for your work on these activities.
   - Create this feature branch from the branch you created for the tutorials to continue from your prior work.
   - OR create this feature branch from `development` to work from the provided solution.

## Reacting when the User Changes

When a user of our (really bad) social media site picks another user from the "Users" select the page should display the posts that have been made by the selected user.  To do so, we'll first need to be able to detect when the selected user is changed. We can use a Vue `watch` to do this.

1. Add a `watch` that will execute when the `selectedUser` property in the Vue `data` changes.
   - Hint: Ask your favorite AI for "a simple vue watch example using the options api" and then adapt it.
2. Log the selected user's `name` to the console.
3. Change the selected user a few times to verify that the `watch` is working correctly.
4. Commit the changes to your feature branch with a meaningful commit message. 

## The `posts` API Endpoint

The {JSON}Placeholder API provides a `posts` endpoint that returns posts that have been made. We'll use this endpoint with a query parameter to fetch the posts for the newly selected user.

1. Visit the URL below in your browser to see the response that the `posts` endpoint generates.
   - [https://jsonplaceholder.typicode.com/posts](https://jsonplaceholder.typicode.com/posts)
2. Notice the following:
   - Each object in the returned array of posts includes the properties:
     - `userID`: the id of the user that created the post.
     - `id`: a unique id for the post.
     - `title`: the title of the post.
     - `body`: the text of the post.
       - Note that the `title` and `text` fields are fake sentences or fragments in Latin.
   - This endpoint, as we used it returned all of the posts made by all of the users.
3. The `posts` endpoint accepts a `userID` query parameter that allows us to filter the results so that we get only the posts from a specific user.  Visit the URL below in your browser to see the posts that were made by the user with `id=1`.
   - [https://jsonplaceholder.typicode.com/posts?userId=1](https://jsonplaceholder.typicode.com/posts?userId=1)
4. Confirm that the response now contains only the posts for which the `userId` field is `1`.

## Fetching the new User's Posts

Now we need to use the `watch` to fetch the posts that were made by the selected user.

1. Modify the `watch` to use the `posts` endpoint with a query parameter to fetch the `selectedUser`'s posts.
   - Hints:
     - Use JavaScript's `fetch` and `json` methods with `await` like we did to fetch the users.
     - Be sure to add `async` to the `watch` on `selectedUser` because you are using `await` inside of it.
     - Use the `id` of the `selectedUser` to concatenate query parameter to the endpoint URL.
       - Note: String concatenation in JavaScript uses the same `+` operator as Java and Python. For example `"test-" + 1 + "-" + 2` results in the string `"test-1-2"`.
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