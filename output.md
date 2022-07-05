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
![image](https://user-images.githubusercontent.com/108346788/177385596-de3c28ee-cebd-4a55-9cba-98acbca935a0.png)


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

Require pull request reviews before merging
When enabled, all commits must be made to a non-protected branch and submitted via a pull request before they can be merged into a branch that matches this rule.
now the master branch is protected from unwanted merge reqests.

answer to question 15 - 
15 - replace the homescreen logo with a different one 
[TL;DL - didn't have enough time to keep digging due to heavy workload, so i mentioned the thinking process and steps i did in order to try and resolve it]

I wasn't able to complete this task  - will explain the TS steps i tried:
so my first thought was to launch the localhost page and right click on the image then "inspect"
![image](https://user-images.githubusercontent.com/108346788/177379756-225e9fe1-9fd2-4b27-98f0-685c126eb7e3.png)

then to locate the path in which the picture is saved and just download a new pic and rename it to "stan.png" and paste it instead  of the current one, so it will replace the current logo. 
after doing so, and firing up stan's workshop again, i can see that the image was not changed, so what i did is i tried to remove the pic completely from my local folder in the computer and then ran the microservice again
and still - the old pic was showing.

after trying to investigate further and realizing that the docker is taking the pic from some remote image / repo 
i tried to change the pic in my forked git repo as well , and it didnt help. 
so what i tried to do is to search which container is the one who is running this stan.png and i found out it was robotshop/rs-web container 
so what i searched next is how to find the location of the file and replace it in that container. 
i used these commands to find out
to see all running containers used [docker ps], then used the copy command  [docker cp stan.png a8aabbbeaa77:/media]
![image](https://user-images.githubusercontent.com/108346788/177382345-b7600777-00e6-453c-abec-bd842ed4096e.png)

then it didn't work as well, so tried to search and invastigate deeper. 
after searching for a while, i found out that the docker is using a remote imgae that contains the files (robotshop\rs-web) and i tried to create my own image 
![image](https://user-images.githubusercontent.com/108346788/177383503-173078cc-1051-4683-b447-021f82aeb7c0.png)

and uploaded it to the dokcer hub, then pulled it and used it but it didnt work  - also modified the docker-compose.yaml
![image](https://user-images.githubusercontent.com/108346788/177386289-65cf2cf8-58d3-481c-8b0f-3b06c1a59148.png)

but then got an error while launching the robotshop:  hermajesty/re-web is invalid reference format

also read a little about creating a volume in docker, but afer playing with the .env file and the dokcer-compose file, the robtshop didnt fireup at all 
so i had to remove everything and start over. 

to conclude: 
after all the invastigation i did (if i had more time im sure i would have figured it out), i didnt manage to resolve this task, but if i had more time 
i would have searched on creating an image like i tried and importing it correctly + modifying the docker file correctly. 













