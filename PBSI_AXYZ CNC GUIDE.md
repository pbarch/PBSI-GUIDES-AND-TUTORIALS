# CNC Milling Hand Off Document

### 1) Installing BlenderCAM
**Note:** The version of BlenderCAM prepared for the studio only works on Linux. Make sure you are using a PBSI computer running in the Linux Operating System.

<!SET UP LINUX DUAL BOOT ON A PBSI COMPUTER LIST WHICH ONE HERE>

Download the Custom Version of Blender with BlenderCAM and OpenCamLib installed from Basecamp here:
https://3.basecamp.com/3129796/buckets/6027913/messages/3077089290

Or from the server here:
<!(PUT BLENDERCAM ON THE SERVER AND PASTE LOCATION HERE) >

### 2) Generating Toolpaths


### 3) Basic CNC Operation

#### Start Up Procedure

1. Pull out the emergency stop.
2. Press the green on button
3. Press enter for the machine to seek home
4. Keep Hands away from the spindle
5. Press enter to warm up the spindle
6. Wait 10 mins for warm up to complete.

#### Changing the bit.

1. Place one wrench on the top of the Spindle, and the second on the Cover nut.
2. Turn Cover nut Clockwise to loosen.
3. Remove the Cover nut, Collet, and Bit.
4. Insert New Collet and bit. **Don't Bottom out the bit or it becomes very difficult to remove**
5. Replace the Cover nut and **Lightly** tighten with the two wrenches.

### Useful Functions

- **FUNC 13:** Return the milling head to the last Job origin.
- **FUNC 84:** Set the material surface, and Lift Top and Lift Bottom milling heights.
- **FUNC 1:** Override the milling feed rate. _Note: You can use this to exceed the max feed-rate imposed in the Toolpath software. When milling foam and removing small amounts of material, I've used a feed-rate as high as 1500 without any issue. **This can be adjusted mid Job**_
- **FUNC 9:** Abort a cut job.
- **FUNC 91:** Delete a file.

### Setting Up A Job

#### Sending A File
1. Open 'ToolPath for Windows' on the CNC control computer
2. Open your .nc g-code file
    - To check the file in 3D go to View-> 3D enter your view angle and press go (45 Z & 52X for a typical axo view)
3. To send a file to the CNC, Select Output.
4. Set the Spindle RPM to 9000,  Leave all the settings at their default
5. Hit send and transfer to begin sending the g-code file to the CNC.

#### Setting the Machine Limits & Job Home
##### The First Job in a Sequence
1.  On the CNC control panel enter **FUNC 84** to set the Material surface, and Min and Max Milling Heights (move the CNC head up and down with the 5 and 0 buttons)
    - **Surface:** The bit should be touching the surface of the material being Milled.
    - **Lift Bottom:** The lowest Z height the bit should travel to, I set this around 1/4" above the bed for the San Jose milling jobs.
    - **Lift Top:** This  will be the travel height the bit will move at when not cutting. In general this should be set above the height of the material clamps for safety. If you are **absolutely sure** that your toolpath is clear of the material clamps, even when the bit is traveling, you can set this close to the material surface to save some milling time.
2. Use the 8,6,2,4 (Forward, Right, Backward, Left) to move the CNC head to your desired home location for this Job.

##### Running another Job in a Sequence
1. You only need to reset the Limits and surface height if you have changed the bit.
2. use **FUNC 13** to return to the home location of the last job. **Always do this when running jobs in sequence, otherwise your passes could get out of alignment**

#### Starting a Job
1. Use the File Button  on the CNC  control panel to move through the files in memory.
2. When you get the file you want to run press start. **Ensure you have set the limits and home location before pressing start**
3. You can press 'Enter' at this point to key in a shape number for the job to start on.
4. When you've selected the shape you wish to begin the job at, press start again to begin the job.

#### Previewing Job Shapes
I'll often key in shape numbers before starting a job to get a sense of the job extents, and make sure that the entire area of the job is clear of the clamps, before I run a job.
to do this.

1. In 'Toolpath for Windows' select 'Edit' and use the Previous & Next Buttons to move preview the shapes in the job
2. Flip through the shapes to find ones that begin at the extents of the job, for the initial roughing pass this is usually the 2nd and last shape
3. Enter these shapes when starting a job on the CNC to move the CNC head to their location. Ensure that they are within the working area of the machine and are clear of the material clamps.
4. Enter shape 1 again to begin the job when you are done previewing.

#### Adjusting Feed Rate Mid Job.
To speed up the milling process you can override the max feed rate set in 'Toolpath for Windows' at any time during a job.
1. Pause the Job with the Stop Button
2. Enter **FUNC 1**
3. Key in your desired Feed Rate (For foam cuts removing minimal material, 1200 - 1400 seems to work well)
4. Press Start to Resume the Job.
