# Nagios-Release

## Overview
A simple nagios script to check the release version of a server against the stable/LTS versions.

## Authors
Ahmed Ismail < aismail> - (at) - auto.tuwien.ac.at

## Usage
### Install on Client Server
--  Copy the script to the client server's libexec folder and make sure it is executable by the nrpe-configured user:
<pre><code>
cp check_release /usr/local/nagios/libexec/
chown nagios:nagios check_release
chmod +x check_release
</code></pre>

-- Edit your nrpe.cfg file on the client server to add the command:
<pre><code>
command[check_release]= /usr/local/nagios/libexec/check_release
</code></pre>
### Configure Nagios Server
-- Edit the client's .cfg file on the Nagios server to monitor the check_release service:
<pre><code>
define service {
        use                             generic-service
        host_name                       trolldin
        service_description             Check Release
        check_command                   check_nrpe!check_release
        notifications_enabled           0
}
</code></pre>

## Limitations 
Currently limited to Ubuntu & Debian.

Release versions are currently statically configured.

