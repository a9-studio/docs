---
title: How to get a list of public images in {{ compute-full-name }}
description: Follow this guide to get a list of public images in {{ compute-full-name }}.
---

# Getting a list of public images

When creating a VM, you need to select its [image](../../concepts/image.md) with the software that you want to use.

{% list tabs group=instructions %}

- Management console {#console}

  You can view a list of public images when creating a virtual machine:

  1. In the [management console]({{ link-console-main }}), select the folder to create the virtual machine in.
  1. At the top right, click **{{ ui-key.yacloud.iam.folder.dashboard.button_add }}**.
  1. In the list that opens, select **{{ ui-key.yacloud.iam.folder.dashboard.value_compute }}**.
  1. Under **{{ ui-key.yacloud.compute.instances.create.section_image }}**, click **{{ ui-key.yacloud.compute.instances.create.button_show-all-marketplace-products }}**. A list of all available public images will appear.

  To [view information](./get-info.md) about a specific image, click ![image](../../../_assets/console-icons/circle-info.svg).

- CLI {#cli}

  {% include [cli-install](../../../_includes/cli-install.md) %}

  {% include [standard-images](../../../_includes/standard-images.md) %}

- API {#api}

  1. Get an [IAM token](../../../iam/concepts/authorization/iam-token.md) used for authentication in the examples:
     * [Guide](../../../iam/operations/iam-token/create.md) for users with a Yandex account.
     * [How to get a token](../../../iam/operations/iam-token/create-for-sa.md) for a service account.
     * [How to get a token](../../../iam/operations/iam-token/create-for-federation.md) for a federated account.
  1. Get the list of public images from {{ yandex-cloud }} using the [list](../../api-ref/Image/list.md) REST API method for the [Image](../../api-ref/Image/index.md) resource or the [ImageService/List](../../api-ref/grpc/Image/list.md) gRPC API call. In the request, specify the following parameters:
     * Specify `standard-images` as the folder ID.
     * The folder contains many images, so specify `pageSize=1000` or use the obtained value of `nextPageToken` to get the next page.

    Write the result to a file, e.g., `output.json`:

    ```bash
    export IAM_TOKEN=CggaATEVAgA...
    curl \
      --header "Authorization: Bearer ${IAM_TOKEN}" \
      "https://compute.{{ api-host }}/compute/v1/images?folderId=standard-images&pageSize=1000" > output.json
    ```

{% endlist %}

You can also view information about all available public images in [{{ marketplace-name }}](/marketplace).
