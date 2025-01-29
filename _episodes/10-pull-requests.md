---
title: Pull Requests
teaching: 60
exercises: 15
questions:
- "What are pull requests for?"
- "How can I make a pull request?"
objectives:
- "Define the terms fork, clone, origin, remote, upstream"
- "Understand how to make a pull request and what they are useful for"
keypoints:
- "Pull requests suggest changes to repos where you don't have privileges"
---


Pull requests are a great way to collaborate with others using github.
Instead of making changes directly to a repository you can suggest changes to a repo.
This can be useful if you don't have permission to modify a repository directly or
you want someone else to review your changes.

For this lesson we will be working on the `countries` repository together.
Open the github link for the `countries` repo provided by the instructor 
in your browser window.

UPDATE INSERT IMAGE: GitHub browser window

> ## Repo owner differences
>
> You may have noticed that the `countries` repo in this lesson's pictures 
> is owned by the 'NclRSE-Training' organization and this doesn't match
> the address you were given.
> This is to be expected because this will differ depending on 
> what organization your instructor used to setup the `countries` repo.
> 
> UPDATE:  You will also see your username where the 'XXXXXXX' is in the pictures.
> 
{: .callout}


UPDATE INSERT IMAGE: showing 'branch' like https://carpentries-incubator.github.io/git-novice-branch-pr/fig/github_screenshot_switch_github_branch.png

Now let's each add a new country to the repository.
First let's make a new branch to work on.  This will keep our 'main' version
in sync with the authoritative version of the repository.
We can name our branch descriptively after the country we will be adding.
Mine will be `editMyCountry` since I'll be working with France.
UPDATE EMPHASISE: Please pick a different country and shout it out (or add it to the collaborative document) 
so no one else chooses the same one.

Once at the `countries` repo, click **Branch** which can be found above the list of files, on the left
Previously, we created a branch on our local copy of a repository.  Now we are creating a branch in the online copy of the repository.
Click the **New branch** button at the top right, and enter a name for your branch. Select your branch from the list to start working on it.

Next we will copy `united_states.md` and change the name to the name of our chosen country.
Hint: You may need to do some internet searching to fill in the information.

UPDATE INSERT IMAGE: show use of file navigator to edit

Open the file navigator on the left
Click the name of the file we want to copy
Click the copy icon (Copy raw file) next to Raw at top right of the view/edit panel
In the navigator, click the + (Add File) button at the top
Type your country name into the box 'Name your file'
Click then paste into the edit panel
Change the text


~~~
Population: 66,991,000
Capital: Paris
~~~
{: .output}

Next let's add and commit the changes to the repo.

Click **Commit Changes** at top right
In the pop up box, enter an extended description and click **Commit Changes** button
      _note the option to "Create a new branch for this commit and start a pull request" here_

In some cases we may not have permission to push changes directly to the 
upstream/authoritative repo or we might like our changes to be reviewed regardless 
of permissions, so we'll create a `pull request`. 
A `pull request` is a **request** for a member of the upstream repository to **pull** 
our changes into the upstream repository from a `fork`, allowing them to request further 
changes/improvements and make comments on the changes before doing so. 

Use the breadcrumb trail to navigate to the top level of the countries repository
Github already suspects that we are going to want to make a pull request so we can click
the 'Compare & pull request' button to start a new pull request.

UPDATE INSERT IMAGE: create pull request like https://carpentries-incubator.github.io/git-novice-branch-pr/fig/github_screenshot_makingPR1.png

The base should be the main branch and compare to your branch
You can add more a description if there is anything you'd like 
to add for the person who reviews your suggestion.
Then you can click the 'create pull request button' to submit the pull request.

UPDATE INSERT IMAGE: create PR2 like https://carpentries-incubator.github.io/git-novice-branch-pr/fig/github_screenshot_makingPR2.png


Now someone with privileges to the repo can review it, give comments and
suggestions, and merge it into the main branch.
In our pull request they can see any messages we left or click and look at the commits that were made and see the files changed.

Our collaborator reviewing the pull request noticed that we forgot to add the largest city so let's add it and update our pull request.

~~~
Population: 66,991,000
Capital: Paris
Largest City: Paris
~~~
{: .output}

Next we will add and commit these changes.

If we reload the pull request, we'll see that the new commit was added to the 
pull request and the changes have been automatically updated.
New commits pushed to the same branch are included in the previous pull request.
If you want to suggest changes separately you need to make separate branches but 
if you want the changes to be considered together you should put them in the same branch.

UPDATE INSERT IMAGE: reviewer's view of pull request like https://carpentries-incubator.github.io/git-novice-branch-pr/fig/github_screenshot_after_new_commit.png

Once your branch has been merged, it's good practice to delete it.

UPDATE INSERT IMAGE: delete your branch

