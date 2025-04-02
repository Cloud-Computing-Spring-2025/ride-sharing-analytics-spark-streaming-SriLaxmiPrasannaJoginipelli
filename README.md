# Ride-Sharing Analytics with Apache Spark Streaming

## Objective
This project uses Apache Spark Structured Streaming to analyze ride-sharing data in real-time. In order to get insights like average distances, windowed fare aggregation, and total fares, streaming ride-sharing data must be processed and analyzed.

## Dependencies
Ensure the following dependencies are installed before running the scripts:
```sh
pip install faker
pip install pyspark
```
Additionally, the data_generator.py script is responsible for generating live ride event data, which is used in the streaming pipeline.

```sh 
python data_generator.py
```

## Task 1: Real-Time Data Ingestion
```sh
python task1.py
```


**Objective:**
- Simulates ride-sharing data using a socket stream.
- Reads incoming ride events and parses JSON data.
- Saves parsed data as CSV files for further processing.

## Task 2: Driver-Level Aggregations
```sh
python task2.py
```

**Objective:**
- Reads streaming ride data from Task 1.
- Performs real-time aggregations on fare amounts and distances per driver.
- Saves aggregated results in batches to CSV files.

## Task 3: Windowed Fare Aggregation
```sh
python task3.py
```

**Objective:**
- Reads streaming data.
- Computes total fare within a 5-minute sliding window.
- Saves windowed fare aggregates to CSV files.

## Difficulties Faced
- **Data Source Constraints:** The socket source used in Spark Structured Streaming does not support fault tolerance.
- **Output Mode Issues:** `update` mode is not supported for CSV; required using `foreachBatch` for batch-wise processing.
- **Timestamp Handling:** Needed proper conversion and watermarking to enable time-windowed aggregations.

## Outputs
The processed data is saved in the `output/` directory:
- **Task 1:** `output/task1/parsed_data/` (Raw parsed ride data)
- **Task 2:** `output/task2/` (Driver-level fare and distance aggregations)
- **Task 3:** `output/task3/` (Sliding window fare aggregations)

- **Task 1 Output**
  
- ![image](https://github.com/user-attachments/assets/1a315c79-2f53-4a63-85f4-a1442d84aef6)

- **Task 2 Output**

- ![image](https://github.com/user-attachments/assets/cb697884-a396-4bdf-8dad-e573ec65f838)

- **Task 3 Output**

- ![image](https://github.com/user-attachments/assets/4e499c26-db12-40e2-a38d-c2c8b97d36a6)

- **From Console**

- ![image](https://github.com/user-attachments/assets/08834626-d5eb-43df-95a2-640d91e59e8e)






