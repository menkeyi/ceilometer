Enable Block Storage meters for openSUSE and SUSE Linux Enterprise
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Telemetry uses notifications to collect Block Storage service meters.
Perform these steps on the controller and Block Storage nodes.

.. note::

   Your environment must include the Block Storage service.

Configure Cinder to use Telemetry
---------------------------------

Edit the ``/etc/cinder/cinder.conf`` file and complete the
following actions:

* In the ``[oslo_messaging_notifications]`` section, configure notifications:

  .. code-block:: ini

     [oslo_messaging_notifications]
     ...
     driver = messagingv2

Finalize installation
---------------------

#. Restart the Block Storage services on the controller node:

   .. code-block:: console

      # systemctl restart openstack-cinder-api.service openstack-cinder-scheduler.service

#. Restart the Block Storage services on the storage nodes:

   .. code-block:: console

      # systemctl restart openstack-cinder-volume.service

#. Use the ``cinder-volume-usage-audit`` command on Block Storage nodes
   to retrieve meters on demand. For more information, see the
   `OpenStack Administrator Guide <http://docs.openstack.org/admin-guide/
   telemetry-data-collection.html#block-storage-audit-script-setup-to-get-
   notifications>`__.
