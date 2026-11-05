# A Redis timeout that could lose a job

**Problem.** The worker logged a Redis timeout about 58 times an hour. It looked like noise, but a job popped at the exact moment of a timeout could be lost.

**Cause.** The worker waits for a job with a 5-second `BLPOP`. A new version of the client library changed the default read timeout to 5 seconds. Both limits landed at the same moment, and the client sometimes gave up first.

**How I found it.** The hourly count was flat, which pointed to a timer. The client defaults inside the container showed 5 seconds, and the server does not drop idle clients.

**Fix.** The worker's client now has a 30-second timeout.

**Rule.** A client that makes blocking calls needs a timeout longer than its longest wait.
