1. In the [management console]({{ link-console-main }}), select a folder to create your VM group in.
1. In the list of services, select **{{ ui-key.yacloud.iam.folder.dashboard.label_compute }}**.
1. In the left-hand panel, select ![image](../../_assets/console-icons/layers-3-diagonal.svg) **{{ ui-key.yacloud.compute.switch_groups }}**.
1. Click **{{ ui-key.yacloud.compute.groups.button_create }}**.
1. Under **{{ ui-key.yacloud.compute.groups.create.section_base }}**:
   * Enter a name and description of the instance group. The naming requirements are as follows:

     {% include [name-format](../name-format.md) %}

     {% include [name-fqdn](../compute/name-fqdn.md) %}

   * Select a [service account](../../iam/concepts/users/service-accounts.md) from the list or create a new one. To be able to create, update, and delete VM instances in the instance group, assign the `editor` role to the service account. By default, all operations in {{ ig-name }} are performed on behalf of a service account.

     {% include [sa-dependence-brief](../../_includes/instance-groups/sa-dependence-brief.md) %}

   * Enable the **{{ ui-key.yacloud.compute.groups.create.field_deletion-protection }}** option, if needed. You cannot delete a group with this option enabled.
1. Under **{{ ui-key.yacloud.compute.groups.create.section_allocation }}**, select the required ones in the **{{ ui-key.yacloud.compute.groups.create.field_zone }}** field. VM groups may reside in [different availability zones](../../overview/concepts/geo-scope.md).
1. Under **{{ ui-key.yacloud.compute.groups.create.section_instance }}**, click **{{ ui-key.yacloud.compute.groups.create.button_instance_empty-create }}** to configure a basic instance:
   * Under **{{ ui-key.yacloud.compute.instances.create.section_base }}**, enter a description for the [template](../../compute/concepts/instance-groups/instance-template.md).
   * Under **{{ ui-key.yacloud.compute.instances.create.section_image }}**, select a system to be deployed on the VM instance's boot [disk](../../compute/concepts/disk.md).

   * Under **{{ ui-key.yacloud.compute.instances.create.section_storages }}**:
     * Select the [disk type](../../compute/concepts/disk.md#disks_types).
     * Specify the disk size.
     * To add more disks, click **{{ ui-key.yacloud.compute.component.instance-storage-dialog.button_add-disk }}**.
   * Under **{{ ui-key.yacloud.compute.instances.create.section_platform }}**:
     * Choose a [platform](../../compute/concepts/vm-platforms.md).
     * Enter the required number of vCPUs, [guaranteed vCPU performance](../../compute/concepts/performance-levels.md), and the amount of RAM.

     * {% include [include](specify-preemptible-vm.md) %}
     
     * (Optional) Enable a [software-accelerated network](../../compute/concepts/software-accelerated-network.md).
   * Under **{{ ui-key.yacloud.compute.instances.create.section_network }}**:

     {% include [network-settings-group](../../_includes/compute/network-settings-group.md) %}

   * Under **{{ ui-key.yacloud.compute.instances.create.section_access }}**, specify the data for access to the VM:
     * Select a service account to link to the instance.
     * If you selected a Linux [image](../../compute/concepts/image.md), fill out the fields **{{ ui-key.yacloud.compute.instances.create.field_user }}** and **{{ ui-key.yacloud.compute.instances.create.field_key }}**. For a key, use the contents of the [public key](../../compute/operations/vm-connect/ssh.md#creating-ssh-keys) file.
     * Select `{{ ui-key.yacloud.compute.instances.create.field_serial-port-enable }}`, if needed.
   * Click **{{ ui-key.yacloud.compute.groups.create.button_edit }}**.
1. Under **{{ ui-key.yacloud.compute.groups.create.section_deploy }}**:
   * In the **{{ ui-key.yacloud.compute.groups.create.field_deploy-max-expansion }}** field, specify the number of instances you can exceed the group size by.

       {% include [max-expansion-notice](./max-expansion-notice.md) %}
   * In the field **{{ ui-key.yacloud.compute.groups.create.field_deploy-max-unavailable }}**, specify the number of instances you can decrease the group size by.
   * In the **{{ ui-key.yacloud.compute.groups.create.field_deploy-max-creating }}** field, specify how many instances can be created at the same time.
   * In **{{ ui-key.yacloud.compute.groups.create.field_deploy-startup-duration }}**, specify the period after which the VM instance will start receiving the load.
   * In the **{{ ui-key.yacloud.compute.groups.create.field_deploy-max-deleting }}** field, specify how many instances can be stopped at the same time.
   * In the **{{ ui-key.yacloud.compute.groups.create.field_deploy-strategy }}** field, specify one of the [strategies](../../compute/concepts/instance-groups/policies/deploy-policy.md#strategy):
     * `{{ ui-key.yacloud.compute.groups.create.value_strategy-proactive }}`: {{ ig-name }} itself chooses which instances to stop when updating or scaling down the group.
     * `{{ ui-key.yacloud.compute.groups.create.value_strategy-opportunistic }}`: {{ ig-name }} waits for the instances to stop on their own or be stopped by the user.
1. Under **{{ ui-key.yacloud.compute.groups.create.section_scale }}**:
   * Select the `{{ ui-key.yacloud.compute.groups.create.value_scale-fixed }}` [scaling type](../../compute/concepts/instance-groups/scale.md).
   * Specify the instance group size.
1. If needed, enable the **{{ ui-key.yacloud.compute.groups.create.section_health-check }}** to get information about the state of instances and their automatic recovery on failure.
   * In the **{{ ui-key.yacloud.load-balancer.network-load-balancer.label_health-check-protocol }}** field, select the protocol for the health checks: `{{ ui-key.yacloud.common.label_http }}` or `{{ ui-key.yacloud.common.label_tcp }}`.
   * In the **{{ ui-key.yacloud.load-balancer.network-load-balancer.label_health-check-path }}** field (for the HTTP type), specify the URL path for the HTTP check requests sent from {{ ig-name }}.
   * In the **{{ ui-key.yacloud.load-balancer.network-load-balancer.label_health-check-port }}** field, specify the port number from 1 to 32767 for {{ ig-name }} to send the health check requests to.
   * In the **{{ ui-key.yacloud.load-balancer.network-load-balancer.label_health-check-timeout }}** field, specify the response waiting time from 1 to 60 seconds.
   * In the **{{ ui-key.yacloud.load-balancer.network-load-balancer.label_health-check-interval }}** field, specify the interval between the repeat checks from 1 to 60 seconds. The interval must be at least 1 second longer than the waiting time.
   * In the **{{ ui-key.yacloud.load-balancer.network-load-balancer.label_health-check-healthy-threshold }}** field, specify the number of successful health checks required for the instance to be considered healthy.
   * In the **{{ ui-key.yacloud.load-balancer.network-load-balancer.label_health-check-unhealthy-threshold }}** field, specify the number of failed health checks for the instance to be considered unhealthy.
1. Under **{{ ui-key.yacloud.compute.groups.create.section_variables }}**, enter the `{{ ui-key.yacloud.common.label_key }}`-`{{ ui-key.yacloud.common.value }}` pairs, if needed.
1. Click **{{ ui-key.yacloud.common.create }}**.
