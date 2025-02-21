# 3D-Speaker

Dataset introduction and download address: [3D-Speaker](https://3dspeaker.github.io/) <br>
Related paper address: [3D-Speaker](https://arxiv.org/pdf/2306.15354.pdf)

### Running experiments
``` sh
# Speaker verification: ERes2Net on 3D Speaker
cd egs/3dspeaker/sv-eres2net/
bash run.sh
# Speaker verification: CAM++ on 3D Speaker
cd egs/3dspeaker/sv-cam++/
bash run.sh
# Self-supervised speaker verification: RDINO on 3D Speaker
cd egs/3dspeaker/sv-rdino/
bash run.sh
```
 Performance of systems (EER) on different tracks.
| Model | Params | Cross-Device | Cross-Distance | Cross-Dialect |
|:-----:|:------:| :------:|:------:|:------:|
| ECAPA-TDNN | 20.8M | 8.87% | 12.26% | 14.53% |
| CAM++ Base | 7.2M | 7.75% | 11.29% | 13.44% |
| ERes2Net Base | 4.6M | 7.06% | 9.95% | 12.76% |
| ERes2Net Large | 18.3M | 6.55% | 9.45% | 11.01% |
| RDINO | 45.44M | 20.41% | 21.92% | 25.53% |

### Inference using pretrained models from Modelscope
All pretrained models will be released on [Modelscope](https://www.modelscope.cn/models?page=1&tasks=speaker-verification&type=audio). <br>

``` sh
# Install modelscope
pip install modelscope
# CAM++ trained on 3D-Speaker
TO DO
# CAM++ trained on 200k labeled speakers
model_id=damo/speech_campplus_sv_zh-cn_16k-common
# ERes2Net trained on 3D-Speaker
model_id=damo/speech_eres2net_large_sv_zh-cn_3dspeaker_16k
# ERes2Net trained on 200k labeled speakers
mode_id=damo/speech_eres2net_sv_zh-cn_16k-common
# Run CAM++ or ERes2Net inference
python speakerlab/bin/infer_sv.py --model_id $model_id --wavs $wav_path

# RDINO trained on 3D-Speaker
model_id=damo/speech_rdino_ecapa_tdnn_sv_zh-cn_3dspeaker_16k
# Run RDINO inference
python speakerlab/bin/infer_sv_rdino.py --model_id $model_id --wavs $wav_path
```

## Citations
If you are using 3D Speaker dataset in your research, please cite: 
```BibTeX
@inproceedings{chen2023pushing,
  title={3D-Speaker: A Large-Scale Multi-Device, Multi-Distance, and Multi-Dialect Corpus for Speech Representation Disentanglement},
  author={Siqi Zheng, Luyao Cheng, Yafeng Chen, Hui Wang and Qian Chen},
  url={https://arxiv.org/pdf/2306.15354.pdf},
  year={2023}
}
```

