# 01 - Introduction Hands-On Activities

These hands-on activities will guide you through the setup of the FarmData2 Development Environment where you will complete all of the FD2 School Activities. Typically in-class, hands-on activities can be completed in pairs or small groups.  However, because everyone must have a working FarmData2 Development Environment, this first activity must be done individually.

## Preliminaries

1. Visit the upstream FarmData2-School repository that your instructor created for your team.
2. Skim the content in the `README.md` file displayed.
3. In the "Help and Communications" section, use the link to the "FarmData2 Zulip Chat" to create an account (or possibly remember that you already have one).
   - Notice that there is a "FarmData2 School" channel specifically for discussion FD2 School activities. 
   - You should use this channel to ask questions about the FD2 School activities.
   - Also, feel free to respond to questions from others!

## Running the FarmData2 Development Environment in the Browser

All of your work on the FD2 School activities should be done in the FD2 Development environment. This ensures that you are working with the correct versions of all of the tools and libraries used by FarmData2.

1. Find the installation directions in your upstream FarmData2-School repository (hint: See `INSTALL.md`).
2. Follow the instructions for "Running in GitHub Codespaces".
   - In step 11, follow part "i. Open in your Browser".
3. Be sure that you follow the link in step 12 to finish the setup.
   - In step 3 you will run the `setup.bash` script. This script takes some time to run. Eventually (after a few minutes) it will ask you to authenticate with GitHub. To do so:
     1. Choose "__HTTP__" as the preferred protocol git Operations on this host.
     2. Respond "__Yes__" to authenticating Git with your GitHub credentials.
     3. Choose "__Paste an authentication token__" when asked how you would like to authenticate GitHub CLI.
     4. Copy your GitHub token to the Clipboard
     5. Paste it into the "_NoVNC Clipboard_" using the tool palate at the left of the window. 
     6. Use "__Ctrl-Shift-V__" to paste the token into the terminal.
4. After you have completed step 12, practice stopping and then restarting your FD2 Development Environment using the instructions at the bottom of the "Running in GitHub Codespaces" installation page.

## Running the FarmData2 Development Environment in VNC

Running the development environment in the browser works very well as long as everything you do is within the environment. However, copying and pasting information between your host machine and the development environment in the browser the copy/paste process is cumbersome, as you saw when pasting your PAT earlier.

If you are happy to work fully within the development environment for these assignments you can continue running it in the browser. However, if you prefer to have a more natural copy and paste operation between your host machine and the development environment you will want to run it in a Virtual Network Client (VNC).

To run the FarmData2 Development Environment in VNC, return to step 11 of the "Running in GitHub Codespaces" document and follow part "ii. Open on your Machine with VNC".
    - Note that this will required you install two pieces of software on your machine.  Reach out on the "Install" channel on Zulip if you have any difficulties with these installs.