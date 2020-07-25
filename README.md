# What is Neural Style Transfer ?

Neural style transfer is an optimization technique used to take two images—a content image 
and a style reference image (such as an artwork by a famous painter)—and blend them together 
so the output image looks like the content image, but “painted” in the style of the style reference image.

This is implemented by optimizing the output image to match the content statistics of the content image
and the style statistics of the style reference image. These statistics are extracted from the images using a convolutional network.

## Working Explanation

1. We take a content image and style image and resize them to equal shapes.
2. We load a pre-trained CNN (VGG16).
3. Knowing that we can distinguish layers that are responsible for the style (basic shapes, colors etc.) 
and the ones responsible for the content (image-specific features), we can separate the layers to independently work on the content and style.
4. Then we set our task as an optimization problem where we are going to minimize:

     (i) content loss (distance between the input and output images - we strive to preserve the content)

    (ii) style loss (distance between the style and output images - we strive to apply a new style)

    (iii) total variation loss (regularization - spatial smoothness to denoise the output image)

5. Finally, we set our gradients and optimize with the L-BFGS algorithm.

## Content Image
   ![](Content.png)
