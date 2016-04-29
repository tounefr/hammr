.. Copyright (c) 2007-2016 UShareSoft, All rights reserved

.. _stack-os:

os
==

Within a ``stack``, the ``os`` sub-section describes the operating system to use when building the machine image. This includes the operating system version, architecture and the os profile to use. The os profile is a pre-determined group of packages that will be installed as part of the machine image build. Extra packages can be specified to include in the build that are available in the operating system repository, and the build date can be set to get the latest updates, or roll-back. For more information on os package updates, refer to :ref:`pkg-updating`.

To use a particular operating system, you must have access to it in the UForge server you are using. To determine which operating systems are available, use the ``os list`` command (please refer :ref:`command-line` for more information).

The definition of an os section is:

.. code-block:: javascript

	"os": {
	    ...the os definition goes here.
	}

The valid keys to use within the os object are:

* ``arch`` (mandatory): a string providing the architecture to use
* ``name`` (mandatory): a string providing the name of the operating system to use
* ``pkgs`` (optional): an array providing any extra packages to install (see pkgs key sub-section for more information)
* ``profile`` (mandatory): a string providing which operating system profile to use
* ``updateTo`` (optional): a string providing the date where package versions should be calculated (determines which package versions to use to * calculate the package dependency tree)
* ``version`` (mandatory): a string providing the version of the operating system to use

Sub-Sections
------------

The ``os`` sub-sections are:

.. toctree::
   :titlesonly:

   stack-os-pkgs


Examples
--------

Basic Example
~~~~~~~~~~~~~

The following example describes using CentOS 6.4 64 bit operating system for the template. The profile ``Minimal`` is used, which automatically adds a pre-determined group of packages to the template.

.. code-block:: json

	{
	  "os": {
	    "name": "CentOS",
	    "version": "6.4",
	    "arch": "x86_64",
	    "profile": "Minimal"
	  }
	}

The name, version, arch and profile values for an operating system can be found by using the command ``os list``. This lists all the operating systems you have access to.

Specifying a Build Date
~~~~~~~~~~~~~~~~~~~~~~~

By using the ``updateTo`` key will specify the date to calculate the version and release of all the packages to use in the template during the build phase of a machine image. This allows you to roll-back or update the operating system packages used. If no date is provided, then the date the template is created is used. The example below sets the date to 14 May 2014.

.. code-block:: json

	{
	  "os": {
	    "name": "CentOS",
	    "version": "6.4",
	    "arch": "x86_64",
	    "profile": "Minimal"
	    "updateTo": "2014-05-14"
	  }
	}