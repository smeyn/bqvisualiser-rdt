# Release Notes


**June 2023**

* Upgrade to Node 18
* UI improvements
* login issue remains
* Stages with performance issue:
   * Tree display will highlight nodes in red 
   * Stage Details will list cause of performance issue
* Progress tab now shows `Estimated Runnable Units` metric
* bottom tabs
  * Query tab now wraps long SQL
  * list referenced tables
  * lists reservation details and slot usage by reservation
  * optional error tab if query has errors


**11 Nov 2021**

Upgraded to Node V 12

**14 January 2020**

* Add ability to retrieve query by query id
* Added option 'AllUsers' to let user choose between listing their own queries or queries for all users in project
* tightened layouts
* improved display of failed queries

**6 October 2019**

* Added Progress View. See graphic display of work units comnpleted over time
* Highlight nodes that are still running. Useful for jobs that die
* Fix Stage display bug - when job was cancelled stage status was not displayed

**15 July 2019**

in order to have the application whitelisted on appspot.com, the automatic login
had to be disabled to allow users to access the Terms and Privacy page prior to logging in.

Treeview will by default hide reparttions.

Added a Display Options card at the bottom where this can be changed.
