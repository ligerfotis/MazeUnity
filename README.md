# Maze Unity
This is the graphical simulation developed in Unity of the real world experiment from Shafti et al. (2020) [1] used from the [MazeRL](https://github.com/ligerfotis/maze_RL_online)

Forked from https://github.com/panos-stavrianos/MazeUnity and adjusted accordingly for [MazeRL](https://github.com/ligerfotis/maze_RL_online)

The environment receives actions (plus other important information) and sends back observations (plus other important information) to MazeRL.

The above messages are being exchanged via an HTTP server.

MazeRL and MazeUnity work as HTTP clients.

### Edit MazeUnity
* Download git
  
      git clone https://github.com/ligerfotis/MazeUnity.git
  
* [Install Unity](https://docs.unity3d.com/2020.1/Documentation/Manual/GettingStartedInstallingHub.html)(Version: 2020.3.13.f1)
* Open with unity
  * If project is not recognized in UnityHub, create a new one and replace the new project's folders.
* Remove default scene
* Drag and drop main scene from Scenes in the Hierarchy

#### Add Rider in unity (Recommended for editting)
https://www.jetbrains.com/help/rider/Unity.html#getting-started

### Play

#### Prerequisites 
* Start the dedicated [Maze Server](https://github.com/panos-stavrianos/maze_server)
* Start the experiment [MazeRL](https://github.com/ligerfotis/maze_RL_online) 

#### Play in Unity EditorZ
Just open the game in Unity and press the `play` button.

#### Play in Web Browser
Every time a user opens the link to the webgl in the browser the game is being sent to it from a docker.
##### Start webgl server with docker
* Build Settings -> web_build -> (switch platform) -> build
* Choose web_build and name it “webgl”
* Go to to MazeUnity/web_build
        
        cd MazeUnity/web_build
* Edit webgl.conf 'server_name' to the name of your server without the ‘http://’ header (default: localhost)
* Make sure the ports used below are open.
*       docker build -t <image_name>:<version> . (docker build -t maze-unity:1.0.0 .)
*       docker run -p <host_port>:80 <image_name>:<image_version> (docker run -p 12000:80 maze-unity:1.0.0)
* Open <server_name>:<host_port> (localhost:12000) in a browser.
* If you want to stop the docker: `docker stop maze`
* If you want to remove the docker: `docker rm maze`

### HTTP connectivity

In [Assets/Scripts](https://github.com/ligerfotis/MazeUnity/tree/main/Assets/Scripts) folder.

### MazeUnity Environment Overview
![MazeUnity](./maze.png)

#### Dimensionality
  * Tray: 50cm x 50cm
  * Wall thickness: 3cm
  * Obstacles opening: 9 cm 
  * Ball radius: 5cm
  * Hole radius: 5 cm

### References
[1] Shafti, Ali, et al. "Real-world human-robot collaborative reinforcement learning." arXiv preprint arXiv:2003.01156 (2020).
