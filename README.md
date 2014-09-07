docker-bleve-wiki-indexer 
=========================

Dockerizing [bleve library](https://github.com/blevesearch/bleve) to build an index of the [bleve wiki](https://github.com/blevesearch/bleve/wiki). See [wikisearch](http://wikisearch.blevesearch.com/search/) online example and his [bleve-wiki-indexer](https://github.com/blevesearch/bleve-wiki-indexer) source code. See also the amazing [blevesearch.com](http://www.blevesearch.com/). 

## Use 

   $ docker run -i -p 8099:8099 -t lgsd/docker-bleve-wiki-indexer bash
   root@52fe5e02d8f9:/#

This way, you are pulling a `Trusted Docker Image` from public [Docker Hub](https://registry.hub.docker.com/u/lgsd/docker-bleve-wiki-indexer/). Now run `bleve-wiki-indexer` from source directory to ensure the static content is found by default (read more [here](https://github.com/blevesearch/bleve-wiki-indexer))

   root@52fe5e02d8f9:/# cd $GOPATH/src/github.com/blevesearch/bleve-wiki-indexer
   root@52fe5e02d8f9:/gopath/src/github.com/blevesearch/bleve-wiki-indexer# bleve-wiki-indexer -dir /data/bleve.wiki
   2014/09/07 12:27:17 Creating new index...
   2014/09/07 12:27:18 watching '/data/bleve.wiki' for changes...
   2014/09/07 12:27:18 updated: /data/bleve.wiki/ANSI Result Match Highlighter.md
   2014/09/07 12:27:18 checking commit 1a1083b7093e79890dc480d2b9dad0112a43ffbd
   2014/09/07 12:27:18 checking commit d781519f66ca8894b1a303bd3db3196f95ae04e4
   ...
   2014/09/07 12:27:23 gravatar hash is: 16cdfb0c4af5297e261cb36e30fa5c20
   2014/09/07 12:27:23 Listening on :8099

open your browser at  `http://localhost:8099/`, or do `curl` to check it works:

   $ curl localhost:8099
   <a href="/static/index.html">Found</a>.

You can also build by forking/downloading the repo then run docker interactive like before:

   $ git clone https://github.com/lgs/docker-bleve-wiki-indexer && cd docker-bleve-wiki-indexer
   $ docker build -t lgsd/docker-bleve-wiki-indexer --rm=true .
   $ docker run -i -p 8099:8099 -t lgsd/docker-bleve-wiki-indexer bash
   root@52fe5e02d8f9:/#

Now proceed as before. 

First time you `build` without having any previous intermediate image locally (like google/golang for example), it could take more then 5 minutes to pull & build everithing, so take it easy and relax. In my case, having `google/golang` already present, I spent 3m14.457s.

## Project Ref. 

   bleve-wiki-indexer Dockerfile
   (see amazing http://www.blevesearch.com/)
  
   https://github.com/lgsd/docker-bleve-wiki-indexer
  
   VERSION 0.1
  
   bleve is a modern text indexing for Go
   see online full text search engine:
   http://wikisearch.blevesearch.com/search/
  
   Pull base image by google/golang
   go version go1.3.1 linux/amd64
   based on google/debian:wheezy:
  
   Linux version 3.11.0-18-generic (buildd@toyol)
   gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8)
   32-Ubuntu SMP Tue Feb 18 21:11:14 UTC 2014

## Copyright

Copyright (c) 2014 Luca G. Soave
