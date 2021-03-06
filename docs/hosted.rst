Hosted Kingfisher
=================

Open Contracting Partnership operates a hosted instance of the Kingfisher tool suite for the use of OCP staff and OCDS Team members. If you think you should have access to this, contact `<mailto:code@opendataservices.coop>`_.

Access
------

You can connect to the server via SSH to run commands, or via a Postgres client to run queries on the database. Details of this are below. 

From time to time, we create development servers to try things out before deploying them. If you're involved in the development of new Kingfisher components, you may be asked to log into the dev server to try things out. If so, substitiute the address of the dev server you've been provided with for the address of the live server in the examples below. 

Over the course of a typical use of Hosted Kingfisher, you'll need to log in to run scrapers, then log out and back in as a different user to run process operations, and potentially connect to Postgres to carry out database operations. 


Access for kingfisher-scrape
----------------------------

If you're running scrapers, SSH in as the *ocdskfs* user::

  ssh ocdskfs@scrape.kingfisher.open-contracting.org

Once logged in, you can run scrapers as per the `kingfisher-scrape documentation <https://kingfisher-scrape.readthedocs.io/en/latest/use-hosted.html>`_


Access for kingfisher-process
-----------------------------

If you're running process operations, SSH in as the *ocdskfp* user::

  ssh ocdskfp@process.kingfisher.open-contracting.org

Once logged in, you can run process operations as per the `kingfisher-process documentation <https://kingfisher-process.readthedocs.io/en/latest/cli.html>`_

You can `browse the information in the web UI. <http://process.ocdskingfisher.opendataservices.coop/app>`_

Access for analysis
-------------------

If you're running analysis operations, SSH in as the *analysis* user::

    ssh analysis@analyse.kingfisher.open-contracting.org

Once logged in, you can take advantage of the powerful server to carry out analysis operations, such as using flatten-tool on files, more quickly than on your local machine. The analysis user has read-only access to the files downloaded by the scrapers. Please remember to delete your files when you're done! 

Access to the archives
----------------------

There is an archive server which contains files that have been downloaded previously but are no longer held on the main server. In almost all cases, the data from them is still in the process database, but they are retained for reference. If you would like to access them, SSH in as the *archive* user::

    ssh archive@archive.kingfisher.open-contracting.org

Access for Postgres Database queries
------------------------------------

In order to access the database, you'll need a Postgres client such as `pgadmin <https://www.pgadmin.org/>`, and some details that are stored on the server. 

To obtain the details, SSH into the server as the *ocdskfp* user (as above), and then run:::
  cat ~/.pgpass

The output contains two lines, for the two different database users that are available. It is recommended that you use the read-only user unless you're making changes to the database. The lines have the format:

localhost:*port*:*database*:*username*:*password*

These should be all the details you need to connect with a Postgres client.

Access for Redash
-----------------

A Redash server is available. Contact Open Data Services for access. 

Access for development
----------------------

If you're developing new scrapers or working on any of the code for Kingfisher, then you may access a development server in order to try things out. The development server is low-spec, so intensive operations may fail. Don't rely on this server address, as it may change, or additional servers may be provided for your use. Please ensure that any development is co-ordinated with Open Data Services Co-Op. 

The development server is at::

    ocdskingfisher-dev.default.opendataservices.uk0.bigv.io

The development server is largely configured in the same way as the production server, so logins and commands should still work in the same way. 

To see the scrapyd web interface, visit: http://scrape.ocdskingfisher-dev.default.opendataservices.uk0.bigv.io/ The username and password can be supplied by Open Data Services Co-op on request.

To see the Process app web interface, visit: http://process.ocdskingfisher-dev.default.opendataservices.uk0.bigv.io/app
