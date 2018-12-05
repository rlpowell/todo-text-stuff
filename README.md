# todo-text-stuff
Stuff I've written for my todo.txt setup.

#### Currently contains:

`ice_recur`: A recurring item generator for todo.txt.  Yes, there are like 14 of these, but I couldn't find a single one that could do "every 2 weeks" and would run the script for previous days that the script was missed if your computer wasn't turned on, so I wrote my own.
  - REQUIREMENTS: Ruby and gems: ice_cube, optimist, fileutils
  - Run `todo.sh ice_recur --help` for info on how to use this. Also, command line options posted at the bottom of the README.

`templated_checklists`: A file to keep available copies of one-time checklists (i.e. "stuff to take when going swimming")
  - Read the comments at the top of the `templated_checklists` file for info on how to use this.

#### Installation:

This script goes in `$TODO_DIR/actions/`

You put your entries in `$TODO_DIR/ice_recur.txt` , and add something like this:

      ~/bin/todo.sh ice_recur

to your crontab, to run once a day.

Every entry that matches the current day or previous days after `.ice_recur_completed` was last touched will be added, as long as there is no other entry with the same text content.

Comments can be added to the file using `#` but `ice_recur.txt` can contain no blank lines between entries or the script won't execute properly.

#### Recurrence Format (`ice_recur.txt`)

Entries look like:

  `@[optional starting date] [timing] - [task]`

like:

  `@2016-02-03 Weekly ; day Monday - (B) Mon Recur Test`

Where `[timing]` is a sequence of timing specifiers seperated by " ; ".  Each timing specifier makes the item more specific.

The starting date (marked by `@`) is entirely optional; if specified, the script won't start to run until that date.

#### Tests:

Run `ice_recur` tests like this if you want pretty output and failure if you miss tests: `prove -v --exec "./ice_recur --test" ice_recur`

#### Changelog:

1. ice_recur 1.2   29 Nov 2018: Added support for `day_of_week`, `day_of_year` and `month_of_year`
2. ice_recur 1.3   29 Nov 2018: Now uses the timestamp on the `.ice_recur_completed` file, and runs the schedule for each day since then, so you can run it less than once a day and it'll still work properly.
3. ice_recur 1.4   30 Nov 2018: No longer uses `todotxt-rb`; this means better handling of key/value tags, at least potentially
4. ice_recur 1.5    2 Dec 2018: Added `-n, -p, and -o`.  Won't run twice on the same day anymore.  Additional clarity on what's getting added.
5. ice_recur 1.5.1  3 Dec 2018: Bugfix: Start the run the day *after* the last touch to the completed file.
6. ice_recur 1.5.2  4 Dec 2018: Added `-f`

#### Options:
```
  -t, --test               Run tests on the recurrence code.
  -c, --check=<s>          Check the completion file to see if ice_recur has actually run in the last
                           two days.  Takes an email address to complain to if not as argument.
  -s, --show-next          Instead of generating entries, show the next date that each entry *would*
                           run.
  -n, --dry-run            Show the resulting entries but do not add them to the todo file
  -p, --ignore-projects    By default, projects ("+foo") are counted as part of the text when
                           deciding if ice_recur is about to add a duplicate entry, so "new entry"
                           would be added even if "new entry +foo" already exists.  If you use this
                           flag, those two will be considered the same entry and so it wouldn't be
                           added.
  -o, --ignore-contexts    By default, contexts ("@foo") are counted as part of the text when
                           deciding if ice_recur is about to add a duplicate entry, so "new entry"
                           would be added even if "new entry @foo" already exists.  If you use this
                           flag, those two will be considered the same entry and so it wouldn't be
                           added.
  -v, --version            Print version and exit
  -h, --help               Show this message
 ```
