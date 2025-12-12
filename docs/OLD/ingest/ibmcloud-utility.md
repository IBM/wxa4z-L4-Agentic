# Log into COS via IBM Cloud Utility

Next you will connect to your COS instance via command-line, using the credential values you recorded previously.

1. Navigate to your local workstation’s command prompt or terminal window. Make sure the **ibmcloud** CLI is already installed.
   
    This can be verified by running the following command:

    ```
    ibmcloud help
    ```

    ***If you do not have it installed***, do so by following [these instructions](https://cloud.ibm.com/docs/cli?topic=cli-getting-started).

2. Install the COS Plugin by running the following command:
   
    ```
    ibmcloud plugin install cloud-object-storage
    ```

3. Run the following command to authenticate to IBM Cloud using HMAC authentication:
   
    ```
    ibmcloud cos config auth --method HMAC
    ```

4. Run the following command to authenticate to your IBM COS instance:
   
    ```
    ibmcloud cos config hmac
    ```
   
5. You will then be prompted for your **Access key**. Copy and paste the value of your **access_key_id** that you recorded earlier and hit **enter**. 
   
    ![](_attachments/zassist7.png)

    **NOTE:** *your **access_key_id** is unique and will not be the same as above*

6. Next, you will be prompted for your **Secret key**. Copy and paste the value of your **secret_access_key** that you recorded earlier and hit **enter**. 
   
    ![](_attachments/zassist8.png)

    **NOTE:** *your **secret_access_key** is unique and will not be the same as above*

7. You should then get the following message:
   
    ```
    Successfully saved HMAC Credentials to file
    ```

8. Finally, run the following command to list the buckets created in your instance:
   
    ```
    ibmcloud cos buckets
    ```

    In the output, you should see that no buckets have been created:

    ![](_attachments/zassist9.png)

