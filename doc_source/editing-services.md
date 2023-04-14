# Updating Services<a name="editing-services"></a>

To update a service, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

1. On the **Namespaces** page, choose the namespace that you want to edit the service for\.

1. On the **Namespace: *namespace\-name*** page, select the service you want to edit and click **Edit**\.

1. On the **Service: *service\-name*** page, click **Edit**\.

1. On the **Edit service** page, enter the applicable values\.

1. Click **Update service**\.

------
#### [ AWS CLI ]
+ Update a service with the `[update\-service](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/update-service.html)` command \(replace the *red* value with your own\)\.

  ```
  aws servicediscovery update-service \
      --id  srv-xxxxxxxxxxx \
      --service "Description=new description,DnsConfig={DnsRecords=[{Type=A,TTL=60}]}"
  ```

  Output:

  ```
  {
      "OperationId": "l3pfx7f4ynndrbj3cfq5fm2qy2z37bms-5m6iaoty"
  }
  ```

------
#### [ AWS SDK for Python \(Boto3\) ]

1. If you don't already have `Boto3` installed, you can find instructions for installing, configuring, and using `Boto3` [here](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html#installation)\.

1. Import `Boto3` and use `servicediscovery` as your service\.

   ```
   import boto3
   client = boto3.client('servicediscovery')
   ```

1. Update a service with `update_service()` \(replace the *red* value with your own\)\.

   ```
   response = client.update_service(
       Id='srv-xxxxxxxxxxx',
       Service={
           'DnsConfig': {
               'DnsRecords': [
                   {
                       'TTL': 300,
                       'Type': 'A',
                   },
               ],
           },
           'Description': "new description",
       }
   )
   ```

   Example response output

   ```
   {
       "OperationId": "l3pfx7f4ynndrbj3cfq5fm2qy2z37bms-5m6iaoty"
   }
   ```

------