Running rCDS for an Event
=========================

This section provides a detailed guide on how to set up rCDS for your event, from initializing a managed Kubernetes cluster to promoting an admin team.

Setup Managed Kubernetes Cluster
--------------------------------

1. **Choose a Managed Kubernetes Service**: Select a managed Kubernetes service from providers like Google Kubernetes Engine (GKE), Amazon EKS, or Azure Kubernetes Service (AKS). We used Amazon EKS for the most recent event.

2. **Create the Cluster**: Follow the provider's instructions to create a Kubernetes cluster. Ensure you have enough nodes and resources allocated based on the expected load.

Install Ingress Controller
--------------------------

1. **Install NGINX Ingress Controller**:

   - For detailed instructions and the latest deployment methods for the NGINX Ingress Controller, visit the official Kubernetes NGINX Ingress Controller deployment page at `NGINX Ingress Controller Deployment <https://kubernetes.github.io/ingress-nginx/deploy/>`_.

   - Follow the guidelines specific to your environment to ensure the Ingress Controller is properly set up.

Deploy rCTF using Helm
----------------------

1. **Add the Helm Repository**:

   .. code-block:: bash

      helm repo add rctf https://helm.redpwn.net

2. **Install rCTF**:

   - Prepare a `values.yaml` file specifically for setting proxy configurations, such as port mappings and other network-related settings. This file is essential for customizing how external traffic is managed and routed to the deployment.

   - Deploy rCTF with your custom proxy settings by executing:

     .. code-block:: bash

        helm install rctf rctf/rctf -f values.yaml

This setup emphasizes the use of the `values.yaml` file for configuring network aspects like proxy settings, ensuring that the Helm deployment is aligned with your specific environmental requirements.

Non-rCDS Deployment Setup
-------------------------

1. **Create an Admin Team**:

   - After deploying rCTF, create a team through the platform's user interface.

2. **Promote to Admin**:

   - Access the database associated with rCTF.
   - Update the team's role to 'admin' using a database query:

     .. code-block:: sql

        UPDATE teams SET role='admin' WHERE team_name='your_admin_team_name';

Verification
------------

1. **Verify Installation**:

   - Ensure that all components are running correctly by checking the statuses of all pods and services.
   - Access the rCTF platform through the ingress IP to confirm that the installation is functional.

2. **Test with Sample Challenges**:

   - Deploy a few sample challenges to verify that challenges are being loaded and executed correctly.

.. note::

   It is important to perform a dry run of the setup before the actual event to ensure all components are configured correctly and operational.




Deployment Backends
===================

rCDS uses a pluggable backend model for the task of actually deploying
challenges to infrastructure. rCDS contains a few built-in backends, and
third-party backends may be loaded by specifying their module name.

Backends are specified in the top-level configuration :file:`rcds.yaml`:

.. code-block:: yaml

    backends:
    - resolve: name
      options:
        key: value

The top-level key ``backends`` is an array of backend objects, which consist of
their name (``resolve``) and the options for the backend (``options``).
``resolve`` first attempts to load a built-in backend of the corresponding name,
and, if it does not exist, then interprets the name as a package name and loads
from it.

Each backend may also modify the ``challenge.yaml`` schema---be sure to read
the docs for the backends you are using to understand challenge options specific
to that backend.

.. _backends#scoreboard:

Scoreboard Backends
-------------------

These are responsible for displaying the challenge to competitors; they handle
uploading the challenge's metadata (description, flags, point value, etc) and
any assets that are served to competitors.

- :doc:`rCTF <rctf/index>`

.. _backends#container-runtime:

Container Runtime Backends
--------------------------

These are responsible for running the built challenge containers. By design,
none of the built-in backends will start containers on the machine that rCDS is
being run from.

- :doc:`Kubernetes <k8s/index>`
