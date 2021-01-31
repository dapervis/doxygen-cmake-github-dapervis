# doxygen-cmake-github
Demonstrates Doxygen html generation and publishing on GitHub Pages. The Doxygen files for this project can be seen [here](https://github.com/dapervis/doxygen-cmake-github-dapervis).

# How to use
1. Point your browser to this repository (https://github.com/semcneil/doxygen-cmake-github)
2. Press the "Use this template" button
3. Give your repository a new name
4. Write a short (one sentence) description of what your project will do
5. Click the Create repository from template button

## VS Code VM Instructions
1. VS Code needs the following extension added:
    1. C/C++ from Microsoft
    1. CMake Tools also from Microsoft
1. Connect to Host in New Window
2. Open a terminal (ctrl+\`)
1. Initialize git if you haven't already using the same email you used on your GitHub account:
    1. `git config --global user.email "you@example.com"`
    1. `git config --global user.name "Your Name"`
3. Navigate to the parent directory for your project
4. Clone your repository using the URL from the GitHub Code button on your repository and on VS Code either clone repository on the Welcome screen or open the Command Palette (ctrl+shift+P), type `git clone` and select `Git: Clone`
    1. Select the parent directory for your project
    1. Open the cloned repository either as prompted or by adding the newly created folder to your workspace by the Welcome tab's Open folder link or File -> Add Folder to Workspace
    1. If you use the command line `git clone` the authentications for pushing to your online repository are not set up
6. If you wait a bit it should ask you which kit you want to use (at the time of this writing I typically use GCC 9.3.0)
7. Allow Intellisense if prompted
8. Edit README.md to reflect your new project
9. Edit the `project` line in the CMakeLists.txt file to have your project's name and version
10. Edit the `add_executable` line in the CMakeLists.txt file to change the name of the executable file to something relevant
11. Change the @brief, @details, @author, and @date in src/main.cpp
1. To create the PDF on a standard Ubuntu install, the following need to be added: `sudo apt install graphviz texlive-latex-base texlive-latex-recommended texlive-latex-extra`
1. Doxygen also needs installing: `sudo apt install doxygen`
12. In the terminal, change to the `build` directory (should have been automatically generated)
13. Run the following:
    1. `make`
    1. `make docs`
    1. `make pdf`
14. Add the newly named PDF to git staging (`git status` -> `git add docs/yourprojectname.pdf`)
15. Commit all the changes: `git commit -a -m "Initial commit"`
16. Push the changes to GitHub: `git push origin main`
17. Back at your repository on GitHub, refresh the page to show latest commit
18. In the Settings tab, scroll down to GitHub Pages
19. Select "Branch: main" as source and "/docs" as the folder and then press Save
20. Scroll back down to GitHub Pages and click the link to the published site
21. You now have a C++ repository with doxygen output hosted on GitHub Pages
    1. The link usually doesn't work for a while (minutes to hours). This can be worked around by adding `index.html` to the end of the URL. A second commit will also fix it once the commit propagates over to GitHub Pages.
    1. You can see the PDF file generated by Doxygen by adding the name of the PDF to the end of the URL. It will be of the form `projectname.pdf` and can be seen in the `docs` folder.
    1. It can take a few minutes for a new `git push origin main` to propagate over to GitHub Pages
1. Edit README.md to reflect your project usage and point to the Doxygen output for your project
1. Stage the commit (`git add README.md`)
1. Commit (`git commit -a -m "Describe your changes here"`)
1. Push your changes to GitHub as before (`git push origin main`)

## General Usage
During normal development, you will change main.cpp, maybe add more files in the src directory, make them, and run them. To update the documentation on the web do the following at a terminal prompt in your project's `build` directory:
1. `make`
1. `make docs`
1. `make pdf`
Then in your project's root directory do the following:
1. Check the git status: `git status`
1. `git commit -a -m "Describe your changes since last commit"`
    1. The `-a` flag is used to commit all the updated documentation files
    1. VS Code also has git built into it, but the use of branches isn't as easy a workflow as the commandline offers for me (personal opinion).

# References
1. https://www.doxygen.nl/manual/docblocks.html
1. https://stackoverflow.com/questions/44212101/cmake-how-to-have-add-custom-command-run-after-all-project-files-are-built
1. Very useful overview: https://caiorss.github.io/C-Cpp-Notes/Doxygen-documentation.html
1. https://devblogs.microsoft.com/cppblog/clear-functional-c-documentation-with-sphinx-breathe-doxygen-cmake/
1. https://vicrucann.github.io/tutorials/quick-cmake-doxygen/
1. https://medium.com/practical-coding/c-documentation-with-doxygen-cmake-sphinx-breathe-for-those-of-use-who-are-totally-lost-7d555386fe13
1. https://stackoverflow.com/questions/18590445/cmake-custom-command-to-copy-and-rename
