# Unity Tutorial
Learning Unity from the official site
https://learn.unity.com/course/create-with-code

Within this short project I am expected to learn about:
  - Unit 1: Player Control
  - Unit 2: Basic Gameplay
  - Unit 3: Sound Effects
  - Unit 4: Gameplay Mechanics
  - Unit 5: User Interface

# Jan 16, 2024

View Controls in Unity
Pan and Zoom | Right Click + wasd
360          | ALT + Left Click
Zoom         | ALT + Right Click
Pan          | Hold Middle Button and Drag

Tools
View Tool - Q
Move Tool - W
Rotate Tool - E
Scale Tool - R
Rect Tool - T (This is a combination of move, rotate and scale) use for 2D
Transform Tool - Y (This is a combination of move, rotate and scale) use for 3D

Tips:
If ever lost select object in Hierarchy tab and press 'F'

Today I covered:
1) Create new project
2) Import assests and open Prototype
   - Assets > Import Package > Custom Package
4) Add object to scene
5) Reposition obstacles

# Jan 17, 2024

5) Locate Camera and Run the Game
  - select camera from play and press 'F' to focus on it
  - to run the game hit the play button

# Jan 18, 2024

6) Moving Camera
   - Moving & rotating camera

7) Customize the Interface Layout
   - Top right contains:
    - 2 by 3
    - 4 split (good for 2D)
    - Default
    - Tall
    - Wide
   - You can save your own custom layout

All seven "Getting Started" components are now completed

1) Create and Apply first C# Script
   - Go to Project tab > right click on Assets > Create > Folder "Scripts"
   - Navigate to newly created "Scripts" Folder and create C# script "PlayerController"
   - NOTE: If you ever rename a C# Script you will also have to change the public class to the same name
   - Left click on your script and drag it to your object(ex player controller to a vehicle)
       - This is called Adding Component in Unity
2) Opening C# script in Unity
   - Double click on your C# script and it will open up Visual Studios Code
3) Since we want to affect the 'Transform' tab in Unity we will create a line of code in Update()
   >>> transform.Translate(0,0,1);


