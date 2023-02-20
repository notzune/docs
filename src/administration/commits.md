# Proper Git Commits
On this page you will find some guidelines and tips to keeping well organized and written commit messages. This guideline is just a suggestion ofcourse as even I (zune) am guilty of writing subpar and nondescriptive commit messages or commiting a million files at once. This is a habit that I hope to break and that we should all aim to break as well.   

Most of the information on this page was taken from these sources:
> See: [tbaggery.com](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html), [openstack](https://wiki.openstack.org/wiki/GitCommitMessages), [chris.beams.io](http://chris.beams.io/posts/git-commit/)

## Commit Message Guidelines
Here’s a model Git commit message:

```
Capitalized, short (50 chars or less) summary

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug."  This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too

- Typically a hyphen or asterisk is used for the bullet, followed by a
  single space, with blank lines in between, but conventions vary here

- Use a hanging indent
```

A properly formed git commit subject line should always be able to complete the following sentence:
    
"If applied, this commit will *\<your subject line here\>*"
   
Examples:    
"If applied, this commit will **fix issue #2**", "If applied, this commit will **add new pages to the documentation**"

### Rules For Formatting Git Commit Messages
* Separate subject from body with a blank line
* Do not end the subject line with a period
* Capitalize the subject line and each paragraph
* Use the imperative mood in the subject line
* Wrap lines at 72 characters
* Use the body to explain what and why you have done something. 
  * In most cases, you can leave out details about how a change has been made, rather, this should be explained within the code via adding comments

### Information in Commit Messages
* Describe why a change is being made.
* How does it address the issue?
* What effects does the patch have?
* Do not assume the reviewer understands what the original problem was.
* Do not assume the code is self-evident/self-documenting.
* Read the commit message to see if it hints at improved code structure.
* The first commit line is the most important.
* Describe any limitations of the current code.
* Do not include patch set-specific comments.

Details for each point and good commit message examples can be found [here](https://wiki.openstack.org/wiki/GitCommitMessages#Information_in_commit_messages)

## References in commit messages
If the commit refers to an issue, add this information to the commit message header or body. e.g. the GitHub web platform automatically converts issue ids (e.g. #123) to links referring to the related issue. 

In header:
```
[#123] Refer to GitHub issue…
```

In body:
```
…
Fixes #123, #124
```

## Structural Split of Changes
***The cardinal rule for creating good commits is to ensure there is only one "logical change" per commit***.   

There are many reasons why this is an important rule:

- The smaller the amount of code being changed, the quicker & easier it is to review & identify potential flaws.
- If a change is found to be flawed later, it may be necessary to revert the broken commit. This is much easier to do if there are not other unrelated code changes entangled with the original commit.
- When troubleshooting problems using Git's bisect capability, small well defined changes will aid in isolating exactly where the code problem was introduced.
- When browsing history using Git annotate/blame, small well defined changes also aid in isolating exactly where & why a piece of code came from.

## Things to Avoid
Here are some things to avoid when writing your commit messages:

### **Mixing whitespace changes with functional code changes.**
The whitespace changes will obscure the important functional changes, making it harder for a reviewer to correctly determine whether the change is correct.    

**Solution:** Create 2 commits, one with the whitespace changes, one with the functional changes. Typically the whitespace change would be done first, but that need not be a hard rule.

### **Mixing two unrelated functional changes.**
Again the reviewer will find it harder to identify flaws if two unrelated changes are mixed together. If it becomes necessary to later revert a broken commit, the two unrelated changes will need to be untangled, with further risk of bug creation.

### **Sending large new features in a single giant commit.**
It may well be the case that the code for a new feature is only useful when all of it is present.   

This does not, however, imply that the entire feature should be provided in a single commit. New features often entail refactoring existing code.    

It is highly desirable that any refactoring is done in commits which are separate from those implementing the new feature. This helps reviewers and test suites validate that the refactoring has no unintentional functional changes. Even the newly written code can often be split up into multiple pieces that can be independently reviewed.    

For example, changes which add new internal APIs/classes, can be in self-contained commits. Again this leads to easier code review. It also allows other developers to cherry-pick small parts of the work, if the entire new feature is not immediately ready for merge.