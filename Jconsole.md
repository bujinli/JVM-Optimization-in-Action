# Jconsole

## connection is unsuccess [local]
* ensure hostname is local machine ip
```
-Djava.rmi.server.hostname=10.58.69.65 
```
## secure connection failed jconsole
* disable ssl & auth
```
-Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
```

## get dump file
```
-XX:+HeapDumpOnOutOfMemoryError
-XX:HeapDumpPath="./memleaktest.hprof"
```

# Jvisualvm
## analysis dump file
jvisualvm 


## OQL console
select cr from byte[] cr where cr.length > 10000
select heap.findClass("java.io.InputStream").subclasses() 

# MAT
## concept
### Shallow vs. Retained Heap
Shallow heap is the memory consumed by one object. An object needs 32 or 64 bits (depending on the OS architecture) per reference, 4 bytes per Integer, 8 bytes per Long, etc. Depending on the heap dump format the size may be adjusted (e.g. aligned to 8, etc...) to model better the real consumption of the VM.

Retained set of X is the set of objects which would be removed by GC when X is garbage collected.

Retained heap of X is the sum of shallow sizes of all objects in the retained set of X, i.e. memory kept alive by X.

Generally speaking, shallow heap of an object is its size in the heap and retained size of the same object is the amount of heap memory that will be freed when the object is garbage collected

