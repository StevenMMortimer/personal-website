Learning Git with Scenarios
========================================
author: Steve Mortimer
date: August 11, 2015
css: css-presentations.css
width: 960
height: 700



git-like stuff
====================================================
title: false
type: subsection
<h3>
  Using <span style="font-family: monospace">git</span> in the real world
</h3>

* <span style="font-family: monospace">git</span> has commands to manage changes to folders and files, it doesn't 
necessarily host those folders and files (i.e. you could just run locally)
* <span style="color:red">Github</span> hosts public repositories and offers an interface to them + some extra features
* <span style="color:red">Bitbucket</span> hosts on cloud private repositories + some extra features
* <span style="color:red">Stash</span> hosts on cloud or on-premise private repositories + some extra features
* GUIs visualize repositories and associated actions (e.g. Tower, Gitbox, GitX, Sourcetree, etc., plus 
other language-specific editors have plugins)

Awareness of SSH Keys
====================================================
type: subsection

**Scenario:** My repository is hosted elsewhere, so I first need to authenticate
before adding, modifying, and deleting content. Otherwise anyone could modify
my stuff or snoop on my stuff during transfer.

* There are multiple protocols for transferring git content <a href="https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols" target="_blank">(see here)</a>, but most common is SSH which securely encrypts and compacts data while sending.
* You might not really need a key <a href="https://help.github.com/articles/do-i-need-ssh-keys-to-use-github-for-windows/" target="_blank">(see here)</a>, 
but you should be familiar and setting up your own key is probably a good idea.
* How to setup SSH keys by Github <a href="https://help.github.com/articles/generating-ssh-keys/" target="_blank">(see here)</a>. **The takeaway:** 
Generate private/public key pair in .ssh directory inside your home directory. Copy paste the contents of the public key to Github.

Start with Simple HTML Page in a Folder
====================================================
type: subsection

</br>
1. On your compter create a folder called 'test'  
2. Add a blank text file in that folder  
3. Rename the file "Hello World.html"  
4. Copy paste the example text from: <a href="http://www.mkyong.com/html/html-tutorial-hello-world/" target="_blank">http://www.mkyong.com/html/html-tutorial-hello-world</a>


This is just to simulate a project you've started with some work.

git init et. al.
====================================================
title: false
class: ignore-links
type: subsection
<h3>
  <span style="font-family: monospace">git init</span> et. al.
</h3>

**Scenario:** I have a folder on my computer locally and want to
push it to a Github repository

1. Create the repository on Github by <span style="color:red">Clicking New</span>
2. Run  <span style="font-family: monospace; font-size: 75%;">git init</span> 
3. Run  <span style="font-family: monospace; font-size: 75%;">git add .</span> 
4. Run  <span style="font-family: monospace; font-size: 75%;">git commit -m "first commit"</span> 
5. Run  <span style="font-family: monospace; font-size: 70%;">git remote add origin git@github.com:{YourAcctName}/test.git</span> 
6. Run  <span style="font-family: monospace; font-size: 75%;">git push -u origin master</span>

Create a simple html text file

git init et. al. breakdown
====================================================
title: false
type: subsection
<h3>
  <span style="font-family: monospace">git init</span> et. al. Breakdown
</h3>

**Mini-Scenarios:**

* <span style="font-family: monospace; font-size: 75%;">git init</span> = I want to start using git here
* <span style="font-family: monospace; font-size: 75%;">git add</span> = I want to add these files to this commit
* <span style="font-family: monospace; font-size: 75%;">git commit</span> = I want to track these changes
* <span style="font-family: monospace; font-size: 75%;">git push</span> = I want to take the changes and enforce them elsewhere


break-1
====================================================
title: false
<h3>
  <div class="midcenter" style="margin-left:-400px; margin-top:-300px;">
  Break</br></br></br><span style="font-weight: 700; color:#25679E;">I can:</span> Create a repository with files and push changes to a remote repository
  </div>
</h3>


