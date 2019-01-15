# CSC 519 - DevOps
## HW0
### Complete moodle, mattermost, stack overflow profiles
* Moodle - https://moodle-courses1819.wolfware.ncsu.edu/user/profile.php?id=131227
* Mattermost - Username: rayandasoriya
* StackOverflow - https://stackoverflow.com/c/ncsu/users/201/

### Opunit checks
The Opunit check contains several validations of the software and settings which are required for this course. All the changes have been successfully made. The screenshot of the check is available below.


### Pipeline workshop
The pipeline workshop was a process to create and automate the deveopment and production processes using the concept of pipeline. Following tasks have been performed.
1. Clone the Pipelines repo from GitHub adn runt he opunit verify local. We can see that most of the checks are failing right now. 
![](/images/2.png)
2. A hook-demo repository has been created which contains a post commit file. This file will open automatically whenever a commit has been created. When a commit has been created, it triggers the post commit file and this file will open the google.com homepage in the default browser.
!(/images/3.png)
3. Installing npm inside the App/ directory and running it and verifying the results using npm test.
!(/images/4.png)
!(/images/5.png)
4. Add a tets stage and check if the program fails on changing the desired output. Here, we have changed "Hi From" to "Bye From" and we observed that the test has failed. We created a pre-commit hook to perform this task.
!(/images/6.png)
5. Create two new directories under deploy. This will contain the hooks which will help us to hold the contents of our deployed web application. We created a post-receive hook. After that, pm2 is installed which makes sure that the webapplication is working even after the crashes. Final step consists of linking with the remote repo. Now the chnages in the main.js is reverted and the changes are commited. Upon committing the chabges and psuhing, we were able to visit the localhost and see the changes.
!(/images/7.png)


### Screencast
The screencast contains following items:
*
* 

