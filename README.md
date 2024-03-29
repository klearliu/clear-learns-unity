# Unity Tutorial
Learning Unity from the official site
https://learn.unity.com/course/create-with-code

Within this short project I am expected to learn about:
  - Unit 1: Player Control
  - Unit 2: Basic Gameplay
  - Unit 3: Sound Effects
  - Unit 4: Gameplay Mechanics
  - Unit 5: User Interface

<details close>
<summary># Jan 16, 2024</summary>

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
1.1.1) Create new project
1.1.2) Import assests and open Prototype
   - Assets > Import Package > Custom Package
1.1.4) Add object to scene
1.1.5) Reposition obstacles
</details>

<details close>
<summary># Jan 17, 2024</summary>

1.1.5) Locate Camera and Run the Game
  - select camera from play and press 'F' to focus on it
  - to run the game hit the play button
</details>

<details close>
<summary># Jan 18, 2024</summary>

1.1.6) Moving Camera
   - Moving & rotating camera

1.1.7) Customize the Interface Layout
   - Top right contains:
    - 2 by 3
    - 4 split (good for 2D)
    - Default
    - Tall
    - Wide
   - You can save your own custom layout

All seven "Getting Started" components are now completed

1.2.1) Create and Apply first C# Script
   - Go to Project tab > right click on Assets > Create > Folder "Scripts"
   - Navigate to newly created "Scripts" Folder and create C# script "PlayerController"
   - NOTE: If you ever rename a C# Script you will also have to change the public class to the same name
   - Left click on your script and drag it to your object(ex player controller to a vehicle)
       - This is called Adding Component in Unity
1.2.2) Opening C# script in Unity
   - Double click on your C# script and it will open up Visual Studios Code
1.2.3) Since we want to affect the 'Transform' tab in Unity we will create a line of code in Update()
  `transform.Translate(0,0,1);`
</details>

<details close>
<summary># Jan 19, 2024</summary>

1.2.4) Using Vector3 as Movement
  - Instead of `transform.Translate(0,0,1);`
  - We can use `transform.Translate(Vector3.forward);`
    - makes code more understandable

1.2.5) Adjusting Movement Speed
  - Update() is called every frame and it is different for every computer, because of hardware
  - To fix this we can change the movement speed to update every second instead
      - We do this by `transform.Translate(Vector3.forward * Time.deltaTime * int)`
      - The higher the int value the faster
</details>

<details close>
<summary># Jan 20, 2024</summary>

1.2.6) Add RigidBody Components to Objects
  - RigidBody component auto adds physics to our game, ex. collision and gravity
  - Select Object > Add Component > Physics > RigidBody
  - You usually want to have another object to have a RigidBody to see the effect
  - The Mesh Collider tab is just a way to state if an object can be collided with

1.2.7) Duplicate Obstacles
  - Select game object in Hierarchy and do (ctrl/cmd + D) or right click and select duplicate
  - Rename duplicated object accordingly, and adjust anything in the inspector
  - You can also duplicate more than one objects at a time
</details>

<details close>
<summary># Jan 21, 2024</summary>

1.3.1) Variables in C# and Unity
  - by setting up `public float speed = 5.0f;` we can see speed outside of its class
  - you can also now modify the speed within the script inspector
</details>

<details close>
<summary># Jan 22, 2024</summary>

1.3.2) Creating script for camera
  - Create a new C# in your scripts folder `FollowPlayer.cs`
  - In Unity drag script to camera
  - In C# script create a public member variable `public GameObject variable;`
  - In Unity drag game object (from hiearchy) to camera's inspector
  - In C# script inside Update() `transform.position = player.transform.position;`
      - transform transform.position means current position
      - so by opening access to camera's position to GameObject's position the camera
        will track our desired GameObject

1.3.3) Create an Offset for Camera's Position
  - In C# script of Update()
      - `transform.position = player.transform.position + new Vector3(0,6,-9);`

1.3.4) Making Vector3 a Variable
  - Initialize a private member variable `private Vector3 offset = new Vector3(0,6,-9);`
  - Update() `transform.position = player.transform.position + offset;`

1.3.5) Smoothen Camera with LateUpdate()
  - Sometimes the camera might move before the GameObject or the other way around
  - To resolve this issue we change Update() to LateUpdate()
      - This makes it so that update is only made after all the updates are made

1.3.6) Edit PlayMode tint colour
  - Sometimes it may be hard to tell if you are in playmode or not
  - To counter this we can use some GUI tinting
  - Go to Preferences > Colours > Playmode tint
      - Adjust as needed

1.4.1) Moving PlayerObject Left/Right
  - Create a public member variable `public float turnSpeed;` inside PlayerController
  - Inside Update() `transform.Translate(Vector3.right * Time.deltaTime * turnSpeed);`

