# 12 - OSS2 - In Class Hands-On 

Today we begin the project work part of the course. In the project work you will work in pairs to address issues that have been posted in the issue tracker. Each of these issues addresses a bug or requests a new feature for the Harvest form on which you have been working.  This hands-on activity will help you get setup to collaborate on this work.

## Collaboration

You will be working in pairs to resolve an issue. You will collaborate by sharing one of your FD2-School repositories so that you are both able to push feature branches with changes. To share a repository you will add one partner to the other partner's fork of FD2-School as a collaborator.

### Adding a Collaborator

To add a collaborator:
1. Decide which partner's repository you will use.
2. Go to that repository on GitHub.
3. Go to the "Settings" for the repository (The _gear_ icon at the top).
4. Click on "Collaborators" (In the left panel).
5. Click the "Add people" button.
6. Enter your partner's GitHub id.
7. Click the "Add ..." button.
8. The invited partner will need to:
   - Accept the invitation (check your e-mail).
   - Run the FarmData2 Development Environment from the repo:
     - [Using GitHub Codesapces](https://github.com/FarmData2/FarmData2-School/blob/development/docs/install/codespaces.md)
     - [Locally with Docker Desktop](https://github.com/FarmData2/FarmData2-School/blob/development/docs/install/local.md)

### A Collaboration Workflow

One workflow for collaborating on an issue with a shared repository is to have a shared feature branch that everyone working on the issue works from. Each collaborator will creates their own feature branch from that shared feature branch. When a collaborator has changes to share, they push their own feature branch and make a pull request to the shared feature branch. The collaborators then merge the pull request into the shared feature branch. They then synchronize their copy of the shared feature branch with the merged changes and the process repeats until the shared feature branch contains a solution to the issue. They then make a pull request for the shared feature branch to the upstream repository.

That's easy to say, but hard to follow, so let's do a practice run before taking on actual development work.

#### Creating the Shared Feature Branch

Use the following steps to create a shared feature branch in GitHub:

1. Visit your shared fork of FarmData2-School.
2. Click the `development` branch button
   - ![The `development` branch button.](./images/developmentbranch.png)
3. Type `oss2-practice` into the "Find or create a branch..." box.
4. Click "Create branch **oss2-practice** from **development**".
   - This will create and switch to the new feature branch in your repository on GitHub.

#### Fetching the Shared Feature Branch

You that now have a shared feature branch, each partner needs to get a copy of the `oss2-practice` feature branch into their own local repository. 

1. Start your development environment.
2. Synchronize your `development` branch with the upstream `development` branch.
3. `git fetch origin oss2-practice`
4. `git switch oss2-practice`
5. `git status`
   - This should show that `oss2-practice` is now the active branch.

#### Making Some Changes

For practice, each partner should make a change to the `README.md` file as follows:

1. Switch to the `oss2-practice` branch.
2. Create and switch to a new feature branch from `oss2-practice` for your work.
3. Open `README.md`.
4. Add a line at the very top of the file (above `# FarmData2`) containing your name.
   - You may then need to add your name to the dictionary as well.
5. Stage and commit your change.
6. This commit will fail due to a linter that checks for broken links.
   - Remove the broken link.
7. Stage and commit your change.
8. Push your feature branch to the `origin`.
9. Visit the origin repository on GitHub and create a pull request making sure that the: 
   - **base repository:** is set to your shared fork of the FarmData2-School repository and not the upstream.
   - **base:** is the `oss2-practice` feature branch where you want the changes to go.
   - **compare:** is the feature branch with your changes.
10. Find the Pull Request in your FarmData2-School fork.
11. Visit the "Files changed" tab and confirm that the change you made are there.

#### Merging the Changes

Your fork of the FarmData2-School repository should now show that there are two pull requests. 

One partner should merge these pull requests by as follows:

1. Visit your shared fork of FarmData2-School on GitHub.
2. Open the "Pull request" tab.
3. Open one of the pull requests.
4. Review the changes in the "Files changed" tab.
5. Click the "Merge" button.
6. Return to the "Pull request" tab.
7. Open the other pull request.
8. Scroll down and notice that there is a message indicating "This branch has conflicts that must be resolved."
   - Notice also that the "Squash and merge" button is disabled.

#### Resolving Conflicts

Because you both changed the same line of the `README.md` file, there is now a conflict between the change that was merged into `oss2-practice` and the change that is contained in this pull request.  Git is unable to automatically determine which change to retain, thus you must resolve the conflict manually.

The most straight forward way to resolve small conflicts is to use GitHub's Merge tool as follows:

1. Click the "Resolve conflicts" button.
2. You will see the contents of the "README.md" file displayed in an editor.
3. The conflict will be displayed something like the following:
   - ![A conflict in the `README.md` file.](./images/conflict.png)
4. To resolve the conflict you may:
   - Edit the file manually.
   - Use the "Accept..." options just above the conflict.
5. In this case click "Accept both changes".
   - You will see the contents of the file change to include both of the changes.
6. Click the "Mark as resolved" button.
7. You will see a green checkmark appear next to the `README.md` file in the left panel.
   - If there were more files containing conflicts you would address each of them.
8. Click the "Sign off and commit merge" button.
   - This merges the changes into your feature branch and make them a part of your pull request.
9. Click the "Squash and merge" button.
10. Go to the `oss2-practice` branch and confirm that the `README.md` file now contains both of your changes.

#### Contributing to the Upstream

You have now collaborated on changes and merged them into your shared feature branch. Assuming those changes address an issue you are ready to contribute them to the upstream.  

1. Make a pull request to the upstream repository for your `oss2-practice` branch.
   - This is exactly like making the pull requests you've been making in all of the assignments thus far.
2. Visit the upstream FarmData2 repository.
3. Click the "Pull requests" tab.
4. Confirm that your pull request for your `oss2-practice` branch is there and contains your changes.

#### Getting the Changes

Now that the changes have been merged into the `oss2-practice` branch in your shared repository you'll want get those changes.

1. Change to the `oss2-practice` branch in your local repository.
2. `git pull origin oss2-practice`
3. Confirm that the `README.md` file in your local repository has the changes.

You now have the most up to date version of the `oss2-practice` branch. If you were to continue working on the feature you would make a new feature branch for your next set of changes.

#### Reducing Conflicts

As you have seen, conflicts between changes can arise when working with this type of collaborative workflow. There are several strategies that you can use to reduce the frequency and magnitude of conflicts:
- Make small changes.
  - By making small changes they are less likely to conflict with other's changes. 
- Merge changes frequently.
  - By merging changes frequently others will be able to pull your changes sooner. This allows them to continue their work from from the most up to date code and thus makes it less likely that their work will conflict with yours.
- Coordinate your work.
  - By coordinating your work you can often avoid working on the same files or the same sections of the same file.  This will reduce the likelihood of creating conflicts.
- Work side-by-side.
  - When you need to make changes to the same section of a file or changes across a range of files that are likely to create conflicts, you can work side-by-side and make all of the changes together. These changes would then be included in a single pull request and would not create a conflict.

---

![Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png "Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License") All textual materials used in this repository are licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/)

![GPL V3 or Later](https://www.gnu.org/graphics/gplv3-or-later-sm.png "GPL V3 or later") All executable code in this repository is licensed under the [GNU General Public License Version 3 or later](https://www.gnu.org/licenses/gpl.txt)
