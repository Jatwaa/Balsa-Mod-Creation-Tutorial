# Balsa-Mod-Creation-Tutorial
High level steps to creating a Balsa part mod

Download and install Unity Hub

Install Unity 2019.4.25f1

Download the SDK project

Create Part in Blender

Remove Camera and Light 

Export as FBX

Open SDK Project 

Import your part to Unity and set it to Read/Write Enabled
Import part into Unity scene

Remove Camera from Unity Scene

Remove Light from Unity Scene

For the imported part, rename the part to the desired name in the Inspector

Click on Tools > Floating Origin Interactive > Experimental > Part Setup Tools

The tool will add all the basic scripts to your part

Once the scripts are setup, you can add nodes/ports/planes

	fore or aft for front and rear nodes for attaching your craft via connection points
	
	surf for surface attachments
	
	Resource Ports are required for parts that need/provide resources
	
	In Balsa
		Engines provide Drive power via DriveShaft node
		
		Engines need Electric or Fuel to work
		
		Need an Input Actuator to interact with the throttle
		
		Propellers need Drive power and connect to the DriveShaft node
		
		Propellers will be covered in a separate document
		
		Fuel/Electrical require a Resource Port to provide resources

Duplicate the Mesh that you imported, and add in a Mesh Collider, set it to Convex

If it is not a Mesh collider, ignore the Convex requirement

Rename the duplicated mesh "collider"

Remove the Mesh Renderer and Mesh Filter from the collider

Add in the reference sizers from Assets > balsa.sdk  > assets > shared > reference

Resize part to match the desired reference part on the Resize child

Remove the reference part
		
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
