# Blender Render Layers and Passes – Compositing Template

- A blender file with data passes and layers set up for compositing export. 
- For further details and for easier reading (than below) with structured numbered steps - please see the post here:
- https://www.motionforgepictures.com/blender-render-layers-and-passes-compositing-template/


# Introduction
Blender comes with compositing tools that provide a wide array of options to edit your renders. However, if just getting started with these tools or if new to blender it can be a little fiddly to set up. So to assist new users to the compositor or experienced users that are learning or moving to Blender. I’ve created a Blender file template that can be downloaded for free from Github.

The template/file is set up for use with Cycles, but can be easily adjusted for Eevee.

Please note the overview below provides a detailed summary for how to use the template, but it does require some knowledge of Blender, photo editing programs and Davinci Resolve.

# How To Use the Blender File Template

- Simply click on the code button to download and then unzip the file. Where you will find a blender file that you can save, and use for your renders.

This template is set up only for exporting out your renders into a folder so they can be used with a different program such as Davinci Resolve, Affinity Photo, Photoshop, Nuke, After Effects etc...

This is not set up for editing the layers internally in Blender.

Whilst I have called this a template you can simply save the file and copy, and use where ever you wish. Or in Blender > go to > File > Defaults > Save Startup File (Be careful as this will override any startup default settings you have) to save with this compositor set up.

These settings may need changing depending on your specific requirements or program you are exporting to.

- Go to Github (link above) > Press the Green Code button and download the zip file.
- Unzip the file and save the Blender file where is appropriate for you.
- Open the Blender file.
- Go to the View layers tab.
- Check or uncheck required passes. e.g. Diffuse Direct, Indirect etc...
- Go to the Compositing Tab.
- In the Output node(s).
- Make sure that the output folder is correctly selected for where you want to save the renders.
- Make sure you have selected the appropriate color profile .e.g. ACEScg, sRGB etc...
- Change compression settings where required and make sure it's a multilayered EXR.
- Click the Render button or F12 to render a single image.
- Open the EXR in Photoshop, Affinity Paint, Davinci Resolve (or your preferred program).
- Arrange layers - edit as required.

You can then use this set up (or however you have updated the settings) in your own CG work with Blender. Either just duplicate the file and then create your model, scene or animation, or save the Start up file to have this with every new Blender file you create.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/PNG_Featured_Image_Featured.jpg)

# Blender File Template Notes

Compositor Notes:

- Remember to select a path in the compositor for the output(s).
- You don't need Denoising for the color passes and some other passes.
- It's only the light passes (e.g. Diffuse Direct) that create noise.
- Data passes don't automatically add the alpha layer so it's been added in the different passes.
- You don't need denoise option ticketed in render properties tab if using the denoise node in the compositor. See further details below. This denoise option only denoises the combined pass.
- The layers are only denoised in the output folder (not the viewer panel).
- If you uncheck a data pass it will appear as an empty layer in the exported image unless the socket is deleted from the export node.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/Compositor%20v2.jpg)


# Back To Beauty
The term ‘back to beauty’ relates to rendering the different elements (e.g. colour, direct and indirect lighting etc..) of a rendered image (also known as Data Passes) and then afterwards combining these different rendered passes/elements back to the original image.

The benefit this creates is that firstly the denoising is usually much improved when done per data pass and also it gives granular control over the different elements of the image.

So for example you have control over the Diffuse colour and Direct and Indirect lighting. This can be extremely valuable when colour grading, making changes or correcting the image. It makes it easy to change or tint a colour or make the areas of the image darker or lighter (without having to go back and do the render again). So changing the colour on a robot, or a car will be much easier doing this with the diffuse passes. As opposed to the combined image – where it may not be possible or limited.

If using EXR you also get a higher range of data so your image comes with more detail (specifically in light and dark areas, colour range, and the gradient between light and dark). Where as in a format such as JPG, much detail is lost.

