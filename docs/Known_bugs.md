# Known Bugs
 

On clicking the Login button, the login dialog appears. After completing 
the dialog successfully, the login button is still highlighted.
The user needs to click the button again so that the logout button is highlighted,
before being able to download query plans.

Download from Google Cloud => Get Projects function is very slow.

The Records Transferred displayed on the graph edges are inferred numbers based on
`records read` and `records written` values in stages.
They are mostly correct, but in some cases 
they can't be exactly inferred due to missing detail.

