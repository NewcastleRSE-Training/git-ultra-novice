

This lesson was forked from UCL's git-novice

## Instructor Notes

### Pull Requests Episode
This episode has been significantly reworked from Sarah Stevens' https://carpentries-incubator.github.io/git-novice-branch-pr/10-pull-requests.html

#### Countries Repository

## before
RESET the 'countries' repo https://github.com/NclRSE-Training/countries (see below)
instructor permissions ?
review settings ?

## lunchtime
enrol participants as collaborators on 'countries' repo 
https://github.com/NclRSE-Training/countries/settings/access automatically with https://github.com/NewcastleRSE-Training/AddCollaborators/
role:  write

## after

### Revert Countries Repository
https://github.com/NclRSE-Training/countries
_(NB this repository will be reset in a few days time so that we can use it for our next course)_

remove outside collaborators https://github.com/NclRSE-Training/countries/settings/access?query=filter%3Aoutside_collaborators

Robin Wardle
5 Feb 2025 4:01 PM
I've reset the countries repo, 
## procedure:
#### Github
- Disable branch protection rules in GitHub Repository Settings (Danger Zone) https://github.com/NclRSE-Training/countries/settings

#### In local terminal:

1. cd to local repo (clone if necessary)
2. `git pull`
3. `git reset --hard v1.0.1` (v1.0.1 is the last "stable" tag, if we update the repo we will need a newer tag)
4. `git push origin +main` (forces a HEAD reset)
#### On GitHub

7. Re-enable branch protection rules in GitHub Repository Settings
8. Delete all the student-created branches (this will also delete pending attached pull requests) in GitHub Repository (try? https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/delete-all-branches-except-master-main-local-remote)
7. Revoke all the student collaborator permissions in the GitHub OrganizationI haven't done the last step yet in case any of the students did want to practice on the repo again. Maybe do that next week.
This is why I didn't want to get into resetting a repo in the lesson, it's moderately complex when dealing with GitHub. `git revert` will reset the HEAD but it does this by undoing each commit in turn, adding each older commit as a new commit which preserves the history. This can cause merge conflicts and be otherwise a headache. `git reset` removes history but you need to force the change. I can't actually remember what `git rebase` does! 
