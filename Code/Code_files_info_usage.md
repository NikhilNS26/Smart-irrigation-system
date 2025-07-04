# Code info and usage

### This file help to undersatding  implements an edge-AI solution for precision irrigation using a Raspberry Pi Pico W. It includes sensor data acquisition, weather fetching, ET₀ prediction with an MLP model, and MQTT-based logging and control.

Files
-----
## 1. main.py
   • Entry point for the Pico W application  
   • Manages Wi-Fi and secure MQTT connections  
   • Fetches weather data via OpenWeatherMap API  
   • Invokes the ET₀ prediction function  
   • Calculates irrigation needs (ET₀, ETc, pump run time)  
   • Publishes control commands and logs via MQTT  
   • Handles daily sampling, logging to CSV, and loop timing  

## 2. mlp_et0_predictor.py
   • Hard-coded MLP regressor parameters extracted from scikit-learn  
   • Implements feature scaling (StandardScaler logic)  
   • Defines feed-forward inference (ReLU activations, identity output)  
   • Returns a single ET₀ prediction value based on [T₂ₘ₋ₘₐₓ, RH₂ₘ, ALLSKY_SFC_SW_DWN]  

## 3. simple.py
   • Lightweight MQTT client for MicroPython  
   • Implements CONNECT, DISCONNECT, PUBLISH, SUBSCRIBE, PING, and message callbacks  
   • Supports last-will, QoS 0/1, SSL/TLS on port 8883  
   • Used by main.py to handle all MQTT communication  

## 4. Data_processing_code_(optional).ipynb
   • Jupyter notebook for initial data exploration and model development  
   • Includes dataset loading, cleaning, exploratory data analysis (EDA)  
   • Demonstrates feature engineering, scaler fitting, and MLP model selection  
   • Generates the parameters (weights, biases, scaler) embedded in mlp_et0_predictor.py  

## Usage
-----
1. Clone this repository to your Raspberry Pi Pico W project directory.  
2. Copy all four files to the Pico’s filesystem (e.g., via Thonny).  
3. Update Wi-Fi and MQTT credentials in `main.py`.  
4. Ensure `mlp_et0_predictor.py` is named correctly and importable.  
5. Run `main.py`; logs and control commands will flow over MQTT.


