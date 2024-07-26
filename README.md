# V-HACD JS Wrapper

This library provides a simple JavaScript wrapper around the [V-HACD](https://github.com/kmammou/v-hacd) library, which decomposes 3D surfaces into near-convex parts. It leverages Emscripten to compile the V-HACD C++ code into WebAssembly for use in web applications.

## Installation

To use this library, you'll need to install Emscripten. Follow these steps:

```bash
git clone https://github.com/emscripten-core/emsdk.git
cd emsdk
./emsdk install latest
./emsdk activate latest
emsdk_env.bat
export PATH=$PATH:$(pwd) # For bash
```

## Usage

Here's a quick guide on how to use the `vhacd-js` library to decompose a 3D mesh:

1. **Import the Library**

   ```ts
   import { ConvexMeshDecomposition } from "vhacd-js";
   ```

2. **Create a Decomposer Instance**

   You can create a decomposer instance which can be used to decompose multiple meshes:

   ```ts
   const decomposer = await ConvexMeshDecomposition.create();
   ```

3. **Configure Decomposition Options (Optional)**

   You can specify options to control the decomposition process. For example, you can set a maximum number of hulls:

   ```ts
   const options = { maxHulls: 32 };
   ```

4. **Compute Convex Hulls**

   Use the decomposer instance to compute an array of convex hulls from your mesh data:

   ```ts
   const hulls = decomposer.computeConvexHulls({ positions, indices }, options);
   ```

   Here, `positions` is an array of vertex positions and `indices` is an array of indices defining the mesh's faces.

## API Reference

For detailed information on the JavaScript API, see `vhacd.ts`.
