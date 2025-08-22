# FarmData2 School Instructor Guide

The FarmData2 (FD2) School materials are structured to be used in a course where students are familiar with git/gitHub, have worked in a linux environment, and have some prior programming experience. However, while FD2 is written primarily in HTML, CSS, JavaScript and Vue.js prior experience with those is not required.  The materials introduce enough of each technology that a student with prior programming experience can be successful.

The FD2 School activities move students through a series of introductory tutorials, hands-on activities, and homework applications. Each topic begins with students independently following an introductory tutorial outside of class that introduces them to a topic (e.g. HTML/CSS) and has them build a small artifact. Hands-on activities in the subsequent class has students expand their knowledge of the topic with several additional challenges that build upon the result of the tutorial. Finally, the a homework application following the class has them apply what they've learned to a feature in the FarmData2 project. The final result of completing the homework applications is that students will have added a basic Harvest feature to FarmData2.

The figure below illustrates visually how students progress through the introductory tutorials, hands-on activities and homework applications. Class 1 is an introductory class that introduces students to FarmData2 and the development environment and sets the stage for what they will be doing. In homework 1 (HW 1), student complete an HTML tutorial and a CSS tutorial that guide them through building a small static web page. Through hands-on activities in Class 2 they learning some new HTML elements and additional CSS Selectors and attributes and extend that web page. In homework 2 they apply what they've learned about HTML and CSS to begin implementing the basic FarmData2 harvest feature. This pattern then repeats for [each of the topics](#topic-outline)

![Diagram illustrating how students move through introductory tutorials, hands-on activities and homework applications.](AssignmentPipeline.png "The assignment pipeline.")

### Timing

- The hands-on activities for each class are nominally targeted to take 30-45 minutes. These activities have some initial activities and then some additional challenges. This is designed to ensure everyone has something to do for the allotted time and to allow the time to be adjusted based on other classroom needs.
- Each set of tutorials is nominally targeted to take between 1 and 2 hours outside of class.
- Each homework assignment is nominally targeted to take between 2 and 3 hours outside of class.

## Topic Outline

1. Introduction
2. HTML/CSS
3. Vue Data Binding / List Rendering
4. Retrieving Data in FarmData2
5. Vue Inputs / Events / Methods
6. FarmData2 Vue Components
7. Vue Conditional Rendering / Attribute Binding / Computed Properties
8. Writing Data in FarmData2
9. End-to-End Testing
10. FarmData2 Idioms



## Assignment Submission Logistics

- first exposure following tutorials is individual assignment.
  - submitted by PR by the student from the team's fork to the team's upstream.
- implementation of the feature in FD2 is a team assignment.
  - submitted by PR by someone on the team from the team's fork to the team's upstream.

## Instructor ToDo
- Form teams.
- Create an upstream FarmData2-School repo for each team and distribute the URLS
  - These should contain only development and production branches.
- Create instructor repo
  - This will contain all branches
  - Add remotes for each team's upstream
    - So can push the solution/starter branches and PR them into their repos.

