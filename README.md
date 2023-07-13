# CNN-deterministic-decoupling

## Description
This project explores the feasability of implementing nested normalizations as defined in [1] to the features used by a texture model based on DISTS [2]. It calculates the visual difference between input images and a predefined reference image using the model and there are tree types of experiments texture syntehsis, style transfer and rebersability. The code is developed for Google Colab, and the project folder should be uploaded to the base directory of Google Drive without changing its name.

[1] Eduardo Martínez-Enrí quez, Maria del Mar Gonzalez, and Javier Portilla. “Deterministic Decoupling of Global Features and its Application to Data Analysis”. In: arXiv preprint arXiv:2207.02132 (2022).

[2]Keyan Ding et al. “Image quality assessment: Unifying structure and texture similarity”. In: IEEE transactions on pattern analysis and machine intelligence 44.5 (2020), pp. 2567–2581.


## Packages

### DISTS_mod


The `DISTS_mod` package provides the implementation of the DISTS model and related functions.

### L2pooling class

The `L2pooling` class is used to replace the MaxPooling operations in VGG16. It helps prevent aliasing issues commonly caused by MaxPooling.

### DISTS class

The `DISTS` class is the main model used to calculate the visual difference between images. It provides the following functions:

- `forward_once(x)`: Performs a forward pass in the neural network for an input `x` and returns the intermediate outputs of each layer up to the specified layer.
  - Parameters:
    - `x`: Tensor - The input to the neural network.
  
- `forward(x)`: Performs a forward pass in the neural network for an input `x` and returns the DISTS distance between the input's features and a predefined reference.
  - Parameters:
    - `x`: Tensor - The input to the neural network.

- `set_target(ref)`: Sets a reference image to be used for distance calculation.
  - Parameters:
    - `ref`: Tensor - The reference image.

You can import the `DISTS` class from `DISTS_mod` package and use these functions to calculate visual differences between images.


## ImageFunctions

The `ImageFunctions` package contains functions for image processing.

### prepare_image

The `prepare_image` function adjusts the size of a texture and transforms it into a tensor.


- `prepare_image(image, size)`: The `prepare_image` function adjusts the size of a texture and transforms it into a tensor.

   - Parameters:
        `image`: Image - The image to transform.
        `size`: int - The size to which the texture will be resized.


- `show_image(image)`: The show_image function transforms a tensor into an image and displays it.

   -  Parameters:
        `image`: Tensor - The tensor to display as an image.


- `save_image(image, name)`: The save_image function transforms a tensor into an image and saves it to a directory.

    - Parameters:
    `image`: Image - The image to transform.
    `size`: int - The size to which the texture will be resized.

You can import the ImageFunctions package and use these functions for image processing tasks.

## Runge_Kutta

The `Runge_Kutta` package provides functions for Runge-Kutta methods.


- `RungeKutta4(x, c, step_size, list)`: The `RungeKutta4` function implements the fourth-order Runge-Kutta method for solving differential equations. It calculates the function value at four different points and their corresponding gradients. Finally, it updates the value of `x` using the fourth-order Runge-Kutta formula.

    - Parameters:
        `x`: Tensor - The tensor to adjust (should be a texture).
        `c`: Callable - The cost function.
         `step_size `: float - The step size for RK.
         `list `: array_like - Records the cost value.

You can import the Runge_Kutta package and use the RungeKutta4 function to apply the fourth-order Runge-Kutta method.

