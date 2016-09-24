# fun_3000 workflow basics

## I want to open an issue ...
#### on github
1. Click the green "New Issue" button
2. Give your issue a title and be very descriptive in what the problem and proposed solution is. Include psuedo code, clear inputs and outputs, and any relevant links because, let's face it, we're all going to forget pretty shortly after discussing these things. If you know there are multiple steps,
   - [ ] << checkboxes are super handy (syntax is ` - [ ] `), and it automagically makes a little progress bar at the bottom of the issue. This and other markdown fanciness are available [here] (https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#links)
3. Add some labels
  * Procedural: "in progress"; "ready for QA"; "not ready yet"
  * Parts of the project
      * "build corpus" refers to anything dealing with amassing text for the corpus
      * "evaluation" refers to the evaluation task
      * "enhancement" is where we've been dumping all the nice-to-haves
  * Don't label anyone "invalid" unless you've talked to them IRL :)
4. Assign some folks
5. We don't really use milestones, but these are another way of organizing things
6. Hit submit

#### So many issues ...
  * @username will draw someone else into the conversation
  * #issue_number will reference another issue
  * example: typing `@laura : I think this has to do with #50` will ping Laura, and also link to Issue 50, whatever that may be.
  * even more [here] (https://guides.github.com/features/issues/)

## I want to work on an issue ...

#### on your local machine
1. Do a pull request from develop to make sure your local copy is up to date
 ```shell
 git pull master
 ```

2. See what branch you're on
```shell
git branch
```

which should give you something like ...
```shell
(fun_3000) nybbler:ddl_nlp ayo$ git branch
  generate_folds
  * master
  post_gensim_similarity_ml
```

3. Get on the right branch

##### Creating a new branch
```shell
git checkout -b [your new branch]
```
* **Naming branches:** We've settled into a pattern of [issue no.]_[some description of what you're doing]. For example, a branch fixing Issue 38, which describes an issue with toasters exploding for like, no reason, would be `38_exploding_toasters`.

##### Moving to an already-created branch
```shell
git checkout [your branch name here]
```

4. Add your code
5. Push to github
```shell
git add .
git commit -m [THE BEST MESSAGE EVER]
git push
```

#### on github
1. Go to the issue you're addressing, make a note of your fixes/open discussion for outstanding issues
2. Assign ready for QA label


## I want to QA someone else's contribution ...
1. Grab their branch
2. Test the code on your local machine
3. Once it's OK, note on the issue that everything's great, or fix any issues you encounter after discussion with the creator

## I want to close an issue ...
#### on your local machine
Push any fixes/changes to github
```shell
git add .
git commit -m "YOUR AWESOME COMMIT MESSAGE"
git push
```
* To add longer commit messages, just do `git commit` and it will automagically open a vim editor. Hit `i` and you can type your message in the terminal. The first line is what shows up next to the commit, so keep it short, and then everything on subsequent lines shows up when they click on that commit.

#### on github
1. Hit "New Pull Request"
2. Name your pull request like: closes [issue no. you're addressing]. some more details. (e.g., `closes 38. stops toasters from exploding.`)
3. Hook your branch up against develop. Pray there are no conflicts.
   * **Base** the branch you want to merge into (usually develop)
   * **Compare** the branch your changes are on (so, the one you made, like `38_exploding_toasters`)
4. Add any notes, outstanding issues, important emoji expressions, etc. 
   * [All the things.] (http://www.webpagefx.com/tools/emoji-cheat-sheet/)
5. Let everyone know you're ready to merge! :tada: :tada:
