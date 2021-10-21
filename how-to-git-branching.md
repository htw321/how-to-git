# Branching in GIT
### Create Repository
Create Test repository with some data for testing

    mkdir test; cd test;
    git init
    echo "Milk" >> shopping-basket
    echo "Bread" >> shopping-basket
    git add shopping-basket
    git commit -m "Started the shopping list"

### List branches
Only returns a list of branches available with the current one maked with an asterix. In our case just `*master`

    git branch

### Create and work in a Branch
Creates a new branch called BBQ and add some burgers to the shopping list

    git branch BBQ
    git checkout BBQ
    echo "Burger" >> shopping-basket
    git commit -a -m "Let's have a BBQ" 

Switch and create another branch to add Breakfast stuff to the basket

    git checkout -b breakfast master
    echo "weetabix" >> shopping-basket
    git commit -a -m "Don't know who likes that stuff" 

### Merging and Deleting Branches
Merge BBQ into master and remove the branch (but keep the track that it was developed in a branch)

    git checkout master
    git merge --no-ff BBQ
    git branch -d BBQ

`git branch -d BBQ` is a save delete of a branch - only works if all changes are merged
:exclamation: `git branch -D BBQ` forces a merge and discard any changes. So better be sure and take it :snail:

### Merging with Conflicts

    git merge --no-ff breakfast

````
Auto-merging shopping-basket
CONFLICT (content): Merge conflict in shopping-basket
Automatic merge failed; fix conflicts and then commit the result.
```
The conflict is marked in the shopping-basket file, which needs to be edited

    vi shopping-basket
    git add shopping-basket
    git commit -m "merged shopping baskets"
    git branch -d breakfast


### Other merges
Now we remember that we forgot to add veggie burgers to the BBQ, inserted before the burger.

    git checkout -b BBQ master
    head -n 2 shopping-basket > tmp.txt; echo "veggie burgers" >> tmp.txt; tail -n 2 shopping-basket  >> tmp.txt
    cat tmp.txt > shopping-basket; rm tmp.txt
    git commit -a -m "An alternative food source"

And Marmite for the breakfast basket

    git checkout -b breakfast master
    echo "Marmite" >>  shopping-basket
    git commit -a -m "Some weird and wonderful stuff"

Start the merging process - however you like it.
breakfast <- BBQ
master <- BBQ
master <- breakfast

    git checkout breakfast
    git diff BBQ
    git merge --no-ff BBQ
    git checkout master
    git merge --no-ff BBQ
    git merge --no-ff breakfast


