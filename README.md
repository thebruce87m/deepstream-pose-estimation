# deepstream-pose-estimation

https://developer.nvidia.com/blog/creating-a-human-pose-estimation-application-with-deepstream-sdk/

https://github.com/NVIDIA-AI-IOT/deepstream_pose_estimation

https://github.com/NVIDIA-AI-IOT/trt_pose


```bash

# Clone the repo
git clone https://github.com/NVIDIA-AI-IOT/deepstream_pose_estimation

cd deepstream_pose_estimation/

# Set the directory that we will copy the repo to in the docker
export WORKDIR=/opt/nvidia/deepstream/deepstream-5.0/sources/apps/sample_apps/deepstream_pose_estimation/

# Run the docker
docker run \
--gpus all \
-it \
--rm \
--net=host \
--ipc=host \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-v $(pwd):${WORKDIR} \
-e DISPLAY=$DISPLAY \
-w ${WORKDIR} \
nvcr.io/nvidia/deepstream:5.0.1-20.09-devel

# Copy the modified OSD library
cp bin/x86/* /opt/nvidia/deepstream/deepstream-5.0/lib/

# Build the code
make

# Make a directory for the output
mkdir output

# Run the code
./deepstream-pose-estimation-app /opt/nvidia/deepstream/deepstream-5.0/samples/streams/sample_720p.h264 ./output/


```
