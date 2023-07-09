# Multiprocessing (processes are completely isolated, no locking :) (and no GIL!), instead of locking: messaging)#
import multiprocessing
import os
import time

def func():
    print "hello from process %s" % os.getpid()
    time.sleep(1)

proc = multiprocessing.Process(target=func, args=())
proc.start()
proc = multiprocessing.Process(target=func, args=())
proc.start()

# Multiprocessing has its own multiprocessing.Queue which handles interprocess communication. #
# Also has its own versions of Lock, RLock, Semaphore # 
from multiprocessing import Queue, Lock
from multiprocessing import Pipe
parent_conn, child_conn = Pipe()
child_conn.send("foo")
print parent_conn.recv()

# Pooling - a processing pool contains worker processes with only a configured number running at one time. #
from multiprocessing import Pool
pool = Pool(processes=4)

# Pooling example #
from multiprocessing import Pool
def f(x):
    return x*x
if __name__ == '__main__':
    pool = Pool(processes=4)

    result = pool.apply_async(f, (10,))
    print(result.get(timeout=1))
    print(pool.map(f, range(10)))

    it = pool.imap(f, range(10))
    print(it.next())
    print(it.next())
    print(it.next(timeout=1))

    import time
    result = pool.apply_async(time.sleep, (10,))
    print(result.get(timeout=1))
	
# ThreadPool. Threading also has a pool. Confusingly, it lives in the multiprocessing module. #
from multiprocessing.pool import ThreadPool
pool = ThreadPool(processes=4)