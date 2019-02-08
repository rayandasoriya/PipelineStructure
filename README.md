# Building Pipeline Structure

The pipeline workshop was a process to create and automate the development and production processes using the concept of a pipeline. Following tasks have been performed.
1. Clone the Pipelines repo from GitHub and run the opunit verify locally. We can see that most of the checks are failing right now. 

For cloning: `git clone --recursive https://github.com/CSC-DevOps/Pipelines`

For Opunit verification: `opunit verify local`

![](/images/2.png)

2. A hook-demo repository has been created which contains a **post-commit** file. This file will open automatically whenever a commit has been created. When a commit has been created, it triggers the post-commit file and this file will open the google.com homepage in the default browser.
The script for post-commit might look something like this:

```sh
#!/bin/sh
open https://google.com/
```

![](/images/3.png)

3. Installing npm inside the App/ directory and running it and verifying the results using npm test.

![](/images/4.png)

![](/images/5.png)

4. Add a test stage and check if the program fails on changing the desired output. Here, we have changed "Hi From" to "Bye From" and we observed that the test has failed. We created a **pre-commit** hook to perform this task.

```sh
#!/bin/bash

npm install
# Get the exit code of tests.
if npm test; then
  echo "Passed tests! Commit ✅ allowed!"
  exit 0
fi
echo "Failed npm tests. Canceling 🚫 commit!"
exit 1
```

![](/images/6.png)

5. Create two new directories under deploy. This will contain the hooks which will help us to hold the contents of our deployed web application. We created a **post-receive** hook. After that, pm2 is installed which makes sure that the web application is working even after the crashes. The final step consists of linking with the remote repo. Now the changes in the main.js are reverted and the changes are committed. Upon committing the changes and pushing, we were able to visit the localhost and see the changes.

The post-receive hook looks like this:

```sh
#!/bin/sh
echo "Current location: $GIT_DIR"
GIT_WORK_TREE=../production-www/ git checkout -f
echo "Pushed to production!"
cd ../production-www
npm install --production
npm run stop
npm run start
```

![](/images/7.png)

6. The opunit verification of the pipeline was also successful. The output is shown below.

![](/images/8.png)

**Note:** The Pipelines directory will open once you recursive clone this repository. The code snippets, images, and screencast contain all the required content for this homework.

### Screencast
The screencast contains the following items:
* Opunit check for the system software
* Initial opunit check for the pipeline
* Implementation of the pipeline 
* Final opunit check for the pipeline

**Link**: http://rayandasoriya.com/DevOps/HW0.mp4

### References
* https://github.com/CSC-DevOps/Course/blob/master/HW/HW0-Pipelines.md
* https://github.com/CSC-DevOps/Pipelines
