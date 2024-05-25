# OpenGL 101

A cross-platform, hardware-accelerated, language-independent, industrial standard API for producing 3D (including 2D) graphics.

## Table Of Content

- [Create Window](#create-window)

## Create Window

```cpp
#include <iostream>
#include <glad/glad.h>
#include <GLFW/glfw3.h>

using namespace std;

int main() {
  // Initialize GLFW
  glfwInit();

  // Tell GLFW what version of OpenGL we are using
  glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3);
  glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3);
  // Tell GLFW we are using the CORE profile
  // So that means we only have the modern functions
  glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);

  // Create a GLFWwindow object of 800 by 600 pixels, naming it "OpenGL"
  GLFWwindow * window = glfwCreateWindow(800, 600, "OpenGL", NULL, NULL);
  // Termination if the window fails to create
  if (window == NULL) {
    cout << "Failed to create GLFW window" << endl;
    glfwTerminate();
    return -1;
  }
  // Introduce the window into the current context
  glfwMakeContextCurrent(window);

  // Load GLAD so it configure OpenGL
  gladLoadGL();
  // Specify the viewport of OpenGL in the Window
  // In this case the viewport goes from x = 0, y = 0, to x = 800, y = 600
  glViewport(0, 0, 800, 600);

  // Specify the color of the background
  glClearColor(0.07 f, 0.13 f, 0.17 f, 1.0 f);
  // Clean the back buffer and assign the new color to it
  glClear(GL_COLOR_BUFFER_BIT);
  glfwSwapBuffers(window);

  // Main while loop
  while (!glfwWindowShouldClose(window)) {
    glfwPollEvents();
  }

  // Delete window before ending the program
  glfwDestroyWindow(window);
  // Terminate GLFW before ending the program
  glfwTerminate();
  return 0;
}
```
