# xlsx-git
Convert .xlsx files to XML before committing them to git

## Overview
.xlsx (and other MS Office files) are stored as ZIP-compressed XML files. Git, by default, treats them as binary files, so whenever you make a change to an Excel file and then commit it to your repo, almost the entire content of the file changes. Git tools like git-diff or git-revert thus can't do much good. 

xlsx-git provides hooks to convert .xlsx files into their XML format before committing them. This means you get the benefit of plain text source files, but you don't have to convert your .xlsx files back and forth yourself.

## Issues
 - **NOT TESTED AND MAY WIPE OUT ALL YOUR FILES**.
 - xlsx-git automatically adds and commits *any* .xlsx files in your working tree, regardless of whether you've added them yet.
 - risk of conflicts with other files
 - xlsx files don't actually appear in the repository

## Installation and Use
1. Place pre-commit and post-commit in the .git/hooks/ directory of your repository. 
2. Make sure they are executable (e.g., `chmod 755 *-commit`)

## Dependencies
I use Cygwin and the GNU tools that go with that. With Git Extensions or MinGW you may need some other basic commands, like dirname and basename. Some packages in particular:
* `bash` >= 4.0
* `xmllint`
* `zip` and `unzip`
