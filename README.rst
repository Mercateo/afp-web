AFP-WEB
=======

What it is?
-----------
This is a web frontend, which communicates with the aws federation proxy (afp)
via its rest api and displays the results:

* Give an overview of all available accounts and their usable
  roles for the logged in user
* Get and show temporary credentials for the selected account and role
* Automatic login to the aws management console for the desired account

Configuration & Setup
---------------------
Webserver
^^^^^^^^^
The files should be made accessible for your webserver. How is up to you.
For example in a vhost with:

.. code-block:: apache

  DocumentRoot '/var/www/afp-web'

API access
^^^^^^^^^^
Use the ``app.js`` file to configure the location of the ``afpApiEndpoint``.
By default uses the same host as this webui with an endpoint of ``/afp-api/latest/``

Logo configuration
^^^^^^^^^^^^^^^^^^
If you want to replace the default logo just put a image file called
``logo.png`` into the ``DocumentRoot``.

Costs link
^^^^^^^^^^
For each account afp-web can show a link to your own AWS costs dashboard. To enable this feature create a ``config.json`` file at the top of your ``DocumentRoot`` with this content:

.. code-block:: json

    {
        "costsLink": "http://ice/ice/dashboard/summary#account="
    }

The name of the AWS account will be appended to this URL.

Development
-----------

* Install node
* go to the ``devel`` subdirectory
* ``npm install apimocker``
* Use ``node node_modules/apimocker/bin/apimocker.js -c config.json`` to start the apimocker web server
* Point your browser to http://localhost:8080

Copyrights
^^^^^^^^^^
* The CSS spinner (throbber.css) was taken from https://github.com/jlong/css-spinners.git
* AngularJS v1.4.3 (Licensed under MIT) http://angularjs.org
* Bootstrap v3.3.5 (Licensed under MIT) https://github.com/twbs/bootstrap/blob/master/LICENSE
