# Introductory to Git Workshop!
This guide assumes that you have some bash shell on your computer and a little bit of experience with it. If you don't its completely ok, just tell Jake!

## Installation and Setup

The first step is to make sure Git is installed and setup on your system. Follow either of these guides to get started with git on your computer. I recommend the first guide since its a little more recent.

- [Guide 1](https://github.com/git-guides/install-git)
- [Guide 2](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

After installing and setting up git open your terminal and type out this command:
``` bash
git clone https://github.com/JakasaurusRex/GitWorkshop.git
```

You are all setup now if this worked! If you need any help wiht this workshop on a windows machine, let Jake know! 

## Gitting started!
(You can also follow along with this guide using Github Desktop or another git GUI based application)

Normally you would create your repo using the following command, but since we cloned an existing repo (short-hand for repository) from online, we don't need to worry about it:

``` bash
git init
```

This establishes the current folder you are in as a git repository by setting up some stuff behind the scenes. We won't get to into exactly how it works but look into **Advanced Systems Programming** taught by Jae Woo Lee if you are interested!

Sweet! Now we have our working git repository all setup. Lets check out the existing changes that have been made to the git repo. You can use the ``` git log ``` command to see what changes have been committed in the past. Lets do that and see what happens!

You can also check the status of the repository. We can see if any new files have been created, if there are any updates to existing tracked files, or if there is any file deletions that we added to our git repository. You can type this command to see that information:

``` bash
git status
```

At the moment, it should say working tree clean - nothing to commit. Lets start making some changes then!

First lets do some modifying of existing files. Type out ```ls``` to display the contents of the folder you are currently in. Lets use ```cd``` to change into the **example** directory.

``` bash
cd example
```

Now that we are in the example directory lets check out hello.c. Let's edit this .c file and change what is being printed in the first line of code. You can open up any text editor to change it.

After you have edited the file lets check the status of our repo again

```bash
git status
```

You should now notice something like below.

<img width="600" alt="Screenshot 2024-10-05 at 11 12 37 AM" src="https://github.com/user-attachments/assets/367dea24-e509-4496-a67f-bab732b3c824">

git has recognized that we have modified the file from its previous state. We can restore the file to its existing state if the changes were an accident by running:

```bash
git restore hello.c
```

Or we can add the changes to our current change list by running:

```bash
git add hello.c
```

Now that we have git added the file, we have added the changes to a list of changes to our repository. The list of changes is known as the **staging area**. Those changes are only local to the machine and can always be reverted by

```bash
git restore --staged hello.c
```

Lets tell git that we want to commit these changes. We want others to be able to see the changes you made. We can commit and add a message to go along with our change list by

```bash
git commit -m "<Your message here>"
```

You have officially made your first changes using git! Lets check the **git log** again and see if its changed!

```bash
git log
```

If you have done everything correct you should see your change with your message at the top of the list! 

Lets make some more changes. Lets try adding a file. Create a new file in the example folder. After this check the status of the folder. You should see something like this. 

<img width="549" alt="Screenshot 2024-10-05 at 11 21 33 AM" src="https://github.com/user-attachments/assets/3a67d04b-9dc8-4bd2-9ad9-d072edfb15b3">

In order to include the file in the tracked files of your git repo you need to run the git add command. git only tracks files that you specifically ask it to. This is useful if you don't want to track your API keys, or binary files that are automatically generated. You can also read up on [.gitignore](https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files) that can help you stay organized by automatically ignore certain file types.

```bash
git add <filename>
```

Once you have added the file, you should try to commit like we did before and see if you can add your changes to the git log! 

Lets also try deleting files! Delete the file you just created using the ```rm`` command or another deletion method. After running git status, git should tell you that the file has been deleting. In order to track this change you need to do add that change (this is a bit confusing).

```bash
git add <deleted filename>
```

After doing that, you can commit the change like you did before!

Try messing around and getting used to doing things using git!

In order to upload these changes to github for collaborators to see, you need to setup [github CLI](https://cli.github.com/manual/) or one of the GUI based github applications I mentioned earlier! Check those out now that you now how git works!

If you wanna learn more about git run the following command!

```bash
man gittutorial
```

## Gitting Advanced

Branching is a super useful tool! In order to see what branches are available run
```bash
git branch
```

Lets create a new branch that we can make some changes on!

```bash
git branch newbranch
```

Now if we run ```git branch```, we should be able to see it on the list of branches. We can move to working on that branch by running ```git switch newbranch``` or ```git checkout newbranch```

On our new branch make some changes and commit them and switch back to the main branch. 

Now lets try to merge our changes and see what happens.
```bash
git merge newbranch
```

This should merge without issue! If you changed some files on the main branch and committed them, you might run into a merge conflict. If this happens, theres a bunch of ways to solve the conflict but its best to try to figure that out on your own. Try to create a merge conflict and resolve it! At this point read through the git tutorial mentioned earlier to learn more about branching and collaborating with others!

I also recommending reading [Yet Another Git Guide by John Hui](https://j-hui.com/pages/yagg/#merging-vs-rebasing), a former instructor of Advanced Programming!
