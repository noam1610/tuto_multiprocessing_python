# Tutorial multiprocessing python

The goal of this article is to present shortly a solution for the following problem.

![Screenshot](problem.png)

## The full problem

Let's imagine we have a flow of files getting in the system from the the web.
We need to process each file with **Process1** and then with **Process2**.
Of course we don't want to wait for all the files to be processed by **Process1** and then by **Process2**.
So we need a way to make a pipeline so that the flow is continuous.

## The "simple" Solution

### Processes and Queues

Here we will use, the multiprocessing package of python 3.6. [for more details](https://docs.python.org/3.6/library/multiprocessing.html#module-multiprocessing)
This package allows to run several instances of python.exe, each python.exe is responsible for a specific task.
In order to create a flow between them we use a Queue (LILO).
Basically, the first in the queue will be th efirst to go out to the next process.


### The code

Let's moke the data coming in with a simple function:
'''python
ENTRY_ARRAY = range(0, 5000)

def process_init(queueIn):
    for val in ENTRY_ARRAY:
        print("entering the Q : ", val)
        queueIn.put(val)
'''

