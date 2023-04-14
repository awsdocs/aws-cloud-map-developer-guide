# Viewing a List of Services That You Created in a Namespace<a name="listing-services"></a>

To view a list of the services that you created in a namespace, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

1. Choose the name of the namespace that contains the services that you want to list\.

------
#### [ AWS CLI ]
+ List services with the `[list\-services](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/list-services.html)` command\.

  ```
  aws servicediscovery list-services
  ```

------
#### [ AWS SDK for Python \(Boto3\) ]

1. If you don't already have `Boto3` installed, you can find instructions for installing, configuring, and using `Boto3` [here](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html#installation)\.

1. Import `Boto3` and use `servicediscovery` as your service\.

   ```
   import boto3
   client = boto3.client('servicediscovery')
   ```

1. List services with `list_services()`\.

   ```
   response = client.list_services()
   # If you want to see the response
   print(response)
   ```

   Example response output

   ```
   {
       'Services': [
           {
               'Arn': 'arn:aws:servicediscovery:us-west-2:123456789012:service/srv-xxxxxxxxxxxxxxxx',
               'CreateDate': 1587081768.334,
               'DnsConfig': {
                   'DnsRecords': [
                       {
                           'TTL': 60,
                           'Type': 'A',
                       },
                   ],
                   'RoutingPolicy': 'MULTIVALUE',
               },
               'Id': 'srv-xxxxxxxxxxxxxxxx',
               'Name': 'myservice',
           },
       ],
       'ResponseMetadata': {
           '...': '...',
       },
   }
   ```

------