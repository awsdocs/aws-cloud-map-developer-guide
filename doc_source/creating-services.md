# Creating Services<a name="creating-services"></a>

To create a service, perform the following procedure\.<a name="creating-services-procedure"></a>

**To create a service**

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

1. On the **Namespaces** page, choose the namespace that you want to add the service to\.

1. On the **Namespace: *namespace\-name*** page, choose **Create service**\.

1. On the **Create service** page, enter the applicable values\. For more information, see [Values That You Specify When You Create Services](services-values.md)\.

1. Choose **Create service**\.

**Note**  
For services that are accessible by DNS queries, you cannot create multiple services with names that differ only by case \(such as EXAMPLE and example\)\. Otherwise, these services will have the same DNS name\. If you use a namespace that's only accessible by API calls, then you can create services that with names that differ only by case\.