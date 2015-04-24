# xlsx-git
Convert .xlsx files to XML before committing them to git

## Overview
.xlsx (and other MS Office files) are stored as ZIP-compressed XML files. Git, by default, treats them as binary files, so whenever you make a change to an Excel file and then commit it to your repo, almost the entire content of the file changes. Git tools like git-diff or git-revert thus can't do much good. 

xlsx-git provides hooks to convert .xlsx files into their XML format before committing them. This means you get the benefit of plain text source files, but you don't have to convert your .xlsx files back and forth yourself.

## Issues
 - **NOT TESTED AND MAY WIPE OUT ALL YOUR FILES**.
 - risk of conflicts with other files

### Checkout restrictions
When you have .xlsx files in your repo, you won't be able to checkout other branches or commits because the post-checkout hook always leaves the .xlsx files in a "modified" state. This protects you against accidentally losing saved but not committed work in Excel. Before `checkout`, use `git stash` to get to a clean state by hiding away your Excel files.

## Installation and Use
1. Place pre-commit and post-commit in the .git/hooks/ directory of your repository. 
2. Make sure they are executable (e.g., `chmod 755 *-commit`)

## Dependencies
I use Cygwin and the GNU tools that go with that. With Git Extensions or MinGW you may need some other basic commands, like dirname and basename. In addition:
* `zip` and `unzip`
