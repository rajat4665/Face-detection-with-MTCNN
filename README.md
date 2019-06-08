# Face-detection-with-MTCNN
In this repository i will show you how to detect faces from an image using mtcnn

<img class="alignnone size-full wp-image-103" src="https://getpython.files.wordpress.com/2019/06/burnstowndam1559987409.png" alt="burnstowndam1559987409" width="800" height="600" />
<h3>How to run this code:</h3>
<ul>
	<li>download this code from my GitHub</li>
	<li>clone this repository</li>
	<li>open it into Jupyter notebook</li>
	<li>Now run its cells one by one</li>
</ul>
<h3>How to install jupyter notebook in ubuntu:</h3>
open your terminal and paste these commands one by one.
<pre class="code-pre command"><code>sudo apt install python3-pip python3-dev</code></pre>
<pre class="code-pre command"><code>pip install jupyter</code></pre>
<h3>How to install jupyter notebook in windows:</h3>
Follow this <a href="https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/install.html">Link for windows</a>
<h3></h3>
<h3>Introduction:</h3>
As you know Python programming language has great significance in the world of computer vision. Face detections is a live application of computer vision you may have used it in your daily life for example face unlock, autofocus and snapchat filters. In this article, I will explain how one can use face detection using pre rained MTCNN model.

There are many face detection algorithms such as Haar-feature based cascade classifiers, HOG, and MTCN for more information you can go for this <a href="https://towardsdatascience.com/whats-the-difference-between-haar-feature-classifiers-and-convolutional-neural-networks-ce6828343aeb">article</a>
<h3>Install these requirements:</h3>
<pre><span id="pip-command">pip install mtcnn</span></pre>
<pre><span id="pip-command">pip install matplotlib</span></pre>
<h3>Source Code:</h3>
<pre># face detection with mtcnn on a photograph
from matplotlib import pyplot
from matplotlib.patches import Rectangle
from mtcnn.mtcnn import MTCNN
%matplotlib inline
# load image from your local directory
pixels = pyplot.imread('123.jpg')
# create the detector, using default weights
detector = MTCNN()
# detect faces in the image
faces = detector.detect_faces(pixels)
print("Number of face :",len(faces))
print()
print("Cordinates details :",faces)
print()
print("Confidence score:",float(faces[0]['confidence'])*100,"percent")
# plot the image
pyplot.imshow(pixels)
# get the context for drawing boxes
ax = pyplot.gca()
# get coordinates from the first face
x, y, width, height = faces[0]['box']
a,b = faces[0]['keypoints']['nose']
c,d = faces[0]['keypoints']['left_eye']
e,f = faces[0]['keypoints']['right_eye']
# create the shape
rect2 = Rectangle((a, b), 15, 15, fill=True, color='red')
rect3 = Rectangle((c, d), 10, 10, fill=True, color='blue')
rect4 = Rectangle((e, f), 10, 10, fill=True, color='blue')
rect = Rectangle((x, y), width, height, fill=False, color='red')
# draw the box
ax.add_patch(rect)
ax.add_patch(rect2)
ax.add_patch(rect3)
ax.add_patch(rect4)
# show the plot
pyplot.show()

</pre>
 
