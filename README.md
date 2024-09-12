## Method for Splitting the DeepShip Dataset
- Welcome to this repository. :smiley:

- Underwater acoustic target recognition based on deep learning is gradually drawing widespread attention from researchers. However, due to the unique nature of the data, the cost of collection is usually high.
Although the use of the [DeepShip](https://www.sciencedirect.com/science/article/pii/S0957417421007016) dataset is becoming increasingly popular, the dataset has not disclosed its method for splitting the training and test sets. This situation makes it difficult for existing methods to be effectively compared. Therefore, we plan to publish the data splitting method used in our paper, in order to provide a reference for subsequent research and to facilitate comparative experiments.

### :white_check_mark: Papers Adopting this Splitting Method
- [Paper1](https://www.sciencedirect.com/science/article/pii/S0003682X2300350X): Zhu P, Zhang Y, Huang Y, et al. Underwater acoustic target recognition based on spectrum component analysis of ship radiated noise[J]. Applied Acoustics, 2023, 211: 109552.
- [Paper2](https://ieeexplore.ieee.org/document/10305190): Zhu P, Zhang Y, Huang Y, et al. SFC-Sup: Robust Two-Stage Underwater Acoustic Target Recognition Method Based on Supervised Contrastive Learning[J]. IEEE Transactions on Geoscience and Remote Sensing, 2023.
- [Paper3](https://ieeexplore.ieee.org/document/10599169): Lin B , Gao L , Zhu P ,et al.An Underwater Acoustic Target Recognition Method Based on Iterative Short-Time Fourier Transform[J].IEEE Sensors Journal, 24[2024-09-12].DOI:10.1109/JSEN.2024.3424500.

###  :white_check_mark: Statement
- We need to declare several details: First, the splitting of the data was done randomly, without any prior knowledge. We hope to conduct comparisons based on this fair approach. Secondly, we endeavor to adhere as closely as possible to the detailed information in the [DeepShip](https://www.sciencedirect.com/science/article/pii/S0957417421007016) dataset paper.

### :white_check_mark: Dataset Splitting Steps
- Download the DeepShip dataset. Since we are not the original authors of the dataset and do not own the copyright to it, we cannot directly publish this data. To download the dataset, please refer to the original authors' response to this [issue](https://github.com/irfankamboh/DeepShip/issues/1#issuecomment-1378942555).
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

<div style="text-align: center; font-size: 12px;">
  <table border="1" style="margin: 0 auto;">
    <thead>
      <tr>
        <th></th>
        <th>Train</th>
        <th>Train</th>
        <th>Test</th>
        <th>Test</th>
        <th>Total</th>
        <th>Total</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td></td>
        <td>Sample</td>
        <td>Recording</td>
        <td>Sample</td>
        <td>Recording</td>
        <td>Sample</td>
        <td>Recording</td>
      </tr>
      <tr>
        <td>Cargo</td>
        <td>27482</td>
        <td>78</td>
        <td>10686</td>
        <td>31</td>
        <td>38168</td>
        <td>109</td>
      </tr>
      <tr>
        <td>Passenger Ship</td>
        <td>31545</td>
        <td>120</td>
        <td>14303</td>
        <td>71</td>
        <td>45848</td>
        <td>191</td>
      </tr>
      <tr>
        <td>Tanker</td>
        <td>32330</td>
        <td>158</td>
        <td>11480</td>
        <td>82</td>
        <td>43810</td>
        <td>240</td>
      </tr>
      <tr>
        <td>Tug</td>
        <td>26377</td>
        <td>42</td>
        <td>13965</td>
        <td>27</td>
        <td>40342</td>
        <td>69</td>
      </tr>
      <tr>
        <td>No Background</td>
        <td>117734</td>
        <td>398</td>
        <td>50434</td>
        <td>211</td>
        <td>168168</td>
        <td>609</td>
      </tr>
      <tr>
        <td>Background</td>
        <td>19635</td>
        <td>138</td>
        <td>8133</td>
        <td>59</td>
        <td>27768</td>
        <td>197</td>
      </tr>
      <tr>
        <td>Total</td>
        <td>137369</td>
        <td>536</td>
        <td>58567</td>
        <td>270</td>
        <td>195936</td>
        <td>806</td>
      </tr>
    </tbody>
  </table>
</div>


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
- I hope this dataset splitting method will be helpful to everyone, and I also hope that it will make it more convenient for everyone to conduct comparative experiments :point_left:. May everyone enjoy smooth sailing and fruitful achievements in their research :smiley:.
