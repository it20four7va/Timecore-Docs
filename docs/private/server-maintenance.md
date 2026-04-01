## Weekly maintenance tasks include the following.
- Creating zip files from screenshots and push that backup to DropBox
- Deletion of  screenshots from 3rd previous week
- Optimization of Screenshot table
- Take backup until now and upload that to DropBox.
  
 **Important Notes:** 

- **Maintenance app must be started before Sunday 23:59:59 ET on the 3rd week to set default dates for associated tasks. Otherwise you'll have to give it manually as an argument.**
- **All tasks must be executed in the given sequence.**
- **Make sure the internet stays stable, if the local session will expire, the process running on server will also be terminated from server.**

## Steps to run the maintenance:

 **Windows**

1. Login to Digital Ocean by SSH client like PUTTY
   
 - In windows you’ve to configure PUTTY.
 - Run PUTTY: Enter server IP to host name and click on Open button.
 - Add username and password.
 - After successful login, you will see command line screen.

 **MAC & Linux**
  - Open Terminal & run the following commands:

        ssh user@IP-Address
        username
        password
        

  NOTE: 

 - IP 147.182.130.19
 - root
 - 39c&=z3tvN)*_2TnhoGB 
  
## Next Steps

1.  Make sure that the backup directory is empty before starting the process
   
        rm -R /mnt/volume_nyc1_02/data/*

    NOTE: If it’s empty it will show ‘No such file/directory

2. Go to the maintenance app folder 
   
        cd /home/ttdev/screenshot-sync

3. Create zip for stored screenshot 
   
        gradle run --args="screenshots_to_zip"

    NOTE: In case Gradle not found, run the following command -

        source ~/.bashrc

    Then run the gradle script

4. Take a note of numbers of files created, to verify later from DropBox.
   
5. Upload screenshot to DropBox, use the following command:
    
        gradle run --args="upload_zip_to_dropbox" 

6. Verify all uploaded files, we need to check if all files are uploaded without error. If we find any errors, it should be fixed.
   
7. Optimize screenshot table, run the following command -
    
        gradle run --args="optimize -nth_previous_week 1"

      NOTE: Optimization process can not be resumed if stopped from the same place, so make sure that it’ll be running constantly.

8. Clear backup directory for future process, run the following command:
    
        rm -R /mnt/volume_nyc1_02/data/*

9.  Delete screenshots which are already pushed to DropBox
    
        gradle run --args="delete_screenshot_files"

10. Remove old database backup
    
        rm /mnt/volume_nyc1_02/ttAppData/databaseBackups/*

11. Take database backup

        gradle run --args="take_db_backup"

12. Upload database backup to dropbox

        gradle run --args="db_backup_dropbox_upload"

    NOTE: All user data will be stored in **“data”** directory and associated data will have **“Reg. ID”**
