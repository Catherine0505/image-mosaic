Name: Catherine Gai

SID: 3034712396

Email: catherine_gai@berkeley.edu

Link to project report website: https://inst.eecs.berkeley.edu/~cs194-26/fa21/upload/files/proj4A/cs194-26-aay/catherine_gai_proj4a/Project%2004.html



This folder contains four functional python files: "define_features.py", "compute_projection.py", "warp_image.py", "mosaic.py". 



The folder also contains extra image files: "left.jpeg" (left view of University Library reading room), "right.jpeg" (middle view of University Library reading room), "mosaic2_right.jpeg" (right view of University Library reading room). "mosaic3_left.jpeg" (left view of the nighttime Bay Area), "mosaic3_right.jpeg" (right view of the nighttime Bay Area). The last two images are only used during mosaicing. 



Furthermore, the folder contains a few .csv files that records pre-selected feature points: "im_pts.csv", "standard_pts.csv", "rectify3_pts.csv", "standard3_pts.csv" (for rectifying left view image); "rectify2_pts.csv", "standard2_pts.csv", "rectify4_pts.csv", "standard4_pts.csv" (for rectifying right view image); "left_im_pts.csv", "right_im_pts.csv" (for creating mosaic between left view and middle view); "left_im_pts_2.csv", "right_im_pts_2.csv" (for creating mosaic between middle view and right view); "left_im_pts_3.csv", "right_im_pts_3.csv" (for creating mosaic between the left view of Bay Area and right view of Bay Area). 



**define_features:**

This python file contains a function that allows users to choose a certain number of feature points on an image.

* get_points(*params*): Given the number of features a person wants to choose and the input image, the function records all chosen feature points and return an $n \times 2$ numpy array, where the first column indicates row coordinates of the feature points, and the second column indicates column coordinates. 



**compute_projection.py:**

This python file contains a function that computes the projective transformation matrix from one image to another. 

* computeH(*params*): Given the corresponding feature locations in image 1 and image 2, the function outputs a $3 \times 3$ Projective transformation matrix that warps image 1 to the same projection plane as image 2. 



**warp_image.py:**

This python file contains a function as well as other commands that warps a image to a certain projection plane given the transformation matrix. It also does image rectification for the left and right view of University Library reading room. 

* warpImage(*parmas*): Given an image, the reversed projective transformation and size of the resulting image (height * width), the function outputs a new image of indicated size, with contents of the input image warped to another projection plane. 

To generated rectified image, run `python warp_image.py`. The command will generate four images: an upward-to-eyelevel warped image for left view of University Library reading room, and a subsequent front view of the image; an upward-to-eyelevel warped image for right view of University Library reading room, and a subsequent front view of the image. While the output will be two final rectified images, all four images will be saved. For each image rectification, you will be prompted with a question that asks if you would like to use existing features. Typing "`Y`" would enable the program to use  "im_pts.csv", "standard_pts.csv", "rectify3_pts.csv", "standard3_pts.csv" to rectify the left view image, and "rectify2_pts.csv", "standard2_pts.csv", "rectify4_pts.csv", "standard4_pts.csv" to rectify the right view image. Otherwise, for a complete rectification, you would manually pick 8 feature points on the original image and 8 points on the warped eyelevel image. 

If you choose not to use existing feature points, you would also be asked whether to save your manually selected feature points after visualizing the rectified images. Typing "`Y`" would enable the program to overwrite current feature points. 



**mosaic.py:**

This python file contains commands that generates three panorama. Run `python mosaic.py` and the program will output six images: an unfeathered and feathered image for every panorama. 

For each panorama, you will be prompted with a question that asks if you would like to use existing features. Typing "`Y`" would enable the program to use  "left_im_pts.csv", "right_im_pts.csv" to create mosaic between left view and middle view), "left_im_pts_2.csv", "right_im_pts_2.csv" to create mosaic between middle view and right view), "left_im_pts_3.csv", "right_im_pts_3.csv" to create mosaic between the left view of Bay Area and right view of Bay Area. Otherwise, you would manually pick 8 feature points on each image that composes the panorama. 

If you choose not to use existing feature points, you would also be asked whether to save your manually selected feature points after visualizing the panorama. Typing "`Y`" would enable the program to overwrite current feature points. 

