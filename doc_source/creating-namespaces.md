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

  Create a namespace with the command for the instance discovery type you would prefer \(replace the *red* values with your own\):
  + Create an HTTP namespace using `[create\-http\-namespace](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/create-http-namespace.html)`\. Service instances registered using an HTTP namespace can be discovered using a `DiscoverInstances` request, but they can't be discovered using DNS\.

    ```
    aws servicediscovery create-http-namespace --name name-of-namespace
    ```
  + Create a private namespace based on DNS and only visible inside a specified Amazon VPC using `[create\-private\-dns\-namespace](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/create-private-dns-namespace.html)`\. You can discover instances that were registered with a private DNS namespace by using either a `DiscoverInstances` request or using DNS\.

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