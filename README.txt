The following instructions can be used to get the moodgenie up and running.

1. WampServer2 can be used to setup a PHP/Mysql Webserver on nearly any desktop machine
	This requires some configuration knowledge.
	The default PHP5 options should work
	register_globals = off
	magic_quotes_gpc = off
	enable the mysqli extension in PHP

2. Connection to Mysql With a user who has 'create database' priviledges
	The default root user on Wamp2 installation will work fine.

3. Run /moodgenie/dbschema.sql
	Mysql5 is required for the triggers in the dbschema.sql to install correctly.  However they 		are not critical to the functionality.


4. Setup a webserver (localhost) is acceptable.  Php5 is required with mod_rewrite turned enabled

5. Configure /public to serve as the document root
	/application + /library should be below the document root

	Configure a vhost for the moodgenie:

	Sample VHOST configuration included:


	<VirtualHost *>
        	DocumentRoot    "C:\wamp\www\moodgenie\public"
        	ServerName      local.moodgenie.com
	
        	<Directory C:\wamp\www\moodgenie\public>
		  	DirectoryIndex index.php index.html
		   	Options Indexes FollowSymLinks Includes ExecCGI
    		   	AllowOverride All
			Order allow,deny
			Allow from all
	        </Directory>
	</VirtualHost>
	
	NOTE: This VHOST setup on a local box requires and additional line be added to a windows/linux hosts file

	Example: c:\windows\system32\drivers\etc\hosts
	Append line: 127.0.0.1	local.moodgenie.com


6. Open /application/configuration/configuration.ini
	Modify the database connection settings per your mysql configuration


7. Using internet explorer Visit http://localhost/ or the URL for the virtual host you have configured.

8. Register a new user, or use the username/password: newguy / newguy


Note: Please use IE 7.  It appears there is a bug in prototype1602 or possibly firefox 3.0.1 causing problems with XMLRPC.  Additional time would be needed to troubleshoot this.  