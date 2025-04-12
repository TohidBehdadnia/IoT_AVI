# DDoS Attack Vector Identification in IoT Networks Using Wavelet Transform and Hybrid Deep Learning

To effectively execute the proposed method outlined in our manuscript, it is essential to first convert the dataset by Yucheng Liu et al., titled "IEEE P2668-Compliant Multi-Layer IoT-DDoS Dataset (IEEE P2668-MLIDD)," available on IEEE Dataport with the DOI: [https://dx.doi.org/10.21227/j0f2-8h67](https://dx.doi.org/10.21227/j0f2-8h67), into CSV format. The resulting files, such as `ICMP.csv`, `TCP.csv`, `UDP.csv`, `HTTP.csv`, `CoAP.csv`, `MQTT.csv` should include headers in the following order: `No`, `Time`, `Source`, `Destination`, `Protocol`, `Length`, `Info`.

Our methodology encompasses four main stages:   

1. **Traffic Capturing Phase:** Start by running `traffic_capture_phase_(sliding_time_windows).py` to capture the network data with sliding time windows.
2. **Feature Extraction Phase:** Next, process the captured data using `feature_extraction_phase_and_normalization_(DWT).py` for wavelet transformation and normalization.
3. **Dataset Preparation:** Generate the training, validation, and testing sets with `trainset_valset_testset_generator_DWT.py`.
4. **Model Training and Testing:** Finally, execute `train_and_test_DL_models_dwt.py` to train and evaluate the deep learning models.

For the code to function correctly, the following Python libraries need to be installed:

- Via pip:
  ```bash
  pip install numpy pandas PyWavelets matplotlib scikit-learn scikit-image seaborn imbalanced-learn optuna
  ```
- Via conda:
  ```bash
  conda install -c cjj3779 tensorflow-gpu
  ```

Ensure that each script is executed in the order listed, as each phase depends on the output from the previous one.
