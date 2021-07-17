<h2><b>Project:</b></h2>
This project mainly consists a combination of two models and very popular deep fashion-2 dataset.
<h3><b>1. DeepFashion2 Dataset</b></h2>
<h3><b>2.Cloth Category Recognition Model</b></h2>
<h3><b>3. Style Translation using Cycle GAN</b></h2>
<br>
<br>
<h2><b>DeepFashion2 Dataset</b></h2>

<p>It contains 491K diverse images of 13 popular clothing categories from both commercial shopping stores and consumers. It totally has 801K clothing clothing items,
where each item in an image is labeled with scale, occlusion, zoom-in, viewpoint, category, style, bounding box, dense landmarks and per-pixel mask.There are also 873K Commercial-Consumer clothes pairs.</P>
<p>The dataset is split into a training set (391K images), a validation set (34k images), and a test set (67k images).</p>

<h3><b>Data Organization</b></h3>
<p>Each image in seperate image set has a unique six-digit number such as 000001.jpg. A corresponding annotation file in json format is provided in annotation set such as 000001.json.
Each annotation file is organized as below:</p>
<ul>
<li><b>source:</b> a string, where 'shop' indicates that the image is from commercial store while 'user' indicates that the image is taken by users.</li>
<li><b>pair_id:</b> a number. Images from the same shop and their corresponding consumer-taken images have the same pair id.
</li>
<li><b>category_name: </b>a string which indicates the category of the item.</li>
<li><b>category_id:</b> a number which corresponds to the category name. In category_id, 1 represents short sleeve top, 2 represents long sleeve top, 3 represents short sleeve outwear, 4 represents long sleeve outwear, 5 represents vest, 6 represents sling, 7 represents shorts, 8 represents trousers, 9 represents skirt, 10 represents short sleeve dress, 11 represents long sleeve dress, 12 represents vest dress and 13 represents sling dress.
</li>
<li><b>style:</b>a number to distinguish between clothing items from images with the same pair id. Clothing items with different style numbers from images with the same pair id have different styles such as color, printing, and logo. In this way, a clothing item from shop images and a clothing item from user image are positive commercial-consumer pair if they have the same style number greater than 0 and they are from images with 
the same pair id.(If you are confused with style, please refer to issue#10.)</li>
<li><b>bounding_box:</b>[x1,y1,x2,y2]，where x1 and y_1 represent the upper left point coordinate of bounding box, x_2 and y_2 represent the lower right point coordinate of bounding box. (width=x2-x1;height=y2-y1)
</li>
<li><b>landmarks: </b>[x1,y1,v1,...,xn,yn,vn], where v represents the visibility: v=2 visible; v=1 occlusion; v=0 not labeled. We have different definitions of landmarks for different categories. The orders of landmark annotations are listed in figure 2.</li>
<li><b>segmentation:</b>[[x1,y1,...xn,yn],[ ]], where [x1,y1,xn,yn] represents a polygon and a single clothing item may contain more than one polygon.</li>
<li><b>scale:</b> a number, where 1 represents small scale, 2 represents modest scale and 3 represents large scale.</li>
<li><b>occlusion:</b> a number, where 1 represents slight occlusion(including no occlusion), 2 represents medium occlusion and 3 represents heavy occlusion.
</li>
<li><b>zoom_in:</b>a number, where 1 represents no zoom-in, 2 represents medium zoom-in and 3 represents lagre zoom-in.</li>
<li><b>viewpoint:</b>a number, where 1 represents no wear, 2 represents frontal viewpoint and 3 represents side or back viewpoint.</li>
</ul>
<h2><b>Results of Cloth Category Recognition Model</b></h2>
<br>
<p>Mask R-CNN is an instance segmentation technique which locates each pixel of every object in the image instead of the bounding boxes. Mainly it has two stages: region proposals and then classifying the proposals and generating bounding boxes and masks.It also uses the Region Proposal Network (RPN) which scans all FPN top to bottom and proposes regions which may contain objects. It uses anchors which are a set of boxes with predefined locations and scales itself according to the input images. Individual anchors are assigned to the ground-truth classes and bounding boxes. RPN generates two outputs for each anchor - anchor class and bounding box specifications. The anchor class is either foreground class or Background Class. Another module that is different in Mask R-CNN is the ROI Pooling. </p> <br><br>
<img src="https://user-images.githubusercontent.com/39325832/126036361-3ff8fcdc-4f3f-4734-a724-cd27f1e2b7fa.PNG"/>
<h2><b>Results of Cycle Gan</b></h2>
<br>
<p>
Cycle-GAN is an approach to training image-to-image translation models using
the generative adversarial network, or GAN, model architecture. It performs the s the task of transforming an image from one domain
to another.It uses The GAN architecture approach to train a model for image synthesis that
is comprised of two models: a generator model and a discriminator model. The
generator takes a point from a latent space as input and generates new plausible
images from the domain, and the discriminator takes an image as input and predicts
whether it is real (from a dataset) or fake (generated). Both models are trained in a
game, such that the generator is updated to better fool the discriminator and the
discriminator is updated to better detect generated images</p><br><br>
<img src="https://user-images.githubusercontent.com/39325832/126036436-4e3fab6a-3c48-4046-9f6d-4dc6606ec325.PNG"/>





