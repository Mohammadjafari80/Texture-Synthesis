# Texture-Synthesis

Texture Synthesis is the process of algorithmically constructing a large digital image from a small digital sample image by taking advantage of its structural content. It is an object of research in computer graphics and is used in many fields, amongst others digital image editing, 3D computer graphics and post-production of films.

Texture synthesis can be used to fill in holes in images (as in inpainting), create large non-repetitive background images and expand small pictures.

Here we implement an algorithm to create 2500x2500 textures based on small textures.

First, we set a size for our patch. All the images below are constructed using a patch size 150x150.

We select a random patch and put it on the top-left corner of the large texture for starting the process. After that, we consider a 30-pixel overlap for each neighbor pair of patches. Therefore we look for the best matches of the overlap region of the current patch and select randomly from the best ten places. After that, we find the minimum cut path of the overlap region, and we create a mask based on that so that it looks seamless.
<br/>

<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/v-mask-1.jpg' height='500px'>
    <img src='./images/v-mask-2.jpg', height='500px'>
</p>
<br/>
We repeat that process until we reach the next row. Here our overlap region is horizontal, but we apply the same procedure.
<br/>

<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/h-mask-1.jpg' width='40%'>
    <img src='./images/h-mask-2.jpg', width='40%'>
</p>
<br/>

Now for our new patches, we have two overlaps. So we have to look for L shape matchings. So our final masks will look like this.
<br/>

<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/L-mask-1.png' width='40%'>
    <img src='./images/L-mask-2.png', width='40%'>
</p>
<br/>

If we visualize this process, it would be almost identical to the image below.

<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/EXPLAIN.png' width='80%'>
</p>
<br/>

We apply the same procedure for each row and column until we reach the end of the image.

Here are some results of this implementation.

<div  style="display: flex; align-items: flex-start; flex-direction: column; justify-content:space-evenly; width=100%;">
<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/texture-big-1.jpg' width='70%'>
    <img src='./images/texture-small-1.jpg' width='15%'>
</p>
<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/texture-big-2.jpg' width='70%'>
    <img src='./images/texture-small-2.jpg' width='15%'>
</p>
<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/texture-big-3.jpg' width='70%'>
    <img src='./images/texture-small-3.jpg' width='15%'>
</p>
<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/texture-big-4.jpg' width='70%'>
    <img src='./images/texture-small-4.jpg' width='15%'>
</p>
<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/texture-big-5.jpg' width='70%'>
    <img src='./images/texture-small-5.jpg' width='15%'>
</p>
<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/texture-big-6.jpg' width='70%'>
    <img src='./images/texture-small-6.jpg' width='15%'>
</p>
<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/texture-big-7.jpg' width='70%'>
    <img src='./images/texture-small-7.jpg' width='15%'>
</p>
<p align='center' style="display: flex; align-items: center; justify-content: space-evenly; margin:15px; width:100%;">
    <img src='./images/texture-big-8.jpg' width='70%'>
    <img src='./images/texture-small-8.jpg' width='15%'>
</p>
</div>
