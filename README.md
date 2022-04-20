# README
----

This is a small demo of some SRE use cases. This is Demo contains the following:

- 3 Docker Compose files that will create the following containers
  - Cribl
  - Splunk
  - Nginx
- A simple nginx cribl pack

## Requirements Section

Before you begin, ensure that you have met the following requirements:

* A linux system to run your docker containers on
* A willingness to try new things
* A basic understanding of Docker

## Getting Started

To use this Demo, follow these steps:

1. Download the nginx.crbl file and place it somewhere you can easily access
2. Place the *app-cribl* folder wherever you normally store Docker-Compose.yml files (I suggest /projects/)
3. Start the docker container by changing directory into where you stored the above file and run `docker-compose up -d`
4. Place the *app-splunk* folder wherever you normally store Docker-Compose.yml files (I suggest /projects/)
5. Place the *app-nginx* folder wherever you normally store Docker-Compose.yml files (I suggest /projects/)
6. Navigate to your Cribl instance (<host_IP>:19000)and create a username and password to log in (replace <host_IP> with the IP Address of your linux host)
7. While still in your Cribl instance navigate to Processing/Packs -> Packs -> Add New -> Import from file -> Choose the nginx.crbl file you downloaded earlier

## Getting data into Splunk

To get data from Cribl into Splunk do the following:

1. Go to Data -> Sources -> Splunk HEC -> Enable the default in_splunk_hec Source
2. Don't forget to commit and deploy your changes! 
3. Go to Data -> Destinations -> Splunk -> Enable to default Splunk destination

To get your nginx data from your Nginx Docker Container into Cribl do the following:

1. Navigate to the location that you stored the *app-nginx* folder.
2. Inside the *app-nginx* folder change line 8 to: splunk-url: http://<host_ip>:8088 (replace <host_IP> with the IP Address of your linux host)
3. Inside the *app-nginx* folder change line 9 to: splunk-token: <splunk_token> (replace <splunk_token> with the Splunk Token in your Splunk HEC source)

Don't forget to commit and deploy your changes on the Cribl Leader!!!

## Release Notes

### Version 0.0.1 - 2022-04-20
This is the initial release of the demo


## Contact
To contact us please email james.l.curtis@gmail.com
