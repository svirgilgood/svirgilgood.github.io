---
layout: post 
title: "Installing Docker"
--- 

# Sunday, Aug 4, 2019 

## Install Docker 

I installed Docker on Mac from the installer. [Found here](https://docs.docker.com/docker-for-mac/). 

After installation, you need to increase the RAM allowable for docker to 4GB.
(More would probably be helpful, I just don't have it on my machine)

After the RAM is increased through the settings in the docker desktop, docker
will need to be restarted.

## Pull the Docker Image for Wikibase

[Installation instructions can be found on the MediaWiki
page](https://www.mediawiki.org/wiki/Wikibase/Installation). I just used a
[docker
install](https://github.com/wmde/wikibase-docker/blob/master/README-compose.md). 

The steps are:

1. Grab the `docker-compose.yml`.
```
wget https://raw.githubusercontent.com/wmde/wikibase-docker/master/docker-compose.yml 
```
2. Pull the image:
```
docker-compose pull 
```
3. Start the container:
```
docker-compse up
```

I ran all of these inside the directory with the `docker-compose.yml`

## Install WikibaseImport 

[WikibaseImport](https://github.com/filbertkm/WikibaseImport) is an extension
that allows you to clone many of the Wikidata entities and properties, so that 
you don't have to recreate them. 


To install the image inter the docker container. The general docker container on 
my machine was called `wikibase/wikibase:1.33-bundle`. 

```
docker exec -it CONTAINER_ID /bin/bash 
``` 

### Cloning the Extension if it doesn't exist

When I ran this, I found that wikibase was already installed in the container.
But if you need to install it do the following: 

Once inside the container, `cd` into the extensions directory and clone the
wikibaseImport github repo.  
``` git clone https://github.com/filbertkm/WikibaseImport.git ```

then enable the extension in `LocalSettings.php`
``` sfLoadExtension( 'WikibaseImport' ); ``` 

### Importing Wikidata Items 

Once inside the `WikibaseImport` extension directory inside the container, you
can import the properties with:

``` php maintenance/importEntities.php --all-properties ``` 

I had to run this script multiple times to get the properties to install. 

You can allso install a specific entity with:

``` php maintenance/importEntities.php --entity Q147 ``` 

## Summary 

You can log into the local wikibase install through a webbrowser at
`localhost:8181`. You will need to create a local user to edit and correct
the data. 

Even after installing, not all of the entities are spelled out, and many didn't
import, even after running it multiple times.  


