import time

init = time.perf_counter() 

init = time.perf_counter() 
for i in range(TIMES): 
    value = math.sqrt(i * math.fabs(math.sin(i) * math.cos(i)))

# Measured time
print("Measured time: %s" % (time.perf_counter() - init))