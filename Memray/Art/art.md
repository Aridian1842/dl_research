### DeepDream
Jot down something based on [this](https://github.com/google/deepdream/blob/master/dream.ipynb).
Making the "dream" images is very simple. Essentially it is just a gradient ascent process that tries to maximize the L2 norm of activations of a particular DNN layer. Here are a few simple tricks that we found useful for getting good images:
  - offset image by a random jitter
  - normalize the magnitude of gradient ascent steps
  - apply ascent across multiple scales (octaves)

TOO BE HONEST, I didn't get the sense of the code.


**Controlling dreams**
The image detail generation method described above tends to produce some patterns more often the others. One easy way to improve the generated image diversity is to tweak the optimization objective. Here we show just one of many ways to do that. Let's use one more input image. We'd call it a "guide".

Note that the neural network we use was trained on images downscaled to 224x224 size. So high resolution images might have to be downscaled, so that the network could pick up their features. The image we use here is already small enough.

Now we pick some target layer and extract guide image features.
Instead of maximizing the L2-norm of current image activations, we try to maximize the dot-products between activations of current image, and their best matching correspondences from the guide image.

This way we can affect the style of generated images without using a different training set.

### A Neural Algorithm of Artistic Style
The system uses neural representations to separate and recombine content and style of arbitrary images, providing a neural algorithm for the creation of artistic images. Moreover, in light of the striking similarities between performance-optimised artificial neural networks and biological vision,3–7 our work offers a path forward to an algorithmic understanding of how humans create and perceive artistic imagery.
