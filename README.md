# 🚨 Real-Time Fraud Detection

A comprehensive, production-ready fraud detection solution built with modern MLOps practices, featuring real-time streaming, automated model training, and scalable inference pipelines.

## 🏗️ **System Architecture**

```
┌─────────────────┐    ┌──────────────┐    ┌─────────────────┐
│   Transaction   │──▶│    Kafka     │───▶│   Inference     │
│   Producer      │    │   Streaming  │    │   Pipeline      │
└─────────────────┘    └──────────────┘    └─────────────────┘
                              │                      │
                              ▼                      ▼
┌─────────────────┐    ┌──────────────┐    ┌─────────────────┐
│     Airflow     │◄───│   Training   │    │ Fraud Alerts    │
│  Orchestration  │    │   Pipeline   │    │   (Kafka)       │
└─────────────────┘    └──────────────┘    └─────────────────┘
         │                      │
         ▼                      ▼
┌─────────────────┐    ┌──────────────┐
│     MLflow      │    │    MinIO     │
│   Tracking      │    │   Storage    │
└─────────────────┘    └──────────────┘
```

## ✨ **Key Features**

- **Real-Time Processing**: Kafka streaming with Spark for sub-second fraud detection
- **Advanced ML**: XGBoost classifier with SMOTE for class imbalance handling
- **MLOps Excellence**: Airflow orchestration, MLflow tracking, containerized deployment
- **Production Ready**: Comprehensive logging, health monitoring, and data validation

## 🛠️ **Technology Stack**

| Component | Technology | Purpose |
|-----------|------------|---------|
| **Streaming** | Apache Kafka, Confluent Cloud | Real-time data streaming |
| **Processing** | Apache Spark, PySpark | Distributed data processing |
| **ML Framework** | XGBoost, Scikit-learn | Machine learning models |
| **Orchestration** | Apache Airflow | Workflow automation |
| **Tracking** | MLflow | Experiment tracking & model registry |
| **Storage** | MinIO (S3-compatible) | Artifact and model storage |
| **Database** | PostgreSQL | Metadata storage |
| **Containerization** | Docker, Docker Compose | Service deployment |

## 🚀 **Quick Start**

### **Prerequisites**
- Docker & Docker Compose
- 8GB+ RAM
- Internet connection for Confluent Cloud

### **Setup & Run**
```bash
# Clone and navigate
git clone <repository-url>
cd real-time-fraud-detection/src

# Configure environment
cp .env.example .env
# Update Kafka credentials in .env

# Start all services
docker-compose up -d

# Start data pipeline
docker-compose up -d producer
```

### **Access Interfaces**
- **Airflow UI**: http://localhost:8080 (admin/admin)
- **MLflow UI**: http://localhost:5500
- **MinIO Console**: http://localhost:9001 (minio/minio123)

## 📊 **System Components**

### **Transaction Producer**
Generates realistic synthetic transaction data with configurable fraud patterns including account takeover, card testing, merchant collusion, and geographic anomalies (1-2% fraud rate).

### **Model Training Pipeline**
Automated daily training with Kafka data ingestion, feature engineering (temporal, behavioral, monetary), SMOTE for class imbalance, hyperparameter optimization, and MLflow tracking.

### **Real-Time Inference**
Spark Structured Streaming with vectorized prediction using Pandas UDF, configurable fraud threshold, and output to fraud_predictions topic.

## 🔍 **Monitoring**

```bash
# View real-time processing
docker-compose logs -f inference
docker-compose logs -f producer

# Monitor training pipeline
docker-compose logs -f airflow-scheduler
```

## 📋 **Project Structure**

```
src/
├── airflow/                 # Airflow configuration
├── dags/                   # Training workflows
├── producer/               # Transaction generator
├── inference/              # Real-time inference
├── models/                 # Trained model storage
├── config.yaml            # System configuration
├── docker-compose.yml     # Infrastructure setup
└── .env                   # Environment variables
```

## 🚨 **Sample Fraud Alert**

```json
{
  "transaction_id": "uuid-here",
  "user_id": 1234,
  "amount": 2500.00,
  "prediction": 1,
  "confidence": 0.87,
  "timestamp": "2025-06-05T15:30:00Z"
}
```

---

**Built with ❤️ for real-time fraud detection**
