=============
Good Practice
=============

There are a couple of things that will help you to get the best experience
out of the CFMS HPC systems:

- setting a realistic 'timelimit' on your jobs (via -t DD-HH:MM:SS) will help the job scheduler work out when your job should run, and if it can be backfilled.   Without a timelimit set, the scheduler will assume 'unlimited' meaning that it will go to the back of the queue.
- request only the number of nodes that your job need.   For many code, more compute doesn't necessarily mean more performance.
- do ask for support.  Chances are we have run into any issues you might experience, and if not hopefully we can find a solution together. 