git clone
====================================================
title: false
class: ignore-links
type: subsection
<h3>
  <span style="font-family: monospace">git clone</span>
</h3>

**Scenario:** I want to take an existing repository of mine on Github and 
bring it down to my computer locally

1. Create and/or Go to folder where you want repositories to be locally:  
 a. Run  <span style="font-family: monospace; font-size: 75%;">mkdir ~/cloned-repos</span>  
 b. Run  <span style="font-family: monospace; font-size: 75%;">cd ~/cloned-repos</span>  
2. Copy to clipboard the SSH clone URL to use with <span style="font-family: monospace">git clone</span>  
3. Run  <span style="font-family: monospace; font-size: 70%;">git clone git@github.com:{YourAcctName}/test.git</span>


git remote add
====================================================
title: false
class: ignore-links
type: subsection
<h3>
  <span style="font-family: monospace">git remote</span>
</h3>

**Scenario:** I have cloned a repo, made some changes locally, and
I want to push those changes to the remote repo

1. Check existing remote sources:  
 a. Run  <span style="font-family: monospace; font-size: 75%;">git remote -v</span>  
2. Add your target remote path to the remote sources:  
 a. Run  <span style="font-family: monospace; font-size: 70%;">git remote add origin git@github.com:{YourAcctName}/test.git</span>  
3. Verify it's been added:  
 a. Run  <span style="font-family: monospace; font-size: 75%;">git remote -v</span>  

**The Takeaway:** You've given a nickname to where to push changes not just locally, but elsewhere. You've named it origin.


git push -u
====================================================
title: false
class: ignore-links
type: subsection
<h3>
  <span style="font-family: monospace">git push (-u)</span>
</h3>

**Scenario (cont.):** I have cloned a repository and made some changes locally and
I want to push those changes to the remote repository

1. Go through the normal routine to commit changes:  
 a. Run  <span style="font-family: monospace; font-size: 75%;">git add .</span> and  
 b. Run  <span style="font-family: monospace; font-size: 75%;">git commit</span>  
2. Push "upstream", that's what the option <span style="font-family: monospace; font-size: 75%;">-u</span> stands for  
 a. Run  <span style="font-family: monospace; font-size: 75%;">git push -u origin master</span>  
 
**The Takeaway:**You've designated your master branch to be pushed upstream to the remote nicknamed origin


git reset
====================================================
title: false
type: subsection
<h3>
  <span style="font-family: monospace">git reset</span>
</h3>

**Scenario:** I have committed some changes to my repository, but it was a mistake and I want to go back.

The most common options are "soft" and "hard" resets. The former keeps your changes, but rolls back the commit status to say that you've got changes to commit. The latter completely erases your changes and the commits.

1. Find the commit hash on Github
2. Run  <span style="font-family: monospace; font-size: 75%;">git reset `--`hard \<hashcode_here\></span>
3. The soft reset is <span style="font-family: monospace; font-size: 75%;">git reset `--`soft \<hashcode_here\></span>
4. Note: <span style="font-family: monospace; font-size: 75%;">git push</span> may require 
<span style="font-family: monospace; font-size: 75%;">`--`force</span>


git fetch and git pull
====================================================
title: false
type: subsection
<h3>
  <span style="font-family: monospace">git fetch/pull</span>
</h3>

**Scenario:** I want to bring down changes from the remote repository into my local copy.

It depends on whether you have local changes. Remember you might have local edits not pushed.<div align="center">
<span style="font-family: monospace; font-size: 75%;">git pull</span> does a <span style="font-family: monospace; font-size: 75%;">git fetch</span> followed by a <span style="font-family: monospace; font-size: 75%;">git merge</span>
</div>  
So if you want to see the differences before merging then:

1. Run <span style="font-family: monospace; font-size: 75%;">git fetch</span> (sync with remotes) 
2. Run <span style="font-family: monospace; font-size: 75%;">git diff origin/master</span>
-otherwise-  
1. Run <span style="font-family: monospace; font-size: 75%;">git pull</span> (resolve merge conflicts if they arise)
                                     

