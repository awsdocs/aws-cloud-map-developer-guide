# Values That You Specify When You Create Namespaces<a name="namespaces-values"></a>

When you create an AWS Cloud Map namespace, you specify the following values\.

**Note**  
After you create a namespace, you can change tags\. However, you can't change any other values\.

**Values**
+ [Namespace name](#namespace-creating-values-name)
+ [Namespace description](#namespace-creating-values-description)
+ [Instance discovery](#namespace-creating-values-instance-discovery)
+ [Tags](#namespace-creating-values-tags)
+ [VPC](#namespace-creating-values-vpc)

**Namespace name**  
The name that you specify for a namespace depends on how you want your application to discover instances\. The method of how instances are discovered is determined by the option that you choose for **Instance discovery**\. The options appear later on the current page in the console\. They are as follows:    
**API calls**  
If you choose this option, your application discovers service instances by specifying the namespace name and service name in a [DiscoverInstances](https://docs.aws.amazon.com/cloud-map/latest/api/API_DiscoverInstances.html) request\. For more information, see [DiscoverInstances](https://docs.aws.amazon.com/cloud-map/latest/api/API_DiscoverInstances.html) in the *AWS Cloud Map API Reference*\.  
You can specify a name that's up to 1,024 characters in length\. A name can contain both uppercase and lowercase letters, numbers, underscores \(\_\), and hyphens \(\-\)\.  
**API calls and DNS queries in VPCs**  
Enter the domain name that you want your applications in a VPC to use when they discover instances by submitting DNS queries\. AWS Cloud Map automatically creates an Amazon Route 53 private hosted zone that has this name\. When you register service instances, AWS Cloud Map creates DNS records in the hosted zone that have names in the following format:  
*service\-name*\.*namespace\-name*  
If you choose this option, your application can also discover instances by specifying the namespace name and service name in a [DiscoverInstances](https://docs.aws.amazon.com/cloud-map/latest/api/API_DiscoverInstances.html) request\. For more information, see [DiscoverInstances](https://docs.aws.amazon.com/cloud-map/latest/api/API_DiscoverInstances.html) in the *AWS Cloud Map API Reference*\.  
You can specify an internationalized domain name \(IDN\) if you convert the name to Punycode first\. For information about online converters, perform an internet search on "punycode converter"\.  
You can also convert an internationalized domain name to Punycode when you create namespaces programmatically\. For example, if you're using Java, you can convert a Unicode value to Punycode by using the `toASCII` method of the java\.net\.IDN library\.  
**API calls and public DNS queries**  
Enter the domain name that you want your applications to use when they discover instances by submitting public DNS queries\. This must be a domain name that you have registered\. When you create the namespace, AWS Cloud Map automatically creates an Amazon Route 53 public hosted zone that has the same name\. When you register service instances, AWS Cloud Map creates DNS records in the hosted zone that have names in the following format:  
*service\-name*\.*namespace\-name*  
If you choose this option, your application can also discover instances by specifying the namespace name and service name in a [DiscoverInstances](https://docs.aws.amazon.com/cloud-map/latest/api/API_DiscoverInstances.html) request\. For more information, see [DiscoverInstances](https://docs.aws.amazon.com/cloud-map/latest/api/API_DiscoverInstances.html) in the *AWS Cloud Map API Reference*\.  
You can specify an internationalized domain name \(IDN\) if you convert the name to Punycode first\. For information about online converters, perform an internet search on "punycode converter"\.  
You can also convert an internationalized domain name to Punycode when you create namespaces programmatically\. For example, if you're using Java, you can convert a Unicode value to Punycode by using the `toASCII` method of the java\.net\.IDN library\.

**Namespace description**  
Enter a description for the namespace\. The value that you enter here appears on the **Namespaces** page and on the detail page for each namespace\.

**Instance discovery**  
Choose how you want your application to discover registered instances:     
**API calls**  
Choose this option if you want your application to use only API calls to discover registered instances\.  
**API calls and DNS queries in VPCs**  
Choose this option if you want your application to be able to discover instances using either API calls or using DNS queries in a VPC\. You aren't required to use both methods\.  
**API calls and public DNS queries**  
Choose this option if you want your application to be able to discover instances using either API calls or using public DNS queries\. You aren't required to use both methods\.

**SOA TTL**  
For **API calls and DNS queries in VPCs** or **API calls and public DNS queries**, the time to live \(TTL\) value for the start of authority \(SOA\) DNS record of the Route 53 hosted zone created with your namespace\. The value determines how long DNS resolvers cache information for this record before the resolvers forward another DNS query to Amazon Route 53 to get updated settings\. A smaller value will also reduce the time a missing entry will be cached \(negative caching\) at the expense of additional queries for that namespace\.

**Tags**  
You can specify one or more tags to add to your namespace\. A tag is an optional label that you can assign to an AWS resource\. Each tag consists of a key and a value\. For example, you can define a tag with Key = Environment and Value = Production\. Tags enable you to categorize your AWS resources so you can more easily manage them\.  
You can update or remove tags on your namespaces after they have been created\. For more information, see [Tagging your AWS Cloud Map resources](using-tags.md)\.

**VPC**  
When you choose **API calls and DNS queries in VPCs** for the value of **Instance discovery**, AWS Cloud Map creates an Amazon Route 53 private hosted zone that has the same name\. AWS Cloud Map associates the VPC that you choose in the **VPC** list with that private hosted zone\.  
Route 53 Resolver resolves DNS queries that originate in the VPC using records in the private hosted zone\. If the private hosted zone doesn't include a record that matches the domain name in a DNS query, Route 53 responds to the query with `NXDOMAIN` \(non\-existent domain\)\.  
You can associate additional VPCs with the private hosted zone\. For more information, see [AssociateVPCWithHostedZone](https://docs.aws.amazon.com/Route53/latest/APIReference/API_AssociateVPCWithHostedZone.html) in the *Amazon Route 53 API Reference*\.