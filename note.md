# 复现笔记
## 配置
```sh
docker build -f docker/simulation.dockerfile -t quad_swarm_image:v0 --network=host --progress=plain .

docker run --name quad-swarm -itd --privileged --gpus all --network=host \
    -v /tmp/.X11-unix:/tmp/.X11-unix:ro \
    -v /home/dzp/projects/quad-swarm-rl:/workspace/quad-swarm-rl \
    -e DISPLAY=$DISPLAY \
    -e LOCAL_USER_ID="$(id -u)" \
    quad_swarm_image:v0 /bin/bash

docker exec -it quad-swarm /bin/bash

cd /workspace/quad-swarm

pip install -e .
```