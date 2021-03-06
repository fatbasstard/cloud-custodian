.. _azure_examples_routetable_with_subnet:

Find Route Tables With A Specific Subnet
============================================

Returns all route tables that route to the subnet named `subnetname` in the virtual network named `vnetname`.
Since the relationship between route tables and subnets is one-to-many, there will only ever be 0 or 1
route tables associated with a given subnet.

.. code-block:: yaml

     policies:
       - name: routes-to-specific-subnet
         resource: azure.routetable
         filters:
           - type: value
             key: properties.subnets[?ends_with(id, 'vnetname/subnets/subnetname')] | [0]
             value: not-null

