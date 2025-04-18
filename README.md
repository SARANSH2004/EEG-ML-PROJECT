# Brain_EEG
minor project 1

EEG Analysis App with Arduino Integration
Overview
This project is an EEG (Electroencephalography) analysis application designed to work with both multi-channel EEG data and real-time single-channel EEG data captured from an Arduino device. The application performs various signal processing tasks, including bandpower computation, mental state classification, and 3D brain visualization. It also provides recommendations based on dominant brainwave bands (e.g., Alpha, Beta, Gamma) for different cognitive states.

Key Features
Multi-Channel EEG Analysis:

Load and preprocess EEG data from a CSV file.

Train a Random Forest model to classify mental states based on EEG bandpower features.

Visualize the results in 3D space, mapping brain regions and displaying affected channels.

Show detailed recommendations based on dominant EEG bands (e.g., Alpha, Beta).

Real-Time Single-Channel EEG Analysis:

Capture real-time EEG data from an Arduino board using the analogRead function.

Apply filtering to the raw EEG signal using a custom filter.

Compute bandpower and provide recommendations for mental states.

Visualize the signal in real-time with a line chart.

3D Brain Visualization:

Visualize the brain regions in 3D space, highlighting affected regions based on the dominant EEG band.

Customize the brain regions for each subject.

Power Distribution Visualization:

Show the power distribution of each affected EEG channel for a selected subject.

Technologies Used
Arduino: Used to capture real-time EEG data through the analog pin (A0).

Processing: A Java-based language used to handle the real-time data collection from Arduino and save it to CSV files.

Python:

Streamlit: For creating the web-based EEG analysis interface.

Plotly: For creating interactive 3D visualizations of the brain.

SciPy: For signal processing tasks such as Welch's method for computing bandpower.

scikit-learn: For training and evaluating a machine learning model (Random Forest) based on EEG data.

Pandas and NumPy: For data manipulation and numerical computation.

Prerequisites
Before running the project, ensure you have the following:

Python Libraries:

streamlit

pandas

numpy

scipy

scikit-learn

plotly

You can install them using pip:

bash
Copy
Edit
pip install streamlit pandas numpy scipy scikit-learn plotly
Arduino IDE:

Install the Arduino IDE to upload the provided code to the Arduino.

Ensure that you have the proper Arduino board connected (e.g., Maker UNO).

Ensure the correct serial port is selected for communication.

Processing IDE:

Install the Processing IDE for reading real-time data from Arduino and saving it to a CSV file.

Setup and Usage
1. Arduino Setup
Upload the provided Arduino code to the board. The code will continuously read the analog signal from the EEG electrodes and store the filtered signal in a buffer.

The signal is then sent via serial communication to the connected computer.

2. Processing Setup
Use the provided Processing code to read real-time EEG data from the Arduino. The data is saved into a CSV file for later analysis.

3. Streamlit App Setup
Start the Streamlit app by running the following command in the terminal:

bash
Copy
Edit
streamlit run eeg_analysis_app.py
The app will open in your browser, where you can choose between two analysis options:

Multi-Channel Analysis: Upload a CSV file with multi-channel EEG data.

Real-Time Single-Channel Analysis: Upload a CSV file from real-time Arduino EEG data.

4. Multi-Channel Analysis
Upload a CSV file containing multi-channel EEG data, with each channel representing a different EEG electrode.

The app will compute bandpower for each frequency band (Delta, Theta, Alpha, Beta, Gamma) and generate a machine learning model to classify mental states.

The results are displayed in tabbed sections:

Recommendations: Suggestions based on the dominant EEG bands.

3D Brain Visualization: Visual representation of the brain regions with affected channels highlighted.

Channel-wise Power Distribution: Visual display of the power distribution for each affected EEG channel.

5. Real-Time Single-Channel Analysis
Upload a CSV file containing EEG data collected in real-time using Arduino.

The app will compute the bandpower and display recommendations based on the dominant band (e.g., Alpha).

A real-time EEG signal visualization is provided as a line chart.

Code Explanation
Arduino Code:
The Arduino code reads an EEG signal from an electrode connected to pin A0, applies a filter, and sends the data over serial communication. The code uses a timer interrupt to read the data at a specified sample rate and stores the data in a buffer.

Processing Code:
The Processing code reads data from the Arduino, performs a Fast Fourier Transform (FFT) on the signal to extract frequency-domain features, and saves the data to a CSV file. This file is later uploaded into the Streamlit app for further analysis.

Python (Streamlit App):
The app provides the interface for loading CSV files, computing bandpower, training the machine learning model, and visualizing the results. It uses the Welch method for computing bandpower and the Random Forest classifier to classify mental states based on EEG data.

Troubleshooting
Arduino Not Detected: Ensure the correct serial port is selected and that the Arduino is properly connected to the computer.

File Upload Issues: Make sure the uploaded CSV file is correctly formatted with the necessary columns (e.g., EEG Signal, Timestamp, Subject).

Model Training Errors: Ensure the CSV file contains sufficient data for training the model. The app will show an error message if no valid data is found.

Future Enhancements
Real-Time Visualization: Enhance the real-time visualization of the EEG signal from Arduino.

More Advanced Signal Processing: Implement more advanced signal processing techniques such as wavelet transforms.

Extended Machine Learning Models: Implement additional models for better classification accuracy and multi-class predictions.


