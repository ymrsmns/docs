# Enabling public access for bucket operations

By default, buckets are created with restricted [access](../../concepts/bucket.md#bucket-access). You can use the management console to enable public access:

{% include [storage-public-operations](../../_includes_service/storage-public-operations.md) %}

{% list tabs %}

- Management console

   1. In the [management console]({{ link-console-main }}), select the appropriate folder.
   1. Select **{{ objstorage-name }}**.
   1. Click the name of the desired bucket.
   1. Go to the **Settings** tab.
   1. Select the type of access for bucket operations.
   1. Click **Save**.

- {{ yandex-cloud }} CLI

   {% include [cli-install](../../../_includes/cli-install.md) %}

   {% include [default-catalogue](../../../_includes/default-catalogue.md) %}

   1. View a description of the CLI command to update a bucket:

      ```bash
      yc storage bucket update --help
      ```

   1. Get a list of buckets in the default folder:

      ```bash
      yc storage bucket list
      ```

      Result:

      ```text
      +------------------+----------------------+-------------+-----------------------+---------------------+
      |       NAME       |      FOLDER ID       |  MAX SIZE   | DEFAULT STORAGE CLASS |     CREATED AT      |
      +------------------+----------------------+-------------+-----------------------+---------------------+
      | first-bucket     | b1gmit33ngp6cv2mhjmo | 53687091200 | STANDARD              | 2022-12-16 13:58:18 |
      +------------------+----------------------+-------------+-----------------------+---------------------+
      ```

   1. Save the name of the bucket using the `NAME` column to enable public access to.
   1. Allow public access to operations with the bucket:

      ```bash
      yc storage bucket update \
        --name <bucket_name> \
        --public-read \
        --public-list \
        --public-config-read
      ```

      Where:
      * `--name`: Name of the bucket to enable public access to.
      * `--public-read`: Flag to enable public read access to bucket objects.
      * `--public-list`: Flag to enable public access to view the list of bucket objects.
      * `--public-config-read`: Flag to enable public read access to the bucket configuration.

      The `name` parameter is required. Other parameters are optional. By default, no public access to buckets is allowed.

      Result:

      ```yaml
      name: first-bucket
      folder_id: b1gmit33ngp6cv2mhjmo
      anonymous_access_flags:
        read: true
        list: true
        config_read: true
      default_storage_class: STANDARD
      versioning: VERSIONING_DISABLED
      max_size: "53687091200"
      acl: {}
      created_at: "2022-12-16T13:58:18.933814Z"
      ```

- {{ TF }}

   {% include [terraform-definition](../../../_tutorials/terraform-definition.md) %}

   
   If you do not have {{ TF }} yet, [install it and configure the {{ yandex-cloud }} provider](../../../tutorials/infrastructure-management/terraform-quickstart.md#install-terraform).


   To enable public access to bucket operations:

   1. Open the {{ TF }} configuration file and add a section called `anonymous_access_flags` to the bucket description fragment.

      ```hcl
      resource "yandex_storage_bucket" "log_bucket" {
        access_key = "<static_key_ID>"
        secret_key = "<private_key>"
        bucket     = "my-tf-log-bucket"

        anonymous_access_flags {
          read = true
          list = false
        }
      }
      ```

      Where:
      * `access_key`: The ID of the static access key.
      * `secret_key`: The value of the secret access key.
      * `read`: Read access to bucket objects.
      * `list`: Access to list of bucket objects.

      For more information about `yandex_storage_bucket` resource parameters in {{ TF }}, see the [provider documentation]({{ tf-provider-link }}/storage_bucket#bucket-anonymous-access-flags).

   1. Make sure that the configuration files are valid.

      1. In the command line, go to the directory where you created the configuration file.
      1. Run the check using the command:

         ```
         terraform plan
         ```

      If the configuration is described correctly, the terminal displays a list of created resources and their parameters. If the configuration contains errors, {{ TF }} will point them out.

   1. Deploy the cloud resources.

      1. If the configuration doesn't contain any errors, run the command:

         ```
         terraform apply
         ```

      1. Confirm the resource creation: type `yes` in the terminal and press **Enter**.

         Afterwards, all the necessary resources are created in the specified folder. You can check that the resources are there with the correct settings using the [management console]({{ link-console-main }}).

{% endlist %}
