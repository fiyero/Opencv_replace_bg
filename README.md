# Use OpenCV to extract object and replace the background
## https://medium.com/@patrickhk/use-opencv-to-extract-object-and-replace-the-background-80f2ba016621

I will write about how to use OpenCV and color channel to extract an object and replace with another background. The demonstration code is in the bottom of this article.<br/>

### Choose the Color space
First we have to decide one or several color space to help us better distinguish object from the background. There are several options such as RGB, HSV, CMYK..etc<br/>
![pizza](https://cdn-images-1.medium.com/max/800/1*hLlB1c0LJR19IJ-QBePBGg.png)<br/>
For this image obviously RGB is the first choice as the background is blue


### Create masking for the object/background
We can make use of the cv2.inrange function to create masking for the object/background. In this example we create masking for the background so we set lower boundary as 230 and upper boundary as 255 for the Blue channel, so only the background can pass the cv2.inrange function and obtain binary image like this<br/>
![p2](https://cdn-images-1.medium.com/max/800/1*v5wc6qRLAgNtidbpXhgfcw.png)

### Isolate the object
Apply masking to the original image to select the blue background and turn it into black by directly assign the pixel as (0,0,0)<br/>
![p3](https://cdn-images-1.medium.com/max/800/1*uo8Q6gRbzGAD8KlhtI_OUw.png)

### Get a new background
First we should resize the new background image as the same size of the masking. Then we apply the same masking to turn the same area on the new background as black.<br/>
![p4](https://cdn-images-1.medium.com/max/800/1*fhy3CugDn63E0wzWxMYIbw.png)

### Combine the extracted object and new background
Now we can just simply add them together to form a new image<br/>

![p5](https://cdn-images-1.medium.com/max/800/1*tDxGJgPFzRWPLVLjGmKdMg.png)

### Discussion:
1. It seems very easy to extract an object from the above example, but usually object is not that distinguishable. Initially I want to demonstrate by using this cat image<br/>
![p8](https://cdn-images-1.medium.com/max/800/1*VSHdbE4SOVse8d3pNVH9-Q.png)
The difficulty is that the paws and chest of the cat have very similar color to the pillow and mattress, apparently RGB color space along will fail and I don’t think using HSV can help. We may have to add another constraint , such as specify the location and combine with the color threshold. But if that’s the case using Photoshop is much faster and easier. Why bother to stay in openCV?

2. Now I kind of understanding why actors or streamer always make video on a green background because easier to do post video editing.<br/>
-------------------------------------------------------------------------------------------------------------------------------------
### More about me
[[:pencil:My Medium]](https://medium.com/@patrickhk)<br/>
[[:house_with_garden:My Website]](https://www.fiyeroleung.com/)<br/>
[[:space_invader:	My Github]](https://github.com/fiyero)<br/>

