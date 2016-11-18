Vulkan Flocking: compute and shading in one pipeline!
======================

**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Project 6**

* Ethan Brooks
  Tested on: Windows 7, Intel(R) Xeon(R), GeForce GTX 1070 8GB (SIG Lab)

![](https://github.com/lobachevzky/Project6-Vulkan-Flocking/blob/master/boids.gif)

* Why do you think Vulkan expects explicit descriptors for things like generating pipelines and commands? HINT: this may relate to something in the comments about some components using pre-allocated GPU memory.

 This is because descriptors can be reused. This way the GPU does not need to reallocate memory for the objects every time they are reused.

* Describe a situation besides flip-flop buffers in which you may need multiple descriptor sets to fit one descriptor layout.

  If you were swapping out textures in the same pipeline, you might assign one texture to one descriptor set and another texture to a different descriptor set.

* What are some problems to keep in mind when using multiple Vulkan queues?
  * take into consideration that different queues may be backed by different hardware
  * take into consideration that the same buffer may be used across multiple queues

  Queues often need to be synchronized -- for example. One a graphics queue might start rendering before another compute queue is done calculating the values to be rendered. It is also important to take advantage of the fact that compute pipelines can run in parallel by spreading work among multiple compute pipelines

* What is one advantage of using compute commands that can share data with a rendering pipeline?

  This eliminates the need to copy data back and forth between pipelines.


### Credits

* [Vulkan examples and demos](https://github.com/SaschaWillems/Vulkan) by [@SaschaWillems](https://github.com/SaschaWillems)
