
# _Terraform Module: terraform-module-aws-vpc-nat-gateway_
_Terraform module for **_AWS VPC NAT Gateway_**_


<!--BEGIN STABILITY BANNER-->
---

![_Code : Stable_](https://img.shields.io/badge/Code-Stable-brightgreen?style=for-the-badge&logo=github)

> **_This is a stable example. It should successfully build out of the box_**
>

---
<!--END STABILITY BANNER-->

## _General_

_This module can be used to deploy a_ **_VPC NAT Gateway_** _on AWS Cloud Provider......_


---

## _Prerequisites_

_This module needs **_Terraform 0.12.23_** or newer._
_You can download the latest Terraform version from_ [_here_](https://www.terraform.io/downloads.html).



---

## _Features Branches_

_Below we are able to check the resources that are being created as part of this module call:_

- **_VPC NAT Gateway_**


---

## _Usage_

## _Using this repo_

_To use this module, add the following call to your code:_

- **_Sample Code:_**

```tf
module "vpc_nat_gateway" {
  source = "git::https://github.com/nitinda/terraform-module-aws-vpc-nat-gateway.git?ref=master"

  allocation_id = var.allocation_id
  subnet_id     = var.subnet_id
  tags          = {
    Environment = "prod"
    Project     = "POC"
  }
}

```

```tf
module "vpc_nat_gateway" {
  source = "git::https://github.com/nitinda/terraform-module-aws-vpc-nat-gateway.git?ref=master"

  allocation_id = aws_eip.nat.id
  subnet_id     = aws_subnet.public.id
  tags          = {
    Environment = "prod"
    Project     = "POC"
  }
}

```

```tf
module "vpc_nat_gateway_private_1a" {
  source = "git::https://github.com/nitinda/terraform-module-aws-vpc-nat-gateway.git?ref=master"

  allocation_id = module.eip_nat_gateway_1a.id
  subnet_id     = module.vpc_subnet_public_1a.id
  tags          = merge(
    var.common_tags,
    {
      Environment = "prod"
      Name        = "rabbitmq-vpc-internet-gateway"
    }
  )
}
```


---

## _Inputs_

_The variables required in order for the module to be successfully called from the deployment repository are the following:_

|**_Variable_** | **_Description_** | **_Type_** | **_Argument Status_** | **_Default Value_** |
|:----|:----|-----:|:---:|:---:|
| **_allocation\_id_** | _The Allocation ID of the Elastic <br/> IP address for the gateway_ | _string_ | **_Required_** |  |
| **_subnet\_id_** | _The Subnet ID of the subnet <br/> in which to place the gateway._ | _string_ | **_Required_** |  |
| **_tags_** | _A mapping of tags to assign to the resource_ | _map(string)_ | **_Optional_** | **_{}_** |


---


## _Outputs_

### _General_

_This module has the following outputs:_

* **_id_**
* **_allocation\_id_**
* **_public\_ip_**
* **_network\_interface\_id_**

---

### _Usage_

_In order for the variables to be accessed at module level please use the syntax below:_

```tf
module.<module_name>.<output_variable_name>
```


_The output variable is able to be accessed through terraform state file using the syntax below:_

```tf
data.terraform_remote_state.<layer_name>.<output_variable_name>
```

---



## _Authors_

_Module maintained by Module maintained by the -_ **_Nitin Das_**
