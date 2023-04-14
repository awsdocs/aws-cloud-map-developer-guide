# Registering Instances<a name="registering-instances"></a>

To register a service instance, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

1. On the **Namespaces** page, choose the namespace that contains the service that you want to use as a template for registering a service instance\.

1. On the **Namespace: *namespace\-name*** page, choose the service that you want to use\.

1. On the **Service: *service\-name*** page, choose **Register service instance**\.

1. On the **Register service instance** page, enter the applicable values\. For more information, see [Values That You Specify When You Register or Update Instances](instances-values.md)\.

1. Choose **Register service instance**\.

------
#### [ AWS CLI ]
+ 

  When you submit a `RegisterInstance` request:
  + For each DNS record that you define in the service that's specified by `ServiceId`, a record is created or updated in the hosted zone that's associated with the corresponding namespace\.
  + If the service includes `HealthCheckConfig`, a health check is created based on the settings in the health check configuration\.
  + Any health checks are associated with each of the new or updated records\.

  Register a service instance with the `[register\-instance](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/register-instance.html)` command \(replace the *red* values with your own\)\.

  ```
  aws servicediscovery register-instance \
      --service-id srv-xxxxxxxxx \
      --instance-id myservice-xx \
      --attributes=AWS_INSTANCE_IPV4=172.2.1.3,AWS_INSTANCE_PORT=808
  ```

------
#### [ AWS SDK for Python \(Boto3\) ]

1. If you don't already have `Boto3` installed, you can find instructions for installing, configuring, and using `Boto3` [here](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html#installation)\.

1. Import `Boto3` and use `servicediscovery` as your service\.

   ```
   import boto3
   client = boto3.client('servicediscovery')
   ```

1. 

   When you submit a `RegisterInstance` request:
   + For each DNS record that you define in the service that's specified by `ServiceId`, a record is created or updated in the hosted zone that's associated with the corresponding namespace\.
   + If the service includes `HealthCheckConfig`, a health check is created based on the settings in the health check configuration\.
   + Any health checks are associated with each of the new or updated records\.

   Register a service instance with `register_instance()` \(replace the *red* values with your own\)\.

   ```
   response = client.register_instance(
       Attributes={
           'AWS_INSTANCE_IPV4': '172.2.1.3',
           'AWS_INSTANCE_PORT': '808',
       },
       InstanceId='myservice-xx',
       ServiceId='srv-xxxxxxxxx',
   )
   # If you want to see the response
   print(response)
   ```

   Example response output

   ```
   {
       'OperationId': '4yejorelbukcjzpnr6tlmrghsjwpngf4-k95yg2u7',
       'ResponseMetadata': {
           '...': '...',
       },
   }
   ```

------