# Build Your Own World Design Document

**Partner 1: Yi Heng Zhuang Zhuo**

**Partner 2: Ayumu Ueda**

## Description
Developed a Mini-Game using Java that allows the user to move the avatar with the keys "WASD/wasd" and collect clovers, turn the light off and back on with the key "L/l", create new random worlds by entering random numerical seeds or loading the most recently saved world.

## Output 
![wonder-world](https://github.com/yihz019/Wonder-World/assets/93494138/7e2d6134-9063-4c4f-96e7-bae95624589c)


## Classes and Data Structures 
### Clases:
- **World**: Instantiates a world object given a fixed size of the screen/world
and gets user inputs to create a new world, load the most recent world, or quit the game.*
  - _Instance variables_: 
    - Width and Height: dimensions of the screen or the world.
    - TETile board: 2D array of Tiles 
    - Container: The root of the tree of containers
    - Rooms: Object to pass down containers and world information to room class to create rooms and hallways.
    - Seed: Saves the given seed by the user. 
    - TERenderer: Renders the board, menu window, or overall game state to the screen.

- **Container**: Takes the main container(screen) and splits it into smaller containers randomly.
  - _Instance variables_:
    - Height and Width of each container.
    - Left & Right pointers for children containers.
    - xPos, yPos: x and y coordinates that represent the bottom left position of the container.
    - Room: the room object created inside the container.

- **Room**: Given a tree of containers create rooms within each container.
  - _Instance variables_:
    - Height and Width of each room.
    - xPos, yPos: x and y coordinates that represent the bottom left position of the room.

- **Hallway**: Creates horizontal or vertical hallways that connect rooms.
  - _Instance variables_:
    - vertical and horizontal: integers 0 and 1 respectively that represent in what direction the hallways are created.

- **Point**: A coordinate point object that holds the starting and ending position.
Starting position (x,y) was set as the bottom left, ending position (endX, endY) represents the width and height.

- **Theme**: To be implemented

- **Character**: To be implemented

### Data Structures:
- _BST tree_: Used the inspiration of a BST tree, but created our own class that simulates a tree of Container objects, 

## Algorithms:
- **World**: Renders a fixed-size world/screen. Initially shows a menu window that allows the user to create a new world,
load the most recent world, or quit the game. This World object delegates its containers object to randomly split 
the screen into smaller containers and then assigns the rooms object to create rooms within each container and connect 
them with hallways.
- **Container**: Using the logic of a BST tree, recursively split the main container(screen) into 2 smaller containers 
of random size rectangles/squares. Then, make the 2 newly created containers the 
left and right child of the container. Stops splitting when the container has a minimum size of 3-4 tiles.
- **Room**: Given the Tree of containers, traverse the tree and create a room when a leaf has been reached.
The room will be of random size and position within the container's frame, the size will be greater than 1
  tile to distinguish it from the hallway. Calls the Hallway object to connect the rooms.
- **Hallway**: Traverse the tree of containers and create vertical/horizontal hallways to connect 
containers 2 by 2 according to their positions.

## Persistence
For saving and loading the state of the world we have:
- saveWorld: This method creates a txt file called "saveandload" and writes the width, height, and seed as strings
of the current world.
- loadWorld: Reads from the txt file stated in saveWorld, and creates a new World object with the given dimensions 
and given seed information to render the world. 
