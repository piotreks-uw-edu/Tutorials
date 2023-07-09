# Mutex locks (threading.Lock) (Only one lock per thread! (or risk mysterious deadlocks).)#
x = 0
x_lock = threading.Lock()

with x_lock:  # Example critical section
	## statements using x
	
# Or use RLock for code-based locking (locking function/method execution rather than data access) #
import threading
import time

lock = threading.Lock()

def f():
    lock.acquire()
    print("%s got lock" % threading.current_thread().name)
    time.sleep(1)
    lock.release()

threading.Thread(target=f).start()
threading.Thread(target=f).start()
threading.Thread(target=f).start()

# Nonblocking Locking #
# .acquire() will return True if it successfully acquires a lock.  #
# Its first argument is a boolean which specifies whether a lock should block or not. The default is True #
import threading
lock = threading.Lock()
lock.acquire()
if not lock.acquire(False):
    print("couldn't get lock")
lock.release()
if lock.acquire(False):
    print("got lock")


#Example
import sys
import threading
import time

def func():
    for i in range(5):
        print("hello from thread %s" % threading.current_thread().name)
        time.sleep(1)

threads = []
for i in range(3):
    thread = threading.Thread(target=func, args=())
    thread.start()
    threads.append(thread)
	
# Subclassing Thread #
import threading

class MyThread(threading.Thread):

    def run(self):
        print("hello from %s" % threading.current_thread().name)

thread = MyThread()
thread.start()
		
# Subprocesses (subprocess) #
## Invocation ##
import subprocess

subprocess.run('ls')

# =========================================Semaphore example #
# Import the necessary modules
import random
import sys
import threading
import time

# Initialize a Semaphore object with a count of 2. This means that 2 threads can 
# hold the lock at any given time. Any additional threads that attempt to acquire
# the lock will have to wait until one of the current holders releases it.
lock = threading.Semaphore(2)

# This function will be run by each thread. It writes to stdout, 
# which is a shared resource.
def write():
    # Try to acquire the semaphore. If the maximum number of threads (2)
    # are already holding it, this will block until one of them releases it.
    lock.acquire()

    # Write to stdout that the thread is starting to write.
    sys.stdout.write("%s writing.." % threading.current_thread().name)

    # Sleep for a random amount of time. This simulates the time it takes to 
    # complete the task (writing in this case).
    time.sleep(random.random())

    # Write to stdout that the thread is done writing.
    sys.stdout.write("..done\n")

    # Release the semaphore so that another thread can acquire it if any are waiting.
    lock.release()


# Main loop of the script
while True:
    # Create a new Thread object that will run the write function when started.
    thread = threading.Thread(target=write)

    # Start the new thread.
    thread.start()

    # Wait for a short period of time before starting the next thread. This gives
    # the current thread some time to start and potentially acquire the semaphore
    # before the next one is started.
    time.sleep(.1)
	
# =========================== Queues allow multiple producers and multiple consumers to exchange data safely.#
from queue import Queue

# Create a queue object, q, with a maximum size of 10. This means that the queue #
# can hold up to 10 items before put() calls start to block, waiting for space to become available. #
q = Queue(maxsize=10)

# Put the integer 37337 onto the queue. Since the queue is currently empty and its maximum size is 10,
# this operation will not block.
q.put(37337)

# Set block to True. When block is True, Queue.get() will block until it can return an item,
# rather than raising the Empty exception if the queue is currently empty.
block = True

# Set timeout to 2. This is the maximum number of seconds Queue.get() will block for when block is True,
# before raising the Empty exception.
timeout = 2

# Attempt to get an item from the queue. Because block is True and the queue is not empty, this will 
# immediately return the item and print it. If the queue was empty, it would block for up to 2 seconds
# waiting for an item to be put onto the queue, before raising the Empty exception.
print(q.get(block, timeout))

# ============================== Common use: producer/consumer patterns of queues#
from Queue import Queue
data_q = Queue()

Producer thread:
for item in produce_items():
    data_q.put(item)

Consumer thread:
while True:
    item = q.get()
    consume_item(item)
	
# ================================ Timed events (threading.timer) #
import threading
import time

def called_once():
    """
    this function is designed to be called once in the future
    """
    print("I just got called! It's now: {}".format(time.asctime()))

# setting it up to be called
t = Timer(interval=3, function=called_once)
t.start()

# you can cancel it if you want:
t.cancel()

# ================================ Threading example with a queue #
#!/usr/bin/env python

import threading
import queue
import time

from integrate import f, integrate_numpy

def timer(func):
    def wrapper(*arg, **kw):
        ''''
        Secondary source: https://stackoverflow.com/questions/1622943/timeit-versus-timing-decorator
        Primary source: http://www.daniweb.com/code/snippet368.html
        '''
        t1 = time.time()
        res = func(*arg, **kw)
        t2 = time.time()
        total_time = t2 - t1
        print(f"Total time: {total_time} seconds")
        return res
    return wrapper

@timer
def threading_integrate(f, a, b, N, thread_count=2):
    """break work into N chunks"""
    N_chunk = int(float(N) / thread_count)
    dx = float(b - a) / thread_count

    results = queue.Queue()

    def worker(*args):
        results.put(integrate_numpy(*args))

    for i in range(thread_count):
        x0 = dx * i
        x1 = x0 + dx
        thread = threading.Thread(target=worker, args=(f, x0, x1, N_chunk))
        thread.start()
        print("Thread %s started" % thread.name)

    return sum((results.get() for i in range(thread_count)))


if __name__ == "__main__":

    # parameters of the integration
    a = 0.0
    b = 10.0
    N = 10**8
    thread_count = 8

    print("Numerical solution with N=%(N)d : %(x)f" %
          {'N': N, 'x': threading_integrate(f, a, b, N, thread_count=thread_count)})
		  


