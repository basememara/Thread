# Thread
[![](http://img.shields.io/badge/Swift-2.1-blue.svg)](https://developer.apple.com/swift) [![](http://img.shields.io/badge/Platforms-iOS_|%20OS%20X_|%20tvOS_|%20watchOS-blue.svg)]()

A simple wrapper on NSThread to run blocks on *exactly* the same thread. It’s guaranteed First-In-First-Out (FIFO). 

This code is based on the following StackOverflow answer: http://stackoverflow.com/a/22091859. Permission to redistribute has been granted by the original author (Marc Haisenko).

```swift
let thread = Thread()
thread.enqueue {
    // Block is run on the thread
}
```
Blocks are removed from the queue just before they get run.

Start and stop the thread:
```swift
let thread = Thread(start: false)
thread.enqueue {
    // Block is run on the thread
}
thread.enqueue {
    // Block is run on the thread
}
// Start the thread to begin running queued up blocks
thread.start()
// and maybe stop the thread again. Blocks still in the queue
thread.stop()
```

Clear queue:
```swift
// Remove any blocks still in queue
thread.clearQueue()
```

### When *not* to use
**Thread** is very strict for running on *exactly* the same thread. For do-on-background-return-on-main stuff, use the brilliant [**Async**](https://github.com/duemunk/Async) wrapper for GCD.

### License
The MIT License (MIT)

Copyright © 2015 Tobias Due Munk

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
