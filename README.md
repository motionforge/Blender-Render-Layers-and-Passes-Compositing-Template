# Blender Render Layers and Passes – Compositing Template
 A blender file with data passes and layers set up for compositing export


# Introduction
Blender comes with compositing tools that provide a wide array of options to edit your renders. However, if just getting started with these tools or if new to blender it can be a little fiddly to set up.

So to assist new users to the compositor or experienced users that are learning or moving to Blender. I’ve created a Blender file template that can be downloaded for free from Github.

Simply clide on the code button to download and then unzip the file. Where you will find a blender file that you can save, and use for your renders.

The template/file is set up for use with Cycles, but can be easily adjusted for Eevee.

Please note the overview below provides a detailed summary for how to use the template, but it does require some knowledge of Blender, photo editing programs and Davinci Resolve.

# Back To Beauty
The term ‘back to beauty’ relates to rendering the different elements (e.g. colour, direct and indirect lighting etc..) of a rendered image (also known as Data Passes) and then afterwards combining these different rendered passes/elements back to the original image.

The benefit this creates is that firstly the denoising is usually much improved when done per data pass and also it gives granular control over the different elements of the image.

So for example you have control over the Diffuse colour and Direct and Indirect lighting. This can be extremely valuable when colour grading, making changes or correcting the image. It makes it easy to change or tint a colour or make the areas of the image darker or lighter (without having to go back and do the render again). So changing the colour on a robot, or a car will be much easier doing this with the diffuse passes. As opposed to the combined image – where it may not be possible or limited.

If using EXR you also get a higher range of data so your image comes with more detail (specifically in light and dark areas, colour range, and the gradient between light and dark). Where as in a format such as JPG, much detail is lost.

Blender.org has a detailed breakdown of these different render passes in the documentation here. It should also be noted that 3D programs do sometimes differ in the exact set up for render passes and this only details Blenders.

Combining Data Passes:

After these data passes have been rendered they have to be recombined to get back to the original image. There is a process for combining layers (however feel free to experiment!).

The Light passes of the Diffuse, glossy, Transmission are added together. These are then multiplied by the colour pass. The volume has no color pass so is just added. As are the other layers. Then they are all added together to create the combined image (or beauty pass).

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Rendered_Images/Data%20Passes%20Flow%20Chart.jpg)

# Passes Set Up
Detailed below is how to set up data passes and view layers. In the Blender file (that can be download from Github – link above) the template/file already has all these settings set up – so you can view what’s been done and edit where you require.

In Blender:

Go to the Data Tab – To Activate Data Layers.
Check all the boxes for the data passes you wish to export.
You can just export a mist or emissive pass.
It really depends on your requirements for what passes you require.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Rendered_Images/data%20passes%20tab.jpg)

# Denoising Passes Set Up

Denoising:

Combined Single Layer Denoising:

Turn off Denoise in the Scene tab – you do not need this on if using the compositor.
As shown in image below – This is for single layer Denoising.
Please note you can keep this on – but it only denoises your combined image.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Rendered_Images/data%20passes%20tab.jpg)


