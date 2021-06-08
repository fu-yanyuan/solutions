set the permissions of the key
---  
[#troubleshoot-unprotected-key](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/TroubleshootingInstancesConnecting.html#troubleshoot-unprotected-key)  

### If you are connecting from MacOS or Linux, run the following command to fix this error, substituting the path for your private key file.

`[ec2-user ~]$ chmod 0400 .ssh/my_private_key.pem`
### If you are connecting from Windows, perform the following steps on your local computer.

> 1. Navigate to your .pem file.
> 
> 2. Right-click on the .pem file and select **Properties**.
> 
> 3. Choose the **Security** tab.
> 
> 4. Select **Advanced**.
> 
> 5. Verify that you are the owner of the file. If not, change the owner to your username.
> 
> 6. Select **Disable inheritance** and **Remove all inherited permissions from this object**.
> 
> 7. Select **Add**, Select a **principal**, enter your username, and select **OK**.
> 
> 8. From the **Permission Entry** window, grant **Read** permissions and select **OK**.
> 
> 9. Select **OK** to close the Advanced Security Settings window.
> 
> 10. Select **OK** to close the Properties window.

You should be able to connect to your Linux instance from Windows via SSH.

From a Windows command prompt, run the following commands.

From the command prompt, navigate to the file path location of your .pem file.

Run the following command to reset and remove explicit permissions:

`icacls.exe $path /reset`
Run the following command to grant Read permissions to the current user:

`icacls.exe $path /GRANT:R "$($env:USERNAME):(R)"`
Run the following command to disable inheritance and remove inherited permissions.

`icacls.exe $path /inheritance:r`
You should be able to connect to your Linux instance from Windows via SSH.