1.4.2) Creating input to move PlayerObject Left/Right
  - Edit > Input Manager > Axes
  - Our focus will be Horizontal axis
  - Note: we will be focusing on the negative and positive button section
  - In our C# script for PlayerObject
      - Create a public member variable `public float horizontalMovement;`
      - Inside Update() `horizontalInput = Input.GetAxis("{whatever the Name section is on Input Manager > Horizontal}")`
      - `transform.Translate(Vector3.right * time.DeltaTime * turnSpeed * horizontalInput);`
      - Typically you would want speed, turnSpeed, and horizontalInput to be private, but for testing public is better

1.4.3) Creating input to move PlayerObject Forward/Backward
  - Edit > Input Manager > Axes
  - Our focus will be Verticle axis
  - Note: we will be focusing on the negative and positive button section
  - In our C# script for PlayerObject
      - Create a public member variable `public float forwardInput;`
      - Inside Update() `forwardInput = Input.GetAxis("{whatever the Name section is on Input Manager > Horizontal}")`
      - `transform.Translate(Vector3.right * time.DeltaTime * turnSpeed * forwardInput);`

1.4.4) Creating Rotation Effect for PlayerObject when moving Left/Right
  - In Update() replace `transform.Translate(Vector3.right * time.DeltaTime * turnSpeed * horizontalInput);`
    with `transform.Rotate(Vector3.up, time.DeltaTime * turnSpeed * horizontalInput);`
  - At the top left we have local/global toggle
      - Local: Z - Axis points to forward direction
      - Global: Z - Axis points in the positive direction of the world
      - When POSITIONING objects it is best to use global mode to better accuracy
      - During playmode local has a friendlier interface

1.4.5) Organizing Hierarchy
  - Right click on blank space in Hierarchy > Create Empty > {rename to how you see fit}
  - Drag related GameObjects to that Empty
  - This is called Nesting GameObject, we will learn more features about Nesting GameObject
  - In your C# scripts change any finalized variables to private to reduce clutter and any unwanted changes
  - In FollowPlayer class, ensure that GameObject player is still public since we have a reference to it in unity
</details>

<details close>
<summary># Jan 23, 2024</summary>

Challenge 1 Plane from here:
<br>
https://connect-prd-cdn.unity.com/20210506/913574fa-af65-4d95-abe8-d90282b27a83/Challenge%201%20-%20Starter%20Files.zip
<br>
In this challenge I downloaded some .zip files of a flappy bird like game with a plane.
Bugs and objectives identified goes as followed:
1) Plane is going backwards
  - Objective: Make plane go forward
  - Solution:
    - PlayerControllerX.cs line 24
    - `transform.Trnslate(Vector3.forward * speed);`

2) Plane is going too fast
  - Objective: Make plane go at a proper speed
  - Solution:
    - PlayerControllerX.cs line 7
    - `public float speed = 0.2f;`

3) The plane is tilting automatically
  - Objective: Make the plane tilt only if the user presses the up/down arrows
  - Solution:
    - PlayerControllerX.cs lines 27
    - `transform.Rotate(Vector3.left*rotationSpeed*Time.deltaTime*verticalInput);`

4) The camera is in front of the plane
  - Objective: Reposition it so it’s beside the plane
  - Solution:
    - Find main camera and go to inspector and adjust position settings to 40,2,5
    - Rotation to 0, 270, 0

5) The camera is not following the plane
  - Objective: Make the camera follow the plane
  - Solution:
    - From Hierarchy drag Player to Main Camera's Inspector GameObject
    - FollowPlayerX.cs line 8
    - `private Vector3 offset = new Vector3(60, 2, 5);`

6) Bonus: The plane’s propeller does not spin
  - Objective: Create a script that spins the plane’s propeller
  - Solution:
    - Click Player object from Hierarchy > Propeller
    - Create new C# script `SpinPropeller.cs`
    - Add Component > Scripts > SpinPropeller.cs
    - Edit SpinPropeller.cs in Update()
    - initialize a member variable `public float spinSpeed = 500;`
    - `transform.Rotate(Vector3.forward, Time.deltaTime*spinSpeed);`
</details>

<details close>
<summary>#Feb 6, 2024</summary>
Lab 1: Creating a sample GDD document
Quiz 1: 9/10

Basic Gameplay Unit 2
2.1) Player Positioning

2.1.1) Setting up Prototype 2

2.1.2) Add the Player, Animals, and Food
  - Position game objects (ie humans and animals) onto a plane
  - Changing textures of a plane

