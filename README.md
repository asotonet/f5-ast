https://github.com/f5devcentral/application-study-tool 

https://github.com/mikempw/application-study-tool

https://f5devcentral.github.io/application-study-tool/config/config_helper/config_datafabric.html

This is the third generation Blue Print for the Application Study Tool. This BP can be used for 1) F5 Academy Lab Series, 2) Used as a lab to build the Application Study Tool, or 3) For a demonstration (See the internal tab)

LET'S RUN THE LAB: ------> LAB GUIDE <------

Details
Please see the Lab Guide linked above for how to work through the lab.

The environment uses three standalone BIG-IP's with the "Central" BIG-IP being fully provisioned. AST is already configured and running on the Application Study Guest under /home/ubuntu/pre-built/application-study-tool. Everything is configured under the ubuntu account so please use the ubuntu account and sudo where appropriate. Traffic generation is from two sources: ubuntu users' cron on the App Services guest and aggressive bigip health monitors from the west's web_pool and east's web-pool-*.

If you make changes to the config file remember to regenerate the config:


yamllint -d relaxed /home/ubuntu/pre-built/application-study-tool/config/bigip_receivers.yaml

cd /home/ubuntu/pre-built/application-study-tool

sudo docker run --rm -it -w /app -v ${PWD}:/app --entrypoint /app/src/bin/init_entrypoint.sh python:3.12.6-slim-bookworm --generate-config

sudo docker-compose down
sudo docker-compose up -d
Troubleshooting
If Grafana charts are not populating run:

cd /home/ubuntu/pre-built/application-study-tool
sudo docker-compose down
sudo docker-compose up -d
