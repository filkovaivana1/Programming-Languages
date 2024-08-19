# Debugging

Whether you are just getting started with Java, and you are new to IntelliJ idea, the first thing you need to learn is debbuging.
Knowing how to debbug your application is an essential skill for any Java developer. Here we cover best technicks to debbug Java applications in IntelliJ IDEA using an example application. 
Let's get right to it !!

## So why do we need debugging ?
Sometimes during execution of your appliacation, it behaved in a way it wasn't intended, and sometimes we know why this was, but other times it is not quite so clear. So in order to understand what's going on inside of your application, that's when we use the technik called debugging. So while we are looking inside of your application to see what's going on inside the code and what values the variables have hopefully to try to diagnose your problem and come up with a solution. 

## The way it works in Java
When your application starts up, and the Java Virtual Machine (JVM) you can start your application in debbug mode, which allows another Debugg proccess to attach itself to the JVM, and to see what's happening inside. This is useful not only to diagnose issue running inside your IDE, but it can also be used after deployment even if your application is runnign on the cloud for example, you can still attach debbug session to it. Here we will focus on the first scenario, when we've got an application running inside IntelliJ IDEA, using all the tools IntelliJ IDEA offers to make as simple as possible for us to debbug our application. In this class we will debug few examples in Java, and show how to use the debugger to debug some code 

