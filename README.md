# Terraform Notes
Terraform is a popular open-source infrastructure as code (IaC) tool used for managing and provisioning cloud infrastructure. Here are some of the most important Terraform commands that you should be familiar with:

1. `terraform init`: Initializes a new or existing Terraform working directory, downloads and installs any required providers, and initializes the backend.

2. `terraform plan`: Generates an execution plan for applying the desired changes to the infrastructure.

3. `terraform apply`: Applies the changes specified in the Terraform configuration files to the infrastructure.

4. `terraform destroy`: Destroys the infrastructure that was created by Terraform.

5. `terraform validate`: Validates the syntax and configuration of the Terraform files.

6. `terraform refresh`: Refreshes the current state of the infrastructure and updates the Terraform state file.

7. `terraform state`: Allows you to manage the state of the infrastructure managed by Terraform.

8. `terraform output`: Displays the values of the outputs defined in the Terraform configuration files.

9. `terraform fmt`: Formats the Terraform configuration files in a consistent style.

10. `terraform get`: Downloads and installs any modules required by the Terraform configuration files.

11. `terraform import`: Imports existing infrastructure into Terraform state. This command allows you to import existing resources into your Terraform configuration, which can be useful if you're migrating an existing infrastructure to Terraform.

12. `terraform graph`: Generates a visual representation of the Terraform configuration files as a graph. This command creates a graph of the dependencies between resources in your Terraform configuration files, which can help you visualize the relationships between different resources.

13. `terraform taint`: Marks a resource as tainted, which forces it to be destroyed and recreated on the next `terraform apply`. This command is useful if you want to recreate a resource with a new configuration, or if you suspect that the resource is in an inconsistent state.

14. `terraform workspace`: Allows you to manage multiple workspaces for the same Terraform configuration. Workspaces allow you to maintain multiple sets of infrastructure with the same Terraform code, which can be useful for development, testing, and production environments.

15. `terraform providers`: Lists the installed Terraform providers and their versions. This command is useful if you need to check which providers are installed and their versions, or if you need to install a new provider.

16. `terraform show`: Displays the current state of the infrastructure managed by Terraform. This command shows the current state of all resources managed by Terraform, which can be useful for troubleshooting and verifying that the infrastructure is in the desired state.

17. `terraform output`: Displays the values of the outputs defined in the Terraform configuration files. This command shows the values of any output variables that are defined in your Terraform configuration, which can be useful for retrieving information about your infrastructure.

18. `terraform plan -out=plan.tf`: Saves the execution plan to a file, which can be useful for reviewing the plan before applying it. This command generates a plan for applying the changes to the infrastructure and saves it to a file named `plan.tf`. You can review the plan before applying it to ensure that it is correct and that there are no unintended consequences.

19. `terraform workspace list`: Lists all the available workspaces for the current configuration. This command shows a list of all the available workspaces for the current Terraform configuration, which can be useful for managing multiple environments and configurations.

20. `terraform state pull`: Pulls the state file from the remote backend. This command retrieves the Terraform state file from the remote backend and saves it to a local file. You can use this command to download the state file and review it locally, or to restore the state file if it has been deleted or corrupted.

21. `terraform console`: Launches a command-line interface for evaluating expressions in the context of a Terraform configuration. This command allows you to test expressions and get immediate feedback on their results, which can be useful for debugging and experimentation.

22. `terraform state mv`: Moves a resource in the Terraform state file. This command allows you to move a resource to a new location in the state file, which can be useful for reorganizing the state file or fixing errors.

23. `terraform state rm`: Removes a resource from the Terraform state file. This command allows you to remove a resource from the state file, which can be useful for cleaning up resources that are no longer needed.

24. `terraform import`: Imports an existing resource into the Terraform state file. This command allows you to import an existing resource into the state file, which can be useful for integrating an existing infrastructure into your Terraform configuration.

25. `terraform force-unlock`: Releases a lock on a state file that was not released properly. This command allows you to release a lock on a state file that was not released properly, which can occur if Terraform terminates unexpectedly or if the state file becomes corrupt.

26. `terraform apply -target=resource`: Applies changes only to the specified resource. This command allows you to apply changes to a specific resource in your Terraform configuration, which can be useful for making targeted changes without affecting other resources.

Overall, these commands provide the essential functionality required for managing and provisioning infrastructure with Terraform. It is important to understand the purpose and functionality of each command to effectively use Terraform in your projects.

