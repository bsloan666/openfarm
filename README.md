OpenFarm
========

A scalable, robust, cloud-aware render farm.
--------------------------------------------

OpenFarm takes the divide-and-conquer approach to the complex problem of
distributed computing, relying on existing, general-purpose, high-performance 
tools running as separate sevices with very little additional glue.

The majority of source "code" is configuration and schemas. The separate 
components consist of:

*   Task Sheduler   - adjusts task queue order based on priority, execution time, etc. 
*   Host Scheduler  - tracks avaliable resources per host 
*   Task Dispatcher - assigns a queue of tasks to a pool of resources 
*   State Manager   - tracks the run state of each task (QUEUE, HOLD, RUN, DONE, FAIL, etc.)
*   Dependency Manager - blocks tasks with unsatisfied dependencies
*   Log Router      - sends realtime task logs to requesters
*   ClientAPI       - submit, query and modify jobs 
*   Daemon          - accepts and executes tasks from dispatcher

The objects that define the pieces of computational work the system is designed 
to execute consist of:
*   Process Group   - a bundle of independent or interdependent jobs
*   Job             - a distributable piece of work
*   Task            - one of an array of simultaneously runnable job fragments 
*   Phase           - one of a sequence of steps in a task  

Other objects that are manifested in parts of the system are:
*   Host            - a render node with some knowledge of its avaliable resources
*   Dependency      - can exist between any of the above work objects or external condtions
*   License         - as software licenses are typically not a host-bound resource...

The author has yet to make a comprehensive survey of possible candidates for the
components of the system. It is assumed that some parts may be subsumed under a
SQL database. Cayley graph database might be a fit for the dependency manager. A 
colleague has suggested the docker swarmkit as a possible candidate for the task
scheduler/dispatcher. 


As of August 1 2016, OpenFarm is pure vaporware. 



