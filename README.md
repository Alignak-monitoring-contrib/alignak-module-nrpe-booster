Alignak NRPE booster module
===========================

*Alignak module to boost NRPE checks*

**This module is not yet available...**

Short description
-------------------

This module allows Alignak Pollers to bypass the launch of the check_nrpe process. 
It reads the check command and opens the connection by itself. 
It scales the use of NRPE for active supervision of servers hosting NRPE agents.


Requirements
-------------------
To use NRPE/SSL install `pyOpenssl` Python wrapper module with the OpenSSL library.


Configuration
-------------------

No configuration is necessary for this module::

    define module{
        module_alias    nrpe_booster
        python_name     alignak_module_nrpe_booster
    }

Configure an Alignak poller to use this module:

    - edit your poller daemon configuration file
    - add the `module_alias` parameter value (`nrpe_booster`) to the `modules` parameter of the daemon

Tag the NRPE commands with the `module_type` parameter::

    define command {
        command_name   check_nrpe
        command_line   $USER1$/check_nrpe -H $HOSTADRESS$ -c $ARG1$ -a $ARG2$
        module_type    nrpe_poller
    }


Bugs, issues and contributing
----------------------------------------

Please report any issue using the project `GitHub repository: <https://github.com/Alignak-monitoring-contrib/alignak-module-backend/issues>`_.

License
----------------------------------------

Alignak Backend Modules is available under the `GPL version 3 <http://opensource.org/licenses/GPL-3.0>`_.

