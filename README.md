# ColorDetectorApp
A project I completed for mobile programming: it scans the color of the object you are pointing at with your mobile phone's camera.

This app detects colors using the CameraX API and ImageAnalysis
SQLite for the color library and user logins 

**1. Capturing Frames from the Camera**
Your app initializes the camera using CameraX.
The ImageAnalysis use case is set up with STRATEGY_KEEP_ONLY_LATEST, ensuring only the most recent frame is analyzed.
**2. Extracting Pixel Data**
The analyze(image: ImageProxy) function gets each camera frame as an ImageProxy object.
The image is in YUV_420_888 format, which consists of three planes (Y, U, and V) representing brightness and color information.
Your app extracts pixel values from the central region of the frame (centerX, centerY).
**3. Converting YUV to RGB**
The raw pixel data is in YUV color space, so it must be converted to RGB for comparison.
The app retrieves Y (luminance), U (chrominance-blue), and V (chrominance-red) values.
It then applies a conversion formula to get the final RGB color.
**4. Finding the Closest Named Colo**r
Your app has a predefined color map with various shades and their RGB values.
It calculates the Euclidean distance between the detected RGB color and each stored color.
The closest match is chosen as the detected color.
**5. Displaying the Result**
The detected color name is displayed on the screen (binding.colorName.text).
When a photo is taken, the app overlays the detected color name on the image before saving it.