## 1. How does Terraform help in discovering plugins?
Terraform provides a plugin system that allows users to extend the functionality of Terraform by writing plugins. These plugins are written in Go and are compiled as shared libraries that Terraform can load and use at runtime.

Terraform's plugin system uses a discovery mechanism to find and load plugins. When Terraform is executed, it searches for plugins in a specific directory on the local machine. By default, this directory is `$HOME/.terraform.d/plugins` on Unix-based systems and `%APPDATA%\terraform.d\plugins` on Windows systems. However, this directory can be customized by setting the `TF_PLUGIN_CACHE_DIR` environment variable.

Plugins can be discovered in two ways:

1. Automatic plugin discovery: Terraform automatically searches for plugins in the plugin directory and loads them if they match the requirements of the current Terraform configuration. These requirements are specified in the `required_providers` block in the Terraform configuration file. For example, if the configuration file requires the `aws` provider, Terraform will search for a plugin that provides this functionality.

2. Manual plugin installation: If a plugin is not found automatically, it can be installed manually by placing the plugin binary in the plugin directory. The plugin binary must be compiled for the appropriate platform and architecture, and it must be named in the format `terraform-provider-<NAME>_vX.Y.Z`, where `<NAME>` is the name of the provider and `X.Y.Z` is the version number.

Terraform's plugin system makes it easy to extend the functionality of Terraform by adding new providers or resources. By following the plugin development guidelines provided by Terraform, developers can create high-quality plugins that are compatible with the Terraform ecosystem.

## 2. Can I add policies to the open-source or pro version of Terraform enterprise?
Terraform Enterprise is a paid offering from HashiCorp that provides additional features and functionality beyond the open-source version of Terraform. One of the features of Terraform Enterprise is Policy as Code, which allows you to define policies that enforce compliance and governance in your infrastructure deployments.

The Policy as Code feature is only available in the paid versions of Terraform Enterprise. It is not available in the open-source version of Terraform or the free version of Terraform Cloud.

With Policy as Code in Terraform Enterprise, you can write policies in a variety of languages, including HCL, JSON, and Rego. These policies can be used to enforce a wide range of compliance and governance requirements, such as access control, resource tagging, and configuration standards.

Additionally, Terraform Enterprise provides a policy framework that allows you to easily integrate with external policy engines, such as Sentinel, to enforce policies across your infrastructure deployments.

So, to answer your question, if you want to use Policy as Code in Terraform, you will need to use the paid versions of Terraform Enterprise. The open-source version of Terraform and the free version of Terraform Cloud do not provide this feature.

## 3. Define Modules in Terraform?
In Terraform, a module is a self-contained package of Terraform configurations that can be used as a building block to create larger, more complex infrastructure deployments. A module can be thought of as a reusable component that encapsulates a set of related resources, configurations, and variables.

Modules in Terraform have several benefits, including:

1. Reusability: Modules can be shared and reused across different Terraform configurations and projects, making it easier to manage and maintain infrastructure deployments.

2. Abstraction: Modules provide a level of abstraction that allows you to hide the complexity of your infrastructure deployments and expose only the necessary inputs and outputs.

3. Separation of concerns: Modules allow you to separate your infrastructure resources into logical groups, making it easier to manage and maintain your deployments.

4. Versioning: Modules can be versioned and managed separately from your main Terraform configurations, providing better control over changes and updates.

A module in Terraform consists of a set of files that define the resources and configurations to be created. These files are typically organized into a directory structure that follows a standard naming convention. The main file in a module is called `main.tf`, and it defines the resources to be created. Additional files can be used to define variables, outputs, and other configurations.

To use a module in a Terraform configuration, you must first declare the module and provide any necessary input variables. This is done using the `module` block in your main configuration file. Once the module is declared, you can reference its resources and outputs just like any other Terraform resource.

Overall, modules are a powerful feature in Terraform that allow you to create reusable and maintainable infrastructure deployments. By encapsulating resources and configurations into modules, you can reduce complexity and increase reusability, making it easier to manage and maintain your infrastructure over time.

## 4. What are the ways to lock Terraform module versions?
Terraform provides several ways to lock module versions to ensure that your infrastructure deployments are consistent and predictable over time. These include:

1. Terraform Configurations: You can specify a specific version of a module in your Terraform configuration files using a version constraint. For example, you can use the `version` argument in the `module` block to specify a specific version of a module.

```
module "example" {
  source = "git::https://example.com/modules/example.git?ref=v1.2.0"
}
```