2.1.3 and 4) Moving player left/right
  - `horizontalInput = Input.GetAxis("Horizontal");`
  - `transform.Translate(Vector3.right*horizontalInput*Time.deltaTime*speed);`

2.1.5) Keep the player inbounds
  - `transform.Translate(Vector3.right*horizontal*Time.deltaTime*speed);`
      - Make sure that is inside `if(transform.position.x < -10){...}`

2.2.1) Understanding Prefab
  Prefab short for prefabricated. We can utilize this to reuse components in our scene
  Instantiate: make a new copy or clone
  Making object move immediately upon play
  `transform.Translate(Vector3.forward*Time.deltaTime*speed);`

2.2.2) Make the projectile into a prefab
  - Create a new folder in Assests /Prefabs
  - Drag the food object (from Hierarchy) into the Prefabs folder > Original Variant
  - "think of prefab as a defined template of a gameobject"
  - next we need to create a reference of the pizza to the PlayerControl script
      - in PlayerControl.cs:
      - `public GameObject projectilePrefab;`
  - Drag the food object from /Prefabs and drag it into the GameObject inspector of Player

2.2.3) Test for spacebar press
  - In PlayerController.cs
  - `if(Input.GetKeyDown(KeyCode.Space))`

2.2.4) Launch projectile on spacebar press
  - Inside our just created if statement
      - `Instantiate(projectilePrefab, transform.position, projectilePrefab.transform.rotation);`

2.2.5) Make animals into prefabs
  - Rotate all animals in your scene by 180 degrees
  - Drag MoveForward.cs into all the animal objects
  - Adjust any speeds or templated attributes
  - Drag to /Prefabs from Hierarchy

2.2.6) Destroy projectiles offscreen

</details>

<details close>
<summary>#Feb 12, 2024</summary>

2.2.6 and 2.2.7) Destroy projectiles offscreen
  - Create a new script for Pizza and inside update do `if(transform.position.z>30){Destroy(gameObject);}`
  - Inside Unity: Go to Pizza and find Overrides drop-down > apply all
  - We can also do the same for lower bounds
  - `if(transform.position.z<)`

2.3.1) Create a spawn manager
  - In hiearchry an empty gameobect and call it SpawnManager
  - Create a C# script also called SpawnManager.cs and add it as a component to SpawnManger from hiearchy
  - `public GameObject[] animalPrefabs;`
  - In Unity drag the three animals from prefabs to the C# GameObject section

2.3.2) Spawn an animal if S is pressed
  - SpawnManager.cs
      - `public int animalIndex;`
      - `if(Iinput.GetKeyDown(KeyCode.S)){
           Instantiate(animalPrefabs[animalIndex], new Vector3(0,0,20),animalPrefabs[animalIndex].transform.rotation);}`

2.3.3) Spawn random animals from array
  - remove the `public int animalIndex;`
  - redeclare inside the if statment as:
      - `int animalIndex = Randm.Range(0,animalPrefabs.Length);`

2.3.4) Randomize the spawn location
  - `private float spawnRangeX = 10;`
  - `private float spawnPosZ = 10;`
  - inside Update()
      - `Vector3 spawnPos = new Vector3(Random.Range(-spawnRangeX,spawnRange),0,spawnPosZ);`
      - `Instantiate(animalPrefabs[animalIndex], spawnPos, animalPrefabs[animalIndex].transform.rotation);}`

2.3.5) Change the perspective of the camera
  - Select Main Camera from hiearchy
  - Inside Scene Editor toggle between ISO and Persp
      - ISO good for 2D
      - Persp 3D
  - Go to inspector and select your desired project

2.4.1) Make a new method to spawn animals
  - In SpawnManager.cs create a new metheod called SpawnRandomAnimal(){}
  - and paste the contents from the if statement
</details>

<details close>
<summary>#Feb 13, 2024</summary>
2.4.2) Spawn the animals at timed intervals
  - remove the if statement in the update()
  - in Start()
    - `InvokeRepeating("SpawnRandomAnimal", startDelay, spawnInterval);`

2.4.3) Add collider and trigger components
  - on all of your animal prefabs add a box collider and adjust it so that it surrounds the animal
  - do the same with the pizza
  - ensure that isTrigger box is checked
  - for the food GameObject make sure we add a RigidBody component with use gravity turned off

2.4.4) Destroy objects on collision
  - Create a new DetectCollisions.cs and apply to all prefabs
  - Override a metheod `private void OnTriggerEnter(Collider other){...}`
  - `Destroy(gameObject);` and `Destroy(other.gameObject);`

2.4.5) Trigger a “Game Over” message
  - in DestroyOutOfBounds.cs
      - inside the else if
          - `Debug.Log("Game Over!!!");`
  - using `Debug.Log()` is a great way to test our code

</details>








  
