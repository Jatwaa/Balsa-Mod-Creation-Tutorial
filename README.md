# Balsa-Mod-Creation-Tutorial
High level steps to creating a Balsa part mod

Download and install Unity Hub

Install Unity 2019.4.25f1

Download the SDK project

Create Part in Blender

Remove Camera and Light 

Export as FBX

Open SDK Project 

Import part into Unity scene

Remove Camera from Unity Scene

Remove Light from Unity Scene

For the imported part, rename the part to the desired name in the Inspector

*Create a Child Empty and name it: model

*Create a Child Empty to model and name it: Resize

*Create a Child Empty to Resize and name it: mesh

*Create a Child Empty to Resize and name it: collider

Copy the Mesh Filter and Mesh Renderer to the mesh child from the upmost Parent

Remove the meshes from the upmost Parent

Copy the collider or create the collider to the collider child from the mesh
	
	*Note that the collider must be Convex, if it is not, delete the collider and create the collider as Convex
	*If copied from the upmost Parent, then remove the collider from there once done

Create a Child Empty to model and name it node_fore (or node_srf)
	
	node_fore or node_aft for front and rear nodes
	
	node_surf for surface attachments

Add in the reference sizers from Assets > balsa.sdk  > assets > shared > reference

Resize part to match the desired reference part on the Resize child

Remove the reference part

On the upmost Parent, click Add Component and add the following scripts
	
	Scripts > BalsaAddons > 
		Part
		Part Model
		Part Physics
	
	Scripts > BalsaAddons > 
		Part Icon Fitter

On the nodes (IE: node_fore) add the script
	
	Scripts > Attach Node
		Fore: 
			Id: fore
			Type: Stack
		Aft:
			Id: aft 
			Type: Stack
		Surface
			Id: srf
			Type: Surface
			
For the nodes, there are guide arrow, one Yellow, the other Gray

Correct the orientation till:   

	Fore: Gray is pointing Y+ and Yellow is Z+
	
	Aft: Gray is pointing Y+ and Yellow is Z-
	
	Srf: Yellow is pointing Y+ and Gray is Z+
	  
Click on Tools > Floating Origin Interactive > Part Asset Bundle Export Tools

Click Get Prefabs from Scene

Select the parts to process via checking/unchecking their selection box to the right 

Click on Pre-Process Enabled Part Prefabs

This should populate the scripts fields, verify the fields for sanity

Add in extra scripts as needed for resources, engines,  et al

Configure all the scripts, note they (mostly) have tool tips for guidance

	**remember that Part: Part Name must be unique
	**For the Part script, be sure to 
		Click on Tags
		Set Size to 1
		Add in the part type, IE Engine, Motor, et al

Click on Open Asset Bundle Browser {and build}

	Click on the Build tab
	
	Set the Output path
	
	Click on Build
	
Click on Post-Process Asset Bundles

Click on Generate ModCFG File

	**If the CFG is in a separate folder, be sure to copy it to the project folder
	**If the output is NOT set to F:\SteamLibrary\steamapps\common\BALSA Model Flight Simulator Playtest\Addons\*modFileNameHere* then copy the files from output to your mod folder name
	
Cross your fingers and load the game
