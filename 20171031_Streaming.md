## Spark
* Streaming
* Mini-batches
	* **Prefix output consistency**
	* Exachy
	* Straggler

~~Event-time~~

---

### Flink & StreamS

~~Prefix-output~~

* Exactly once
* Event-time
	* CTI
	* Watermark
* Stragglers

Barrier -> ABS

FT: replay from input

---

### StreamS

vertex, edge-local snapshots and checkpoints

Edge: persistent, reliable storage of events

* Near real-time

* "low" latency
 
* Exactly-once

* Stragglers/failures

* rStream

* rVertex

---

#### rStream

log -> ordered by **sequence number**

#### rVertex

```
readNext(i)     // from particular input

Load(snapshot)      // Last seen sequence number from each input 
                    //and the value of vertex's state
```


##### Snapshot

```
   <i_1,i_2, o, t> 
-> <i_1+1, i_2+2, o+1,t'>
-> <...>(=c) 
-> <...>
```
periodic checkpoints

one of the snapshots is written to a persistent store

store -> c

---

local memory buffer -> asynch flushed to a persistent store

? Vertex fails

---

#### Garbage Collection

* Events on every edge that are not needed

* "take out" events on every edge

Look at every output (`O_s`), see the sequence num of input corresponding to this output(i_s1, i_s2,...),
these input are no longer needed.