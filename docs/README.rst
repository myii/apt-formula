.. _readme:

apt
===

|img_travis| |img_sr|

.. |img_travis| image:: https://travis-ci.com/saltstack-formulas/apt-formula.svg?branch=master
   :alt: Travis CI Build Status
   :scale: 100%
   :target: https://travis-ci.com/saltstack-formulas/apt-formula
.. |img_sr| image:: https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg
   :alt: Semantic Release
   :scale: 100%
   :target: https://github.com/semantic-release/semantic-release

A formula to configure and manage update, upgrade, and dist-upgrade within apt.

.. contents:: **Table of Contents**

General notes
-------------

See the full `SaltStack Formulas installation and usage instructions
<https://docs.saltstack.com/en/latest/topics/development/conventions/formulas.html>`_.

If you are interested in writing or contributing to formulas, please pay attention to the `Writing Formula Section
<https://docs.saltstack.com/en/latest/topics/development/conventions/formulas.html#writing-formulas>`_.

If you want to use this formula, please pay attention to the ``FORMULA`` file and/or ``git tag``,
which contains the currently released version. This formula is versioned according to `Semantic Versioning <http://semver.org/>`_.

See `Formula Versioning Section <https://docs.saltstack.com/en/latest/topics/development/conventions/formulas.html#versioning>`_ for more details.

Contributing to this repo
-------------------------

**Commit message formatting is significant!!**

Please see :ref:`How to contribute <CONTRIBUTING>` for more details.

Available states
----------------

.. contents::
   :local:

``apt.dist_upgrade``
^^^^^^^^^^^^^^^^^^^^

Runs ``apt-get -y dist-upgrade``.

``apt.update``
^^^^^^^^^^^^^^

Runs ``apt-get -y update``.

``apt.upgrade``
^^^^^^^^^^^^^^^

Runs ``apt-get -y upgrade``.

``apt.repositories``
^^^^^^^^^^^^^^^^^^^^

Allows you to configure and manage repositories from pillar. Check ``pillar.example``
to see possible values. If used and no repositories are provided, sane default
values from ``map.jinja`` are used.

Check https://wiki.debian.org/SourcesList for an explanation about the resulting
files structure.

``apt.preferences``
^^^^^^^^^^^^^^^^^^^

Allows you to configure and manage apt's preferences from pillar. Check
``pillar.example`` to see possible values. If used and no repositories are
provided, sane default values from ``map.jinja`` are used.

Check https://wiki.debian.org/AptPreferences?action=show&redirect=preferences
and ``man 5 apt_preferences`` for an explanation about the resulting files structure.

``apt.ppa``
^^^^^^^^^^^
Installs ``python-software-properties``
(``$ /usr/bin/apt-add-repository ppa:user/repository``).

``apt.unattended``
^^^^^^^^^^^^^^^^^^
Installs and configures ``unattended-upgrades``

``apt.transports.debtorrent``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Installs ``apt-transport-debtorrent``.

``apt.transports.https``
^^^^^^^^^^^^^^^^^^^^^^^^
Installs ``apt-transport-https``. **Note that `apt-transport-https` has been deprecated
since Debian 9 and it's now a dummy package**

Testing
-------

Linux testing is done with ``kitchen-salt``.

``kitchen converge``
^^^^^^^^^^^^^^^^^^^^

Creates the docker instance and runs the ``apt`` main state, ready for testing.

``kitchen verify``
^^^^^^^^^^^^^^^^^^

Runs the ``inspec`` tests on the actual instance.

``kitchen destroy``
^^^^^^^^^^^^^^^^^^^

Removes the docker instance.

``kitchen test``
^^^^^^^^^^^^^^^^

Runs all of the stages above in one go: i.e. ``destroy`` + ``converge`` + ``verify`` + ``destroy``.

``kitchen login``
^^^^^^^^^^^^^^^^^

Gives you SSH access to the instance for manual testing.

.. vim: fenc=utf-8 spell spl=en cc=100 tw=99 fo=want sts=2 sw=2 et
