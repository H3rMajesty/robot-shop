Steps i did to run this sample microservice application - 
installed docker 
then right click on the repo folder then "open in terminal" (windows powershell) 
then ran these commands: 
[docker-compose pull]
[docker-compose up]
which i took from here: 
![steps ](https://user-images.githubusercontent.com/108346788/176701500-ca109694-813d-4f93-9792-3b206b52edea.png)
then typed in my browser "localhost:8080"
and this is the homepage 
![homepage](https://user-images.githubusercontent.com/108346788/176701833-a3b29a81-0b25-4af6-8e43-354fcde8a102.png)

why is commiting directly to the master branch is wrong?  (i didn't get any error while merging to the master, so searched the web for possible reasons to why commiting directly to the master can be problematic) 

when commiting directly to the master branch this error can come up: "failed to push some refs to"
It occurs most of the time because multiple contributors are working on the same branch and the remote repository is further along than what you currently have on your local machine.

Master branch should contain thoroughly tested and deploy-able version of code which means merge develop branch with master branch whenever you are ready to release your changes.

to prevent that we can create a Branch protection rule 
Git branch protection rules are a powerful configuration option that enables repository administrators to enforce security policies. This helps protect the git branches from unexpected code commits or deletion by any unauthorized person(s) / user group(s)
how to activate:
Step 1: Navigate to your repository homepage at Github. 
Then click on the Settings Option. You’ll be taken to the repository settings page as shown below. Click on the branches to set the branch protection rules.
You’ll see the branches page where you can set the default branch for your repository and also add the branch protection rules. 
Step 2: Click on the Add Rule option
Step 3: Add the branch name you want to protect in the Branch Name field
Step 4:  Add the protection rules to your branch
Next, you’ll add the branch protection rules. There are 6 options available we will use the first one which is - 

 1. Require pull request reviews before merging
When enabled, all commits must be made to a non-protected branch and submitted via a pull request before they can be merged into a branch that matches this rule.
now the master branch is protected from unwanted merge reqests 
