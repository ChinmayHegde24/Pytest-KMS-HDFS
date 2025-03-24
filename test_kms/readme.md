# This is the main directory for running KMS API functionality tests

## Structure
```
test_kms/
├── test_keys.py       
├── test_keyDetails.py 
├── test_keyOps.py    
├── conftest.py       
├── utils.py
```

## Extra features and functionalities used:
  **Parametrization :** for running multiple test cases handling same functionality in single method
  
  **fetch_logs      :** fetches errors or exception from logs when something goes wrong
  
  **cleanup         :** cleaning of all resources used while testing ensuring re-runs of test cases


## conftest.py
Special file used to define fixtures, and shared configurations that pytest can automatically discover and can be used across tests.
Pytest automatically loads this file
Thus helps in code reusability

## utils.py
consists of helper functions or classes used in tests
need to import where it needs to be used

## test_keys.py 
Handles key creation operation
has a class TestKeyManagement consisting of two methods 
  **1.test_create_key          :**  used to create key with necessary payload ,checks for error in that & cleans up created key
  
  **2.test_key_name_validation :**  validates creation of key with different valid and invalid name format

similarly different kind of validation can be done upon the key

## test_keyDetails.py
Handles retrieval of key related data
has a class TestKeyDetails consisting of 3 methods
  **1.test_get_key_names    :** here it fetches all the created keys, and checks the presence of created key
  
  **2.test_get_key_metadata :** checks for the metadata of existent key and non existent key and validates the response
  
  **3.test_get_key_versions :** checks for keyversions of existent key and non existent key

## test_keyOps.py
Handles operation on keys
TestKeyOperations class with 4 methods
  **1.test_temp_key               :**   creation of temporary key used for further roll-over functionality
  
  **2.test_roll_over_key          :**   handles proper rolling over of key
  
  **3.test_roll_over_new_material :**   checks whether roll overed key has new material or not
  
  **4.test_generate_data_key_and_decrypt :** handles two function
  i. Generation of data key from EZ key and checks for presence of EDEK and DEK 
  ii.Decryption of EDEK to get back DEK 
               
