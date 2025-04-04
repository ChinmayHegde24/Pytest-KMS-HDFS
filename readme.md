#    KMS API & HDFS Encryption Pytest Suite


This test suite validates REST API endpoints for KMS (Key Management Service) and tests HDFS encryption functionalities including key management and file operations within encryption zones.

**test_kms  :** contains test cases for checking KMS API functionality  

**test_hdfs :** contains test cases for checking hdfs encryption

## 📂 Directory Structure

```
test_directory/
├── test_kms/                # Tests on KMS API
  ├── test_keys.py           # Key creation and key name validation
  ├── test_keyDetails.py     # getKeyName, getKeyMetadata, getKeyVersion checks
  ├── test_keyOps.py         # Key operations: Roll-over, generate DEK, Decrypt EDEK
  ├── conftest.py            # Reusable fixtures and setup
  ├── utils.py               # Utility methods
  ├── readme.md
├── test_hdfs/               # Tests on HDFS encryption cycle
  ├── test_encryption.py     # Full HDFS encryption cycle testing
  ├── test_config.py         # stores all constants and HDFS commands
  ├── conftest.py            # sets up the environment
  ├── readme.md
├── pytest.ini               # Registers custom pytest markers
├── requirements.txt
├── README.md                # This file
```

## ⚙️ Setup Instructions
Bring up KMS,Hadoop containers and any dependent containers using Docker.
Create a virtual environment and install the necessary packages through requirements.txt

## Run test cases

**to run tests in test_kms folder**
> pytest -vs test_kms/

to run with report included
> pytest -vs test_kms/ --html=kms-report.html


**to run tests in test_hdfs folder**

> pytest -vs -k "test_encryption"
or
>pytest -vs test_hdfs/

to run with report included
>pytest -vs test_hdfs/ --html=hdfs-report.html

📌 Notes
Ensure Docker containers for KMS and HDFS are running before executing tests.

Reports generated using --html can be viewed in any browser for detailed test results.




