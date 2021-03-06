# WESTERN DIGITAL - MyCloud Home - restsdk recovery script
A script to recover data from REST SDK Folder Structure in My Cloud Home (ext4) network hdd.

Thanks a lot to [springfielddatarecovery](https://github.com/springfielddatarecovery/mycloud-restsdk-recovery-script) to share this script opensource.

![alt text](Feature_images_WDCloud.jpg)

WD MyCloud Home offers network HDDs with ONLY ethernet port and a WD Discovery App to connect users to files. In case of badsectors presence or after a breackdown, HDD can appears disconnected in app. After you get an image is with maximum of good sectors from the drive with your best tool, you can mount an ext4 partition used as main volume to store users files.

This script can rebuilt structure and files in original state.

### Configuration confirmed :
Ubuntu 18.04 Python 3.6 already installed

***Original information :***

***Problem:*** *MyCloud devices don't use a simple, flat filesystem like other external drives, they store files with random-seeming names and directory structures. If your MyCloud is not functioning, you will need to read the SQLite database on the device to determine the original file structure.*

***Solution:*** *This script reads the database and a dump of the filesystem and copies the data to another location with the correct filenames and structures. This script is intended for a Linux machine where you already have the file structure and database extracted. This won't work on Windows. I know it's ugly and inefficient, I am new to python. This is tested and working with Python 3.6 on Linux.*

***Notes:*** *SQLite database is stored in /restsdk/data/db/index.db. Inside the DB two main tables appear to be of interest, FILES and ImageTrans. FILES lists each file with a unique ID (primary key) and a ContentID (the name of the file when stored on the filesystem) along with the file name "My important picture.jpg" and some other metadata. I believe ImageTrans is only for thumbnailing purposes but I could be wrong about that. Importantly, the entries in FILES have a "parent" attribute which places each file in a directory structure. This script totally ignores ImageTrans.*


### Change 3 first lines with your own paths :
    #DO NOT ADD SLASHES TO END OF DIRECTORIES
    db='/restsdk/data/db/index.db' #where the file DB is stored example: /data/db/index.db
    filedir='/restsdk/data/files' #where the files are stored example: /restsdk/data/files
    dumpdir='/location/to/dump/files/to' #where you want the new files dumped example:/EXTERNAL/FILES

### Run the script in terminal :
```console
foo@bar:~/Path/To/Python/Script$ sudo python3 restsdk_public.py
```
### Get the files structured in the original folders.
### Different users spaces protected with passwords are recovered.
![alt text](screenshot-2.png)



*If this script has helped you recover your data, please consider saying thanks to springfielddatarecovery with a Bitcoin donation 1DqSLNR8kTgwq5rvveUFDSbYQnJp9D5gfR*