In this example, the `source` argument specifies the URL of the module and the `ref` parameter specifies the specific version to use (`v1.2.0`).

2. Lock files: Terraform also supports lock files, which are files that explicitly specify the versions of modules and providers to use in your deployments. Lock files can be created using the `terraform init` command with the `-lockfile` flag. Once a lock file is created, Terraform will use it to ensure that only the specified versions of modules and providers are used in subsequent deployments.

3. Terraform Enterprise: If you are using Terraform Enterprise, you can use the workspace lock feature to lock modules to specific versions. Workspace locks can be managed from the Terraform Enterprise UI, and can be used to ensure that all deployments within a workspace use the same versions of modules.

Overall, locking module versions is an important best practice in Terraform that can help ensure that your infrastructure deployments are consistent and predictable over time. By using version constraints, lock files, or Terraform Enterprise, you can ensure that only the specified versions of modules are used in your deployments, reducing the risk of unexpected changes or issues.

## 5. What do you mean by Terraform cloud?
Terraform Cloud is a web-based platform that provides a centralized location for managing Terraform infrastructure deployments. It is a hosted version of Terraform Enterprise, which is a commercial offering from HashiCorp.

With Terraform Cloud, you can store your Terraform configuration files, manage your state files, and collaborate with team members on infrastructure deployments. Terraform Cloud provides several features, including:

1. Workspaces: Workspaces are a way to organize and manage your Terraform configurations. Each workspace represents a separate deployment environment, such as development, staging, or production.

2. Remote State Storage: Terraform Cloud provides a remote state storage feature that allows you to store your state files securely in the cloud. This helps ensure that your state files are always up-to-date and accessible from anywhere.

3. Collaboration: Terraform Cloud provides a collaborative environment for managing infrastructure deployments. You can share workspaces with team members, manage access controls, and track changes to your deployments over time.

4. Version Control: Terraform Cloud integrates with version control systems like GitHub, allowing you to manage your Terraform configuration files alongside your application code.

5. Cost Estimation: Terraform Cloud provides a cost estimation feature that allows you to estimate the cost of your infrastructure deployments before actually applying them.

Overall, Terraform Cloud provides a centralized platform for managing Terraform infrastructure deployments, making it easier to collaborate with team members, manage state files, and ensure consistency and reliability in your infrastructure.

## 6. Define null resource in Terraform?
The `null_resource` is a Terraform resource type that allows you to define a resource block with no real resource provider associated with it. Instead, it is used as a placeholder for arbitrary operations or as a means to execute arbitrary code during Terraform's apply phase.

The `null_resource` resource is useful when you want to perform a task that is not supported by a built-in Terraform resource. For example, you may want to run a script or command on a local machine as part of your Terraform deployment. In this case, you can use the `null_resource` to define a resource block that runs a local-exec provisioner.

Here's an example of how to use `null_resource` to execute a local script:

```
resource "null_resource" "local_script" {
  provisioner "local-exec" {
    command = "./my-local-script.sh"
  }
}
```

In this example, the `null_resource` block has a local-exec provisioner that runs the `my-local-script.sh` script when Terraform applies the configuration.

Another use case for `null_resource` is to force a refresh of a resource that does not normally require one. For example, you can use a `null_resource` to trigger a refresh of an AWS EC2 instance by defining a `depends_on` attribute that references the EC2 instance resource:

```
resource "aws_instance" "example" {
  ami = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
}

resource "null_resource" "refresh_instance" {
  depends_on = [aws_instance.example]
  triggers = {
    instance_id = aws_instance.example.id
  }
}
```

In this example, the `null_resource` block has a trigger that references the `id` attribute of the `aws_instance` resource. When Terraform applies the configuration, it will refresh the EC2 instance resource even though there are no other changes to the configuration.

Overall, the `null_resource` resource type is a powerful and flexible tool in Terraform that can be used for a variety of tasks, from executing local scripts to forcing resource refreshes.

## 7. How would you recover from a failed apply in Terraform?
When a Terraform `apply` fails, there are a few steps you can take to recover from the failure and continue with your deployment. Here are some general steps to follow:

1. Identify the cause of the failure: Check the error message to understand what went wrong. It could be a syntax error, a resource conflict, or an issue with the Terraform provider.

2. Fix the issue: Once you understand the cause of the failure, fix the issue by updating your Terraform configuration file, updating your provider, or modifying your infrastructure.

3. Destroy the failed resources (if necessary): If the failed apply partially created resources, you may need to destroy those resources before running Terraform apply again. You can do this using the `terraform destroy` command.