Blender.org has a detailed breakdown of these different render passes in the documentation here. It should also be noted that 3D programs do sometimes differ in the exact set up for render passes and this only details Blenders.

Combining Data Passes:

After these data passes have been rendered they have to be recombined to get back to the original image. There is a process for combining layers (however feel free to experiment!).

The Light passes of the Diffuse, glossy, Transmission are added together. These are then multiplied by the colour pass. The volume has no color pass so is just added. As are the other layers. Then they are all added together to create the combined image (or beauty pass).

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/Data%20Passes%20Flow%20Chart.jpg)

# Passes Set Up
Detailed below is how to set up data passes and view layers. In the Blender file (that can be download from Github – link above) the template/file already has all these settings set up – so you can view what’s been done and edit where you require.

In Blender:

Go to the Data Tab – To Activate Data Layers.
Check all the boxes for the data passes you wish to export.
You can just export a mist or emissive pass.
It really depends on your requirements for what passes you require.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/data%20passes%20tab.jpg)

# Denoising Passes Set Up

Denoising:

Single Layer Denoising:

Turn off Denoise in the Render Tab – you do not need this on if using the compositor.
As shown in image below – This is for single layer Denoising.
Please note you can keep this on – but it only denoises your combined image.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/data%20passes%20tab.jpg)

Multilayer Data Passes Denoising:

Make sure to Turn on Denoising Data in the Data passes tab.
You can denoise the data layers directly in the compositor.
It will denoise the combined image – but for this template a combined image is not used.
You may wish to have a combined image - so can check this option.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/Denoising%20data.jpg)

Compositor Set Up - For Passes:

Go to the Compositor tab.
Tick the Use Nodes Box.
Add a Render layers node (if not there already).
Add an Output node.
Add the required data passes to the output node.
Drag off from each connector and connect to the output node.
Add the required nodes.
You do not need to add or multiple nodes together - This is done in a different program.
Passes that have no direct / indirect lighting can just be added.
Data layers do not automatically have alpha added - so add an Set Alpha node if required.
Only light bounces create noise - so colour passes (and a few others) don't need denoising.
Select the folder for output (in the output node).
In the output node - select Multilayered EXR.
Compression can be DWAA or DWAB - or what ever you prefer!
If its a still image (not an animation sequence) consider using Zip or a lossless format.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/Compositor%20v2.jpg)


# View Layers Set Up

This template comes with three view layers. Combined, background and foreground. The image below is from the provided template and has a render output for the two view layers. In this case – Foreground and Background. The template is not set up to output the combined layer and this is just so the scene in its entirety can be viewed.

In the top right hand corner there is the ‘Viewlayer’ field.
To crate a new view layer. Select the add view layer.
Either copy settings or create a new default view layer.
Now simply, change settings, e.g. hold out, indirect or the required data passes.
The settings will auto save depending on what view layer you have selected.
It is that simple – although don’t forget that the layers now have independent settings.
So if you change a setting in one layer – make sure to change in another layer if requred.
In the compositor you can select to render out view layers separately – via render node.
Then combine them in your compositing software.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/Viewlayers.jpg)

The image below is from the provided template and has a render output for the two view layers. In this case – Foreground and Background.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/view%20layers%20with%20data%20passes.jpg)

# Set Up Affinity Paint

This template is only for exporting out your renders into a folder so they can be used with a different program such as Nuke, After Effects or DaVinci Resolve.

It may be that you won't need all the data passes activated, so select only what you require in Blender. The outline below provides a summary of bringing a single rendered image/frame into a paint program such as Affinity Paint.

Download the Template
Open Blender.
Go to the Compositing Tab.
Make sure that the output folder is correctly selected.
Make sure you have select the appropriate color profile .e.g. ACEScg, sRGB etc...
Click the Render button or F12 to render a single image.
Open the EXR in Photoshop or Affinity Paint (or what image editor you use).
If using Photoshop be sure to use the free - EXR-IO plugin.
If using Affinity see details here for - Affinity EXR set up.
Arrange layers in the program as required - edit as required.

