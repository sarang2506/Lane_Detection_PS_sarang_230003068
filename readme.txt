Implementing Background Isolation for easier Image Processing:

The background_isolation function creates a blank image of same dimensions as the input image (in this case our input image has already been slightly preprocessed by applying Gaussian blur and isolating canny edges, however to show the background isolation another image has been fed to show clearly the isolated area). The major logic here is to create a polygon which is encompassing the region in which we are interested in doing lane detection and fill it with white. This is what we call a mask...now we perform a bitwise and operation between the input image and the mask so as to get our desired area of interest.


Lane Detection:

The image which is now processed with a lesser number of edges is put into the draw_lines function which superimposes the lane lines(detected by the HoughLinesP function) onto a copy of the original image...Some of the lines are discontinuous and cannot be seen in the program.

To fix this we can try to interpolate a straight line for the left and right lane based on slope, starting and ending points of the line and for the lanes that cannot be seen/marked green we would have to change the threshold values for pixel intensity...However I was not able to implement this in the code as of now...overall though we can still see that the lanes have been roughly detected. 

Bitmap creation:

using thresh_binary_inv we can convert to black and white...then the contours(our lane lines) are identified and finally the area between the lines is files is filled and we can output the bitmap