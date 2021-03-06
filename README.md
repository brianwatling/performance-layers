# Vulkan Performance Layers

This project contains three Vulkan layers:
1. Compile time layer for measuring pipeline compilation times. The output log file location can be set with the `VK_COMPILE_TIME_LOG` environment variable.
2. *(Work in Progress)* Runtime layer for measuring pipeline execution times. The output log file location can be set with the `VK_RUNTIME_LOG` environment variable.
3. Frame time layer for measuring time between calls to vkQueuePresentKHR, in nanoseconds. This layer can also terminate the parent Vulkan application after a given number of frames, controlled by the `VK_FRAME_TIME_EXIT_AFTER_FRAME` environment variable. The output log file location can be set with the `VK_FRAME_TIME_LOG` environment variable.

The results are saved as CSV files.

The layers are considered experimental.
We welcome contributions and suggestions for improvements; see [docs/contributing.md](docs/contributing.md).

## Build Instructions

Sample build instructions:

```
# Checkout the submodules.
git submodule update --init

# Build and install performance layers.
mkdir -p <BUILD_DIR> ; cd <BUILD_DIR>
cmake .. \
      -GNinja \
      -DCMAKE_C_COMPILER=<COMPILER> \
      -DCMAKE_CXX_COMPILER=<COMPILER> \
      -DCMAKE_BUILD_TYPE=<CONFIGURATION> \
      -DCMAKE_INSTALL_PREFIX=run \
      -DVULKAN_HEADERS_INSTALL_DIR=<PATH_TO_VULKAN_HEADERS_INSTALL> \
      -DVULKAN_LOADER_GENERATED_DIR=<PATH_TO_VULKAN_LOADER>/loader/generated \
    && ninja \
    && ninja install
```

See docker/build.Dockerfile for detailed Ubuntu build instructions.

## Disclaimer

This is not an officially supported Google product. Support and/or new releases may be limited.

