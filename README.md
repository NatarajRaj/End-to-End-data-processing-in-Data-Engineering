Real-Time Data Pipeline

This project is a real-time data processing pipeline built using a variety of technologies to orchestrate and process data at scale. The pipeline fetches random user data from the randomuser.me API, stores it in a PostgreSQL database, processes the data using Apache Kafka, Spark, and finally stores the processed data in Cassandra.

Components

* Data Source:
o randomuser.me API: Used to generate random user data. The API provides JSON data that mimics user information like name, address, email, etc.
o PostgreSQL Database: Stores the fetched data from the API for processing.

* Orchestration:
o Apache Airflow: Manages the execution and scheduling of workflows (DAGs), from data fetching to the processing pipeline.

* Streaming & Messaging:
o Apache Kafka & Zookeeper: Kafka is used for streaming data in real-time, and Zookeeper is used for managing Kafka brokers.
o Control Center & Schema Registry: Helps monitor Kafka streams and manage the schema for Kafka topics.

* Data Processing:
o Apache Spark: A distributed processing engine to process large amounts of real-time data from Kafka streams.

* Data Storage:
o Cassandra: A distributed NoSQL database that stores the processed data for further analysis.

Technologies Used
* Apache Airflow: Orchestrating and scheduling data pipeline tasks.
* Python: For scripting and logic execution in the pipeline.
* Apache Kafka: Real-time messaging and streaming.
* Apache Zookeeper: Ensures high availability and coordination of Kafka brokers.
* Apache Spark: Processing engine for real-time data streaming.
* Cassandra: Storage for processed data.
* PostgreSQL: Storing initial data fetched from the API.
* Docker: Containerization of all services for easy deployment and scalability.
  
How the Pipeline Works
1. Data Fetching (API ? PostgreSQL):
o Apache Airflow triggers a task that fetches data from the randomuser.me API at a scheduled interval.
o The fetched data is stored in a PostgreSQL database for further processing.
2. Kafka Streaming (PostgreSQL ? Kafka):
o The data in PostgreSQL is streamed to Apache Kafka, acting as a message broker.
o The data is published to a Kafka topic, which is consumed by Spark for processing.
3. Real-Time Data Processing (Kafka ? Spark):
o Apache Spark consumes the data from the Kafka topic, processes it in real-time, and performs any necessary transformations.
4. Data Storage (Spark ? Cassandra):
o The processed data is stored in a Cassandra database for further use or analysis.

Docker Compose Setup
The project is containerized using Docker Compose. The following services are included in the docker-compose.yml file:
* Zookeeper: Manages Kafka brokers.
* Kafka: Messaging system for real-time data streaming.
* Schema Registry: Manages the schema for Kafka topics.
* Airflow: Orchestrates the pipeline tasks.
* Spark: Processes the data in real-time.
* Cassandra: Stores the final processed data.
* PostgreSQL: Stores initial data from the API.

  
Credits:

This project was developed by Yusuf Ganiyu (@airscholar). The concept and tech stack come from real-time data processing requirements and the integration of various tools to achieve seamless data flow and transformation.

