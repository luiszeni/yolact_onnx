FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04
ENV DEBIAN_FRONTEND noninteractive # This is used because opencv installation asks for location sometimes

RUN apt-get update && apt-get install -y --no-install-recommends \
         build-essential \
         git \
         curl \
         ca-certificates \
         libjpeg-dev \
         libpng-dev \
         python3-pip \
         python3-dev \
         python3-tk \
         python3-setuptools\
         libxkbcommon-x11-0 \
         swig\
         eog\ 
         tmux\
         nano\
         htop\
         wget\
         octave\
         && rm -rf /var/lib/apt/lists/*


# packages that are required in python

RUN pip3 install torch==1.0.1 torchvision==0.2.1 -f https://download.pytorch.org/whl/torch_stable.html
RUN pip3 install onnx==1.4.1 onnxruntime==0.4.0
RUN pip3 install opencv-python==4.2.0.34
RUN pip3 install cython
RUN pip3 install pillow pycocotools matplotlib 
     

# stuff that I think that are useful inside the container.

# enables tmux to use mouse
RUN echo "set -g mouse on" > ~/.tmux.conf

#enable pdb autocomplete
RUN  printf "import rlcompleter\nimport pdb\npdb.Pdb.complete = rlcompleter.Completer(locals()).complete" > ~/.pdbrc

WORKDIR "/root/yolact_onnx/"
