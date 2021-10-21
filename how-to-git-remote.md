# Working with a remote repository

### git clone
Get a local checkout of the repository that you can work on it

    git clone git@gitlab....:user/test.git

### git fetch
Fetches remote changes and downloads them, BUT does not merge them to your current checkout. You can review changes before integrating them.

e.g. another person added a README file to master (and I'm also working on master)

    git fetch 

The file is not on your filesystem.

    git diff origin/master
    git merge origin/master
    git log -2

### git pull
Fetches and merges the changes to your checkout.

    git pull

### Pull and Rebase
Rebase makes more sense when branching is used, but instead of comparing the end result, git fetches all the changes done since the last checkout and applies the change to your checkout. Replay the work which was done instead of merging the current status.

    git pull --rebase

### Push
Push your changes to the repository

    git checkout -b BBQ master
    echo "BBQ sauce" >> shopping-basket
    git commit -a -m "Ready for a BBQ"
    git checkout master
    git push --dry-run
    git push --dry-run --all
    git push --all

`git push origin BBQ` would push only BBQ changes

### Handy things you can do
    git clone git@gitlab....:user/test1.git
    git remote -v
    git remote rm origin
    git remote add origin git@gitlab....:user/test2.git
    git remote -v
    git push -u origin master
