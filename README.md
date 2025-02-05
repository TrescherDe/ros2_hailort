# HailoRT with Python 3.12 in ROS2 Jazzy

## Overview
This repository documents the process of setting up HailoRT with Python 3.12 for use in ROS2 Jazzy. The setup is tested on a Raspberry Pi 5 with the AI Hat (Hailo 8L, 13 TOPS).

# Cloning and Building HailoRT
To get started, clone the HailoRT repository and checkout version 4.20.0:
## Clone the repository
```
git clone https://github.com/hailo-ai/hailort.git
cd hailort
```
## Fetch available tags
```
git fetch --tags
```
## Checkout the required version
```
git checkout tags/v4.20.0 -b hailort-4.20.0
```

# Build and Install HailoRT
```
Run the following command to build and install HailoRT:
cmake -S. -Bbuild -DCMAKE_BUILD_TYPE=Release && sudo cmake --build build --config release --target install
```
# Build Python 3.12 Wheel
Navigate to the appropriate directory and build the wheel file:
```
cd hailort/hailort/libhailort/bindings/python/platform/
python3 setup.py bdist_wheel
```

# Setup Virtual Environment
Create and activate a Python virtual environment:
```
python3 -m venv hailort_venv
source hailort_venv/bin/activate
```

# Install the Built Wheel
After activating the virtual environment, navigate to the dist directory and install the wheel file using pip:
```
cd hailort/hailort/libhailort/bindings/python/platform/dist/
pip install hailort-4.20.0-cp312-cp312-linux_aarch64.whl
```
