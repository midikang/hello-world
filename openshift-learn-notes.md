# Install rhc on c9.io
Due to network connection in China, ruby gem source is not stable. Instal rhc(red hat client tools) in c9.io

## Install rhc
	$sudo gem install rhc
## Setup rhc
	$rhc setup
OpenShift Client Tools (RHC) Setup Wizard
This wizard will help you upload your SSH keys, set your application namespace, and check that other programs like Git are properly installed.

## create jboss eap application

	$rhc app create spring jbosseap-6
	$rhc git-clone spring

## add upstream for local git repository
	$ git remote add upstream -m master git://github.com/openshift/spring-eap6-quickstart.git

## pull from upstream
	$git pull -s recursive -X theirs upstream master

## Commit this change, and push.
	$git commit -m ""
## push
	$git push
