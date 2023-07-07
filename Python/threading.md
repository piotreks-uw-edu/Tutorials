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