# todo-text-stuff
Stuff I've written for my todo.txt setup.

Currently contains:

ice_recur : A recurring item generator for todo.txt.  Yes, there are like 14 of these, but I couldn't find a single one that could do "every 2 weeks", so I wrote my own.   REQUIREMENTS: Ruby ; gems: ice_cube, trollop, todotxt-rb
templated_checklists : A file to keep available copies of one-time checklists (i.e. "stuff to take when going swimming")

Tests:

Run ice_recur tests like this if you want pretty output and failure if you miss tests: prove -v --exec "./ice_recur --test" ice_recur

Changelog:

ice_recur 1.2 29 Nov 2018: Added support for day_of_week, day_of_year and month_of_year
