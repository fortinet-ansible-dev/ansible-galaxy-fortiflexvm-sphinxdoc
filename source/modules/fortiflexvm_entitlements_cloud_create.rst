fortiflexvm_entitlements_cloud_create - Create one cloud entitlement based on a FortiFlex Configuration.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1.0

.. contents::
   :local:
   :depth: 1

Synopsis
--------
Create one cloud entitlement on a FortiFlex Configuration. This API is only used to create one cloud entitlement. To modify an entitlement, please refer to fortiflexvm_entitlements_update.

Requirements
------------

The below requirements are needed on the host that executes this module.

- ansible>=2.15


Parameters
----------
.. raw:: html

 <ul>
 <li><span class="li-head">username</span> The username to authenticate. If not declared, the code will read the environment variable FORTIFLEX_ACCESS_USERNAME.<span class="li-normal">type: str</span></li>
 <li><span class="li-head">password</span> The password to authenticate. If not declared, the code will read the environment variable FORTIFLEX_ACCESS_PASSWORD.<span class="li-normal">type: str</span></li>
 <li><span class="li-head">configId</span> The ID of a FortiFlex Configuration.<span class="li-normal">type: int</span><span class="li-normal">required: True</span></li>
 <li><span class="li-head">endDate</span> VM(s) end date. It can not be before today's date or after the program's end date. Any format that satisfies [ISO 8601](https://www.w3.org/TR/NOTE-datetime-970915.html) is accepted. Recommended format is "YYYY-MM-DDThh:mm:ss". If not specify, it will use the program's end date automatically.<span class="li-normal">type: str</span></li>
 </ul>



Examples
-------------

.. code-block:: yaml

  - name: Create cloud entitlement.
    hosts: localhost
    vars:
      username: "<your_own_value>"
      password: "<your_own_value>"
      config_id: 12345
    tasks:
      - name: Create Cloud Entitlement.
        fortinet.fortiflexvm.fortiflexvm_entitlements_cloud_create:
          username: "{{ username }}"
          password: "{{ password }}"
          configId: "{{ config_id }}"
          # endDate: "2024-02-12T00:00:00" # Optional. If not set, it will use the program end date automatically.
        register: result
  
      - name: Display response
        ansible.builtin.debug:
          var: result.entitlements
  


Return Values
-------------
.. raw:: html

 <ul>
 <li><span class="li-head">entitlements</span> A list of virtual machine entitlements and their details.<span class="li-normal">type: list</span><span class="li-normal">returned: always</span></li>
 <ul class="ul-self">
 <li><span class="li-head">accountId</span> The ID of the account associated with the program.<span class="li-normal">type: int</span><span class="li-normal">returned: always</span></li>
 <li><span class="li-head">configId</span> The ID of the virtual machine configuration.<span class="li-normal">type: int</span><span class="li-normal">returned: always</span></li>
 <li><span class="li-head">description</span> The description of the virtual machine.<span class="li-normal">type: str</span><span class="li-normal">returned: always</span></li>
 <li><span class="li-head">endDate</span> The end date of the virtual machine's validity.<span class="li-normal">type: str</span><span class="li-normal">returned: always</span></li>
 <li><span class="li-head">serialNumber</span> The serial number of the virtual machine.<span class="li-normal">type: str</span><span class="li-normal">returned: always</span></li>
 <li><span class="li-head">startDate</span> The start date of the virtual machine's validity.<span class="li-normal">type: str</span><span class="li-normal">returned: always</span></li>
 <li><span class="li-head">status</span> The status of the virtual machine.<span class="li-normal">type: str</span><span class="li-normal">returned: always</span></li>
 <li><span class="li-head">token</span> The token assigned to the virtual machine.<span class="li-normal">type: str</span><span class="li-normal">returned: always</span></li>
 <li><span class="li-head">tokenStatus</span> The status of the token assigned to the virtual machine.<span class="li-normal">type: str</span><span class="li-normal">returned: always</span></li>
 </ul>
 </ul>


Authors
-------

- Xinwei Du (@dux-fortinet)

.. hint::
    If you notice any issues in this documentation, you can create a pull request to improve it.