4. Retry the `apply`: After fixing the issue and destroying any partially created resources, retry the `apply` command. You can do this by running `terraform apply` again.

5. Consider using a state file backup: If the failure is caused by corruption or deletion of the Terraform state file, consider restoring a backup of the state file. Terraform state file backups are created automatically by default, but you can also create manual backups using the `terraform state pull` and `terraform state push` commands.

It's important to note that when recovering from a failed apply, you should carefully review any changes that were made before retrying the `apply` command to avoid any unintended consequences.

## 8. What do you mean by Terragrunt, list some of its use cases?
Terragrunt is a thin wrapper around Terraform that provides extra functionality and best practices for working with Terraform in production environments. Some of the use cases for Terragrunt are:

1. Simplifying Terraform configurations: Terragrunt provides simple ways to define common Terraform configuration settings like remote state storage, locking, and backend configuration.

2. Managing multiple Terraform modules: Terragrunt allows you to manage multiple Terraform modules in a consistent and reusable way, making it easier to maintain your infrastructure over time.

3. Enforcing version control: Terragrunt supports Git repositories, allowing you to enforce version control and provide better tracking of changes to your infrastructure code.

4. Implementing infrastructure as code best practices: Terragrunt helps enforce infrastructure as code (IaC) best practices like code reuse, separation of concerns, and automation.

5. Automating Terraform workflows: Terragrunt provides a simple way to automate complex workflows with Terraform, including bootstrapping environments, deploying changes, and destroying resources.

Overall, Terragrunt helps simplify the management and automation of Terraform configurations, making it easier to maintain, scale, and collaborate on infrastructure code.

## 9. What is a Remote Backend in Terraform?
In Terraform, a remote backend is a storage location for the state file that Terraform uses to keep track of the resources it manages. By default, Terraform stores the state file locally on the machine where it is running. However, when working with a team or in a more complex infrastructure environment, it's often more convenient to use a remote backend.

A remote backend allows multiple users to share the same state file, which is important for collaboration and consistency in a team environment. It also provides additional features, such as locking to prevent concurrent state modifications and versioning to track changes over time.

Terraform supports several types of remote backends, including Amazon S3, Azure Storage, Google Cloud Storage, and HashiCorp's own Terraform Cloud. To use a remote backend, you need to configure it in your Terraform configuration files and provide the necessary credentials and access details.

Using a remote backend in Terraform can improve collaboration and consistency in infrastructure management, as well as provide additional features like locking and versioning. However, it's important to choose a backend that meets your specific requirements and security needs, and to follow best practices for securing and managing access to the state file.

## 10. What is a Tainted Resource?
In Terraform, a tainted resource is a resource that has been marked as "tainted" due to a failure or an error during the last Terraform apply operation. When a resource is tainted, Terraform considers it to be in an unknown or unreliable state, and will plan to recreate it on the next apply operation.

A resource can become tainted due to various reasons, such as a failure during resource creation or a change in a dependency that invalidates the resource. When Terraform detects a tainted resource, it marks it as such in the state file, and includes it in the plan for the next apply operation, which means that it will be destroyed and recreated.

Terraform's behavior with tainted resources helps to ensure that the infrastructure is consistent and reliable, even in the presence of failures or changes. When a resource is recreated, Terraform will create it from scratch, which helps to ensure that it is in the correct state and configuration.

To avoid tainting resources, it's important to follow best practices for testing and validating infrastructure changes before applying them in production. Additionally, it's important to investigate the cause of the taint and address any underlying issues to prevent it from happening again.

## 11. How to prevent Error Duplicate Resource?
In Terraform, the "Error Duplicate Resource" error occurs when you attempt to create a resource that already exists in your infrastructure. This error can occur if you are re-creating a resource that was previously destroyed or if you have two or more resources with the same name.

To prevent the "Error Duplicate Resource" error, you can follow these best practices:

1. Use unique names for each resource: Make sure that each resource has a unique name across your entire infrastructure. This can be achieved by using naming conventions or by including unique identifiers in the resource names.

2. Use Terraform data sources: Instead of creating new resources, you can use Terraform data sources to reference existing resources in your infrastructure. Data sources allow you to retrieve information about resources that were created outside of Terraform.

3. Use Terraform state files: Make sure that you are using the same state file across all instances of Terraform that are working on the same infrastructure. This ensures that Terraform is aware of all existing resources and can prevent the creation of duplicate resources.

