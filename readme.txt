////////////////
// HOW TO RUN //
////////////////

1. EXTRACT the project folder 'CPSC453Boilerplate' 
2. COMPILE program using the command line 'make'
3. RUN the program using the command line './boilerplate.out

*. There is a response to the discussion question at the end
////////////////
// HOW TO USE //
////////////////

keys [1]-[5] changes the scene 
scene 1: Colour Effects (includes negative filter and border of another
		 texture) (competative bonus)
scene 2: Edge Effects
scene 3: Gaussian Blur
scene 4: Seperating the Gaussian Kernel (bonus)
scene 5: Greyscale comparison (Not part of assignment, used to compare
		 Luminance value of the 3 conversions) 

key [escape]	closes the program
key [upArrow]	toggles through the variations of the scene's filter
key [downArrow] toggles through the variations of the scene's filter
key [leftArrow] toggles through the pictures used for texture
key [rightArrow]toggles through the pictures used for texture

mouse [leftClick]+[drag]		pans the texture(similar to google maps)
mouse [scrollUp]				zooms into the scene(respect to origin)
mouse [scrollDown]				zooms outof the scene(respect to origin)
mouse [rightClick]+[scrollUp]	rotates the scene ccw(respect to origin)
mouse [rightClick]+[scrollDown]	rotates the scene cw(respect to origin)

DESCRIPTION OF FILTERS
SCENE 1	
0:	Default image
1:	L = 0.333 R + 0.333 G + 0.333 B
2:	L = 0.299 R + 0.587 G + 0.114 B
3:	L = 0.213 R + 0.715 G + 0.072 B
4:	negative L = (1-R) + (1-G) + (1-B)
5:	negative with border 
SCENE 2
0:	Default image
1:	Vertical Sobel
2:	Horizontal Sobel
3:	Unsharp Mask
SCENE 3
0:	Default image
1:	3x3 gaussian
2:	5x5 gaussian
3:	7x7 gaussian
SCENE 4	 (BONUS)
0:	7x7 gaussian
1:
...:kxk gaussian | k = 7+10n
25(i think): 257x257 gaussian
SCENE 5	(FOR COMPARING GREYSCALES IN SCENE 2) 
0:	colour gradiances from rgb
1:	L = 0.333 R + 0.333 G + 0.333 B
	greyscale of gradiance using average
2:	L = 0.299 R + 0.587 G + 0.114 B
	greyscale of gradiance 
3:	L = 0.213 R + 0.715 G + 0.072 B
	greyscale of gradiance
FROM GRAPHICS 453 W2018 WEEK4 OF SONNY CHAN'S SLIDES 
http://pages.cpsc.ucalgary.ca/~sonny.chan/cpsc453/resources/slides/CPSC453-L10-ImageEffects.pdf
BASED ON SLIDE 27:
-	applying filter 1 averages the intensity of all the pixels, and we get
	a solid grey color throught the entire gradiance
-	The better greyscale filter is the one that best matches the human eye's
	perception of different shades of grey. (green being closer to white due
	to its higher intensity, and blue bing closer to black due to its lower
	intensity)
-	applying filters 2 and 3 both show the greyscales between rgb. If we
	compare the corners of the image to the their respective colors (no
	greyscale) to the scale provided on slide 27, we find that filter 3
	is slightly darker on the red corners than what the human eye perceives
	the filter on reds.
-	Since filter 2 is a closer match:
		L = 0.299 R + 0.587 G + 0.114 B
		will give us a more accurate greyscale


RESPONSE FOR ADDITIONAL BONUS FOR A2
-This phenomenon is a result of aliasing:
-	sampling high frequencies at a low frequency
-	suppose we have an image where the each pixel is either black or white
	similar to that of a checker board. Thus the original image appears
	gray. Now suppose we sample every second pixel. The resulting image
	would be entirely white, or entirely black.
-	After applying various size gaussian filters to image5, I find that
	as you increase the size of your gaussian kernel, the pattern slowly
	starts to shrink. however the black and white streaks start to blend
	as a result of the increased blur. (regarless if i zoome/rotate/pan)
-	The pattern seems to have disappeared at a large kernel size such that
	the black and white patterns are now grey. Therefore it is a compromise
	whether you prefer an image with less aliassing and more blur, vs more
	aliassing and less blur.
-	but in my opinion, a 17x17 gaussian kernal seems to be an ideal balance 
	of the two
