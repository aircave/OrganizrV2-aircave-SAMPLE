# A PERSONAL SETUP GUIDE - A WIP

## [LetsEncrypt](https://github.com/linuxserver/docker-letsencrypt) + [OrganizrV2](https://github.com/causefx/Organizr) + [Fail2Ban](https://github.com/fail2ban/fail2ban) + [NZB360](https://nzb360.com/) + [GeoLite2](https://dev.maxmind.com/geoip/geoip2/geolite2/)
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
 - Installed [unRAID](https://unraid.net/) with [dockers](https://forums.unraid.net/topic/38582-plug-in-community-applications/) of choice setup. And base URLS added where possible.
 - Port forwarding for LetsEncrypt (80/443) and Plex (32400).
 - Give LE access to the following folder: /appdata/organizrv2/www/db
 - A good code editor. I recommend [Notepad++](https://notepad-plus-plus.org/).

## Before your start
 - You will be editing files in the unRAID dockers. Make backups.
 - Create a working directory outside of unRAID. You will edit this files. When changes are made to a file copy them over to the corresponding unRAID directory and restart the docker to test.
 - Remember to go over IP address and port numbers and change them as needed for your setup.
 - All MYDOMAIN references should be changed to your domain.

## Let's Encrypt
Go to the unRAID letsencrypt docker folder. Go to the letsencrypt/nginx/site-confs folder. You will be editing the “[default](https://github.com/aircave/OrganizrV2-aircave-SAMPLE/tree/master/unraid-dockers/letsencrypt/nginx/site-confs)” file. Copy and paste into your default file and change DOMAIN, UNRAID IP and docker PORT numbers as needed.

 - The 1st "SERVER BLOCK" part redirects unencrypted HTTP traffic to HTTPS/SSL.
 - The 2nd "MAIN SERVER BLOCK" gives general instructions and negotiates encryption.
 - The 3rd "SUBDIRECTORIES" part gives access to specific dockers after logging in to OrganizrV2.
	 - Change "auth_request /auth-4;" number as needed; See note inside default file on this
	 - You may also change the main server block to only allow certain users by changing the "(.*)"
	 - Adjust blocks with auth_request off; as needed.
  
Go to the letsencrypt/nginx folder. You will need the nginx, geoblock and geoblocksites files.
You already have an nginx file, so you just have to [uncomment line 24](https://github.com/aircave/OrganizrV2-aircave-SAMPLE/blob/master/unraid-dockers/letsencrypt/nginx/nginx.conf). 

This guide was heavily inspired by [TechnicalRamblings](https://technicalramblings.com) as well as other random guides I found online. Please join the Organizr [Discord](https://organizr.app/discord) chat room for help.