## Alright so here we are in IntelliJ, with a main class whose main method is doing very basic arithmetic with two integers A and B which are multiplied and whose product is compared
with another variable C and then printing out whether it is bigger or smaller. Although this program shouldn't have very buggs in it, and if oyu look at it you would expect it to print
 smaller because 2 times 5 is 10, which is less than 11 not greater, so we think that we should always print smaller, in this case if we run the code just to double check that, and as we expect when we run the code we hit the smaller case here, and it prints smaller. But what if we change the c value to 10 and then rerun the code, so still prints smaller even though actually the values should be equal because 2 time 5 is 10. So let's say the program wasn't this simple and we are trying to figure out why we are getting printing smaller as result instead of equal. So what we might do here is add a print statement before the if code-line printing for example: "Debugg" and then print out aTimesB and then run the code and check to see what the print statement say, and that could work. Or what we might do here is run this code through a debugger, adn that way we can see what value each variable is, so we can literally step through the program. So first thing we do in order to do that is need to run in debug mode bu clicking the little bug symbol in the IDE, and we might think if we run this that that's really debug mode but that's really not a debugg mode that's just turning on additional features in the IDE that we then need to customize in order to really debug our program, and many many people click the green little debugg icon within the IDE and don't see any different results in their program, and then they kind of throw up their hands saying ok  that didn't work now what do I do. Let's show what we do when we are debugging our code in debug mode. The first thing we want to do is we want to insert a break point (a break point is where while we are running in debug mode the IDE will stop execution of our program at our break point and then we can kind of poke around and see that the state of our program is at that break point). So in order to add a break point in our code all we have to do is just click right next to the line number where we want the break point to start. So basically before that line of code is executed, we are going to have the IDE stop execution of the program, so if we run with the debug icon we will see what that does. We are used to normally see the console output which is the standard out, but in this case when running in debug mode we will see the debug window, which is saying that the state of our program is. And the little checkmark on the break point says that we did hit the break point, and the first line from that break point will be highlited which means we are currently on that break point. And it even says here Main 3, which means we are at line 3, and also right next to it it says that the only variable set right now is the args array args = {String[0]@749}[] and that is because that's argument that goes into the main method, and because we haven't executed this line of code yet the debugger doesn't know about the a variable yet. So, what we have to do is "step" which means we want to execute the next line of code and then see what happens. And in order to to that there are different arrows in the debug window. What we want to do here is we want to do a step over (the first arrow symbol) and look at that we just ran step over and since we weren't goint further into what's called the call stack we basically just went to the next line of code, so even though our break point was at line 3 we are now still breaking at line four (b=5) so from here we can see that our value of a is 2, and if we skip one more time then we will see that now our value of b is set to 5, so next if we skip a few times so we can see at line "int aTimesB = a * b;" that next to the line it says "a:2,  b:5 and aTimesB:10", and on the next skipping the next highlighted line is " if (aTimesB > c)" and next to it it says "c:10, aTimesB:10" which is already telling us what next is going to happen (that on the next skip we are going to hit the else block and print "Smaller"). So, this way we are able literally step by step to follow the logic through our program, and we were able to see at what it was doing based of the values of our variables. So now that we know how the program would execute in that situation, we are going to go ahead and rerun the debugger by clicking on bug again and then we will be back at where we just started back at line three (int a=2) and now if we hit step over again the code will behave like the last time, but if we want to see how the code would react if a was a different value. In order to do this we might first think that we need to do that by changing the value of a, and then recompile rerun the code rerun the debugger but nope. We don't have to do that, instead we can set the values of the variables while the debugger is running, and that is doing by clickin on the littel up arrow on the a:2 and set the new value (let's say set value to 9), and now we can step through the code again for a few times and see that now we are going to hit the first branch "aTimesB > c" and thus print "Bigger". Meanwhile beside every codeline we can see the newly set values for the variables, so we can see that now tha value of a is 9, meaning our product is 45 and thus greater than 10. And now that we know that we are going to hit the first statment, we are just going to go ahead and hit resume (on the left side bar on the play button on the debug window and now we print the value bigger). Next, let's say we want to debug our code and we want to specifically look for when we are hitting the else case but really tha value isn't smaller it's equal. So, what we can to is add a break point and we can evaluate a times b relatively to c. So, we currently have a breakpoint still at line 3, and now we are going to add one at line 8 (if (aTimesB > c)), and then we are going to right click on that break point and add a condition aTimesB == c, so no what will happen is this break point will only get hit if the condition is true, and in the case of the code rihgt now we should expect that to be true, so debugging again we have hit our first breakpoint and since we don't want to step over each lines so we are going to hit resume and we can see we are moved on the next breakpoint with all the values set on the lines above the second break point, and also we can see that we've hit our second break point and our value of c and aTimesB are exactly the same (c:10, aTimesB: 10) that's why we hit it. And if we were to rerun the debugger and then change the value of a to three, then if we resume we can see that we just hit the "Bigger" statement and we didn't hit the second break point. So this way we can make break point conditional based off of the stateof our program so that way we dont hit it every single time. Let's say the first break point annoy us an we don't want to use it anymore but we want to generaly keep it in place so for that we can right click on that and we can deselect the enabled which means we have a break point there which we can turn back on but it's not currently enabled, so if we rerun the debugger we directly hit the second conditional breakpoint because th etwo values are the same but skippe the first. So next, instead of primitives we will convert this to use some objects and demonstrate how to use objects in debugger. Here is some more code where we have Strings, and we are adding things into a list and we're printing the list. So if you tak a look at this code you may see a bug immediately, or maybe you don't. Let's go ahead and run it and see what it is doing. After running we can see we have a bug: "String index out of bounds" exception and it happens right here with elem.substring(6). So based on the fact that we are throwing that exception here on line: "secondList.add(elem.substring(6))" we might pretty quickly draw the conslusion that the strings within myList are not long enough, when we take a look at the string "first" example, but let's say it weren't that straight forward and we didn't see                     :
```
int a = 2;
        int b = 5;
        int c = 11;

        int aTimesB = a * b;
        if (aTimesB > c){
            System.out.println("Bigger");
        } else {
            System.out.println("Smaller");
        }
```

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

- **Download from existing remote repository**: `git clone [repo-url]`


As alternative to GitHub we can also use: Gitlab, Bitbucket, SourceForge and so on, but here we will stick on working with Github.


# Github exercises while working with Java

## Example 1: Upload your first Java project to Github

Following the github flow operations, create your Github repository and create a new simple Java "Hello world" project, which you will upload on the Github repository.

### Solution

**TO DO** STEPS:
- **Create an github account** by entering email, password and username

- **Verify our account** by entering code sent on email. 

- **Login** to our github account

- **Choose create repository** and give the repostory name.

- **After creating new repository** we see all commands required to push already existing and new repository (we follow the commands for creating new repository):
```
echo "# Programming-Languages" >> README.md
git init
git add README.md
git commit -m "This is my first commit, let's have some fun!"
git branch -M main
git remote add origin https://github.com/filkovaivana1/Programming-Languages.git
git push -u origin main
```

- **Create simple "Hello world !" Java project** which after creating should look like:
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

The remaining steps we do this by using command prompt approach. 
- **Open cmd and set our current working directory** to the project directory (or simply open terminal from your project in intelliJ):
```
cd [project_directory]
``` 

- **Initialize empty git repository locally** (if already not done while creating the Java project):
```
git init
```

- **Add main branch**:
```
git branch -M main
```

- **And set the remote origin** to be our remote repository (which means everything we push will go there):
```
git remote add origin https://github.com/filkovaivana1/Programming-Languages.git
```

- **Add our code in the local git repository**:
```
git add .
```

- **Commit our changes** with specific message according to the changes done:
```
git commit -m "This is my first commit, let's have some fun!"
```

- **Finaly push everything we commited on the remote git repository**
```
git push -u origin main
```

*Note: Pushing for the frist time may require some preauthorization

![image](https://github.com/user-attachments/assets/55ad39c6-239f-49a6-8f86-7fc768d21b86)


After successful preauthorization we continue pushing our changes and if everything as it should be, we get response message that last operation is done:

![image](https://github.com/user-attachments/assets/6a6afcb3-618a-4b89-a97c-d57d28a902fc)


## Example 2: Create a MD file
In our newly created repository, create 'README.md' and upload it to your github repository.

### Solution
- **Open cmd and set current working directory** to the project directory (or simply open terminal from your project in intelliJ):
```
cd project_directory
``` 

- **Create md file**:
```
echo "# Programming-Languages" >> README.md
```

- **Add our code in the local git repository**
```
git add .
```

- **Commit our changes**
```
git commit -m "Add README file"
```

- **Push everything commited on the remote git repository**
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
Choose clone from the drop down menu on github link:

Or by this commands in terminal:
```
cd [new_project_directory]
git clone https://github.com/filkovaivana1/Programming-Languages.git
```


## Example 5: Delete repository 

### Solution
- **For deleting and getting status of local repo** use this commands in terminal:
```
   git status
   rm -fr .git
   git status
```
After successful deleting on getting the status we should get message: 
```Fatal: not a git repository (or any of the parent directories): .git```

- **For deleting a repo remotely to github**: Go to Settings -> General tab -> (scroll down to) Danger Zone -> Delete this repository
 