break-2
====================================================
title: false
<h3>
  <div class="midcenter" style="margin-left:-400px; margin-top:-300px;">
  Break</br></br></br><span style="font-weight: 700; color:#25679E;">I can:</span> Work around changes in a remote repository
  </div>
</h3>


working-with-others-repos
====================================================
title: false
class: ignore-links
type: subsection
<h3>
  Forking Another Repository
</h3>

**Scenario:** I want to pull down someone else's code and maybe later propose changes.
 
"Forking" brings a copy into a repository that you own, so you control the code base. Different than "cloning" since you don't own.

1. On Github navigate to repository you'd like to fork.
2. <span style="color:red">Click Fork</span> and the repository now exists as part of your account
3. Clone just like any other repo in your account  
<span style="font-family: monospace; font-size: 70%;">git clone git@github.com:{YourAcctName}/html-page.git</span>
4. Make a change and push  
<span style="font-family: monospace; font-size: 60%;">git push -u origin master</span>


working-with-others-repos
====================================================
title: false
class: ignore-links
type: subsection
<h3>
  Staying updated with <span style="font-family: monospace">git rebase</span>
</h3>

**Scenario:** I forked a repository, but the original owner made some changes I want in my local copy.

1. Add Remote that Tracks Original  
  <span style="font-family: monospace; font-size: 65%;">git remote add original git@github.com:757RUG/html-page.git</span>
2. Fetch everything (not pull) to get the original owner's changes  
  <span style="font-family: monospace; font-size: 65%;">git fetch original</span>  
3. Rebase will replay any commits you missed onto your branch  
  <span style="font-family: monospace; font-size: 65%;">git rebase original/master</span>
4. Push changes so they exist on your remote  
  <span style="font-family: monospace; font-size: 65%;">git push -f origin master</span>

proposing-a-change
====================================================
title: false
class: ignore-links
type: subsection
<h3>
  Making a Pull Request
</h3>

**Scenario:** I forked a repository and want to propose changes to the owner for inclusion in the code base.

1. On Github <span style="color:red">Click Pull Request</span> and <span style="color:red">Add a comment</span>. 
You can reference open issues or links that provide context.

2. On Github, on the owner's side, they will be able to review the code diffs and decide on merging. Merge conflicts are resolved by them since they own the recipient codebase in this scenario.


break-3
====================================================
title: false
<h3>
  <div class="midcenter" style="margin-left:-400px; margin-top:-300px;">
  Break</br></br></br><span style="font-weight: 700; color:#25679E;">I can:</span> Fork a repository and propose changes.
  </div>
</h3>


git checkout
====================================================
title: false
type: subsection
<h3>
  Working With Branches and <span style="font-family: monospace">git checkout</span>
</h3>

**Scenario:** I have, or a teammate has, created work apart from the "trunk" or "master" that I want to work on.

0. In Github <span style="color:red">Create Branch</span> (simply type the name of a new branch to create, e.g. gh-pages).
1. Run <span style="font-family: monospace; font-size: 65%;">git fetch</span>
2. If you're not sure what branches, you can check:  
<span style="font-family: monospace; font-size: 65%;">git branch -v -a</span>
3. Checkout the branch you want to work with  
  <span style="font-family: monospace;  font-size: 65%;">git checkout master</span>
4. Confirm with <span style="font-family: monospace;  font-size: 65%;">git status</span>

Items Still Not Covered
====================================================
type: subsection

* Branching and the  <span style="font-family: monospace;  font-size: 85%;">git flow</span> model <a href="https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow" target="_blank">(see here)</a>. Helps separate master code, enhancements, bugs, testing into difference branches.
* Tagging  <span style="font-family: monospace;  font-size: 85%;">git tag</span>  to create a single point to reference code in deployments
* Merging, Conflicts, Code Diffs, Code Reviews with Git to facilitate code cleanliness, early bug catches, shortened development time.