4. Use the "terraform import" command: If you have already created a resource outside of Terraform, you can use the "terraform import" command to import the resource into your Terraform state file. This allows Terraform to manage the resource going forward and prevents the creation of a duplicate resource.

By following these best practices, you can prevent the "Error Duplicate Resource" error in Terraform and ensure that your infrastructure remains consistent and reliable.

## 12. What are the primary responsibilities of Terraform Core?
Terraform Core is responsible for the following primary responsibilities:

1. Configuration Language: Terraform Core defines its own configuration language called HCL (HashiCorp Configuration Language) that is used to describe the infrastructure resources to be managed by Terraform. HCL is designed to be human-readable and easy to learn, allowing users to define infrastructure as code.

2. Resource Management: Terraform Core manages the lifecycle of resources in the infrastructure. It supports a variety of providers (such as AWS, Azure, and Google Cloud Platform) and can manage resources such as virtual machines, networks, load balancers, and more.

3. State Management: Terraform Core keeps track of the state of the infrastructure it manages. This includes the current configuration of resources, as well as any changes that have been made to them. Terraform Core stores this information in a state file, which is used to manage updates and changes to the infrastructure.

4. Plan and Apply: Terraform Core provides the ability to generate an execution plan that shows the proposed changes to the infrastructure resources. Users can review this plan before applying the changes to ensure they are correct. Once the plan is approved, Terraform Core applies the changes to the infrastructure.

5. Module Management: Terraform Core supports modularity by allowing users to organize their infrastructure resources into reusable modules. Users can create and publish modules that can be shared across teams and organizations, making it easier to manage complex infrastructure configurations.

Overall, Terraform Core provides a comprehensive platform for managing infrastructure as code, with features for configuration language, resource management, state management, plan and apply, and module management.

## 13. What if I encounter a serious error and want to rollback?
If you encounter a serious error while running Terraform and need to rollback your infrastructure to a previous state, you can use the "terraform state" command to manage your state files and perform a rollback.

Here are the general steps you can follow to rollback your infrastructure using Terraform:

1. Identify the previous state: Use the "terraform state list" command to list the resources that are currently managed by Terraform. Identify the resource or resources that were affected by the error and note down their resource names and IDs.

2. Revert to the previous state: Use the "terraform state pull" command to download the current state file, and then use a text editor to edit the state file to remove the affected resource or resources. Save the edited state file, and then use the "terraform state push" command to upload the edited state file to the Terraform backend.

3. Apply the previous state: Use the "terraform apply" command to apply the previous state file, which should remove the affected resource or resources and rollback your infrastructure to the previous state.

It is important to note that rolling back your infrastructure using Terraform may have unintended consequences, such as the loss of data or configuration changes. Therefore, it is recommended that you backup your state file before making any changes and carefully review the impact of any changes before applying them.

## 14. What are the ways to lock Terraform module versions?
There are several ways to lock Terraform module versions:

1. Lockfile: Terraform supports generating a `terraform.lock.hcl` file that can be used to lock the version of a module. This file contains the exact version of the module used in the current configuration, and Terraform will use this version during future runs until the lockfile is updated.

2. Provider version constraints: Terraform supports setting version constraints on providers in your configuration using the `version` argument. This ensures that the provider will be compatible with your configuration, and that future updates to the provider will not break your configuration.

3. Terraform Cloud/Enterprise workspaces: If you are using Terraform Cloud or Enterprise, you can create workspaces that are dedicated to a specific version of a module. This allows you to isolate different versions of a module and ensure that changes to one version do not affect other versions.

4. Git tags: You can use Git tags to tag specific versions of your module code. When you reference the module in your Terraform configuration, you can use the Git tag to specify the version of the module to use.

Overall, locking Terraform module versions is an important best practice for managing infrastructure as code, and can help prevent unexpected changes to your infrastructure. By using one or more of the methods above, you can ensure that your Terraform modules are always versioned and controlled.

## 15. What is provider initialization and why do we need it?
Provider initialization is the process of configuring and setting up the provider plugin that Terraform uses to interact with a specific cloud or service provider. When you define a provider block in your Terraform configuration, you are telling Terraform which provider plugin to use and providing the necessary configuration to connect to the provider.

Provider initialization is important because it sets up the foundation for the rest of the Terraform process. Without properly initializing the provider, Terraform would not be able to communicate with the provider and perform any of the desired actions, such as creating, updating, or destroying infrastructure resources.

During provider initialization, Terraform performs several tasks, including:

