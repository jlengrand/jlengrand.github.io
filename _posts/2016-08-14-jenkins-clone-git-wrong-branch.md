Cloning a workspace in Jenkins with a Git SVM setup does not checkout the correct branch. 

Hi there, 

This is a strange behaviour I have noticed when using Jenkins lately, that caused us a few headaches before we realize what was happening. 

At [Spacemetric](http://www.spacemetric.com/ "Spacemetric"), we are using both Gitlab and Jenkins for CI. 

* [Gitlab](https://about.gitlab.com/gitlab-ci/) is used to store the source code, and for each commit we make sure that all our jars can be built fine. 
* [Jenkins](https://jenkins.io/) is used to create our releases, generate our front end products and perform daily/weekly integration and a more complete set of tests and generate test reports. 

One of the main benefits from Gitlab compared to Jenkins is that all branches are tested automatically without creating new jobs, as long as the branch contains the magic **gitlab-ci.yml** file. 
In order for Jenkins to start integration tests on a new branch, we actually have to clone the job that is used for master and set it up against the new branch. We only do this for branches that will be used for a coming release.

And this is where we found strange behavior. 

* Let's say I have a job set up to run against my master branch and I want the same things to be run against our 4.4 branch

* I will use the **new Job** feature, and choose **Clone from existing job**.
* I will then go in the SCM part of my new job and change the branch from **master** to **4.4**
* And I will run the build. 

Now, I would expect my job to run against 4.4. The thing is, it will keep doing a checkout of the **last commit from the master branch on Gitlab**. You can easily verify this by checking the hash of the relevant git commit

![Copy from part of the Jenkins SCM upload](https://dl.dropboxusercontent.com/u/4286043/00_Website/03_Images/2016-08-14_16h56_07.png)

Very troubling, as it does not match what is indicated in the Job configuration. 

Now, fixing this is actually very easy : **Simply wipe out the new Job's workspace and restart the job**.
With a clean workspace, the job will start cloning the git repo from scratch and will behave as expected. 

Hope this helps some of you. 
Cheers, 
Julien
