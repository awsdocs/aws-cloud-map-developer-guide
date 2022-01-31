# Viewing a List of Service Instances<a name="listing-instances"></a>

To view a list of the service instances that you registered using a service, perform the following procedure\.

------
#### [ AWS Management Console ]

1. Sign in to the AWS Management Console and open the AWS Cloud Map console at [https://console\.aws\.amazon\.com/cloudmap/](https://console.aws.amazon.com/cloudmap/)\.

1. In the navigation pane, choose **Namespaces**\.

1. Choose the name of the namespace that contains the service for which you want to list service instances\.

1. Choose the name of the service that you used to create the service instances\.

------
#### [ AWS CLI ]
+ List service instances with the `[list\-instances](https://docs.aws.amazon.com/cli/latest/reference/servicediscovery/list-instances.html)` command \(replace the *red* value with your own\)\.

  ```
  aws servicediscovery list-instances --service-id srv-xxxxxxxxx
  ```

------