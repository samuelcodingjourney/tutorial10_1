### Reflection
1.2 Understanding how it works.

![alt text](<assets/Screenshot (1092).png>)

The reason that the output is like that just like in the screenshot above is because the Samuel's Komputer: hey hey is printed out after spawning the async task. So this is the main thread that is continuing the execution by printing the hey hey message because it is part of the main thread execution flow. So the asynchronous task that prints Samuel's Komputer: howdy! then waits for a timer future to complete which is waiting for 2 seconds, after that the async task resumes execution. It does so by printing the Samuel's Komputer: done! line after that 2 seconds. This also indicates that the executor that runs the async task to completion and ensure that the aysnc task output howdy and done must appears after the hey hey message printed by the main thread. 

1.3 Multiple Spawn and removing drop

Without Spawner:
Screenshot 1:

![alt text](<assets/Screenshot (1095).png>)

Screenshot 2:

![alt text](<assets/Screenshot (1096).png>)

With Spawner:

Screenshot 3:

![alt text](<assets/Screenshot (1097).png>)


Based on the screenshots above, firstly we can see in screenshot 1 that by commenting out drop(spawner), the spawner is not dropped so that it remains in scope even after the tasks have all been spawned. The executor here will continue running and waiting for more tasks to be spawned while we can see in the code and based on the output in the terminal that there are no more tasks to be spawned. This would lead to resource wasting because as can be seen in screenshot 1, the executor will still run so that I had to enter ctrl + c to even stop the executor like in screenshot 2. In screenshot 3 when spawner is not commented out, the spawner will be dropped after all tasks have been spawned. The executor will be notified that no omre tasks will be spawned so that it can shut down and free up the system resources and ensure efficient resource utilization.    