1. Loading the provider plugin code: Terraform loads the provider plugin code into memory so that it can be executed.

2. Authenticating with the provider: Terraform uses the credentials and other configuration provided in the provider block to authenticate with the provider and establish a connection.

3. Fetching provider metadata: Terraform retrieves metadata from the provider, such as the available resource types and their properties, to enable Terraform to create, read, update, or delete resources.

4. Validating the provider configuration: Terraform checks the provider configuration for any syntax or logical errors, and reports any errors back to the user.

Overall, provider initialization is a critical step in the Terraform process that enables Terraform to interact with cloud or service providers and manage infrastructure resources. Without proper provider initialization, Terraform cannot perform any operations on the provider's resources.

## 16. Interpolation variables:
Interpolation variables are a way to dynamically include values in your Terraform configuration using variables. Interpolation variables are denoted by `${}` syntax, and can be used within strings or as stand-alone values.

For example, let's say you have defined a variable called `region` in your Terraform configuration, and you want to use this variable to define the `ami` ID for an EC2 instance. You could use interpolation variables like this:

```
variable "region" {}

resource "aws_instance" "example" {
  ami           = "ami-${var.region}-xyz"
  instance_type = "t2.micro"
}
```

In this example, the `${var.region}` syntax is used to dynamically include the value of the `region` variable in the `ami` ID for the EC2 instance. This means that if the `region` variable is set to `us-east-1`, the resulting `ami` ID will be `ami-us-east-1-xyz`.

Interpolation variables can also be used within strings to dynamically include values, like this:

```
resource "aws_security_group_rule" "example" {
  type        = "ingress"
  from_port   = 22
  to_port     = 22
  protocol    = "tcp"
  cidr_blocks = ["${var.ip_address}/32"]
}
```

In this example, the `${var.ip_address}` syntax is used to include the value of the `ip_address` variable in the `cidr_blocks` list for the security group rule. This means that if the `ip_address` variable is set to `10.0.0.1`, the resulting `cidr_blocks` list will be `["10.0.0.1/32"]`.

Overall, interpolation variables are a powerful feature of Terraform that enable dynamic configuration of infrastructure resources based on the values of variables.

## 17. Implicit and Explicit dependencies:
In Terraform, dependencies represent the relationships between different resources in the infrastructure. Terraform uses these dependencies to determine the order in which resources should be created or destroyed. There are two types of dependencies in Terraform: implicit and explicit.

Implicit Dependencies:
Implicit dependencies are automatically inferred by Terraform based on the resource configuration. For example, if a resource refers to an attribute of another resource, Terraform automatically creates an implicit dependency between them. When Terraform creates the plan for a configuration, it automatically generates an implicit dependency graph based on the resource configurations.

For example, let's say you have a configuration that creates an EC2 instance and an attached EBS volume:

```
resource "aws_instance" "example" {
  ami           = "ami-0c55b159cbfafe1f0"
  instance_type = "t2.micro"
  subnet_id     = "${aws_subnet.example.id}"

  tags = {
    Name = "Example"
  }
}

resource "aws_ebs_volume" "example" {
  availability_zone = "${var.availability_zone}"
  size              = 10
}
```

In this configuration, the EC2 instance resource has an implicit dependency on the `aws_subnet` resource, because it references the `id` attribute of the `aws_subnet.example` resource. Similarly, the `aws_ebs_volume` resource has an implicit dependency on the `aws_instance` resource, because it is attached to the EC2 instance. Terraform automatically generates a dependency graph based on these implicit dependencies.

Explicit Dependencies:
Explicit dependencies are defined using the `depends_on` argument in a resource block. This argument tells Terraform that a particular resource depends on one or more other resources, even if there is no implicit dependency between them.

For example, let's say you have a configuration that creates an S3 bucket and an SNS topic:

```
resource "aws_s3_bucket" "example" {
  bucket = "example"
}

resource "aws_sns_topic" "example" {
  name = "example"
  
  depends_on = [
    aws_s3_bucket.example
  ]
}
```

In this configuration, the `aws_sns_topic` resource has an explicit dependency on the `aws_s3_bucket.example` resource. This means that Terraform will create the S3 bucket resource first, and only then create the SNS topic resource.

Overall, both implicit and explicit dependencies are important concepts in Terraform that help ensure that resources are created and destroyed in the correct order. Implicit dependencies are automatically inferred by Terraform, while explicit dependencies are defined using the `depends_on` argument.

## 18. 