# todo-text-stuff
Stuff I've written for my todo.txt setup.

Currently contains:

ice_recur : A recurring item generator for todo.txt.  Yes, there are like 14 of these, but I couldn't find a single one that could do "every 2 weeks", so I wrote my own.   REQUIREMENTS: Ruby ; gems: ice_cube, optimist
  - Run "todo.sh ice_recur --help" for info on how to use this.
templated_checklists : A file to keep available copies of one-time checklists (i.e. "stuff to take when going swimming")
  - Read the comments at the top for info on how to use this.

Tests:

Run ice_recur tests like this if you want pretty output and failure if you miss tests: prove -v --exec "./ice_recur --test" ice_recur

Changelog:

ice_recur 1.2 29 Nov 2018: Added support for day_of_week, day_of_year and month_of_year
ice_recur 1.3 29 Nov 2018: Now uses the timestamp on the .ice_recur_completed file, and runs the schedule for each day since then, so you can run it less than once a day and it'll still work properly.
ice_recur 1.4 30 Nov 2018: No longer uses todotxt-rb; this means better handling of key/value tags, at least potentially
ice_recur 1.5  2 Dec 2018: Added -n, -p, and -o.  Won't run twice on the same day anymore.  Additional clarity on what's getting added.
