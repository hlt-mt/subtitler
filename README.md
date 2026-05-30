# subtitler
The FBK pipeline to get translated subtitles from an audio file. It is structured as a webservice that receives an audio file in a source language and generate subtitles in a target language.

## Requirements

The subtitler system requires:
1. a GPU card (tested on Tesla T4 16 GB)
2. a Linux OS (tested on Ubuntu 22.04, with nvidia-driver 580.95 e CUDA 13.0)
3. a working docker installation (tested with version 29.1.4)
4. a python3 installation


## Download

The following files are to be downloaded:
1. the HuggingFace cache archive [cache_huggingface.tar.gz (11.5 GB)](https://fbk.sharepoint.com/:u:/s/MTUnit/IQCPmGMLVcCoR7yyfpCfrK-GAXFjaRjMU71Z_oNkCVrv0iA?e=l9Aeal)
2. the SHAS and WHISPER cache archive [cache_shas-whisper.tar.gz (3.2 GB)](https://fbk.sharepoint.com/:u:/s/MTUnit/IQBZc9bKSI-HQoHluxjdLcgOAdynPSb-dokQk6-hht9DHLQ?e=XvcQSs)
3. the adapted MADLAD model archive [model_content.tar.gz (22.3 MB)](https://fbk.sharepoint.com/:u:/s/MTUnit/IQCirQvgZepNRZDFFF2qqzC6AbfDwKh_9NNEt3gpbAzAOco?e=o3JVGK)
4. the docker image SHHE v5.1 [image.shhe_v5-1.tar.gz (7.4 GB)](https://fbk.sharepoint.com/:u:/s/MTUnit/IQAJXMTrSn6ZS4vFlFQ-pwEmAc-dkH7O2Hr0R11CYVoRYhU?e=VUfeEj)
5. the docker image WHMA v5.1 [image.whma_v5-1.tar.gz (8.6 GB)](https://fbk.sharepoint.com/:u:/s/MTUnit/IQAcROjBLY0qTpCr7LSMDlRBAUaBE3ixpEwR9Ask0StkK4I?e=tU8GDP)
6. the docker image sensei_backend v1.0 [image.sensei_backend__v1_0.tar.gz (0.3 GB)](https://fbk.sharepoint.com/:u:/s/MTUnit/IQCmkbaK9yzcQqOGW0SIIuTYAe5d-0JVUiUTMkdWRa8uXuw?e=w7SHOy)
7. the docker image sensei_gui v1.0 [image.sensei_gui__v1_0.tar.gz (0.2 GB)](https://fbk.sharepoint.com/:u:/s/MTUnit/IQA1xOuMyMXmRqm7xKrDtg9qAd4eJ80BBwp0FppRB2KYF1o?e=oWohus)
8. the software [sw.tar.gz (0.02 GB)](https://fbk.sharepoint.com/:u:/s/MTUnit/IQChqyMJutSVS53KUtR6EAjIAUFRtY2cTBEBTkb-7LtvOwQ?e=2xmQmP)



## Installation

### Add docker images
Add the four dowloaded docker images to the docker environment with the following commands:
```
docker load < image.shhe-v5-1.tar.gz
docker load < image.whma-v5-1.tar.gz
docker load < image.sensei_backend__v1_0.tar.gz
docker load < image.sensei_gui__v1_0.tar.gz
```


### Add cache models
```
cd $HOME/.cache
tar xvfz cache_huggingface.tar.gz
tar xvfz cache_shas-whisper.tar.gz
```



### Add software and adapted model
Create a directory (p.es. $HOME/subtitler) and extract there bothe the adapted MADALA models and the software:
```
mkdir -p $HOME/subtitler
cd $HOME/subtitler
tar xvfz sw.tar.gz
tar xvfz model_content.tar.gz
```


## Usage
The following tre script are utilzed to manage the subtitler pipeline:

1. DO_FBK-subtitler_start.sh to start the system
```
bash DO_FBK-subtitler_start.sh
```

2. DO_FBK-subtitler_end.sh to end the system
```
bash DO_FBK-subtitler_end.sh
```

3. DO_FBK-subtitler_check.sh to check if the system is running
```
bash DO_FBK-subtitler_check.sh
```
