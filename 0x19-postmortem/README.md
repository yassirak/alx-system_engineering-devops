# Server Requests Failure Report
Last Month, it was reported that all the requests made to our server is returning a 500 Error, all our services were down.
The root cause was from one of the configuration file of our server web_stack_debugging_1.

## Timeline
The error was realized on 25th of April 11:00 pm(GMT).
When the pager notified one of our team members.
Our engineering team On-call quickly logged in to the server for further analysis and to get to the root of the problem.
The problem was solved later by 25th of April 1:00 am (GMT).

## Root Cause and Resolution
The server stopped working because the config of the software(Nginx) serving the server pages was seen to be a directory instead of a symbolic link to another config file.
The config file(sites-enabled) was quickly deleted.
The config file(sites-enabled) was then made a symbolic link to the original config file(sites-available).
The server was restarted.
100% of traffic is back.

## Prevention against such problm in future
- Always test and thoroughly check the config files before deployment.
- ALways keep an eye on servers to ensure proper running of them.
- Always have backup severs to prevent all of our services from being down during an issue.

However, it is worth noting that such errors are unlikely to occur again because, as programmers, we never make mistakes! 😉
