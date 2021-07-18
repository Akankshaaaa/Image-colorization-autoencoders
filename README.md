# Image-colorization-autoencoders
This project aims to colorize grayscale images with autoencoders.
Given a grayscale image, the model should be able to colorize it and we are going to do so with the help of **autoencoders**.

An autoencoder is a neural networks that are designed to reconstruct the original image. During this process, there might be some reconstruction errors since we take an image and scale it down and then upscale it back to it's original size. 

### Here's the basic idea of the project :
1. Choose an appropriate dataset
2. Resize the Images to 256\*256
3. Convert from RGB --> Lab colorspace
  *   Lab colorspace comprises of 3 channels
      * L : Lightness. values range from `1 - 100`
      * A : represents colors from green to red. values range from `-128 to +128`
      * B : represents colors from blue to yellow. values range from `-128 to +128`

      We're using the lab colorspace because we get to isolate the black and white part from the colored part.

4. Normalize the images.
5. Create the model
6. Provide the L channel i.e the monochrome image as the input to the model.
7. Get ab channels i.e the colored part of the image as the output.
8. Combine the L, a and b channels and convert from Lab to RGB colorspace.
9. Evaluate the results.

The model that worked the best for me was trained on the landscape images dataset for 200 epochs on google colab GPU with adam optimiser and 0.1 validation split.

### Here are some results : 
| Grayscale Image| Predicted Image| Ground Truth|
| :-------------:|:--------------:| :----------:|
| <img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126062471-dbf81e44-49bf-4263-bf71-adf0dcfcd6b3.png">| <img width="111" alt="image" src = "https://user-images.githubusercontent.com/35341758/126062480-38588d75-fb8f-42fd-a066-15b50f90daf2.png">| <img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126062484-ab34e6b3-eebf-4b06-9d49-6734675958c5.png"> |
|<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064031-91e529f9-993e-492a-90ff-a756cf76912a.png">|<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064035-b68c35f4-d019-4b99-88d4-0fadc9a4b4e3.png">|<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064087-d8d56f58-5c99-4b24-a08f-4b0c6122e135.png">|
|<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064106-4578009e-5f52-4ab2-a94b-13e6e52701e4.png">|<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064110-833b6ee9-1bb7-48fe-b07f-bff47781408d.png"> |<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064118-a8afdf4c-308b-4bc3-9759-f6e2add7502b.png">|
|<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064159-014806fe-856e-40e3-a409-6d8eb1c5109c.png">|<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064162-3279d000-b5a6-4e8d-a748-14b16497b334.png">|<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064170-cbb4898f-f88a-40bc-95d3-e1a3680a0fc5.png">|
|<img width="109" alt="image" src="https://user-images.githubusercontent.com/35341758/126064227-4c1305a1-842c-408b-a146-14d2a93ae8fb.png">|<img width="111" alt="image" src="https://user-images.githubusercontent.com/35341758/126064233-619a5487-89cd-475c-9110-3b4a651c588f.png">|<img width="109" alt="image" src="https://user-images.githubusercontent.com/35341758/126064243-576a77d5-e574-45b5-b0f7-4fcbbb00833a.png">|
|<img width="109" alt="image" src="https://user-images.githubusercontent.com/35341758/126064257-12e8fe0b-8879-4057-95bc-65a01241bdb2.png">|<img width="109" alt="image" src="https://user-images.githubusercontent.com/35341758/126064262-06cdd42b-ba03-47f7-9be1-2d546b3fa3f6.png">|<img width="109" alt="image" src="https://user-images.githubusercontent.com/35341758/126064266-b02f522a-65be-4423-8b5e-cf4532ff38fd.png">|

There are a few blindspots in the predicted images but overall the model did a pretty good job of coloring the images. The dataset that I used comprised of 7K landscape images. The results highly depend on the nature and size of the dataset so make sure you choose an appropriate one. 


### References 
[Colorful Image Colorization](https://richzhang.github.io/colorization/)

[Auto Colorization of Black and White Images using Machine Learning “Auto-encoders” technique](https://becominghuman.ai/auto-colorization-of-black-and-white-images-using-machine-learning-auto-encoders-technique-a213b47f7339)