# Set Up in Davinci Resolve

There is an EXR script for splitting out data passes so you don’t need to do this manually. Also you can export and save comp set ups. So you only need to create the comp once and then after that just go to File > Import Comp > And import your fusion composition.

Bring the image file or image sequence into Davinci Resolve.
Bring the image / sequence into the timeline or directly set up a Fusion Clip.
With the file in the time or the fusion clip open.
Arrange layers as required in Fusion by adding, multiplying or merging.
These layers are arranged as noted in the diagram at the top of the page.
See Example Fusion set up below.

![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/Davinci%20Resolve%20Fusion%20Data%20Passes%20Set%20Up%20Example.jpg)

Note: In Davinci Resolve Timeline - it does not preview the Alpha Layer. So you won't be able to see if the Alpha is there or not. But it is recognised in Fusion. So any work done with Alpha layer should be gone in Fusion.

Once the footage is set up in Fusion you should be able to place clips on top of each other and the Alpha mask should just work. - Please post a comment if you can't get this to work. 

YT Video: Import/Export Comps: https://youtu.be/XQ3slO30f8Q?si=z1GBfykIx54B4R12

Whilst the below goes into a Unreal Engine work flow. It does (at around 8 Minutes 15 seconds) show how to install and use the Fusion Reactor script – Split EXR. So you don’t have to manually split out the file every time! (Unfortunately I think this is no longer available for free users – so you will have to upgrade your Davinci Resolve to use this).

YT Cideo: Data Passes Scrip: https://www.youtube.com/watch?v=rVMyktVYiI0&t


# Blender to DaVinci Resolve – ACEScg Color Management

PLEASE NOTE: I and others have experienced performance and playback issues when using Multi layered EXRs. This is something you may wish to consider before using DaVinci Resolve for compositing. DaVinci Resolve is a fantastic program, but one area that does need improvement is its ability to handle Multi Layered EXRs. You will need to make sure you have caching on in the timeline to work with them.

These are different options for setting up your ACEScg color profile. Below covers one way to do this.

- Create a new Resolve Project.
- Go to bottom right hand corner > click on the cog icon.
- This opens project settings.
- Go to Color Management.
- Set to Acescct.
- Aces 1.2 (or a later version - you can test either or use the version best for your workflow)
- Select REC 709 or sRGB as the output.
- Everything else can stay the same.
- In the media browser or timeline - Import the image sequence(s).
- Right click on image sequence > go to > Aces Input Transform > Color space conversion
- Then select Acescg CSC.
- This is all you need to do to get up and running.
- In Fusion it applies a view lut - so it will be different from the timeline and color correction section.
- You can chose Gamut or HDR - to much closer to your timeline / color correction sections.
![](https://github.com/motionforge/Blender-Render-Layers-and-Passes-Compositing-Template/blob/main/Images/Davinci%20Colour%20Managament.jpg)

# Notes

There is a node in Fusion where you can select color profiles, but this is not required if setting system (at a top project level) to ACEScg (as noted above).
Also if using this node you will need to do this for every clip you use – so potentially hundreds of times. So I recommend using the project system settings as it sets it globally.
If you bring in a non ACEScg image or video you can still select the appropriate color profile. E.g. sRGB and it will work.


# Final Note

If you an indie filmmaker or animator then this may well be over kill. Remember that this is (very likely) not required for your work and will add additional time and effort to your renders. You can just render out in a combined layer EXR and use ACEScg. This will give you a high quality image, with a wider colour/highlight/shadow range, but will save any hassle with multilayered passes.

Or just do a more simplified version. You could just render out a Mist pass or AO pass and composite with your combined image.

Of course if you are learning or working in VFX, then processes such as this are pretty much a necessity to know (assuming AI hasn’t taken over the process when your reading this!). Or if you have a team, or people to specialise in VFX then it’s worth doing.

But it’s your story that really counts, so remember to focus on that!


