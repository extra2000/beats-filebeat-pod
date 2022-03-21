Production Deployment
=====================

Example how to deploy Filebeat for production environment.

Clone repository
----------------

Execute the following command to clone repository:

.. code-block:: bash

    mkdir -pv ~/extra2000
    cd ~/extra2000
    git clone https://github.com/extra2000/beats-filebeat-pod.git

Then, ``cd`` into project root directory:

.. code-block:: bash

    cd beats-filebeat-pod

Build Filebeat Image
--------------------

From the project root directory, ``cd`` into ``deployment/production``:

.. code-block:: bash

    cd deployment/production

Build filebeat image:

.. code-block:: bash

    podman build -t extra2000/elastic/filebeat -f Dockerfile .

Deploy Filebeat
---------------

From the project root directory, ``cd`` into ``deployment/production``:

.. code-block:: bash

    cd deployment/production

Create config files and fix permission:

.. code-block:: bash

    cp -v configmaps/beats-filebeat.yaml{.example,}
    cp -v configs/filebeat.yml{.example,}
    chmod go-w configs/filebeat.yml

Create modules and fix permission:

.. code-block:: bash

    cp -v modules/elasticsearch.yml{.example,}
    chmod go-w modules/*

.. note::

    You don't need to enable all modules. Only create modules that you want to be enabled.

Create pod file:

.. code-block:: bash

    cp -v beats-filebeat-pod.yaml{.example,}

For SELinux platform, label the following files to allow to be mounted into container:

.. code-block:: bash

    chcon -R -v -t container_file_t ./configs ./secrets modules

Load SELinux security policy:

.. code-block:: bash

    sudo semodule -i selinux/beats_filebeat.cil /usr/share/udica/templates/{base_container.cil,net_container.cil}

Verify that the SELinux module exists:

.. code-block:: bash

    sudo semodule --list | grep -e "beats_filebeat"

Deploy filebeat:

.. code-block:: bash

    podman play kube --configmap configmaps/beats-filebeat.yaml --seccomp-profile-root ./seccomp beats-filebeat-pod.yaml

Create systemd files to run at startup:

.. code-block:: bash

    mkdir -pv ~/.config/systemd/user
    cd ~/.config/systemd/user
    podman generate systemd --files --name beats-filebeat-pod
    systemctl --user enable pod-beats-filebeat-pod.service container-beats-filebeat-pod-srv01.service
