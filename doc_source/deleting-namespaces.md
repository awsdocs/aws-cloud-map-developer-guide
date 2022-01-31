# Deleting Namespaces<a name="deleting-namespaces"></a>

When you delete a namespace, you can no longer use it to register or discover service instances\. Note the following:
+ Before you can delete a namespace, you must delete all the services that were created in the namespace\. For more information, see [Deleting Services](deleting-services.md)\.
+ Before you can delete a service, you must deregister all the service instances that were registered using the service\. For more information, see [Deregistering Service Instances](deregistering-instances.md)\.
+ When you create a namespace, if you specify that you want to discover service instances using either public DNS queries or DNS queries in VPCs, AWS Cloud Map creates an Amazon Route 53 public or private hosted zone\. When you delete the namespace, AWS Cloud Map deletes the corresponding hosted zone\.

To delete a namespace, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

1. Choose the option for the namespace that you want to delete\.

1. Choose **Delete**\.

1. Confirm that you want to delete the service\.

------
#### [ AWS CLI ]
+ Delete a namespace with the `[delete\-namespace](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/delete-namespace.html)` command \(replace the *red* value with your own\)\. If the namespace still contains one or more services, the request fails\.

  ```
  aws servicediscovery delete-namespace --id srv-xxxxxxxx
  ```

------