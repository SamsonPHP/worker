# SamsonPHP a worker module
Concept:
Create resource for storing list of tasks grouped by module identifier[and sub identifiers splitter by dot as a key], that has a priority in module scope, and a data(no size limit) field, that stores serialized Task class instance.

This Task instances are created by modules whenever they want to
Worker can execute tasks using web gui async requetst(js needed) and ability to modify styles and binding custom js events, and also can be run from cron(simple interface needed to generate correct cron string by specifying module I'd and period, or all except some module maybe.

Maybe better to have one cron input controller(via pure php, no http request) and all tasks have to have isCron and isWeb field, so when you create a task it knows how it can be executed.

So I see a module class files ending with *Task.php which are automatically parsed from module /tasks folder by parent module, or better analyzing all loaded classes who are samsonphp\worker\Task ancestors, it will be also supported by compressed version(we need a separate loading loading logic for it as if run index php it will call s()->start(), need to avoid it somehow). 

Module will have functions that creates tasks instances and this would be considered as task scheduling.

Cron tasks not removed from resource storage file. Web tasks are removed after execution.

Several web tasks can be executed simultaneously this needs to bind them to php session wich has created them.

Only one cron task can be executed they are in fifo queue.

tasks log has to be written to see if there were any errors. We need separate log resource storage.

For all tasks started, ended and elapsed time should be fixed.



Module has to be platform independent can we make SamsonPHP module platform independent? We need ability to bind a route to be worked out by some callback and generate a response independently of what this callback is. But how can we compress this classes modules? 

Throught composer.lock and it's extra parameters! We need parameters to load modules into core, compress them, Identifier specification for not module ancestors.






