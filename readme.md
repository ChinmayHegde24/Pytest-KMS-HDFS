#     ----------KMS API & HDFS Encryption Pytest Suite-------------


This test suite validates REST API endpoints for KMS (Key Management Service) and tests HDFS encryption functionalities including key management and file operations within encryption zones.

test_kms  : contains test cases for checking KMS API functionality
test_hdfs : contains test cases for checking hdfs encryption

test_directory/
├── test_kms/          : tests on kms API
├── test_hdfs/         : tests on HDFS encryption cycle
├── pytest.ini         : registering custom markers
└── README.md

test_kms/
├── test_keys.py       : checks for successful key creation and key name validation
├── test_keyDetails.py : checks on getKeyName, getKeyMetadata, getKeyVersion
├── test_keyOps.py     : checks on key operation like Roll-over, generate DEK, Decrypt EDEK
├── conftest.py        : for resusability of code
├── utils.py           : utility method

test_hdfs/
├── test_encryption.py : checks on full hdfs encryption cycle


# SetUp

Bring up KMS container and dependent containers
Create one venv and install necessary packages : requests, pytest, docker 
Further Environment setup  done in test suite itself no need to add extra things

# Run test cases

to run tests in test_kms folder 
> pytest -vs test_kms/

to run with report included
> pytest -vs test_kms/ --html=kms-report.html


to run tests in test_hdfs folder

> create one my_key in ranger ui as a refernce key for tests
> set this as KMS URL in UI:  kms://http@host.docker.internal:9292/kms 


Now simply run
> pytest -vs -k "test_encryption"
or
>pytest -vs test_hdfs/

With report >pytest -vs test_hdfs/ --html=hdfs-report.html




