---
title: How to get information about {{ interconnect-name }} private connections
---

# Getting information about private connections

{% include [cic-api-access](../../_includes/interconnect/cic-api-access.md) %}

{% list tabs group=instructions %}

- CLI {#cli}

  {% include [cli-install](../../_includes/cli-install.md) %}

  {% include [default-catalogue](../../_includes/default-catalogue.md) %}

  1. See the description of the CLI command to get the information about [private connections](../concepts/priv-con.md):

      ```bash
      yc cic private-connection get --help
      ```

  1. Get a list of private connections in the specified folder:

     ```bash
      yc cic private-connection list --folder-id b1gqf2hjizv2jwj4dnga
      ```

      Result:

      ```text
      +----------------------+--------------------+----------------------+
      |          ID          |        NAME        | TRUNK CONNECTION ID  |
      +----------------------+--------------------+----------------------+
      | euuiog88zphgsq3c15pq | customer-name-prc1 | euuqqctbrflq3ir4n4p2 |
      | euucr7p47329kqxrp4kh | customer-name-prc2 | euuvdjl5shd0fv7bqt38 |
      +----------------------+--------------------+----------------------+      
      ```

  1. Get information about the private connection by specifying its ID obtained in the previous step:

      ```bash
      # yc cic private-connection get <private_connection_ID>
      yc cic private-connection get euuiog88zphgsq3c15pq 
      ```

      Result:

      ```yml
      id: euuiog88zphgsq3c15pq
      name: customer-name-prc1
      folder_id: b1gqf2hjizv2jwj4dnga
      region_id: ru-central1
      trunk_connection_id: euuqqctbrflq3ir4n4p2
      vlan_id: "1531"
      ipv4_peering:
        peering_subnet: 10.211.10.0/30
        peer_ip: 10.211.10.1
        cloud_ip: 10.211.10.2
        peer_bgp_asn: "64515"
        cloud_bgp_asn: "200350"
      ```

      Where:
      * `id`: Private connection ID.
      * `name`: Private connection name.
      * `folder_id`: ID of the cloud folder the private connection was created in.
      * `region_id`: Region of the cloud the private connection was created in.
      * `trunk_connection_id`: Trunk connection ID the private connection belongs to.
      * `vlan_id`: VLAN ID for the private connection
      * IP and BGP connectivity parameters for the private connection’s point-to-point subnet:
         * `peering_subnet`: [Point-to-point subnet](../../interconnect/concepts/priv-con.md#priv-address) for BGP peering.
         * `peer_ip`: IP address of the point-to-point (peered) subnet on the customer's equipment.
         * `cloud_ip`: IP address of the point-to-point (peered) subnet on the {{ yandex-cloud }} equipment.
         * `peer_bgp_asn`: [BGP ASN](../../interconnect/concepts/priv-con.md#bgp-asn) on the customer's equipment.
         * `cloud_bgp_asn`: BGP ASN on the {{ yandex-cloud }} equipment.

{% endlist %}
