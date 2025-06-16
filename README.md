# Basic Postgres CDC (Change Data Capture)

This project demonstrates a basic Change Data Capture (CDC) setup using PostgreSQL, Debezium, Apache Kafka, and Confluent Schema Registry. It provides a complete environment for capturing database changes and streaming them to Kafka topics.

## Architecture

The project consists of the following components:

- **PostgreSQL**: Source database with sample inventory data
- **Debezium**: CDC connector that captures database changes
- **Apache Kafka**: Message broker for streaming the changes
- **Zookeeper**: Required for Kafka cluster management
- **Schema Registry**: Manages and validates Avro schemas

## Prerequisites

- Docker
- Docker Compose

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/N-D-Duy/cdc-postgres
   cd cdc-postgres
   ```

2. Start the services:
   ```bash
   docker-compose up -d
   ```

3. Wait for all services to start up (this may take a few minutes)

## Services

- PostgreSQL: `localhost:5432`
  - Username: postgres
  - Password: postgres
  - Database: inventory

- Kafka: 
  - Internal: `kafka:9092`
  - External: `localhost:29092`

- Schema Registry: `localhost:8081`

- Debezium Connect: `localhost:8083`

## Project Structure

```
.
├── docker-compose.yml
├── postgres/
│   └── Dockerfile
├── kafka/
│   └── Dockerfile
├── schema-registry/
│   └── Dockerfile
├── debezium/
│   └── Dockerfile
└── scripts/
    └── init-db.sql
```

## Usage

1. The PostgreSQL database is initialized with sample data from `scripts/init-db.sql`
2. Debezium connector captures changes from PostgreSQL
3. Changes are streamed to Kafka topics
4. Schema Registry ensures data consistency

## Monitoring

- Kafka Connect UI: `http://localhost:8083`
- Schema Registry UI: `http://localhost:8081`

## Stopping the Services

To stop all services:
```bash
docker-compose down
```

To stop and remove all data (including volumes):
```bash
docker-compose down -v
```

## Contributing

Contributions are welcome! Please feel free to submit a pull request.

## Author

- [@N-D-Duy](https://github.com/N-D-Duy)
