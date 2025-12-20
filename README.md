# MedGuard-AI: Anomaly Detection System for Healthcare

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)](https://www.tensorflow.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-latest-green)](https://scikit-learn.org/)


---

MedGuard-AI is an advanced anomaly detection system designed for healthcare applications. It utilizes multiple machine learning algorithms to detect anomalies in both network traffic and patient health data, providing comprehensive security and patient monitoring capabilities.

## Features

### 🔒 Network Anomaly Detection
- Multi-algorithm approach (Isolation Forest, One-Class SVM, Local Outlier Factor, Autoencoder)
- Real-time network traffic analysis
- Automated email alerts for security threats
- Visualization of anomalous patterns
- Ensemble voting for improved accuracy

### 🏥 Patient Health Monitoring
- Real-time vital signs monitoring
- Anomaly detection in patient health metrics
- Surgery simulation with continuous monitoring
- Automated alerts for critical patient conditions
- Support for multiple health parameters

## Architecture

The system employs an ensemble learning approach combining four powerful anomaly detection algorithms:

1. **Isolation Forest** - Efficient for high-dimensional datasets
2. **One-Class SVM** - Effective boundary detection
3. **Local Outlier Factor** - Density-based anomaly detection
4. **Autoencoder** (Network only) - Deep learning-based reconstruction error analysis

## Installation

### Prerequisites
- Python 3.8 or higher
- pip package manager

### Setup

1. Clone the repository:
```bash
git clone https://github.com/yourusername/medguard-ai.git
cd medguard-ai
```

2. Install required dependencies:
```bash
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow
```

### Required Libraries
```
numpy
pandas
matplotlib
seaborn
scikit-learn
tensorflow
smtplib (built-in)
email (built-in)
```

## Repository Structure
```
medguard-ai/
│
├── README.md
├── requirements.txt
├── MedGuard_AI_Notebook.ipynb
│
├── data/
│   ├── network_data.csv
│   └── public_health.csv
│
├── outputs/
│   ├── network_anomalies_detected.csv
│   ├── detected_anomalies.csv
│   └── surgery_patient_*_anomalies.csv
│
└── visualizations/
    ├── network_anomalies.png
    └── patient_anomalies.png
```

## Usage

### Network Anomaly Detection
```python
from network_anomaly_detector import NetworkAnomalyDetector

# Initialize detector
detector = NetworkAnomalyDetector()

# Run analysis
network_df = detector.run_network_analysis(
    input_file='network_data.csv',
    output_file='network_anomalies_detected.csv'
)
```

**Required CSV Columns:**
- `Source_IP`
- `Destination_IP`
- `Protocol`
- `Packet_Size`
- `Duration`
- `Flags`

### Patient Health Monitoring
```python
from patient_health_monitor import PatientHealthMonitor

# Initialize monitor
monitor = PatientHealthMonitor()

# Run healthcare analysis
patient_df, anomalies = monitor.run_healthcare_analysis()

# Run surgery simulation
surgery_df, surgery_anomalies = monitor.run_surgery_simulation(time_delay=0)
```

**CSV Format:**
The system automatically detects numeric columns in your CSV file for anomaly detection. Include a `Patient_ID` column for patient identification.

## Configuration

### Email Alerts

To enable email alerts, update the email configuration in the respective classes:
```python
self.email_config = {
    "sender_email": "your-email@gmail.com",
    "receiver_email": "recipient@gmail.com",
    "password": "your-app-password",
    "smtp_server": "smtp.gmail.com",
    "smtp_port": 587
}
```

**Note:** For Gmail, use an [App Password](https://support.google.com/accounts/answer/185833) instead of your regular password.

## Output Files

### Network Analysis
- `network_anomalies_detected.csv` - Detected network anomalies
- `network_anomalies.png` - Visualization of results

### Patient Health Analysis
- `detected_anomalies.csv` - Patient health anomalies
- `patient_anomalies.png` - Visualization of results
- `surgery_patient_*_anomalies.csv` - Surgery-specific anomalies

## Model Performance

The system uses an ensemble approach with majority voting:
- An instance is flagged as anomalous if at least 2 out of 3 (or 3 out of 4 for network) algorithms detect it as an anomaly
- Contamination parameter set to 5% (adjustable)
- F1 scores and confusion matrices available when ground truth is provided

## Visualization

The system generates comprehensive visualizations including:
- PCA-reduced 2D scatter plots for each algorithm
- Ensemble model results
- Model correlation heatmaps
- Autoencoder training history (network only)
- Anomaly distribution by protocol/flags
- Packet size and duration distributions

## Alert System

### Network Alerts
Triggered when:
- A source IP generates 3+ anomalous traffic patterns
- Includes details on protocol, packet sizes, and duration

### Patient Health Alerts
Triggered when:
- Vital signs show anomalous patterns
- Critical thresholds are exceeded
- Real-time monitoring detects irregularities

## Customization

### Adjusting Contamination Rate
```python
self.isolation_forest = IsolationForest(contamination=0.05, random_state=42)
```

### Modifying Alert Thresholds
```python
if count >= 3:  # Change threshold value
    self.send_email_alert(subject, message)
```

### Adding Custom Features
Add new features to the feature list in the respective detection methods.

## Limitations

- Email alerts are commented out by default for safety
- Requires properly formatted CSV input files
- Performance depends on data quality and feature selection
- Real-time monitoring simulation may not reflect actual system performance


## Future Enhancements

- [ ] Integration with real-time data streams
- [ ] Deep learning models for time-series analysis
- [ ] Dashboard for real-time monitoring
- [ ] Mobile app integration
- [ ] Multi-patient concurrent monitoring
- [ ] Advanced threat intelligence for network security
- [ ] Integration with hospital information systems


## Disclaimer

**Important:** This system is designed for research and educational purposes. It should not be used as the sole basis for medical decisions or critical security infrastructure without proper validation, testing, and regulatory approval.

## Contact

For questions, suggestions, or collaboration opportunities:

- **GitHub Issues:** [Create an issue](https://github.com/AhzyUmair/medguard-ai/issues)
- **Email:** ahzamumair2003@gmail.com

## Acknowledgments

- scikit-learn community for excellent machine learning tools
- TensorFlow team for the deep learning framework
- Healthcare professionals who provided domain expertise
- Open-source community for various libraries and tools

---

**Made with ❤️ for healthcare security and patient safety**
