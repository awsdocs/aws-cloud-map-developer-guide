# Viewing a List of Namespaces<a name="listing-namespaces"></a>

To view a list of namespaces, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

------
#### [ AWS CLI ]
+ List namespaces with the `[list\-namespaces](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/list-namespaces.html)` command\.

  ```
  aws servicediscovery list-namespaces
  ```

------
#### [ AWS SDK for Python \(Boto3\) ]

1. If you don't already have `Boto3` installed, you can find instructions for installing, configuring, and using `Boto3` [here](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html#installation)\.

1. Import `Boto3` and use `servicediscovery` as your service\.

   ```
   import boto3
   client = boto3.client('servicediscovery')
   ```

1. List namespaces with `list_namespaces()`\.

   ```
   response = client.list_namespaces()
   # If you want to see the response
   print(response)
   ```

   Example response output

   ```
   {
       'Namespaces': [
           {
               'Arn': 'arn:aws::servicediscovery:us-west-2:123456789012:namespace/ns-xxxxxxxxxxxxxxx',
               'CreateDate': 1585354387.357,
               'Id': 'ns-xxxxxxxxxxxxxxx',
               'Name': 'myFirstNamespace',
               'Properties': {
                   'DnsProperties': {
                       'HostedZoneId': 'Z06752353VBUDTC32S84S',
                   },
                   'HttpProperties': {
                       'HttpName': 'myFirstNamespace',
                   },
               },
               'Type': 'DNS_PRIVATE',
           },
           {
               'Arn': 'arn:aws::servicediscovery:us-west-2:123456789012:namespace/ns-xxxxxxxxxxxxxxx',
               'CreateDate': 1586468974.698,
               'Description': 'My second namespace',
               'Id': 'ns-xxxxxxxxxxxxxxx',
               'Name': 'mySecondNamespace.com',
               'Properties': {
                   'DnsProperties': {
                   },
                   'HttpProperties': {
                       'HttpName': 'mySecondNamespace.com',
                   },
               },
               'Type': 'HTTP',
           },
           {
               'Arn': 'arn:aws::servicediscovery:us-west-2:123456789012:namespace/ns-xxxxxxxxxxxxxxx',
               'CreateDate': 1587055896.798,
               'Id': 'ns-xxxxxxxxxxxxxxx',
               'Name': 'myThirdNamespace.com',
               'Properties': {
                   'DnsProperties': {
                       'HostedZoneId': 'Z09983722P0QME1B3KC8I',
                   },
                   'HttpProperties': {
                       'HttpName': 'myThirdNamespace.com',
                   },
               },
               'Type': 'DNS_PRIVATE',
           },
       ],
       'ResponseMetadata': {
           '...': '...',
       },
   }
   ```

------