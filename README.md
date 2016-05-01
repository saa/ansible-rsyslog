bvansomeren.rsyslog
=========

Installs rsyslog. Optionally with TLS.

Requirements
------------

None; Current implementation might be CentOS specific but should be easy to adjust for other `rsyslog` based systems

Role Variables
--------------

Here are some of the included defaults:

	ryslog_packages:
	- rsyslog
	- rsyslog-gnutls

Enables TLS and will include dependencies (gnu-tls)

	rsyslog_hostname: localhost

The host that all logging should be forwarded to

	rsyslog_port: 514

The port that all logging should be forwarded to

	rsyslog_conf: []

A dict with all the "name" and "config" values you want to add to rsyslog.conf

	rsyslog_ca_url:

Optional URL to download the CA cert from for TLS support

	rsyslog_ca_file: "/etc/rsyslog-ca.pem"

Optional name and location where to store the downloaded CA cert

	rsyslog_ca_hash:

Optional checksum of type <algorithm>:<checksum>  

Dependencies
------------


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: bvansomeren.rsyslog }
      vars:
	 rsyslog_enable_tls: yes
	 rsyslog_host: logs.papertrailapp.com
	 rsyslog_port: ****
	 rsyslog_ca_url: "https://papertrailapp.com/tools/papertrail-bundle.pem"
	 rsyslog_ca_file: "/etc/papertrail-bundle.pem"
	 rsyslog_ca_hash: "md5:c75ce425e553e416bde4e412439e3d09"
	 rsyslog_conf:
	 - name: "$ActionSendStreamDriver"
	   config: "gtls"
	 - name: "$ActionSendStreamDriverMode"
	   config: "1"
	 - name: "$ActionSendStreamDriverAuthMode"
	   config: "x509/name"
	 - name: "$ActionSendStreamDriverPermittedPeer"
	   config: "*.papertrailapp.com"
	 - name: "$ActionResumeInterval"
	   config: "10"
	 - name: "$ActionQueueSize" 
	   config: "100000"
	 - name: "$ActionQueueDiscardMark" 
	   config: "97500"
	 - name: "$ActionQueueHighWaterMark" 
	   config: "80000"
	 - name: "$ActionQueueType" 
	   config: "LinkedList"
	 - name: "$ActionQueueFileName" 
	   config: "papertrailqueue"
	 - name: "$ActionQueueCheckpointInterval" 
	   config: "100"
	 - name: "$ActionQueueMaxDiskSpace"
	   config: "2g"
	 - name: "$ActionResumeRetryCount"
	   config: "-1"
	 - name: "$ActionQueueSaveOnShutdown"
	   config: "on"
	 - name: "$ActionQueueTimeoutEnqueue" 
	   config: "10"
	 - name: "$ActionQueueDiscardSeverity"
	   config: "0"
	 

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
