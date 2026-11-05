# Three AI models on one GPU

**Problem.** Three local models from two servers could load at the same time, but the GPU had only 8 GB. With the agent model loaded, another model ran 95% on the CPU. This affected the order path, not only my own tools.

**Fix.** There is now one server, one model and one queue, and all code calls the model through one module. I tested four requests at the same time, and the server answered them one after another, all correct. The server now also needs a key and is not open to the network.

**Lesson.** On limited hardware, a queue and one strong model beat several small models that compete.
