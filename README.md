## Method for Splitting the DeepShip Dataset
- Welcome to this repository. :smiley:

- Underwater acoustic target recognition based on deep learning is gradually drawing widespread attention from researchers. However, due to the unique nature of the data, the cost of collection is usually high.
Although the use of the [DeepShip](https://www.sciencedirect.com/science/article/pii/S0957417421007016) dataset is becoming increasingly popular, the dataset has not disclosed its method for splitting the training and test sets. This situation makes it difficult for existing methods to be effectively compared. Therefore, we plan to publish the data splitting method used in our paper, in order to provide a reference for subsequent research and to facilitate comparative experiments.

### :white_check_mark: Papers Adopting this Splitting Method
- [Paper2](https://ieeexplore.ieee.org/document/10305190): Zhu P, Zhang Y, Huang Y, et al. SFC-Sup: Robust Two-Stage Underwater Acoustic Target Recognition Method Based on Supervised Contrastive Learning[J]. IEEE Transactions on Geoscience and Remote Sensing, 2023.
- [Paper1](https://www.sciencedirect.com/science/article/pii/S0003682X2300350X): Zhu P, Zhang Y, Huang Y, et al. Underwater acoustic target recognition based on spectrum component analysis of ship radiated noise[J]. Applied Acoustics, 2023, 211: 109552.

###  :white_check_mark: Statement
- We need to declare several details: First, the splitting of the data was done randomly, without any prior knowledge. We hope to conduct comparisons based on this fair approach. Secondly, we endeavor to adhere as closely as possible to the detailed information in the [DeepShip](https://www.sciencedirect.com/science/article/pii/S0957417421007016) dataset paper.

### :white_check_mark: Dataset Splitting Steps
- Download the DeepShip dataset from this link, which is the official [address](https://github.com/irfankamboh/DeepShip/issues/1) published by the dataset's authors.
- Although the original paper used marine background noise data, it did not disclose this part. Therefore, we have supplemented it with the marine environmental noise data we collected. You can download it through this [link](https://pan.baidu.com/s/1KlMZC8zxI7fgMPSSJnt30A) (Extraction code:8448).
- The `test.txt` and `train.txt` files represent the outcomes of splitting the original recordings. These files reference specific, intact recordings that have not yet been segmented into equally-sized samples.
- The `code.ipynb` script is responsible for the splitting and segmentation of the dataset. After downloading and organizing the dataset in the `your_dir/DeepShip/…` format, enter `your_dir` into `audio_path` and specify the paths for the two txt files.
- Set the parameters `audlen` and `audstr`, where `audlen` determines the sample length, and `audstr` specifies the offset between segmentation points. For instance, setting `audstr` to `32000*3` ensures that the samples do not overlap. Executing `code.ipynb` produces the segmented results.

###  :white_check_mark: Dataset Splitting Results
- When the category of marine environmental noise is used and `audstr` is set to `32000*1`, the ensuing results will be as follows.

|                      |     Train     |    Train   |     Test     |    Test    |     Total     |    Total    |
|----------------------|:-------------:|:----------:|:------------:|:----------:|:-------------:|:-----------:|
|                      |     Sample    |  Recording |    Sample    |  Recording |     Sample    | Recording   |
| Cargo                |     27482     |     78     |     10686    |     31     |     38168     |     109     |
| Passenger Ship       |     31545     |     120    |     14303    |     71     |     45848     |     191     |
| Tanker               |     32330     |     158    |     11480    |     82     |     43810     |     240     |
| Tug                  |     26377     |     42     |     13965    |     27     |     40342     |     69      |
| No Background        |     117734    |     398    |     50434    |     211    |     168168    |     609     |
| Background           |     19635     |     138    |     8133     |     59     |     27768     |     197     |
| Total                |     137369    |     536    |     58567    |     270    |     195936    |     806     |

- When `audstr` is set to `32000*3` and the category of marine environmental noise is excluded, the resulting data will be as follows.

|                  |     Train    |    Train   |     Test     |    Test    |     Total    |    Total    |
|------------------|:------------:|:----------:|:------------:|:----------:|:------------:|:-----------:|
|                  |    Sample    |  Recording |    Sample    |  Recording |    Sample    | Recording   |
| Cargo            |      9185    |      78    |      3571    |      31    |     12756    |      109    |
| Passenger Ship   |     10555    |     120    |      4794    |      71    |     15349    |      191    |
| Tanker           |     10827    |     158    |      3857    |      82    |     14684    |      240    |
| Tug              |      8804    |      42    |      4662    |      27    |     13466    |      69     |
| Total            |     39371    |     398    |     16884    |     211    |     56255    |      609    |

###  :white_check_mark: Something Else
- Drawing from our experimental experience, marine environmental noises can be easily distinguished. Hence, we recommend using only four types of ship radiated noise to streamline the training process. Furthermore, setting the sample overlap to zero `(audstr=32000*3)` is advisable to lessen the computational load.

### :white_check_mark: Ciation
```bibtex
@article{zhu2023sfc,
  title={SFC-Sup: Robust Two-Stage Underwater Acoustic Target Recognition Method Based on Supervised Contrastive Learning},
  author={Zhu, Pengsen and Zhang, Yonggang and Huang, Yulong and Lin, Boqiang and Zhu, Minwen and Zhao, Kunlong and Zhou, Fuheng},
  journal={IEEE Transactions on Geoscience and Remote Sensing},
  year={2023},
  publisher={IEEE}
}
```

```bibtex
@article{zhu2023underwater,
  title={Underwater acoustic target recognition based on spectrum component analysis of ship radiated noise},
  author={Zhu, Pengsen and Zhang, Yonggang and Huang, Yulong and Zhao, Chengxuan and Zhao, Kunlong and Zhou, Fuheng},
  journal={Applied Acoustics},
  volume={211},
  pages={109552},
  year={2023},
  publisher={Elsevier}
}
```

###  :white_check_mark: At Last
- I hope this data segmentation method will be helpful to everyone, and I also hope that it will make it more convenient for everyone to conduct comparative experiments :point_left:. May everyone enjoy smooth sailing and fruitful achievements in their research :smiley:.
