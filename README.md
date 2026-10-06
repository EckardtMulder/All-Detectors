
				     READ ME 
ESSAY: DETECTOR TECHNOLOGIES USED IN LOW AND MEDIUM ENERGY NUCLEAR TECHNOLOGIES


Good day to whomever downloaded these simulations, each simulation that has
been modeled and meshed can be found here, it is important to note a few important things.

REQUIRED SOFTWARE: PyCharm (or any other python reading IDE), Command prompt(should come with windows, just search "cmd" in the search bar), ParaView, Elmer FEM, and Elmer GUI(This one is optional, as paraview also functions as a graphical interface for viewing the models), and lastly Elmer Solver (This program will solve the electrostatic equations for all the meshed simulations)

==============================================================================
GENERAL WORKFLOW (For all detectors not including scintillation results (The mesh of a scintillation detector follows this however))
==============================================================================
 
	=============================================================
	In command prompt: 
	=============================================================
1) Run python to generate mesh and geometry

	 cd "path to your folder that contains the detector"
  	 python detector_script.py > gen.txt 2>&1
	
2) Convert the mesh to ElmerGrid

	findstr "DEBUG Error Traceback OSError" gen_output.txt

3) Check Converted mesh
	
	cd <mesh folder name>
	type mesh.header
	type mesh.names	
	
4) Run the sif file (this file stores all the physics constants, equations, basically tells Elmer Solver what to solve)	

	cd "path\to\detector\folder"
        "C:\Elmer\Elmer <version>\bin\ElmerSolver.exe" <case>.sif >   	solve_output.txt 2>&1
        findstr "Norm WARNING Error trivially" solve_output.txt

	=============================================================
	In Paraview: 
	=============================================================

1) Open the generated results in paraview by going to files> PLACE WHERE DETECTOR IS STORED > results> "name of files".vtu

2) Click apply located at the bottom left corner, make sure the eye icon is also open next to the name of the detector mesh, this is located in the workflow approximate middle left of the screen

3) Plot over line by pressing "control + space" on your keyboard, then enter the starting and end points of interest, click apply and untick all the options besides "potential" in the check box.

==============================================================================
For Scintillator Monte Carlo results
==============================================================================

1) Simply run the python program for each material Plastic, BGO, NaI(Tl), and read the terminal outputs, each run should give you a slightly different outcome due to the statistical variance of Monte Carlo

