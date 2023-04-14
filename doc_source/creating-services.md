# Creating Services<a name="creating-services"></a>

To create a service, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

1. On the **Namespaces** page, choose the namespace that you want to add the service to\.

1. On the **Namespace: *namespace\-name*** page, choose **Create service**\.

1. On the **Create service** page, enter the applicable values\. For more information, see [Values That You Specify When You Create Services](services-values.md)\.

1. Choose **Create service**\.

------
#### [ AWS CLI ]
+ Create a service with the `[create\-service](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/create-services.html)` command \(replace the *red* value with your own\)\.

  ```
  aws servicediscovery create-service \
      --name service-name \
      --namespace-id  ns-xxxxxxxxxxx \
      --dns-config "NamespaceId=ns-xxxxxxxxxxx,RoutingPolicy=MULTIVALUE,DnsRecords=[{Type=A,TTL=60}]"
  ```

  Output:

  ```
  {
          "Service": {
          "Id": "srv-xxxxxxxxxxx",
          "Arn": "arn:aws:servicediscovery:us-west-2:123456789012:service/srv-xxxxxxxxxxx",
          "Name": "service-name",
          "NamespaceId": "ns-xxxxxxxxxxx",
          "DnsConfig": {
              "NamespaceId": "ns-xxxxxxxxxxx",
              "RoutingPolicy": "MULTIVALUE",
              "DnsRecords": [
                  {
                      "Type": "A",
                      "TTL": 60
                  }
              ]
          },
          "CreateDate": 1587081768.334,
          "CreatorRequestId": "567c1193-6b00-4308-bd57-ad38a8822d25"
      }
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

1. Create a service with `create_service()` \(replace the *red* value with your own\)\.

   ```
   response = client.create_service(
       DnsConfig={
           'DnsRecords': [
               {
                   'TTL': 60,
                   'Type': 'A',
               },
           ],
           'NamespaceId': 'ns-xxxxxxxxxxx',
           'RoutingPolicy': 'MULTIVALUE',
       },
       Name='service-name',
       NamespaceId='ns-xxxxxxxxxxx',
   )
   ```

   Example response output

   ```
   {
       'Service': {
           'Arn': 'arn:aws:servicediscovery:us-west-2:123456789012:service/srv-xxxxxxxxxxx',
           'CreateDate': 1587081768.334,
           'DnsConfig': {
               'DnsRecords': [
                   {
                       'TTL': 60,
                       'Type': 'A',
                   },
               ],
               'NamespaceId': 'ns-xxxxxxxxxxx',
               'RoutingPolicy': 'MULTIVALUE',
           },
           'Id': 'srv-xxxxxxxxxxx',
           'Name': 'service-name',
           'NamespaceId': 'ns-xxxxxxxxxxx',
       },
       'ResponseMetadata': {
           '...': '...',
       },
   }
   ```

------

**Note**  
For services that are accessible by DNS queries, you cannot create multiple services with names that differ only by case \(such as EXAMPLE and example\)\. Otherwise, these services will have the same DNS name\. If you use a namespace that's only accessible by API calls, then you can create services that with names that differ only by case\.