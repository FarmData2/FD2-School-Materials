# 07 - FD1 - Class Notes

## Instructor ToDo Before Class

- Merge 
  - `07-FD1-Tutorial-Soln`
  - `07-FD1-Activity-Starter`
  - `07-FD1-Activity-Soln`
  - `07-FD1-Application-Starter`
  - `08-FD2-Tutorials-Starter`

## Questions

Take questions on:
- Application 06-Vue4
- Tutorial 07-FD1

## Tutorial 07 Review

Ask about the following and review as necessary if it doesn't come up in the questions above.

Tutorial 07 introduced a few new ideas:
- Show `07-FD1-Tutorial-Soln/index.html` to illustrate as necessary.
- APIs and Endpoints.
  - Used by applications to retrieve data or invoke a service on a server.
  - Essentially a URL that when accessed returns JSON data.
  - We used the `users` endpoint to fetch the list of users from the `users` endpoint of the API.
    - The `users` endpoint is at the URL `https://jsonplaceholder.typicode.com/users` 

- Vue's _`created`_ _lifecycle hook_.
  ```
  async created() {
    await this.fetchUsers();
  },
  ```
  - The `created` lifecycle hook runs when the Vue app is "created".
    - This (and other) lifecycle hooks provide a way for apps to automatically perform computations when they are stared.
    - The `created` lifecycle hook is called when:
      - the Vue instance has been created
      - all of the `data` properties are initialized.
      - the computed `properties` are computed as necessary.
      - the `methods` are available to be called.

## New Ideas

In addition to the tutorial content there area few new things you'll need to know about as you move through the hands-on activity and the application.

## The `posts` Endpoint

In addition to the `users` endpoint, the [{JSON}Placeholder API provides other endpoints](https://jsonplaceholder.typicode.com/) including the `posts` endpoint.
- The `posts` endpoint returns all of the posts that have been made.
  - Visit: `https://jsonplaceholder.typicode.com/posts`
    - This returns all posts by all users.
    - Each object in the returned array of posts includes the properties:
      - `userID`: the id of the user that created the post.
      - `id`: a unique id for the post.
      - `title`: the title of the post.
      - `body`: the text of the post.
        - Note that the `title` and `body` fields are fake sentences or fragments in Latin.

## Query Parameters in API Requests

More typically we will want the posts by a specific user.

- So we could filter this data in our JavaScript on the client.
- But that would waste a lot of time and bandwidth by transmitting a lot of data that we don't need.

To prevent the transmission of lots of unnecessary data most API's will allow us to specify _query parameters_ that filter the data on the server side, before it is sent to us.

- A query parameter is often a _key=value_ pair that is appended to the end of the URL following a `?`
  - For example, the following URL requests just the posts for the user with `userID=1`.
    - Visit `https://jsonplaceholder.typicode.com/posts?userId=1`
    - The `key` will usually be one of the properties in the returned result (e.g. `userId` to filter by the `userID` of the user that made the posts).
    - The `value` will be the value of the `key` for the objects that we want to receive (e.g. `1` to get just the users with the `userID` of `1`.)
- APIs endpoints may also allow you to specify multiple query parameters by separating them with an `&`.
  - For example, the `posts` endpoint allows us to also filter by the `id` of the post. 
  - The following URL will fetch just one post. The post made by the user with `userID=1` that has the `id=2`.
    - Visit: `https://jsonplaceholder.typicode.com/posts?userId=1&id=2`

You'll be using query parameters in the hands-on activity and in the application.

## Watching Vue Properties

We now know enough to fetch the posts that are made by the user that we select.  Ideally, this will happen as soon as we pick the user. To do that we'll need to know how to setup a _`watch`_ in Vue. A `watch` in Vue watches a Vue `data` property or a `computed` property and executes some code any time that property changes.

Let's look at how we might use a `watch` to run some code when the selected user changes.

- Use the `07-FD1-Tutorial-Soln` branch for demo.
- Open the `modules/farm_fd2_school/07-FD1-Tutorial-Soln/index.html` file in the browser.
  - Show fetched users as should be in their solutions.
  - Now we want to do something when the user is changed.
    - E.g. Fetch the posts made by that user.
- Add the `watch` to the Vue instance between `data` and `methods`:
  ```
  data: {
    ...
  },
  watch: {
    selectedUser() {
      console.log('New user is ' + this.selectedUser.name);
    },
  },
  methods: {
    ...
  },
  ```
  - String concatenation in JavaScript uses the `+` operator just like it in Java or Python.
    - For example:
      ```
      const s1 = "Testing";
      const n1 = 1;
      const result = s1 + " " + n1 + ", 2, 3";
      console.log(result); // Shows: "Testing 1, 2, 3"
      ```
    - Note that JavaScript also provides _[Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) as a way to insert variables into strings. But using `+` will be sufficient for anything that we need in this course and is what is used throughout FarmData2.
- Save and reload the page.
- Open the Devtools console
- Change the selected user and observe the output in the console.

Note that this `watch` has been included in the starter code for the hand-on activity.

## Hands-on Activity

Use the majority of the remainder of class for the hands-on activity.

## Intro to the Application

In the application assignment you will be using API endpoints provided by farmOS to fetch
- the list of crops for the "Crop" select.
- the list of plants of the selected crop type that are available to be harvested.

Demo this using the solution to the 07-FD1-Application assignment.
- Switch to `08-FD2-Application-Starter`
  - This is what you are aiming for when you have completed the 07-FD1-Application assignment.
- Rebuild the `school` module and reload the page.
- Visit "FD2 School" -> "FD2-Application"
- Notice:
  - There are options for "FD2-Tutorial", "FD2-Activity", "FD2-Application"
    - All work for 08-FD2 will be done in FarmData2 endpoints because we need to access the farmOS database.
  - The "Crop" select now has far more options.
    - When you setup your development environment it installed a sample database into farmOS.
      - This sample database contains a small set of data that is used for testing.
    - You'll add code that uses `fetch` to get the full list of crops that are in the sample database and use them as the options in the "Crop" select.
  - When a crop is selected either:
    - A list of all of the plants of that type will be displayed in the table.
      - "ARUGULA", "BEAN", "BROCCOLI", and others.
    - A message will indicate that there are no plants of that type available for harvest.
      - "ASPARAGUS", "CARROT", and others.
    - You'll add code that uses a `watch` uses `fetch` to get the plants for the selected crop and use them in the table rows.

Notice the distinction between "Crop" and "Plant" here again.
- A _crop_ is a type of _plant_.
- _Plants_ are living things in trays in a greenhouse or planted in the ground.

## Setup for the next Tutorial

As you can imagine the code for `fetching` crops and plants (and pretty much everything else) from the farmOS API will be repeated over and over again in the different features.  As we've seen before that it's a good idea to factor out repeated code to improve the maintainability of the code base.

FarmDat2 factors out all of the code that accesses the farmOS API into a JavaScript library.  All of the features then use this library (`farmosUtil`) to access the API, rather than writing the `fetch` code explicitly. This makes the code more modular improving the maintainability of the code. It also improves the verifiability of the code because the functionality of these library functions can be tested once, rather than on every page that would contain a call to `fetch`.

In the next tutorial (08) you'll:
- learn about the `farmosUtil` library. 
- convert the code you have that fetches the crops to use functions in the `farmosUtil` library.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)