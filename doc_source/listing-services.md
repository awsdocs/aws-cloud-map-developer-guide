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