Supplementary Material to: DDoS Attack Vector Identification in IoT Networks Using Wavelet Transform and Hybrid Deep Learning
===

<a href="https://www.esat.kuleuven.be/electa/research-assistants/00148738">Tohid Behdadnia, Department of Electrical Engineering (ELECTA-EnergyVille), KU Leuven, Leuven, Belgium</a>

<a href="https://www.esat.kuleuven.be/electa/post-doctoral-researchers/00053284">Klaas Thoelen, Department of Electrical Engineering (ELECTA-EnergyVille), KU Leuven, Leuven, Belgium</a>

<a href="http://j.mp/jgalfaro">Joaquin Garcia-Alfaro, SAMOVAR, Telecom SudParis, Institut Polytechnique de Paris, 91120 Palaiseau, France</a>

<a href="https://www.kuleuven.be/wieiswie/en/person/00004317">Geert Deconinck, Department of Electrical Engineering (ELECTA-EnergyVille), KU Leuven, Leuven, Belgium</a>



## Abstract

We propose an attack identification framework that integrates advanced feature extraction and deep learning (DL) techniques. Our framework enables robust and near real-time identification of DDoS attack vectors across diverse network layers and settings, incorporating those configured with TLS, DTLS, and VPN protocols. Our method utilizes the wavelet transform to extract time-frequency features directly from packet inter-arrival times (PIATs), which are then utilized as the exclusive input to a hybrid DL model that integrates a convolutional neural network (CNN) and a bidirectional long short-term memory (BiLSTM). Contrary to related work methods, our solution validates significant adaptability to variations induced by the establishment of secure sessions, making it particularly suitable for encrypted IoT environments where traditional methods face substantial limitations due to their dependence on flow-level or packet-level features, which encryption protocols obscure, alter, or render inaccessible.


## Experimentation

### Feature Extraction and Training Code

The feature extraction and training code is available in <a href="https://github.com/TohidBehdadnia/IoT_AVI/blob/main/code/codebase.zip">this ZIP file</a>.

To effectively reproduce our experimental results, it is essential to first convert the dataset by Yucheng Liu et al., titled "IEEE P2668-Compliant Multi-Layer IoT-DDoS Dataset (IEEE P2668-MLIDD)," available on IEEE Dataport with the DOI: [https://dx.doi.org/10.21227/j0f2-8h67](https://dx.doi.org/10.21227/j0f2-8h67), into CSV format. The resulting files, such as `ICMP.csv`, `TCP.csv`, `UDP.csv`, `HTTP.csv`, `CoAP.csv`, `MQTT.csv` should include headers in the following order: `No`, `Time`, `Source`, `Destination`, `Protocol`, `Length`, `Info`. An example is available in <a href="https://drive.google.com/drive/folders/1TgXL2ryIYQFj8j6b75VowWPDdoLauzMH?usp=sharing">this shared folder</a>.

Once obtained the dataset in CSV format, the following steps must be conducted:

1. **Traffic Capturing Phase:** Start by running `traffic_capture_phase_(sliding_time_windows).py` to capture the network data with sliding time windows.
2. **Feature Extraction Phase:** Next, process the captured data using `feature_extraction_phase_and_normalization_(DWT).py` for wavelet transformation and normalization.
3. **Dataset Preparation:** Generate the training, validation, and testing sets with `trainset_valset_testset_generator_DWT.py`.
4. **Model Training and Testing:** Finally, execute `train_and_test_DL_models_dwt.py` to train and evaluate the deep learning models.

Ensure that each script is executed in the order listed, as each phase depends on the output from the previous one.

Our code has been successfully tested with the following <a href="https://docs.anaconda.com/miniconda/">Conda</a> setup and Python libraries:

  ```bash
  # Create a new conda environment with Python 3.12
  conda create -n iotavi_env python=3.12

  # Activate the environment
  conda activate iotavi_env

  # Ensure pip is installed
  conda install anaconda::pip
  ```

  ```bash
  # Remove previous versions of tensorflow
  pip uninstall tensorflow

  # Install conda cjj3779 version of tensorflow-gpu
  conda install -c cjj3779 tensorflow-gpu
  ```

  ```bash
  # Install all other requirements
  pip install numpy pandas PyWavelets matplotlib scikit-learn scikit-image seaborn imbalanced-learn optuna
  ```

### Experimental Results 

Our code has been successfully tested on some NVIDIA GPUs (e.g., NVIDIA A2 and Tesla T4), using the <a href="https://www.tensorflow.org/">Tensorflow framework</a> and the <a href="https://www.onyxia.sh/">Onyxia Datalab science stack</a>. The Onyxia setup to obtain the released results is shown below:

![](img/onyxiasetup.png?raw=true)

## References

If using this code for research purposes, please cite:

Tohid Behdadnia, Klaas Thoelen, Joaquin Garcia-Alfaro, Geert Deconinck. DDoS Attack Vector Identification in IoT Networks Using Wavelet Transform and Hybrid Deep Learning. 2025.

```
@article{BehdadniaEtAl2025ddos-identification,
  title={DDoS Attack Vector Identification in IoT Networks Using Wavelet Transform and Hybrid Deep Learning},
  author={Behdadnia, Tohid and Thoelen, Klaas and Garcia-Alfaro, Joaquin and Deconinck, Geert}
  pages={1--12},
  year={2025},
  month={April},
  url={},
}
```




