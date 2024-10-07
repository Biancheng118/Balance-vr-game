# Balance-Beam-Challenge-VR-Game

## Project Overview
**Balance Beam Challenge** is a VR game where players interact with different-sized cubes to balance a seesaw (balance beam). The goal is to place the cubes on the balance beam and maintain balance without letting the beam tip over. The game includes intuitive interactions like grabbing, dragging, and placing objects, as well as a "Restart" button to reset the game when needed.

## Table of Contents
1. [Gameplay](#gameplay)
2. [Interactable Elements](#interactable-elements)
3. [Theme](#theme)
4. [Setup and Usage](#setup-and-usage)
5. [Code Explanation](#code-explanation)
6. [Project Structure](#project-structure)

## Gameplay
The player is tasked with placing cubes of different sizes and weights on a balance beam to maintain equilibrium. The beam will tilt based on where the cubes are placed, creating a fun physics-based challenge. If the player fails or wants to restart, they can press the "Restart" button to reset the scene.

## Interactable Elements
The game includes the following key interactions:

### 1. **Grabbable Cubes (Physics-based Interaction)**
   - **Description**: Players can grab, drag, and place cubes on the balance beam. These cubes vary in size and mass, which influences the balance of the beam.
   - **Implementation**: Using Unity’s `Rigidbody` and `XR Grab Interactable` components, players can physically interact with the cubes.
   - **Gameplay Functionality**: The player must strategically place the cubes on the beam to keep it balanced, considering their varying sizes and weights.

### 2. **Cube Hover Color Change (Raycasting with Collider-based Interaction)**
   - **Description**: When the player’s controller cursor hovers over a cube or the restart button, the color of the object changes to indicate that it is interactable.
   - **Implementation**: `Collider` and `XR Ray Interactor` are used to detect the controller's raycast hit, and the object's material changes color when hovered over.
   - **Gameplay Functionality**: Provides visual feedback to the player about which objects are interactable, enhancing the gameplay experience.

### 3. **Restart Button (UI-based Interaction)**
   - **Description**: A "Restart" button is placed in the environment for the player to click when they wish to reset the scene.
   - **Implementation**: A `UI Button` is created using Unity’s Canvas system, and an event listener is added to reload the scene.
   - **Gameplay Functionality**: Clicking this button resets all objects to their initial positions and conditions, allowing players to try balancing the beam again.

## Theme
The game's theme is **"The Art of Balance"**, where players explore balancing physical objects to maintain equilibrium. The setting of a balance beam and cubes emphasizes the delicate nature of balance, requiring the player to experiment with different weights and placements.

## Setup and Usage
1. **Prerequisites**: Make sure you have Unity installed (tested with version 2020.x or later) and the `XR Interaction Toolkit` package.
2. **Clone the Repository**: Clone the repository from GitHub:
    ```bash
    git clone [[GitHub Repo URL](https://github.com/Biancheng118/Balance-vr-game.git)]
    ```
3. **Open in Unity**: Open the project in Unity Hub, and ensure all assets and packages are installed.
4. **Play the Game**:
   - Start the scene in the editor (`Play` button).
   - Use VR controllers to grab and place cubes on the balance beam.
   - Press the "Restart" button to reset the game.

## Code Explanation

### Grabbable Cubes
- **Rigidbody & Grab Interaction**: The cubes have a `Rigidbody` component to enable physics-based interactions and gravity effects. The `XR Grab Interactable` allows players to grab and drag them using their VR controllers.
- **Behavior**: When a cube is released on the beam, the beam tilts according to the cube's weight and position.

### Hover Color Change
- **Hover Feedback**: When the controller's ray hovers over a cube or the button, an `OnHoverEnter` event triggers a color change to indicate interaction.
- **Implementation**: Using `XR Ray Interactor`, the color is temporarily changed when the object is hovered over and reset when the hover ends.

### Restart Button Functionality
- **UI Button Setup**: A `RestartGame` script is attached to the button to handle scene reloading.
- **Code Details**: Below is the `LoadScene.cs` script, which provides two key functionalities: loading a scene by its name and reloading the current scene.

    ```csharp
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine.SceneManagement;
    using UnityEngine;

    /// <summary>
    /// This class provides methods for loading scenes.
    /// It can either load a specific scene by its name
    /// or reload the currently active scene.
    /// </summary>
    public class LoadScene : MonoBehaviour
    {
        /// <summary>
        /// Loads a new scene based on the scene's name.
        /// </summary>
        /// <param name="sceneName">The name of the scene to be loaded.</param>
        public void LoadSceneUsingName(string sceneName)
        {
            SceneManager.LoadScene(sceneName);
        }

        /// <summary>
        /// Reloads the currently active scene.
        /// </summary>
        public void ReloadCurrentScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name);
        }
    }
    ```

- **Explanation**:
   - `LoadSceneUsingName(string sceneName)`: Loads a new scene based on its name, which is passed as a parameter. This is useful for changing scenes during gameplay.
   - `ReloadCurrentScene()`: Reloads the currently active scene. This function is ideal for restarting the game or resetting the current scene's state.

- **Button Interaction**: The `On Click ()` event of the button is configured to call either `LoadSceneUsingName()` or `ReloadCurrentScene()` in the `LoadScene` script to navigate between scenes or reset the game.


## Project Structure
- **Assets**: Contains all game assets, including prefabs for the balance beam, cubes, and the restart button.
- **Scenes**: Stores the main game scene, which is the core of the balance challenge.
- **Scripts**: Holds scripts for interaction logic like grabbing, hovering, and scene management.

## Credits and Resources
- **Assets Used**: 3D models and assets from the Unity Asset Store for the balance beam and cubes.
- **Unity Documentation & Tutorials**: Unity documentation for XR Interaction Toolkit and UI setup was referenced during development.
