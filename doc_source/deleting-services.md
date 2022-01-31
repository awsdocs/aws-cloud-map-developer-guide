# Deleting Services<a name="deleting-services"></a>

Before you can delete a service, you must deregister all service instances that were registered using the service\. For more information, see [Deregistering Service Instances](deregistering-instances.md)\.

To delete a service, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

1. Choose the option for the namespace that contains the service that you want to delete\.

1. On the **Namespace: *namespace\-name*** page, choose the option for the service that you want to delete\.

1. Choose **Delete**\.

1. Confirm that you want to delete the service\.

------
#### [ AWS CLI ]
+ Delete a service with the `[delete\-service](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/delete-service.html)` command \(replace the *red* value with your own\)\.

  ```
  aws servicediscovery delete-service --id srv-xxxxxx
  ```

------