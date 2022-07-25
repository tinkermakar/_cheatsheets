# MongoDB Cheatsheet

## Download/Upload all the collections in a database
    
    1. Download
    
    ```bash
    mongodump -d <database_name> -o <directory_backup>
    ```

    1. Upload
    ```bash
    mongorestore -d <database_name> <directory_backup>
    ```