# Extension 1 Working locally
We don't have to work online in order to branch someone else's repository.  If we have permission, we can clone and branch locally as we did earlier. 
UPDATE REMOVE?: NB some respositories don't allow you to clone.  In this case it's necessary to fork, see https://carpentries-incubator.github.io/git-novice-branch-pr/10-pull-requests/ for an example.
We're allowed to clone this repository so let's get started:

~~~
$ cd ~/Desktop
$ git clone https://github.com/INSTRUCTOR-GIVEN/countries.git
~~~
{: .bash}
_update this URL for the repo we're going to use?_

~~~
Cloning into 'countries'...
remote: Counting objects: 6, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), done.
~~~
{: .output}

_do we need to tlk about upstream remote?_

Copy the web address for this repo 
(from the web address line or click the 'clone and download' and copy that).

UPDATE INSERT IMAGE like https://carpentries-incubator.github.io/git-novice-branch-pr/fig/github_screenshot_upstream_repo.png

Then back in your terminal, navigate into the cloned repo and add the remote 
connection to this repository.
UPDATE - IS THIS CORRECT FOR OUR CASE? For this command we must give the remote a different nickname, 
where our original remote is 'origin'
this new remote will be called 'upstream'.
You could give it a different nickname but 'upstream' is a common nickname for
the authoritative repository.

~~~
$ cd countries
$ git remote add upstream https://github.com/INSTRUCTOR-GIVEN/countries.git
~~~
{: .bash}

> ## If you tried copying the command above...
>
> You will have to replace 'INSTRUCTOR-GIVEN' with the site your instructor
> indicated at the beginning of this lesson. This will vary depending
> on how your instructor set up for this lesson.
> 
> 
{: .callout}

At anytime you can see the remote connections your repo has using the following command:

~~~
$ git remote -v
~~~
{: .bash}

~~~
origin	https://github.com/USERNAME/countries.git (fetch)
origin	https://github.com/USERNAME/countries.git (push)
upstream	https://github.com/INSTRUCTOR-GIVEN/countries.git (fetch)
upstream	https://github.com/INSTRUCTOR-GIVEN/countries.git (push)
~~~
{: .output}

Now that we have this setup done we will be able to suggest 
changes to this repo using a pull request.
Each person will update their country's file with a National Dish (food for which the country is famous).  
Hint: It's fine to make something up or search the internet.

Let's make sure we have the most up to date copy of the remote repository on GitHub

~~~
$ git pull upstream main
~~~
{: .bash}

Please use the same country as before so no one else chooses the same one.
We will create the branch and switch into in one step 
as we learned earlier in the branching lesson.

~~~
$ git checkout -b editMyCountry
~~~
{: .bash}

~~~
Switched to a new branch 'editMyCountry'
~~~
{: .output}

Finally before we proceed to adding the new file, we will double 
check that we are on the right branch.

~~~
$ git branch
~~~
{: .bash}

~~~
* editMyCountry
  main
~~~
{: .output}

Next use nano to edit the file for your chosen country.  
~~~
$ nano MyCountry.md
$ cat MyCountry.md
~~~
{: .bash}

~~~
Population: 66,991,000
Capital: Paris
National Dish: Pot-au-feu
~~~
{: .output}

Next let's add and commit the changes to the repo.

~~~
$ git add MyCountry.md
$ git commit -m "Added National dish for MyCountry"
~~~
{: .bash}

~~~
[editMyCountry 79a312a] Added National dish for MyCountry
 1 file changed, 2 insertions(+), 2 deletions(-)
~~~
{: .output}

As before, we can't or don't want to push changes directly to the main branch.
We will create a `pull request`
In order to create a `pull request`, we must push our new branch containing the
 changes we'd like to submit to the remote `origin`, on GitHub.

 ~~~
$ git push origin editMyCountry
~~~
{: .bash}

~~~
Counting objects: 4, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 783 bytes | 0 bytes/s, done.
Total 4 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
To https://github.com/USERNAME/countries.git
   2037539..79a312a  editMyCountry -> editMyCountry
~~~
{: .output}

Next go to the online repo on GitHub and reload the page.
You won't see the new file added in the list of files but you will see 
that you recently pushed a new branch to the repository.

If you wish to view your new branch you can click on the 'Branch' drop down menu
and select that branch.

UPDATE INSERT IMAGE: like https://carpentries-incubator.github.io/git-novice-branch-pr/fig/github_screenshot_switch_github_branch.png

Then you should be able to view the files and commits in that branch.

UPDATE INSERT IMAGE: like https://carpentries-incubator.github.io/git-novice-branch-pr/fig/github_screenshot_makingPR1.png

Github already suspects that we are going to want to make a pull request so we can click
the 'Compare & pull request' button to start a new pull request as we did earlier.

UPDATE INSERT IMAGE: like https://carpentries-incubator.github.io/git-novice-branch-pr/fig/github_screenshot_makingPR2.png

