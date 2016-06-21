Devan Bicher
dlb213
CSE 420
Fall 2015
Final Project Readme/description

I tested my project on Tumor set 1,
that would be the easiest set to test it on.
the rest of the images were noisier with the clustering results and produced
extra pieces when the active contours and edge selection process was done.

There are definitely improvements I could have made to this, but despite all of the user input, I think it works well.
I will describe improvements and suggestions in the final paper.

This matlab file takes in several images of the tumor by reading all images from a directory
Please do not include anything else in the directory, this will produce errors

Something to note, most of my user input is through the GUI presented, however there is a lot of user interaction
and I did not have time to put everything in the GUI so some of the user feedback is taking in at the matlab console
The important stuff is done at the GUI, the only stuff at the console is mostly selecting which images to manipulate

How to use the program:

After the program is run at the matlab console the GUI will shot up will a blank figure
The first step is to input the directory where the tumor images are stored, they must only be the images with the tumor
otherwise the program will not work
Nothing will happen until this directory is supplied

With the directory supplied the first image in the series will appear, the user can cycle through these images by hitting next
After the user has cycled through all of the images make a choice about which is the largest tumor piece and remember the # of that image

Whenever the console prompts the user for an image the user must choose the image number in the sequence, not the instance or file name

The point of this step is to make the clustering easier and to make the whole process faster and easier, with a smaller region to work in
the clustering will be faster and better.

With that in mind try to choose a region that is relatively close to the tumor edge, but not too close, you don't want to cut off part of the image
you can always redo your choice by clicking crop again.

the buttons are listed in the general order that the program should be executed in, with the buttons to display the edited image sets at the bottom

PLease follow this order to work the program, if you proceed out of order the program will display a message helping you.

(1) CROP one, then CROP ALL

Hit it the 'CROP' button, the console will display a prompt for the user to select which image to 
	crop to make choosing the cropped region easier.
	A cross hair will appear, choose the new boundary you want to use, by clicking 2 points as the corners of your box
	it doesn't matter what order or where select the region in, as long as they are opposite corners of the box

crop ALL: Next hit the 'CROP ALL' when you hit this an automatic process starts that shows each original image in then the new cropped image
		once the sequence is done a message appears

After this step you can cycle through the cropped images by hitting the cropped button under display along the bottom right
You can recrop if you made a mistake by cropping one image again and then hitting crop all

(2)CLUSTER one, cluster all(Segment)

next choose your K value, the number of clusters, since the image is small and usually noisy a number not so high is usually best, I typically
used a value of 4, but I found 3, and 5 also work well
There is decision to make here because you want to try to make sure you are choosing a k that clusters out the tumor image well

When you hit cluster the console will prompt you for the number of the image you want to cluster, try to choose one that best represents the image
boundaries well, but you can redo this later. after you choose and image and hit enter
the GUI will show you the number of clusters, and their gray scale representations together hit next and
it will show the first cluster display on a black background, remember which clusters, the number displayed on top as you cycle through
cycle through the different clusters also displayed on a black background, by hitting next
when you have gotten to the end of the clusters a prompt will appear asking which clusters to keep
please input the cluster indices in matrix format like this [1,2,3]
even if it is only one: [3]
If you don't like the decision or clustering you can always redo it by clicking cluster again
After you have chosen a good clustering, click cluster ALL

it will once again automatically cycle through all of the new segmented tumor images have you chosen
At this point you can once again display all of your clustered images by clicking clustered under display and then then hitting next to cycle through
The clustering works by choosing the centroids of each clustered image that are closest to the clustering you chose originally
This process is not perfect, but in my experimenting it did work quite well
Now if one of the clusters is not ideal, or there are holes in it, or if it is too large, you can recluster it by clicking cluster agian
once you have done so it will again  prompt you to choose the image you want to cluster
after choosing and hitting enter it will ask if you want to recluster one image(1) or recluster everything(0)
choose your option, you can even change k here if you would like for the new clustering of the image

the clustering doesn't have to be perfect, far from it, you can edit your selections before the final 3-D assembly later

(3) GET EDGES

After you are fairly confident in your segmented images hit get edges
This will bring up the first image and a cross hair, please selecting a bounding box as closely around the image as you can
this will perform an active contour on the clustered image and select the boundary of the tumor.
If the clustered images aren't too noisy this usually works well, 
after you have chosen your box it will display the edges by showing a white box on a black background
it will cycle to the next image for you to repeat the process as well, 
again don't worry if this is not perfect

once you have performed the edge detection on all of the images you can again cycle through the newly edged images by hitting edges and then 
hitting next to move through the images

(4) remove outside pieces
the edge selection is not perfect so there almost definitely will be extraneous pieces outside the boundary of the tumor,
if you do not remove these pieces the 3-D assembly will look quite strange, and be inaccurate for that matter

click on the remove button at the bottom, again the console will prompt you for the number of the image to be edited in the sequence
enter the number and hit enter
it will bring up the image and again a cross hair choose a box around the piece to be removed, but be careful not to cut off too much 
of part of the tumor, this process cannot be undone except by hitting the get edges button again
don't worry about selecting something outside the image either I took care of that, and it will default to the edge of the image boundary

it will show your newly edited image automatically, repeat this process on all of the images that have extra little pieces out side of the tumor


(5) ASSEMBLE!!!

That's it, you can cycle through the edges pieces to make sure everything looks good, 
but when you think you have the tumor slices you need
hit the assemble button

The figure will change to a 3-D plot with a 3-D mesh of the tumor.
You cannot manipulate the view at all right away, but the best way to visulaize this tumor is by 
clicking tools at the top, 
then clicking rotate 3-D
you can now rotate the image around to get a better idea of how it looks
However since the axes are of different sizes to get the best view of the image right click on the plot,
and then hover over rotate options, then click 'fixed aspect ratio axes' this is the best way to view the image that is produced!

if you did all of the other steps appropriately this image should look quite nice and should be a fairly accurate
representation of the tumor in 3-D space

At this point, any part of the process can be done again by hitting the appropriate button to try and get a better view of the tumor image again

The program should be pretty robust and if you hit something out of order or do the wrong thing it should display a warning, for the most part
GOOD LUCK
