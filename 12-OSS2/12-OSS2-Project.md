# 12 - OSS2 - Project Work

This assignment begins the project work part of the course. In the project work you will work in pairs to address issues that have been posted in the issue tracker. Each of these issues addresses a bug or requests a new feature for the Harvest form on which you have been working.

## Requesting an Issue

The issue tracker in the upstream FarmData2-School repository has been populated with a number of issues that are available for the project work. Each of these issues is tagged with a number of labels.

1. With your partner, review the issues that are tagged with the "project" label.
2. Select an issue that you would like to collaborate on.
   - You may select any issue that is tagged with "project".
   - Each issue tagged with "project" is also tagged with a label indicating its level of challenge.
     - It is not required that you begin with an issue tagged with the "Easier" label.
     - You may select an issue at whatever level of challenge you would like.
3. Each partner should comment on the issue with a message like:
   - "I would like to work on this with @partnerID"
     - Where "partnerID" is your partner's GitHub ID.
   - Multiple pairs may comment on the same issue.
     - This is practice so there is no harm in having multiple pairs working on the same issue.

## Preliminaries

1. Restart your FarmData2 Development Environment in Codespaces.
2. Synchronize your `development` branch with the upstream `development` branch.
3. Rebuild the `fd2` module using `npm run build:fd2`
   - **NOTE: Not the `school` module.**
   - For the project work the Harvest form has been moved to the main FarmData2 module.
   - Thus any time you make changes to this Harvest module you will rebuild the `fd2` module.
4. Open the "FarmData2" -> "Harvest" page in the browser and confirm that it works correctly.
5. The files for the Harvest form in `modules/farm_fd2/src/entrypoints/harvest`.

## Working on Your Issue

Begin working on your issue using the collaborative workflow that you practiced in the [OSS2 Hands-on activity](./12-OSS2-Hands-On.md). As you work you should:

- Commit changes and create a draft pull request to the upstream as soon as possible.
  - **As you work, ensure that at least one change from each partner is included in the pull request.**
  - Ask questions that are about the specifics of your code in the comments on your draft pull request.
- Ask questions about the issue in the comments on the issue. This might include:
  - Clarification of what is required.
  - Questions about different approaches to solving the problem.
  - Errors or problems you are seeding related to the issue.

## Turing in Your Work

Turn in your work for OSS2 before the due date by having an up to date draft pull request to the upstream that contains at least one commit from each partner.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)
