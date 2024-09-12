## Method for Splitting the DeepShip Dataset

### :white_check_mark: Welcome to this repository. :smiley:
- Underwater acoustic target recognition using deep learning is gaining increasing attention, but data collection is often costly due to the unique nature of the data. Although the [DeepShip](https://www.sciencedirect.com/science/article/pii/S0957417421007016) dataset is widely used, its training and test set splitting method has not been disclosed, making it difficult to compare existing methods effectively. To address this, we plan to publish our data splitting method to serve as a reference for future research.

### :white_check_mark: Papers Adopting this Splitting Method
- [Paper 1](https://www.sciencedirect.com/science/article/pii/S0003682X2300350X): Zhu P, Zhang Y, Huang Y, et al. Underwater acoustic target recognition based on spectrum component analysis of ship radiated noise[J]. Applied Acoustics, 2023.
- [Paper 2](https://ieeexplore.ieee.org/document/10305190): Zhu P, Zhang Y, Huang Y, et al. SFC-Sup: Robust Two-Stage Underwater Acoustic Target Recognition Method Based on Supervised Contrastive Learning[J]. IEEE Transactions on Geoscience and Remote Sensing, 2023.
- [Paper 3](https://ieeexplore.ieee.org/document/10599169): Lin B , Gao L , Zhu P ,et al. An Underwater Acoustic Target Recognition Method Based on Iterative Short-Time Fourier Transform[J]. IEEE Sensors Journal, 2024.

###  :white_check_mark: Statement
- We need to declare several details: First, the splitting of the data was done randomly, without any prior knowledge. We hope to conduct comparisons based on this fair approach. Secondly, we strive to closely follow the detailed guidelines provided in the [DeepShip](https://www.sciencedirect.com/science/article/pii/S0957417421007016) dataset paper.

### :white_check_mark: Dataset Splitting Steps
- **Download the DeepShip Dataset:**
  Since we are not the original authors and do not own the copyright, we cannot directly share this dataset. To download it, please refer to the original authors' guidance in this [issue](https://github.com/irfankamboh/DeepShip/issues/1#issuecomment-1378942555).
- **Marine Environmental Noise:** The original paper mentioned the use of marine environmental noises but did not provide details. We have supplemented this with our own collected noise data, which you can download through this [link](https://pan.baidu.com/s/1KlMZC8zxI7fgMPSSJnt30A) (Extraction code:8448).
- **Training and Testing Files:** The `test.txt` and `train.txt` files indicate how the original recordings are split. These files reference complete recordings that have not been segmented into equal-sized samples.
- **Segmentation Script:** Use the `code.ipynb` script to split and segment the dataset. After organizing the downloaded dataset in the `your_dir/DeepShip/…` format, set `audio_path` to `your_dir` and specify paths for the `train.txt` and `test.txt` files.
- **Segmentation Parameters:** Define `audlen` for sample length and `audstr` for the offset between segments. For example, setting `audstr` to `32000*3` ensures no overlap between samples. Running `code.ipynb` will produce the segmented results.

###  :white_check_mark: Dataset Splitting Results
- When the category of marine environmental noise is used and `audstr` is set to `32000*1`, the spliting results are as follows:
<div align=center>
  <img src="https://github.com/ZhuPengsen/Method-for-Splitting-the-DeepShip-Dataset/blob/main/statisstics1.png" width="600px">
</div>

- When `audstr` is set to `32000*3` and the category of marine environmental noise is excluded, the spliting results are as follows:
<div align=center>
  <img src="https://github.com/ZhuPengsen/Method-for-Splitting-the-DeepShip-Dataset/blob/main/statisstics2.png" width="600px">
</div>

###  :white_check_mark: Something Else
- Based on our experimental experience, marine environmental noises are relatively easy to distinguish. Therefore, we suggest using only four types of ship radiated noise to simplify the training process. Additionally, setting the sample overlap to zero (`audstr=32000*3`) is recommended to reduce the computational load.

###  :white_check_mark: At Last
- I hope this dataset splitting method will be helpful to everyone :smiley:.
