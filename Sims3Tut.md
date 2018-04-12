## Sims 3 Guide to creating custom content from scratch

### *Programs needed:*

[TSR Workshop] (https://www.thesimsresource.com/workshop/)

[Mesh Toolkit] (http://modthesims.info/d/481950)

[Milkshape 3D (requires full paid version)](http://www.milkshape3d.com/)

3D modeling software of your choice (Blender, Maya, 3D Studio Max, Metasequoia)

Image editing software of your choice (Photoshop, GIMP, SAI, etc. for texture creation)

##Getting Started
Download the above files and install them.
Launch TSR workshop and set the file path for Sims 3 so it can locate the game’s files
Click create new project and choose an object to use as a template for your custom content. If you are creating an eyepatch then using glasses is the closest approximation and what you should use as a template.
NOTE: some objects in your window may appear as empty boxes. This is due to you not having an expansion or stuff pack that the piece of clothing come comes from. If you don’t have the packs you can’t use the items.
 
I plan on making a tee-shirt so I’m going to use afTopShirtTee_crew as my template mesh
Give your project a name and title and save it
Currently we don’t care about any of the settings and we’ll come back to them at the end
Go to the last tab and select High Level of detail then the red box 

Save the file in an accessible place

From here you need to load the model into milkshape using the TSR .wso plugin
The plugin you need to install is included with TSR workshop, so navigate to your TSR install. In the TSR folder you will find a plugins folder which should contain msTSRWorkshopExport.dll and msTSRWorkshopImport.dll. move these .dll files to your MilkShape 3D folder.

Once the model is in milkshape you want to delete all the groups except group_base from the group menu. The group base is essentially the neutral form that will be morphed later on while the other groups we are deleting are the extremes of the morphs. Never model on something other than group_base or the morphs will not work correctly. After deleting all but group_base you can export it as an .obj so you can import it into a program of your choice for creating the mesh. I’ll be using metasequoia as that’s what I’m familiar with.

If you want to export any of the textures from the original model you can go to the texture tab and click the edit button on the texture you want, when it brings up a separate window just click the export button and save it wherever you want. Exporting these textures is not required if you plan on creating your own. But they serve as useful reference. 

## Creating the Mesh
This part required knowledge of 3D modeling and your chosen software so I’ll only be giving a brief overview of how you should model things as it applies to sims. 
Once you’ve imported your model you’ll notice it’s all tris and that there are open edges. All open edges should be merged because it will spout errors on reimport if they aren’t + it may cause weird shading in game.
 
Things should be integrated into the preexisting mesh. If you want to make something completely unique and/or don’t want to worry about working it into the original clothing mesh that’s there you can always go through part 1 again and export the nude base and model on that. You will still need the template item later but it may be easier to model on a nude base for certain objects.
 
Here’s my modified mesh which has reshaped a few parts and added an actual collar to the shirt 
As a rough guideline for modeling for sims 3, try to keep things around the same polycount as the original mesh, having things too high poly will make load times slower.
 Next you need to create the UV map 
The UV map of the clothing needs to occupy the space on the map of the body part it covers. The images below show that my shirt UVs cover the upper body, shoulders, and the arms. Make sure that you don’t modify the UVs of thing you aren’t editing, like the arm and neck. The UVs you create for your object should conform to this sort of pattern
  
After creating the map, you need to texture it of course. For Sims all textures need to be create in a grayscale like the body texture you see above. The grayscale texture allows the item to be recolored in game without looking muddy. The game requires several textures but we are just going to create the main one here as there will be a more in-depth explanation later when we make the rest to put it back onto the game.
My final texture looks like this. I borrowed most of my texture from the original since there wasn’t much that needs to be changed about a generic tee-shirt. The final mesh is on the right so you have an idea of how the texture looks applied.
  

## Reimporting
From here export the mesh as an .obj
Go back and reopen milkshape, import the .obj you created
Rename your mesh group_base and delete any materials
Export the mesh as a .wso
Now open the Mesh Toolkit and go to the tab labeled Auto tools for WSO. For this you need both your template item from the game and the one you just exported as .wso.
We want to do both things this tab offers, auto-assign bones and auto-create Morphs
First auto-create bones by selecting the mesh you created in the top blank and the one you want to use as a template in the bottom and clicking so Assignments and save. Don’t overwrite a file as this step can go wrong. 
Next do the same thing but with the Morphs and be sure to check the replace existing morphs box (you shouldn’t have any currently but just to be sure). Again, save it as a different file.
Now it’s ready to be reimported back into TSR workshop
Open the project you created back at the beginning or start a new one with your template object. Go to the mesh tab and select high level of detail and import the mesh. If it asks you about bounding boxes say yes.
Here’s what mine looks like after import. Make sure you use the sliders at the top to test the morphs because if they don’t work you must go back to the mesh Toolkit and try again.
 
Now comes the sims specific texturing bits
You’re going to want to head over to the Texture tab and we’re going to get familiar with the settings
 
The first one we’ll start with is the Multiplier as it’s the base texture.
Import the texture we previously created by hovering over the texture then clicking edit, then import and selecting the image you created. Once it’s loaded select done.

Next up is the specular map which determines the shininess of the object. To create this, load your multiplier texture into your image editor of choice and replace all alpha with pure black and take the shirt texture itself and make it darker. Darker = less shiny, and since we are making a shirt it shouldn’t be very shiny.

Below the specular map is an ambient map, in this tutorial we don’t have to edit it. but if you are an experienced modeler and you’ve rendered an ambient occlusion map for your model this is where you’d put it. all it does it make the shading a bit nicer. Look up ambient occlusion.

Now we are jumping to the top and working on the overlay. If there is anything you want on your object that you don’t want the player to be able to modify with a color change slider then put it here. For me I’m going to put a CSH logo on it do demonstrate the concept. Overlays are based on the same UV mapping so the texture must be just as large as your original texture and you should place the image in the correct location. below is my overlay vs my original texture.
  
The last the texture we will edit in this tab is the mask. Masks control what areas are color changed with sliders. There are 3/4 channels but we will only be using 3 as that’s what the standard is. Channel 1 is (255R/0G/0B), channel 2 is (255R/255G/0B), and channel 3 is (255R/0G/255B). you go into your original texture and determine what it is that you think should be separately recolorable. For me channel one will be the main shirt, channel 2 will be the sleeves, channel 3 might be used for the cuffs. You don’t have to use all the channels but it does add a lot of customizability to your object. Here’s my mask 

So currently your project should look something like this, except the cool colors.
 
To create the cool default colors, go to the bottom of the texture tab and you will see a section titled patterns. The number of patterns corresponds to the number of channels you item can have, mine is enabled to have 3 so there are 3 boxes that all have enabled set to true. 
 
If you have your mask set up differently with only 1-2 channels you will need to disable the unused patterns. In the pattern menu you can set the default colors for each part of your object I selected colors that are close to CSH’s official colors but you can choose whatever. Once you’ve decided on the default colors you can create mode by going to the top of the texture box, at the upper right there is a document icon which allows you to delete and create default styles for this outfit. You can have as many or as few styles as you like.

Next up is the mesh tab again because there are more textures to edit 
In here we are just going to set the alpha and diffuse maps equal to our multiplier map that we created earlier. The specular map is going to be the same as our specular from before.

The really important one here is the normal map, which as you can see from my project isn’t looking so great. Basing this from my knowledge of other sims projects it’s supposed to look like this. The second texture can be downloaded for you to base your texture off of.
  
Anyway, once you have the transparent .png you load in your multiplier and make it transparent to match the background. Then you load it back into TSR. This map is important or your sim’s skin color won’t match from their body to their head and feet.

If you’ve gotten this far then congratulations because we are on the final step.
Go to the project tab and edit the title to a unique name and where it should appear in CAS, for mine it will appear in young adult/adult female everyday tops. Under extras you can also add a custom thumbnail if you want.

Once you’re done double check everything, save the project as you normally would then go to file, export and export it as a Sims3Pack. With your sims3 launcher open double click on your Sims3Pack file and it will install.

Voila! You’re done! Startup sims3 and enter CAS look at your new item.
 
