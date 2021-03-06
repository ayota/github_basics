# fun_3000 workflow basics

This guide covers the main actions y'all will need to perform as a member of the research lab and contributor to fun_3000. In addition to establishing norms of what each facet of github means in the context of the project workflow, the guide also contains a cheat sheet of the terminal commands to accomplish these so y'all won't have to go hunting around for them.

## navigation
* [I want to set up fun_3000 on my local machine ...](#i-want-to-set-up-fun3000-on-my-local-machine-)
* [I want to open an issue ...](#i-want-to-open-an-issue-)
* [I want to QA someone else's code ...](#i-want-to-QA-someone-elses-code-)
* [I want to close an issue ...](#i-want-to-close-an-issue-)


## I want to set up fun_3000 on my local machine ...

#### :octocat: on github
1. We can't force you to be part of the repo, so make sure you accept the invitation from github in your email. Ping @ayota if y'all can't find it.
2. Hit `CLONE OR DOWNLOAD`
3. You will see a link, copy that link. (If you have SSH authentication set up on you machine, use that one, otherwise grab the https one. It will ask for your github password in the next step if you use the https one.)

#### :computer: on your local machine
1. Go to the directory you want to keep your work
2. Making a virtualenv or conda environment is recommended but not required. This will allow you to keep a clean copy of the requirements needed to run/test the components of the program, and easily track any new packages you install for some future feature.
  * To install virtualenv:
    
    ```shell
    nybbler:fun_3000 ayo$ pip install virtualenv
    ```

  * To make virtualenv:
    
    ```shell
    nybbler:fun_3000 ayo$ virtualenv venv
    ```

    * I usually call them venv, but you can call it whatever you want.

  * To activate:

    ```shell
    nybbler:fun_3000 ayo$ source venv/bin/activate
    ```

    * You will know it is activated because your command line will look like this:
    ```shell
    (venv)nybbler:fun_3000 ayo$ echo "bam"
    ```

  * To deactivate:
    ```shell
    (venv)nybbler:fun_3000 ayo$ deactivate
    ```

  * Updating requirements.txt:
    ```shell
    (venv)nybbler:[your_repo] ayo$ pip freeze > requirements.txt
    ```

3. In the terminal (or w/e the command line is on windows):

 ```shell
 git clone [WHAT YOU COPIED FROM THE REPO]
 ```

4. Bam. You now have a copy of the repo on your local machine
5. Hop over to develop because we've been really bad about updating master thus far, so develop has the most up-to-date versions of everything.

 ```shell
 git checkout develop
 git pull
 ```

6. Install requirements.txt 

 ```shell
 cd path/to/ddl_nlp/on/your/machine
 pip install -r requirements.txt
 ```

## I want to open an issue ...

#### :octocat: on github
1. Select the `ISSUES` tab then the green `NEW ISSUE` button
2. Give your issue a title and be very descriptive in what the problem and proposed solution is. Include psuedo code, clear inputs and outputs, and any relevant links because, let's face it, we're all going to forget pretty shortly after discussing these things. 

  :boom: **If you know there are multiple steps,** checkboxes are super handy (syntax is ` - [ ] `), and it automagically makes a little progress bar at the bottom of the issue. This and other markdown fanciness are available [here] (https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links)
3. Add some labels
  * Procedural: `IN PROGRESS` | `READY FOR QA` | `NOT READY YET`
  * Parts of the project
      * `BUILD CORPUS` refers to anything dealing with amassing text for the corpus
      * `EVALUATION` refers to the evaluation task
      * `ENHANCEMENT` is where we've been dumping all the nice-to-haves
  * Don't label anyone `INVALID` unless you've talked to them IRL :bowtie:
4. Assign some folks
5. We don't really use milestones, but these are another way of organizing things
6. Hit submit

#### :boom: helpful hints
  * `@username` will ping someone else to join the conversation
  * `#issue_number` will reference another issue
  * example: typing `yo @laura : I think this has to do with #50` will ping Laura, and also link to Issue 50, whatever that may be.
  * even more [here] (https://guides.github.com/features/issues/)


## I want to work on an issue ...

#### :computer: on your local machine
1. Do a pull from develop to make sure your local copy is up to date
 
 ```shell
 git pull develop
 ```

2. See what branch you're on
 
 ```shell
 git branch
 ```

 which should give you something like ...
 
 ```shell
(fun_3000)nybbler:ddl_nlp ayo$ git branch
* develop
  generate_folds
  master
  new_feature
  post_gensim_similarity_ml
  sample_branch
 ```

3. Get on the right branch

 ##### Creating a new branch from develop

 ```shell
 git checkout -b [YOUR NEW BRANCH] develop
 ```
  :boom: **The convention for naming branches** is [issue no.]_[some description of what you're doing]. For example, a branch fixing Issue 38, which describes an issue with toasters exploding for like, no reason, would be `38_exploding_toasters`.

 ##### Moving to an already-created branch
 ```shell
 git checkout [YOUR BRANCH NAME HERE]
 ```

4. Add your code
5. Push to github

 ```shell
 git add [THE FILE YOU EDITED]
 git add [ANOTHER FILE YOU EDITED]
 ```
 :whale: *... repeat for all the files you changed ...* :whale:
 ```shell
 git commit -m [THE BEST MESSAGE EVER]
 git push
 ```
 :boom: You can just add everything you edited by doing ` git add . ` , but in the interest of not uploading random things like data (.csv, .xls, and friends) or iPython notebooks, sandbox code, etc., it might be better to do it one by one.

 :boom: To see what you have tracked/changed for the upcoming commit, use ` git status `. If you accidentally add a file you don't want to push to the repo, you can untrack files by using ` git reset HEAD ` will unstaged everything and you can start over again.

#### :octocat: on github
1. Go to the issue you're addressing, make a note of your fixes/open discussion for outstanding issues
2. Assign ready for QA label


## I want to QA someone else's code ...

#### :computer: on your local machine
1. Grab the branch

```shell
git branch [THE BRANCH FOR THE NEW FEATURE]
```

2. Test the code on your local machine
3. Once it's OK, note on the issue that everything's great, or fix any issues you encounter after discussion with the creator. Bonus points for updating the readme to clarify instructions based on how you were able to run the code.


## I want to close an issue ...

#### :computer: on your local machine
Push any fixes/changes to github

 ```shell
 git add [ALL THE CHANGED FILES]
 git commit -m "ruined everything. kthxbye."
 git push
 ```

 :boom: **To add longer commit messages,** just do `git commit` and it will automagically open a vim editor. Hit `i` and you can type your message in the terminal. The first line is what shows up next to the commit, so keep it short, and then everything on subsequent lines shows up when they click on that commit. Hit `esc :wq` to save and quit the editor.

#### :octocat: on github
1. Select `PULL REQUESTS` tab, then `NEW PULL REQUEST`
2. Name your pull request like: closes [issue no. you're addressing]. some more details. (e.g., `closes 38. stops toasters from exploding.`)
3. Hook your branch up against develop. Pray there are no conflicts.
   * **Base** the branch you want to merge into (usually develop)
   * **Compare** the branch your changes are on (so, the one you made, like `38_exploding_toasters`)
4. Add any notes, outstanding issues, important emoji expressions, etc. 
   * [All the things.] (http://www.webpagefx.com/tools/emoji-cheat-sheet/)
5. Let everyone know you're ready to merge! :tada: :tada: :tada:

![](http://i.amz.mshcdn.com/TUGnCLIUndmH2H1WOP2VGgfDmq4=/fit-in/850x850/http%3A%2F%2Fmashable.com%2Fwp-content%2Fgallery%2Fcatmemes%2FKeyboardCat.gif)
