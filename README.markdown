puppet-bundler
==============

Install ruby dependencies through Puppet.


Dependencies
------------

- The [`ruby` module](https://github.com/puppetlabs/puppetlabs-ruby) has to be installed alongside this module.


Example
-------

    bundler::install { $app_root:
      user       => $app_user,
      group      => $app_group,
      deployment => true,
      without    => 'development test doc',
    }


Additional options from this fork
---------------------------------

    timeout => 3600,

Installing dependencies can be long on a first run if you start having many of them. Don't hesitate to increase the timeout if that's your case.

    logoutput => true,

If you're in an environment timing outputs to detect stalled processes, puppet-bundler can look like it is stuck. You can also be interested in detecting the slowest gems to install.
If `logoutput` is set to `true`, one line will be output per gem.
