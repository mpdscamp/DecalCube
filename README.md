# OpenGL Computer Graphics Library

## Overview

This repository contains a modern C++20 OpenGL framework designed for computer graphics applications. It provides a clean, object-oriented abstraction over raw OpenGL calls while maintaining the flexibility needed for complex rendering techniques.

## Decal Projection System

The primary showcase of this library is the decal projection system that implements texture mapping through homography transformations. This enables:

1. **Perspective-correct Decal Projection**: Apply textures onto 3D objects with correct perspective
2. **Dynamic Decal Positioning**: Project textures onto moving objects while maintaining visual consistency
3. **View-independent Mapping**: Keep projected decals stable regardless of camera movement

The system uses a computed homography matrix to map between texture space and screen space, ensuring that decals remain visually consistent even as the underlying geometry rotates or moves.

## Technical Implementation

The decal system works by:

1. Computing a homography matrix that maps from source texture coordinates to destination screen coordinates
2. Inverting this homography to obtain a mapping from screen pixels back to texture samples
3. Applying this transformation in a fragment shader to correctly sample textures

This enables advanced effects like projecting logos, signs, or other visual elements onto 3D geometry without the visual distortion that would occur with standard texture mapping.

## Getting Started

### Prerequisites

- CMake 3.10 or higher
- C++20 compatible compiler
- OpenGL 4.6 compatible GPU and drivers

### Building the Project

```bash
# Clone the repository
git clone https://github.com/yourusername/OpenGL.git
cd OpenGL

# Configure the project
cmake -B build

# Build the project
cmake --build build
```

### Controls

- **WASD**: Camera movement
- **Q/E**: Move up/down
- **Mouse**: Look around
- **R**: Toggle cube auto-rotation
- **Left/Right Arrows**: Manually rotate the cube (when auto-rotation is disabled)
- **Tab**: Toggle mouse capture
- **Escape**: Exit application

## Project Structure

The library is organized into several key components:

- `gl/`: Core OpenGL abstractions (buffers, shaders, textures, etc.)
- `managers/`: Resource management for textures, shaders, and other assets
- `scenes/`: Scene implementation with rendering logic
- `window/`: Window and input handling

## Acknowledgments

- [GLFW](https://www.glfw.org/) for windowing and input
- [GLM](https://github.com/g-truc/glm) for mathematics
- [stb_image](https://github.com/nothings/stb) for image loading
