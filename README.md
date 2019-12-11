# A PERSONAL SETUP GUIDE

## LetsEncrypt + OrganizrV2 + Fail2Ban + NZB360
Features:
 - [SSLLabs.com](https://www.ssllabs.com/): **A+** rating
 - Access Organizr via HTTPS/SSL
 - Banning via Fail2ban and basic auth
 - NZB360 android app (mobile access)
 - GeoLite2 (Country blocking)
 - Plex SSO (Organizr > Plex Tab > Logged In)
 - Organizr V2 style custom error pages
 - Setup focusing on the following apps: Radarr/Sonarr/Lidarr/NZBGet/Transmission/Guacamole/Plex/Jackett/Ombi/LazyLibrarian

## Prerequisites
 - Own a domain (i.e., MYDOMAIN.com) - I like [Google Domains](https://domains.google/).
 - Installed unRAID with dockers of choice setup.
 - Port forwarding for LetsEncrypt (80/443) and Plex (32400).
 - A good code editor. I recommend [Notepad++](https://notepad-plus-plus.org/).

## Before your start
 - You will be editing files in the unRAID dockers. Make backups.
 - Create a working directory outside of unRAID. You will edit this files. When changes are made to a file copy them over to the corresponding unRAID directory and restart the docker to test.
 - Remember to go over IP address and port numbers and change them as needed for your setup.
 - All MYDOMAIN references should be changed to your domain.

## Let's Encrypt
Go to the unRAID letsencrypt docker folder. Go the the nginx/site-confs folder. You will be editing the “[default](https://github.com/aircave/OrganizrV2-aircave-SAMPLE/tree/master/unraid-dockers/letsencrypt/nginx/site-confs)” file. 

 1. The 1st "SERVER BLOCK" part redirects unencrypted HTTP traffic to HTTPS/SSL.
 2. The 2nd "MAIN SERVER BLOCK" gives general instructions and negotiates encryption.
 3. The 3rd "SUBDIRECTORIES" part gives access to specific dockers after logging in to OrganizrV2.
