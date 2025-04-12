Supplementary Material to: DDoS Attack Vector Identification in IoT Networks Using Wavelet Transform and Hybrid Deep Learning
===

<a href="https://www.esat.kuleuven.be/electa/research-assistants/00148738">Tohid Behdadnia, Department of Electrical Engineering (ELECTA-EnergyVille), KU Leuven, Leuven, Belgium.</a>

<a href="https://www.esat.kuleuven.be/electa/post-doctoral-researchers/00053284">Klaas Thoelen, Department of Electrical Engineering (ELECTA-EnergyVille), KU Leuven, Leuven, Belgium.</a>

<a href="http://j.mp/jgalfaro">Joaquin Garcia-Alfaro, SAMOVAR, Telecom SudParis, Institut Polytechnique de Paris, 91120 Palaiseau, France.</a>

<a href="https://www.kuleuven.be/wieiswie/en/person/00004317">Geert Deconinck, Department of Electrical Engineering (ELECTA-EnergyVille), KU Leuven, Leuven, Belgium.</a>



## Abstract

We propose an attack identification framework that integrates advanced feature extraction and deep learning (DL) techniques. Our framework enables robust and near real-time identification of DDoS attack vectors across diverse network layers and settings, incorporating those configured with TLS, DTLS, and VPN protocols. Our method utilizes the wavelet transform to extract time-frequency features directly from packet inter-arrival times (PIATs), which are then utilized as the exclusive input to a hybrid DL model that integrates a convolutional neural network (CNN) and a bidirectional long short-term memory (BiLSTM). Contrary to related work methods, our solution validates significant adaptability to variations induced by the establishment of secure sessions, making it particularly suitable for encrypted IoT environments where traditional methods face substantial limitations due to their dependence on flow-level or packet-level features, which encryption protocols obscure, alter, or render inaccessible.


## Experimentation

### Hardware

Training was conducted on two NVIDIA consumer GPUs, a GP102 TITAN Xp and a Tesla T4, using the <a href="https://www.tensorflow.org/">Tensorflow framework</a> and the <a href="https://www.onyxia.sh/">Onyxia Datalab science stack</a>. The Onyxia hardware configuration used to obtain the manuscript results are shown below:

![](img/onyxiasetup.png?raw=true)

### Feature Extraction and Training Code

The code related to this work is available in <a href="https://github.com/TohidBehdadnia/IoT_AVI/blob/main/code/codebase.zip">this ZIP file</a>.

### Reproduction of Results

To effectively reproduce our experimental results, it is essential to first convert the dataset by Yucheng Liu et al., titled "IEEE P2668-Compliant Multi-Layer IoT-DDoS Dataset (IEEE P2668-MLIDD)," available on IEEE Dataport with the DOI: [https://dx.doi.org/10.21227/j0f2-8h67](https://dx.doi.org/10.21227/j0f2-8h67), into CSV format. The resulting files, such as `ICMP.csv`, `TCP.csv`, `UDP.csv`, `HTTP.csv`, `CoAP.csv`, `MQTT.csv` should include headers in the following order: `No`, `Time`, `Source`, `Destination`, `Protocol`, `Length`, `Info`.

Once converted the datasets, conduct the following steps:

1. **Traffic Capturing Phase:** Start by running `traffic_capture_phase_(sliding_time_windows).py` to capture the network data with sliding time windows.
2. **Feature Extraction Phase:** Next, process the captured data using `feature_extraction_phase_and_normalization_(DWT).py` for wavelet transformation and normalization.
3. **Dataset Preparation:** Generate the training, validation, and testing sets with `trainset_valset_testset_generator_DWT.py`.
4. **Model Training and Testing:** Finally, execute `train_and_test_DL_models_dwt.py` to train and evaluate the deep learning models.

Ensure that each script is executed in the order listed, as each phase depends on the output from the previous one.

Our code has been successfully tested with the following Python libraries:

- <a href="https://docs.anaconda.com/miniconda/">Miniconda</a> tensorflow-gpu:
  ```bash
  pip uninstall tensorflow
  conda install -c cjj3779 tensorflow-gpu
  ```
- Additional Python libraries:
  ```bash
  pip install numpy pandas PyWavelets matplotlib scikit-learn scikit-image seaborn imbalanced-learn optuna
  ```

## References

If using this code for research purposes, please cite:

Tohid Behdadnia, Klaas Thoelen, Joaquin Garcia-Alfaro, Geert Deconinck. DDoS Attack Vector Identification in IoT Networks Using Wavelet Transform and Hybrid Deep Learning. 2025.

```
@misc{BehdadniaEtAl2025ddos-identification,
  title={DDoS Attack Vector Identification in IoT Networks Using Wavelet Transform and Hybrid Deep Learning},
  author={Behdadnia, Tohid and Thoelen, Klaas and Garcia-Alfaro, Joaquin and Deconinck, Geert}
  pages={1--12},
  year={2025},
  month={April},
  url={},
}
```




