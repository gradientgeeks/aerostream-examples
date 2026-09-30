# AeroStream Example Applications

[![License](https://img.shields.io/badge/License-Apache--2.0-blue.svg)](LICENSE)
[![GitHub Repo](https://img.shields.io/badge/Repo-gradientgeeks%2Faerostream--examples-blue?logo=github)](https://github.com/gradientgeeks/aerostream-examples)
[![AeroStream](https://img.shields.io/badge/AeroStream-Core_Engine-00E5FF)](https://github.com/gradientgeeks/aerostream)

Production-ready example applications demonstrating how to build streaming and event-driven applications with **AeroStream** across multiple programming languages and frameworks.

Because AeroStream natively implements the **Apache Kafka Wire Protocol** (port `9092`) alongside its own ultra-low-latency **Zero-Copy Binary Protocol** (port `9091`), you can connect using standard ecosystem client libraries as well as zero-overhead native client SDKs.

---

## Available Examples

| Application | Language / Platform | Client / Library | Protocol Used | Key Features |
| :--- | :--- | :--- | :--- | :--- |
| [**Java App**](java-app/) | Java 17+ / Maven | `org.apache.kafka:kafka-clients` | Kafka Wire (`:9092`) | AdminClient, KafkaProducer, KafkaConsumer with consumer groups |
| [**Go App**](go-app/) | Go 1.24+ | Pure Go (Zero-CGO) | Kafka Wire (`:9092`) & Native (`:9091`) | ApiVersions, Metadata, CRC32 Produce/Fetch, Native binary streaming |
| [**Rust App**](rust-app/) | Rust 1.80+ / Tokio | Asynchronous Rust | Kafka Wire (`:9092`) & Native (`:9091`) | Tokio async framing, ApiVersions, Metadata, Produce, Fetch, Native ACK |
| [**.NET App**](dotnet-app/) | C# / .NET 8.0 | `Confluent.Kafka` | Kafka Wire (`:9092`) | Enterprise event streaming in C# |
| [**FastAPI App**](fastapi-app/) | Python 3.10+ | `confluent-kafka` | Kafka Wire (`:9092`) | Webhooks & HTTP-to-Kafka ingestion gateway |

---

## Quick Start: Testing the Examples

### 1. Start AeroStream Locally

Using the official all-in-one container:
```bash
docker run -d --name aerostream \
  -p 9091:9091 -p 9092:9092 -p 9001:9001 -p 8001:8001 -p 7001:7001 \
  quay.io/gradientgeeks/aerostream:latest
```

Or if building from source in the primary [aerostream](https://github.com/gradientgeeks/aerostream) repository:
```bash
make start
```

### 2. Run the Examples

#### Java Application
```bash
cd java-app
mvn compile exec:java
```

#### Go Application
```bash
cd go-app
go run main.go
```

#### Rust Application
```bash
cd rust-app
cargo run
```

#### .NET Application
```bash
cd dotnet-app
dotnet run
```

#### FastAPI Webhook Ingestion Service
```bash
cd fastapi-app
pip install -r requirements.txt
uvicorn main:app --reload --port 8000
```

---

## License

This repository is licensed under the Apache License 2.0. See [LICENSE](LICENSE) for details.
