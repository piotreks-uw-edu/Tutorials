# Multiprocessing (processes are completely isolated, no locking :) (and no GIL!), instead of locking: messaging)#
import multiprocessing
import os
import time

def func():
    print("hello from process %s" % os.getpid())
    time.sleep(1)

if __name__ == '__main__':
    proc = multiprocessing.Process(target=func)
    proc.start()
    proc2 = multiprocessing.Process(target=func)
    proc2.start()

# Multiprocessing has its own multiprocessing.Queue which handles interprocess communication. #
# Also has its own versions of Lock, RLock, Semaphore # 
from multiprocessing import Queue, Lock
from multiprocessing import Pipe
parent_conn, child_conn = Pipe()
child_conn.send("foo")
print parent_conn.recv()

# Pooling - a processing pool contains worker processes with only a configured number running at one time. #
from multiprocessing import Pool
import os
import time

def func(_):  # Note: Pool.map expects a function that takes a single argument. Hence we include a dummy parameter '_'.
    print("hello from process %s" % os.getpid())
    time.sleep(1)

if __name__ == '__main__':
    with Pool(processes=2) as pool:  # Create a Pool with 2 processes
        pool.map(func, range(2))  # Apply 'func' 2 times

	
# ThreadPool. Threading also has a pool. Confusingly, it lives in the multiprocessing module. #
from multiprocessing.pool import ThreadPool
pool = ThreadPool(processes=4)