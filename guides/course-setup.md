Git & GitHub Setup
==================

## Motivation

The motivation for using Git and GitHub for ComS 342 has two parts.

The first part is a convenience factor for the instrutor and TAs. Not
surprisingly, BlackBoard isn't the most friendly for assignments dealing with
code. With Git, we can very easily clone all your solution repositories and pull
in changes as you add to them. Since we make heavy use of unit testing in this
course, we are able to automate things which really helps us as well.

GitHub acts as a collection point for Git repositories. It makes it easy to
collaborate and host code all while using Git either in a GUI or on the command
line. It also has a very powerful API that we've made use to make our jobs
easier.

Secondly, we wish for you to get as much out of this course as possible. In
addition to learning about programming languages, there isn't a single more
powerful tool for programmers that can be learned than a version control system.

## Learning Git

There are numerous guides on using Git that are available. They range from being
interactive ones to just text ones. Find one that works and experiment; making
mistakes and fixing them is a great way to learn. Here is a link to resources
that GitHub suggests:
[https://help.github.com/articles/what-are-other-good-resources-for-learning-git-and-github](https://help.github.com/articles/what-are-other-good-resources-for-learning-git-and-github)

## Setting Up GitHub

Assuming you have a solid enough understanding of Git, it's time to get started
with GitHub.

1. If you don't already have an account, sign up for one here:
   [https://github.com/join](https://github.com/join)

2. Next you need to join the GitHub Organization that we've created for the
   course: [ComS 342](https://github.com/ComS342-ISU)

   To join it, go to the [ComS 342 Registration][http://cs342.joshldavis.com/]
   page and click the **Sign in with GitHub & Join the Class** button.

   This application uses OAuth and it will take you to GitHub where you will
   have to give your permission to join it.

3. If for whatever reason you can't join the organization, contact Josh Davis,
   joshuad@iastate.edu and let him know.

4. You should now be apart of the ComS 342 Organization and should have access
   to a few different repositories here:
   [https://github.com/organizations/ComS342-ISU](https://github.com/organizations/ComS342-ISU)

   You should also now have a repository setup just for your homework solutions.
   This should be located in the ComS342-ISU organization and be called
   `solutions-<GitHub Username here>`.

   This is what you'll setup in the next section to allow you to write your
   homework answers and submit them.

If the above didn't work, contact one of the TAs to help you out.

## Setting Up Git

You should have Git installed and have joined the ComS342-ISU organization from
the previous section.

1. The first thing we have to do is to clone the current homework repository by
   issuing the following commands onto the command line:

   ```bash
        $ git clone git@github.com:ComS342-ISU/TODO.git
   ```

   This will make a complete replica of the homework repository locally. Now we
   are going to change it to point to your personal repository that was created
   for you in the previous section.

2. By default the remote called `origin` is set to the location that you cloned
   the repository from. You should see the following:

   ```bash
        $ git remote -v
            origin git@github.com:TODO.git (fetch)
            origin git@github.com:TODO.git (push)
   ```

    FIX:
   We don't want that remote to be the origin, instead, we want to change it to
   point to your repository. To do that, issue the following command:

   ```bash
        $ git remote rename origin upstream
   ```

   And now you should see the following:

   ```bash
        $ git remote -v
            upstream git@github.com:TODO.git (fetch)
            upstream git@github.com:TODO.git (push)
   ```

3. Lastly we need to give your repository a new `origin` since it is lacking
   one. Issue the following but substituting your GitHub username in place:

   ```bash
        $ git remote add origin git@github.com:TODO.git
   ```

4. Let's test it out by doing a push of your master branch to GitHub by issuing
   the following:

   ```bash
        $ git push -u origin master
   ```

   TODO

5. That last command was a bit special and only needs to be ran the first time
   to setup the remote tracking branches. Now we should be able to just run `git
   push` without the arguments. Try it and you should get the following:

   ```bash
        $ git push
          Everything up-to-date
   ```

If you don't know Git that well, this probably seemed very arcane. Just keep
using Git and you'll keep understanding more and more.

## Getting Newly Released Homework

TODO
