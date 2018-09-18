#### [Drupal 8 Backend Training](README.md)

# Exercise 1:

## Sync your local environment

We're assuming that you've arrived at this point after having completed our [Drupal 8 Theme training](https://github.com/chapter-three/drupal-8-theming), and that you currently have a fair amount of un-committed changes made to your local dev environment. In this exercise we'll review some basic git commands, and get our dev environments into a consistent state in preparation for our upcoming exercises.

1. Go to your drupal docroot on the command line.

2. Run the command 

    ```bash
    git status
    ``` 

  to view your un-committed changes.

3. We're now going to create a new branch, named after you, to store your changes. Run the command 

    ```bash
    git checkout -b YOURNAME
    ``` 
  replacing "YOURNAME" with... your name. The `git checkout` command is what we use to switch between branches, and the `-b` flag is telling git that we want to create a new branch before switching.

4. Now that we're on a new branch we want to commit our changes. Typically we would add files one at a time using the command `git add FILENAME` and write meaningful commit messages for each change, but in the interest of saving time we're going to commit all of our files at once. From the docroot run the command 

  ```bash
  git add .
  ``` 

  Even though we're not following best practices by committing our individual changes and writing meaningful commit messages, we should still run `git status` and review our changes, making sure we're not committing anything unintentionally. We should see all of our files from the theme training in green, meaning they're "staged" or ready to be committed.

5. Run 

  ```bash
  git commit -m "Drupal 8 theme training"
  ``` 

  to commit your files, then run `git status` to make sure everything went as planned.

6. If everything went as planned you should have seen `nothing to commit, working tree clean` after running `git status`, and we're ready to switch back to the master branch. Run 

  ```bash
  git checkout master
  ```

  and we're done!