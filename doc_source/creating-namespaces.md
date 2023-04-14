# Creating Namespaces<a name="creating-namespaces"></a>

To create a namespace, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. Choose **Create namespace**\.

1. On the **Create namespace** page, enter the applicable values\. For more information, see [Values That You Specify When You Create Namespaces](namespaces-values.md)\.

1. Choose **Create namespace**\.

------
#### [ AWS CLI ]
+ 

  Create a namespace with the command for the instance discovery type you would prefer \(replace the *red* values with your own\)\.
  + Create an HTTP namespace using `[create\-http\-namespace](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/create-http-namespace.html)`\. Service instances registered using an HTTP namespace can be discovered using a `DiscoverInstances` request, but they can't be discovered using DNS\.

    ```
    aws servicediscovery create-http-namespace --name name-of-namespace
    ```
  + Create a private namespace based on DNS and only visible inside a specified Amazon VPC using `[create\-private\-dns\-namespace](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/create-private-dns-namespace.html)`\. You can discover instances that were registered with a private DNS namespace by using either a `DiscoverInstances` request or using DNS

    ```
    aws servicediscovery create-private-dns-namespace --name name-of-namespace --vpc vpc-xxxxxxxxx
    ```
  + Create a public namespace based on DNS that is visible on the internet using `[create\-public\-dns\-namespace](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/create-public-dns-namespace.html)`\. You can discover instances that were registered with a public DNS namespace by using either a `DiscoverInstances` request or using DNS\.

    ```
    aws servicediscovery create-public-dns-namespace --name name-of-namespace
    ```
**Note**  
Namespaces configured for public DNS queries must end with a top level domain \(e\.g \.com\)\.
The namespace name can have up to 1,024 characters, and must start and end with a letter\.
Valid characters: a\-z, A\-Z, 0\-9, \. \(period\), \_ \(underscore\), and \- \(hyphen\)\.

------
#### [ AWS SDK for Python \(Boto3\) ]

1. If you don't already have `Boto3` installed, you can find instructions for installing, configuring, and using `Boto3` [here](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/quickstart.html#installation)\.

1. Import `Boto3` and use `servicediscovery` as your service\.

   ```
   import boto3
   client = boto3.client('servicediscovery')
   ```

1. 

   Create a namespace with the command for the instance discovery type you would prefer \(replace the *red* values with your own\):
   + Create an HTTP namespace using `create_http_namespace()`\. Service instances registered using an HTTP namespace can be discovered using `discover_instances()`, but they can't be discovered using DNS\.

     ```
     response = client.create_http_namespace(
         Name='name-of-namespace',
     )
     # If you want to see the response
     print(response)
     ```
   + Create a private namespace based on DNS and only visible inside a specified Amazon VPC using `create_private_dns_namespace()`\. You can discover instances that were registered with a private DNS namespace by using either `discover_instances()` or using DNS

     ```
     response = client.create_private_dns_namespace(
         Name='name-of-namespace',
         Vpc='vpc-1c56417b',
     )
     # If you want to see the response
     print(response)
     ```
   + Create a public namespace based on DNS that is visible on the internet using `create_public_dns_namespace()`\. You can discover instances that were registered with a public DNS namespace by using either `discover_instances()` or using DNS\.

     ```
     response = client.create_public_dns_namespace(
         Name='name-of-namespace',
     )
     # If you want to see the response
     print(response)
     ```
   + Example response output

     ```
     {
         'OperationId': 'gv4g5meo7ndmeh4fqskygvk23d2fijwa-k9302yzd',
         'ResponseMetadata': {
             '...': '...',
         },
     }
     ```
**Note**  
Namespaces configured for public DNS queries must end with a top level domain \(e\.g \.com\)\.
The namespace name can have up to 1,024 characters, and must start and end with a letter\.
Valid characters: a\-z, A\-Z, 0\-9, \. \(period\), \_ \(underscore\), and \- \(hyphen\)\.

------