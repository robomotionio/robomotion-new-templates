# Fork Branch with Memory Queue

The Fork Branch with Memory Queue flow is designed to efficiently screenshot large batches of websites by running multiple browser sessions at the same time. It uses a first in first out Memory Queue to hold website information and a Fork Branch to create parallel workers that process sites independently until the queue is empty.

## Watch the video

👉 https://www.youtube.com/watch?v=QrWmtATwOMo

## How it works

### 1. Initialize

The flow begins by preparing an array of e-commerce sites. Each item includes the website name, URL, and screenshot file path. This array is passed into a Memory Queue, creating a FIFO structure stored inside the robot's memory. Every parallel worker will pull from this same queue.

### 2. Parallel Processing with Fork Branch

A Fork Branch determines how many parallel browser sequences run simultaneously. For example, setting it to six launches six browser sessions that work side by side.

Each branch operates independently:

- Opens a browser
- Dequeues the next website from the Memory Queue
- Opens the link
- Takes a screenshot
- Signals completion with a WG Done node

The Fork Branch waits until all branches have reported completion before continuing, guaranteeing clean synchronization across parallel tasks.

### 3. Exception Handling

When no items remain in the Memory Queue, the Dequeue node throws an exception. An Exception Handler catches this event, closes the browser for that branch, and signals branch completion using WG Done. This ensures the automation ends gracefully without leaving open sessions behind.

## What this flow enables

- High speed screenshot capture for large lists of sites
- Efficient use of parallel browser sessions
- Automatic load balancing through FIFO queue distribution
- Safe shutdown of branches when work is complete

This architectural pattern is ideal for large scale, parallelizable tasks such as monitoring, scraping, or website auditing where each job can be processed independently using shared queued data.
