# Working with Github

GitHub is a website and cloud-based platform where we can store, manage, share code and work together with others by tracking and controlling changes to the code.

## Key fundamentals of GitHub

- **Repositories**: Represents centralized location that stores a collection of files and their revision history for maintaining the versions of development.

- **Branches**: A unique set of code changes with a unique name. When more than one person is working in the project and making changes, in order to encapsulate our changes (like adding a new feature or fixing a bug) we make a new branch.

- **Commits**: Records changes to one or more files in your branch, similar to saving edited file. Git assigns each commit a unique ID, that identifies: the specific change, time of made change and change creator.

- **Pull requests**: Making a pull request is making a proposal to merge changes made in one repository branch into another, typically from a feature branch into the main branch. Before integrating the changes into the main branch the proposed code changes can be reviewed and approved by collaborators.


## Where do we start?

- **Create an account on GitHub**

- **Learn how to post your work on GitHub using the key principles of collaborative working**
  
- **Learn how to download the code for your own use**


## Common "GitHub Flow" Operations

- **Initialize empty repository**: Use `git init`

- **Add changes in our working directory to the staging area**: Use `git add` to add changes in our working directory to staging area where we prepare a snapshot of our project’s current state before committing it to the repository. It tells Git what updates we want to include to a particular file in the next commit. However, changes are not actually recorded until running git commit.

- **Save the changes - and leave a specific message for the changes done**: `git commit -m `.

- **Define the remote repository**: `git remote add origin [repo-url]` and `git remote set-url origin [repo-url]` before push your code to the master branch of the remote repository defined with "origin" and -u let you point your current local branch to the remote master branch.

- **Upload content from local to remote repositorys**: `git push origin 'branch-name'` to send (or push) the commits from our local branch in our local Git repository to the remote repository. 

- **Download from exising remote repository **: `git clone [repo-url]`

Remember, working with files and directories is a common task that can involve complex operations and error handling, especially when dealing with file system permissions, symbolic links, and large directories.


As alternative to GitHub we can also use: Gitlab, Bitbucket, SourceForge and so on, but here we will stick on working with Github.


# Github exercises while working with Java

## Example 1: Upload your first Java project to Github

Following the github flow operations, create a new simple Java "Hello world" project, and upload it on your Github repository.

### Solution

We will do this by using command prompt approach. 

**TO DO** STEPS:
- **Create an github account by entering email, password and username**

- **Verify our account by entering code sent on email.** 

- **Login to our github account**

- **Choose create repository and give the repostory name.**

- **After creating new repository, we see all required commands to push already existing and new repository** (we follow the commands for creating new repository):
```
echo "# Programming-Languages" >> README.md
git init
git add README.md
git commit -m "This is my first commit, let's have some fun!"
git branch -M main
git remote add origin https://github.com/filkovaivana1/Programming-Languages.git
git push -u origin main
```

- **Create simple print "Hello world !" Java project which after creating should look like:**
```java
public class Main {
    public static void main(String[] args) {
        //TIP Press <shortcut actionId="ShowIntentionActions"/> with your caret at the highlighted text
        // to see how IntelliJ IDEA suggests fixing it.
        System.out.printf("Hello and welcome!");

        for (int i = 1; i <= 5; i++) {
            //TIP Press <shortcut actionId="Debug"/> to start debugging your code. We have set one <icon src="AllIcons.Debugger.Db_set_breakpoint"/> breakpoint
            // for you, but you can always add more by pressing <shortcut actionId="ToggleLineBreakpoint"/>.
            System.out.println("i = " + i);
        }
    }
}
```

- **Open command prompt and set our current working directory to the project directory (or simply open terminal from your project in intelliJ)**
```
cd [project_directory]
``` 

- **Initialize empty git repository locally (if already not done while creating the Java project)**
```
git init
```

- **Add main branch**
```
git branch -M main
```

- **And set the remote origin to be our remote repository, which means everything we push will go there**
```
git remote add origin https://github.com/filkovaivana1/Programming-Languages.git
```

- **Add our code in the local git repository**
```
git add .
```

- **We commit our changes**
```
git commit -m "This is my first commit, let's have some fun!"
```

- **And finaly we push everything we commited on the remote git repository**
```
git push -u origin main
```

But pushing for the frist time will require some preauthorization: 
![image](https://github.com/user-attachments/assets/55ad39c6-239f-49a6-8f86-7fc768d21b86)

![image](https://github.com/user-attachments/assets/e2d5b8b4-ead3-4a40-8711-6b3502fcd9be)

After successful preauthorization we can continue pushing our changes and if everything as needed we will get response message that pushing code is done 
![image](https://github.com/user-attachments/assets/6a6afcb3-618a-4b89-a97c-d57d28a902fc)


## Example 2: Create a MD file
In our newly created repository, create 'README.md' and upload it to your github repository.

### Solution
Open command prompt and set our current working directory to the project directory (or simply open terminal from your project in intelliJ)
```
cd project_directory
``` 

Create md file:
```
echo "# Programming-Languages" >> README.md
```

Add our code in the local git repository
```
git add .
```

Commit our changes
```
git commit -m "Add README file"
```

Push everything commited on the remote git repository
```
git push -u origin main

```

## Example 3: Upload to a new branch
Same as Example 1 but upload it to a new branch called "new-branch": 

### Solution
Use this command:  ```git checkout -b new-branch``` to create and switch to new-branch

```
	cd [project_directory]
	git checkout -b new-branch
	git add .
	git commit -m "commit on new branch!"
	git push -u origin new-branch

```


## Example 4: Take already existing project
Get a copy of the project from the git repository: https://github.com/filkovaivana1/Programming-Languages.git 

### Solution
Simply by choosing clone from the drop down menu on github link:

Or by this commands in terminal:
```
cd [new_project_directory]
git clone https://github.com/filkovaivana1/Programming-Languages.git
```


## Example 5: Delete repository
Get the project from the following git repository link: 

### Solution
For deleting local repo use this command in terminal:
```
   git status
   rm -fr .git
   git status
```
After successful deleting on getting the status we should get message: 
```Fatal: not a git repository (or any of the parent directories): .git```

For deleting a repo remotely to github: Go to Settings -> General tab -> (scroll down to) Danger Zone -> Delete this repository
 
