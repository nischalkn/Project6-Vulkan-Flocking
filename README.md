Vulkan Flocking: compute and shading in one pipeline!
======================

**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Project 6**

* Nischal K N
  Windows 8.1, i7-5500U @ 2.40 GHz 16GB, GTX 920M 3839MB (Personal)

### OUTPUT
![](Images/output.gif)

### Q&A
* **Why do you think Vulkan expects explicit descriptors for things like generating pipelines and commands?**

  Vulkan API pre allocates GPU command pool memory and command buffers cannot be allocated/changed at runtime. Hence explicit descriptors for pipelines and commands are required to specify which data to act on at different stages of the system. This also provides us more flexibility in customizing various stages of the design with minimum overhead of data transfer between CPU and GPU.

* **Describe a situation besides flip-flop buffers in which you may need multiple descriptor sets to fit one descriptor layout.**

  Different channels of an RGBA Image. Each channel represents different color value for the same scene. Hence they fit in one descriptor layout.
* **What are some problems to keep in mind when using multiple Vulkan queues?**
  * **take into consideration that different queues may be backed by different hardware**
  * **take into consideration that the same buffer may be used across multiple queues**

  Vulkan Queues are designed to have high parallelism if the workload is highly independent. But however when ever there is a lot of exchange of data between multiple queues, it must be taken care that there are no guarantees on the order of execution of the queues. Hence appropriate semaphores/fences must be used.
* **What is one advantage of using compute commands that can share data with a rendering pipeline?**

  Reduces the expensive copy operations of input and output data from compute to render pipeline.

### Credits

* [Vulkan examples and demos](https://github.com/SaschaWillems/Vulkan) by [@SaschaWillems](https://github.com/SaschaWillems)
