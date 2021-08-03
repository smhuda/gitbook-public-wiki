# Cloud Penetration Testing

<table>
  <thead>
    <tr>
      <th style="text-align:left"><b>account</b>
      </th>
      <th style="text-align:left">
        <p>A formal relationship with AWS that is associated with all of the following:
          <br
          />
        </p>
        <ul>
          <li>The owner email address and password</li>
          <li>The control of resources created under its umbrella</li>
          <li>Payment for the AWS activity related to those resources</li>
        </ul>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>allow</b>
      </td>
      <td style="text-align:left">One of two possible outcomes (the other is deny) when an IAM access policy
        is evaluated. When a user makes a request to AWS, AWS evaluates the request
        based on all permissions that apply to the user and then returns either
        allow or deny.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>AssumeRolePolicy</code>
      </td>
      <td style="text-align:left">A synonym for the Trust policy.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>group</b>
      </td>
      <td style="text-align:left">A collection of IAM users. You can use IAM groups to simplify specifying
        and managing permissions for multiple users.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>NotAction</code>
      </td>
      <td style="text-align:left">An advanced policy element that explicitly matches everything except the
        specified list of actions.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>permission</b>
      </td>
      <td style="text-align:left">A statement within a policy that allows or denies access to a particular
        resource. You can state any permission like this: &quot;A has permission
        to do B to C.&quot; For example, Jane (A) has permission to read messages
        (B) from John&apos;s Amazon SQS queue (C). Whenever Jane sends a request
        to Amazon SQS to use John&apos;s queue, the service checks to see if she
        has permission. It further checks to see if the request satisfies the conditions
        John set forth in the permission.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>policy</b>
      </td>
      <td style="text-align:left">For IAM: A document defining permissions that apply to a user, group,
        or role; the permissions in turn determine what users can do in AWS. A
        policy typically allows access to specific actions, and can optionally
        grant that the actions are allowed for specific resources, like EC2 instances,
        Amazon S3 buckets, and so on. Policies can also explicitly deny access.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>principal</b>
      </td>
      <td style="text-align:left">The user, service, or account that receives permissions that are defined
        in a policy. The principal is A in the statement &quot;A has permission
        to do B to C.&quot;</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>resource</b>
      </td>
      <td style="text-align:left">An entity that users can work within AWS, such as an EC2 instance, an
        Amazon DynamoDB table, an Amazon S3 bucket, an IAM user, an AWS OpsWorks
        stack, and so on.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>role</b>
      </td>
      <td style="text-align:left">A tool for giving temporary access to AWS resources in your AWS account.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Trust policy</b>
      </td>
      <td style="text-align:left">An IAM policy that is an inherent part of an IAM role. The trust policy
        specifies which principals are allowed to use the role. (Synonym for <code>AssumeRolePolicy</code>).</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>user</b>
      </td>
      <td style="text-align:left">A person or application under an account that needs to make API calls
        to AWS products. Each user has a unique name within the AWS account, and
        a set of security credentials not shared with other users. These credentials
        are separate from the AWS account&apos;s security credentials. Each user
        is associated with one and only one AWS account.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>versioning</b>
      </td>
      <td style="text-align:left">Every object in Amazon S3 has a key and a version ID. Objects with the
        same key, but different version IDs can be stored in the same bucket. Versioning
        is enabled at the bucket layer using PUT Bucket versioning.</td>
    </tr>
  </tbody>
</table>

### PACU

Pacu is an open-source AWS exploitation framework, designed for offensive security testing against cloud environments. Created and maintained by Rhino Security Labs, Pacu allows penetration testers to exploit configuration flaws within an AWS account, using modules to easily expand its functionality. Current modules enable a range of attacks, including user privilege escalation, backdooring of IAM users, attacking vulnerable Lambda functions, and much more.

```text
python3 pacu.py
set_keys
```

Enumerate IAM entities using the `iam__enum_users_roles_policies_groups` 

## CloudEnum

Multi-cloud OSINT tool. Enumerate public resources in AWS, Azure, and Google Cloud.

```text
https://github.com/initstring/cloud_enum
```

## Tools

[**actions2aws**](https://github.com/glassechidna/actions2aws)   
****Assume AWS IAM roles from GitHub Actions workflows with no stored secrets.  
  
[**rpCheckup**](https://github.com/goldfiglabs/rpCheckup)   
****rpCheckup is an AWS resource policy security checkup tool that identifies public, external account access, intra-org account access, and private resources.  
  
[**policy-compliance-scan**](https://github.com/Azure/policy-compliance-scan)   
****A GitHub action that scans Azure resources for policy violations.

[**iamlive**](https://github.com/iann0036/iamlive)  
****Generate basic AWS IAM policies using client-side monitoring of calls made from the AWS CLI or SDKs.  
  
[**iam-role-enumeration**](https://gist.github.com/kmcquade/4d5788f8592953f5a3a65ec3f87385b4)  
****Another way to enumerate AWS IAM users/roles without being authenticated to the victim account.  
  
[**cloudlist**](https://github.com/projectdiscovery/cloudlist)  
****Cloudlist is a tool for listing Assets \(Hostnames, IP Addresses\) from multiple Cloud Providers.  
  
[**kctf**](https://github.com/google/kctf)  
****kCTF is a Kubernetes-based infrastructure for CTF competitions.

