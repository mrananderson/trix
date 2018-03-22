# trix - A simple and elegant command-line todo list
------------
Installing trix
------------

`trix` requires [Python][] 2.5 or newer, and some form of UNIX-like shell (bash
works well).  It works on Linux, OS X, and Windows (with [Cygwin][]).

Installing and setting up `trix` will take about one minute.

git clone this repo

Next, decide where you want to keep your todo lists.  I put mine in `~/tasks`.
Create that directory:

    mkdir ~/tasks

Finally, set up an alias to run `trix`.  Put something like this in your
`~/.bashrc` file:

    alias trix='python ~/path/to/trix.py --task-dir ~/tasks --list tasks'

Make sure you run `source ~/.bashrc` or restart your terminal window to make
the alias take effect.

Using trix
-------

### Add a Task

To add a task, use `trix [task description]`:

    $ trix Hello World.
    $ trix Send an email.
    $ trix Buy more beer.
    $

### List Your Tasks

Listing your tasks is even easier -- just use `trix`:

    $ trix
    5  - Hello World.
    30 - Send an email.
    4  - Buy more beer.
    $

`trix` will list all of your unfinished tasks and their IDs.

### Finish a Task

After you're done with something, use `trix -f ID` to finish it:

    $ trix -f 5
    $ trix
    30  - Send an email.
    4   - Buy more beer.
    $

### Edit a Task

Sometimes you might want to change the wording of a task.  You can use
`trix -e ID [new description]` to do that:

    $ trix -e 30 Call mom.
    $ trix
    30  - Call mom.
    4   - Buy more beer.
    $

You can use sed-style substitution strings:

    $ trix -e 4 /more/a lot more/
    $ trix
    9  - Buy a lot more beer.
    30 - Call mom.
    $

### Delete the Task List if it's Empty

If you keep your task list in a visible place (like your desktop) you might
want it to be deleted if there are no tasks in it.  To do this automatically
you can use the `--delete-if-empty` option in your alias:

    alias trix='python ~/path/to/trix.py --task-dir ~/Desktop --list todo.txt --delete-if-empty'