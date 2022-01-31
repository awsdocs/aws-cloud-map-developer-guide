# Deregistering Service Instances<a name="deregistering-instances"></a>

Before you can delete a service, you must deregister all service instances that were registered using the service\.

To deregister a service instance, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

1. Choose the option for the namespace that contains the service instance that you want to deregister\.

1. On the **Namespace: *namespace\-name*** page, choose the option for the service you used to register the service instance\.

1. On the **Service: *service\-name*** page, choose the option for the service instance that you want to deregister\.

1. Choose **Deregister**\.

1. Confirm that you want to deregister the service instance\.

------
#### [ AWS CLI ]
+ Deregister a service instance with the `[deregister\-instance](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/deregister-instance.html)` command \(replace the *red* values with your own\)\. This command deletes the Amazon Route 53 DNS records and any health checks that Cloud Map created for the specified instance\.

  ```
  aws servicediscovery deregister-instance \
      --service-id srv-xxxxxxxxx \
      --instance-id myservice-53
  ```

------