---
title: Deleting API keys
description: Follow this guide to delete an API key.
---

# Deleting API keys

{% list tabs group=instructions %}

- Management console {#console}

  1. In the [management console]({{ link-console-main }}), navigate to the folder the service account belongs to.
  1. In the list of services, select **{{ ui-key.yacloud.iam.folder.dashboard.label_iam }}**.
  1. In the left-hand panel, select ![FaceRobot](../../../_assets/console-icons/face-robot.svg) **{{ ui-key.yacloud.iam.label_service-accounts }}** and select the required service account.
  1. Under **{{ ui-key.yacloud.iam.folder.service-account.overview.section_api_keys }}**, click ![image](../../../_assets/console-icons/ellipsis.svg) in the line with the API key to delete, and select **{{ ui-key.yacloud.iam.folder.service-account.overview.button_action-delete-api-key }}**.
  1. In the window that opens, confirm the deletion.

- CLI {#cli}

    {% include [cli-install](../../../_includes/cli-install.md) %}

    1. Get a list of API key `ID`s for a specific service account. Specify the service account name in the `--service-account-name` parameter:

        ```bash
        yc iam api-key list --service-account-name <service_account_name>
        ```

        Result:

        ```text
        +----------------------+---------------------+
        |          ID          |     CREATED AT      |
        +----------------------+---------------------+
        | ajenhvftf77r******** | 2022-03-13 21:15:40 |
        | ajeq610sgh05******** | 2022-03-13 21:14:43 |
        +----------------------+---------------------+
        ```

        The folder specified in the CLI profile is used by default to search for the service account. You can specify a different folder using the `--folder-name` or `--folder-id` flag.

    1. Delete the old API key. Replace `<ID>` with your API key ID:

        ```bash
        yc iam api-key delete <ID>
        ```

- {{ TF }} {#tf}

    {% include [terraform-install](../../../_includes/terraform-install.md) %}

    1. Open the {{ TF }} configuration file and delete the fragment with the API key description.

        Example API key description in the {{ TF }} configuration:

        ```hcl
        resource "yandex_iam_service_account_api_key" "sa-api-key" {
            service_account_id = "<service_account_ID>"
            description        = "<key_description>"
            pgp_key            = "<PGP_key>"
        }
        ```

    1. Delete the record with information about the resource.

        For more information about the resources you can create with {{ TF }}, see the [provider documentation]({{ tf-provider-resources-link }}/iam_service_account_api_key).

    1. Make sure the configuration files are correct.

        1. In the command line, go to the folder where you created the configuration file.
        1. Run a check using this command:

            ```bash
            terraform plan
            ```

        If the configuration is described correctly, the terminal will display a list of created resources and their parameters. If the configuration contains any errors, {{ TF }} will point them out.

    1. Deploy cloud resources.

        1. If the configuration does not contain any errors, run this command:

            ```bash
            terraform apply
            ```

        1. Confirm creating the resources: type `yes` in the terminal and press **Enter**.

        All the resources you need will then be created in the specified folder. You can check the new resources and their settings using the [management console]({{ link-console-main }}) and this CLI command:

        ```bash
        yc iam key list --service-account-id <service_account_ID>
        ```

- API {#api}

  Delete the API key using the [delete](../../api-ref/ApiKey/delete.md) REST API method for the [ApiKey](../../api-ref/ApiKey/index.md) resource:

    ```bash
    export APIKEY_ID=ajeke74kbp5b********
    export IAM_TOKEN=CggaATEVAgA...
    curl \
        --request DELETE \
        --header "Authorization: Bearer $IAM_TOKEN" \
        https://iam.{{ api-host }}/iam/v1/apiKeys/$APIKEY_ID
    ```
   You can also delete the API key using the [ApiKeyService/Delete](../../api-ref/grpc/ApiKey/delete.md) gRPC API call.

{% endlist %}
