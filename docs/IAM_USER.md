## IAM USER

Provides an IAM user.

## Example of usage

```hcl
resource "minio_iam_user" "test" {
   name = "test"
   force_destroy = true

   tags = {
    tag-key = "tag-value"
  }
}

output "test" {
  value = "${minio_iam_user.test.id}"
}

output "status" {
  value = "${minio_iam_user.test.status}"
}

output "secret" {
  value = "${minio_iam_user.test.secret}"
}
```

## Argument Reference

The following arguments are supported:

* **name** - (Required) The user's name. The name must consist of upper and lowercase alphanumeric characters with no spaces. You can also include any of the following characters: =,.@-_.. User names are not distinguished by case. For example, you cannot create users named both "TESTUSER" and "testuser".
* **force_destroy** - (Optional, default false) When destroying this user, destroy even if it has non-Terraform-managed IAM access keys, login profile or MFA devices. Without force_destroy a user with non-Terraform-managed access keys and login profile will fail to be destroyed.
* **disable_user** - (Optional, default false) Disable a user. If the user is disabled and you add the flag equals to false, it enables a user back.
* **update_secret** - (Optional, default false) Rotation key. Generates a new secret for current user. 
* **tags** - Key-value mapping of tags for the IAM user.

## Output

The following outputs are supported:

* **id** - (Optional) Returns a user's id. It's same of user name.
* **status** - (Optional) Returns a user's status: enable or disable.
* **secret** - (Optional) Returns a user's secret. This option is enabled only when generates a new user.
* **name** - (Optional) Returns a user's name. Same of user's id.
