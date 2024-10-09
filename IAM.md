# IAM
- IAM lets you grant granular access to specific Google Cloud resources and helps prevent access to other resources. IAM lets you adopt the security principle of least privilege, which states that nobody should have more permissions than they actually need

  * who (identity) has 
    * what access (role) for 
      * which resource
     
  **Principal**:  A principal represents an identity that can access a resource. Each principal has its own identifier.

  **Role**: A role is a collection of permissions. Permissions determine what operations are allowed on a resource. When you grant a role to a principal, you grant all the permissions that the role contains.

  **Policy**: The allow policy is a collection of role bindings that bind one or more principals to individual roles. When you want to define who (principal) has what type of access (role) on a resource, you create an allow policy and attach it to the resource.

- In IAM, permission to access a resource isn't granted directly to the end user. Instead, permissions are grouped into roles, and roles are granted to authenticated principals

## Components of IAM

### Principals
    
In IAM, you grant access to principals, which represent an identity that can access a resource. Principals can be one of the following types:
    - Google Accounts
    - Service accounts
    - Google groups
    - Google Workspace accounts
    - Cloud Identity domains
    - allAuthenticatedUsers
    - allUsers
    - One or more federated identities in a workforce identity pool
    - One or more federated identities in a workload identity pool
    - A set of Google Kubernetes Engine Pods

### Permissions
   
Permissions determine what operations are allowed on a resource. In the IAM world, permissions are represented in the form of **service.resource.verb**

### Roles

A role is a collection of permissions. You cannot grant a permission to the user directly. Instead, you grant them a role. When you grant a role to a user, you grant them all the permissions that the role contains

##### Types:

  **Basic roles**: Roles historically available in the Google Cloud console. 

These roles are 

- Owner
- Editor
- Viewer

**Predefined roles:** Roles that give finer-grained access control than the basic roles. For example, the predefined role Pub/Sub Publisher (roles/pubsub.publisher) provides access to only publish messages to a Pub/Sub topic

**Custom roles:** Roles that you create to tailor permissions to the needs of your organization when predefined roles don't meet your needs.

### Allow policy
When an authenticated principal attempts to access a resource, IAM checks the resource's allow policy to determine whether the action is allowed

You can grant roles to users by creating an allow policy, which is a collection of statements that define who has what type of access. An allow policy is attached to a resource and is used to enforce access control whenever that resource is accessed

An allow policy consists of a list of role bindings

![image](https://github.com/user-attachments/assets/1704c44a-7ce0-48fb-848f-4f0ba53c17d0)

The following code snippet shows the structure of an allow policy
~~~
{
  "bindings": [
    {
      "role": "roles/storage.objectAdmin",
      "members": [
        "user:ali@example.com",
        "serviceAccount:my-other-app@appspot.gserviceaccount.com",
        "group:admins@example.com",
        "domain:google.com"
      ]
    },
    {
      "role": "roles/storage.objectViewer",
      "members": [
        "user:maria@example.com"
      ]
    }
  ]
}
~~~
