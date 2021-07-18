# Image-colorization-autoencoders
This project aims to colorize grayscale images with autoencoders.
Given a grayscale image, the model should be able to colorize it and we are going to do so with the help of **autoencoders**.

An autoencoder is a neural networks that are designed to reconstruct the original image. During this process, there might be some reconstruction errors since we take an image and scale it down and then upscale it back to it's original size. 

Here's the basic idea of the project :
1. Choose an appropriate dataset
2. Resize the Images to 256\*256
3. Convert from RGB --> Lab colorspace
  *   Lab colorspace comprises of 3 channels
      * L : Lightness. values range from 1 - 100
      * A : represents colors from green to red. values range from -128 to +128
      * B : represents colors from blue to yellow. values range from -128 to +128

      We're using the lab colorspace because we get to isolate the black and white part from the colored part.

4. Normalize the images.
5. Create the model
6. Provide the L channel i.e the monochrome image as the input to the model.
7. Get ab channels i.e the colored part of the image as the output.
8. Combine the L, a and b channels and convert from Lab to RGB colorspace.
9. Evaluate the results.

The model that worked the best for me was trained on the landscape images dataset for 200 epochs on google colab GPU with adam optimiser and 0.1 validation split.

Here are some results : 
| Grayscale Image| Predicted Image| Ground Truth|
| :-------------:|:--------------:| :----------:|
| <img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126062471-dbf81e44-49bf-4263-bf71-adf0dcfcd6b3.png">| <img width="111" alt="image" src = "https://user-images.githubusercontent.com/35341758/126062480-38588d75-fb8f-42fd-a066-15b50f90daf2.png">| <img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126062484-ab34e6b3-eebf-4b06-9d49-6734675958c5.png"> |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
