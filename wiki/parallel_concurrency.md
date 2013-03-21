the modern world is parallel
=============================

* multicore
* networks
* clouds of cpus
* loads of users

golang supports concurrency
===========================

go provide:
* concurrency execution (goroutines)
* synchronization and messaging (channels)
* multi=way concurrent control (select)

concurrency vs. parallelism
===========================
* concurrency is about dealing with lots of things at once. (DEALING != DOING)
* parallelism is about doing lots of things at once.

> One is about structure, one is about execution.

concurrency porvides a way to structure a solution to solve a problem that may (but not necessarily) be parallelizable.

golang backgroud
==================

goroutines
-----------
A goroutine is a function running independently in the same address space as other goroutines.

    f("hello", "world") // f runs; we wait
    go f("hello", "world") // f starts running
    g() // does not wait for f to return

Like launching a function with shell's & notation.

> Goroutines are not threads
(They're a bit like threads, but they're much cheaper.)
Goroutines are multiplexed onto OS threads as required.
When a goroutine blocks, that thread blocks but no other goroutine blocks.

Channels
---------
Channels are typed values that allow goroutines to synchronize and exchange information.

    timerChan := make(chan time.Time)
    go func() {
        time.Sleep(deltaT)
        timerChan <- time.Now() // send time on timerChan
    }()
    // Do something else; when ready, receive.
    // Receive will block until timerChan delivers.
    // Value sent is other goroutine's completion time.
    completedAt := <-timerChan

Select
-------
The select statement is like a switch, but the decision is based on ability to communicate rather than equal values.

    select {
    case v := <-ch1:
        fmt.Println("channel 1 sends", v)
    case v := <-ch2:
        fmt.Println("channel 2 sends", v)
    default: // optional
        fmt.Println("neither channel was ready")
    }

Closures are also part of the story
------------------------------------
Make some concurrent calculations easier to express.

    They are just local functions.
    Here's a non-concurrent example.
    func Compose(f, g func(x float) float)
                      func(x float) float {
         return func(x float) float {
            return f(g(x))
        }
    }

    print(Compose(sin, cos)(0.5))

Launching daemons
-------------------
Use a closure to wrap a background operation.

This copies items from the input channel to the output channel.

    go func() { // copy input to output
        for val := range input {
            output <- val
        }
    }()

The for range operation runs until channel is drained.

A simple load balancer
---------------------
A unit of work:

    type Work struct {
        x, y, z int
    }

A worker task:

    func worker(in <-chan *Work, out chan<- *Work) {
       for w := range in {
          w.z = w.x * w.y
          Sleep(w.z)
          out <- w
       }
    }

Must make sure other workers can run when one blocks.

The runner:

    func Run() {
       in, out := make(chan *Work), make(chan *Work)
       for i := 0; i < NumWorkers; i++ {
           go worker(in, out)
       }
       go sendLotsOfWork(in)
       receiveLotsOfResults(out)
    }

Easy problem but also hard to solve concisely without concurrency.

ppt: http://concur.rspace.googlecode.com/hg/talk/concur.html#slide-1
