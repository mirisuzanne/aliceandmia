Alice & Mia – Coming Soon!
==========================

aliceandmia.com

Welcome to the collaborative
writing and (future) podcasting
of trans-feminine authors
[Allison Washington][alice] &amp; [Miriam Suzanne][mia] –
exploring gender and transition
separated by a quarter-century.

[alice]: http://allisonwashington.net
[mia]: http://miriamsuzanne.com


Development
-----------

If you want to run this project in a [virtualenv]
to isolate it from other Python projects on your system,
create a virtualenv and activate it.
Then run ``pip install -r requirements.txt``
to install the dependencies for this project
into your Python environment.

[virtualenv]: http://www.virtualenv.org

Run ``yarn`` to install
all the required npm packages
for linting and compiling Sass.

To view the site live locally,
run ``make serve`` to watch rst content files,
or ``gulp`` to watch and compile Sass files as well —
then visit ``http://localhost:5000`` in your browser.

To regenerate the site as static HTML files
under the ``docs/`` directory,
run ``make build``.


Deployment
----------

Commit the changes, and push to master!
