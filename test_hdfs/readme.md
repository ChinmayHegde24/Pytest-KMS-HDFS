# This is the main directory of testing HDFS encryption cycle 

## Structure
```
test_hdfs/
├── test_encryption.py
├── utils.py              #Utility methods
```
## Extra features
Markers: Markers have been used which helps in running only specific test cases

## `test_encryption.py`
        
 **main highlights :** 
 Encryption zone creation in HDFS 
 Giving permissions to specific user over read write operation on the file present in created Encryption zone (EZ)
 Read-write operation by unauthorised user in EZ

**setup_environment:** 
After bringing up containers some extra things needs to be done before directly running test cases
As HDFS needs to communicate with KMS to fetch key details , adding some KMS_PROPERTY in core-site.xml file
Restarting conatiner to bring new added changes

**get_error_logs :**             fetches logs from both KMS and HDFS container and displays in the case of some errors and exceptions while testing

**run_command :**                method which handles running of all HDFS commands inside container

**test_create_encryption_zone:** here EZ gets created using existing EZ key

**test_grant_permissions     :** granting read-write permission for specific users (i.e HIVE in this case)

**test_hive_user_write_read  :** performing write and read operation inside EZ

**Negative test cases**
**test_unauthorized_write    :** checks write functionality by unauth user (i.e HBASE in this case)
**test_unauthorized_read     :** checks read functionality by unauth user

**test_cleanup               :** final cleanup of EZ and files present in it




