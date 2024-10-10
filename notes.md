# Migrate to Google Cloud
Migrating your workloads to Google Cloud

**Types of migrations**

- Rehost: lift and shift
  - Move workloads from a source environment to a target environment with minor or no modifications or refactoring
- Replatform: lift and optimize
  - Lift the existing workloads and then optimize them for the new cloud environment.
- Refactor: move and improve
  - Modify the workloads to take advantage of cloud capabilities, and not just modify the workloads to make them work in the new environment. You can improve each workload for performance, features, cost, and user experience
- Re-architect: continue to modernize
  - Instead of restructuring how the workload code works, re-architect migrations change how that code functions. Those code changes optimize the workload and take advantage of cloud-optimized properties such as scalability, security, and agility.
  - For example, a re-architect migration can take one large, monolithic workload and turn it into several independent microservices that you deploy on Google Cloud.
- Rebuild: remove and replace, sometimes called rip and replace
  - Decommission an existing app and completely redesign and rewrite it as a fully cloud-optimized app
- Repurchase
  - A repurchase migration is when you move from a purchased on-premises workload to a cloud-hosted software-as-a-service (SaaS) equivalent. 
  - For example, you can move from on-premises collaboration software and local storage to Google Workspace.
### Google Cloud Adoption Framework
![migration-to-gcp-getting-started-1-gcp-adoption-framework](https://github.com/user-attachments/assets/6b15a72d-a5f2-4f87-9e34-7ad55f4697c0)

### There are four phases of your migration
**Assess** : In this phase, you perform a thorough assessment and discovery of your existing environment in order to understand your app and environment inventory, identify app dependencies and requirements, perform total cost of ownership calculations, and establish app performance benchmarks. For more information about the assess phase, see Migrate to Google Cloud: Assess and discover your workloads, Migrate to Google Cloud: Best practices, and Migration Center: Start an asset discovery.
**Plan**: In this phase, you create the basic cloud infrastructure for your workloads to live in and plan how you will move apps. This planning includes identity management, organization and project structure, networking, sorting your apps, and developing a prioritized migration strategy. For more information about planning and building your foundation, see Migrate to Google Cloud: Plan and build your foundation.
**Deploy**: In this phase, you design, implement and execute a deployment process to move workloads to Google Cloud. You might also have to refine your cloud infrastructure to deal with new needs. For more information about how to deploy your workloads to Google Cloud and how to migrate data to Google Cloud, see Migrate to Google Cloud: Deploy your workloads, Migrate to Google Cloud: Migrate from manual deployments to automated, containerized deployments, and Migrate to Google Cloud: Transfer your large datasets.
**Optimize**: In this phase, you begin to take full advantage of cloud-optimized technologies and capabilities to expand your business's potential to things such as performance, scalability, disaster recovery, costs, training, as well as opening the doors to machine learning and artificial intelligence integrations for your app. For more information about how to optimize your environment, see Migrate to Google Cloud: Optimize your environment. For more information about costs, see Migrate to Google Cloud: Minimize costs.

# Cloud Key Management Service
Cloud Key Management Service (Cloud KMS) lets you create and manage CMEK keys for use in compatible Google Cloud services and in your own applications

By using the following apporach, Protecting data in Google Cloud.
- Google-owned and Google-managed keys
- Customer-managed encryption keys (CMEKs)
- Customer-supplied encryption keys (CSEKs)
