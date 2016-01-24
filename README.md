docker-bleve-wiki-indexer 
=========================

Dockerizing [bleve library](https://github.com/blevesearch/bleve) to build an index of the [bleve wiki](https://github.com/blevesearch/bleve/wiki). See [wikisearch](http://wikisearch.blevesearch.com/search/) online example and his [bleve-wiki-indexer](https://github.com/blevesearch/bleve-wiki-indexer) source code. See also the amazing [blevesearch.com](http://www.blevesearch.com/). 

## Use 

    $ docker run -i -p 8099:8099 -t lgsd/docker-bleve-wiki-indexer bash
    root@1c1532dec11f:/#

This way, you are pulling a `Trusted Docker Image` from public [Docker Hub](https://registry.hub.docker.com/u/lgsd/docker-bleve-wiki-indexer/). Now run `bleve-wiki-indexer` from source directory to ensure the static content is found by default (read more [here](https://github.com/blevesearch/bleve-wiki-indexer))

    root@1c1532dec11f:/# cd $GOPATH/src/github.com/blevesearch/bleve-wiki-indexer
    root@1c1532dec11f:/gopath/src/github.com/blevesearch/bleve-wiki-indexer# bleve-wiki-indexer -dir /data/bleve.wiki
    2016/01/24 17:41:42 Creating new index...
    2016/01/24 17:41:42 watching '/data/bleve.wiki' for changes...
    2016/01/24 17:41:42 updated: /data/bleve.wiki/ANSI Result Match Highlighter.md
    2016/01/24 17:41:42 checking commit 155f99bcfa0e1ee7ea395a2df1eeec0dad21efee
    2016/01/24 17:41:42 checking commit 1a1083b7093e79890dc480d2b9dad0112a43ffbd
    ...
    2016/01/24 17:41:48 gravatar hash is: 16cdfb0c4af5297e261cb36e30fa5c20
    2016/01/24 17:41:48 Listening on :8099

open your browser at  `http://localhost:8099/`, or do `curl` to check it works:

    $ curl localhost:8099
    <a href="/static/index.html">Found</a>.

You can also build by forking/downloading the repo then run docker interactive like before:

    $ git clone https://github.com/lgs/docker-bleve-wiki-indexer && cd docker-bleve-wiki-indexer
    $ docker build -t lgsd/docker-bleve-wiki-indexer --rm=true .
    $ docker run -i -p 8099:8099 -t lgsd/docker-bleve-wiki-indexer bash
    root@52fe5e02d8f9:/#

Now proceed as before, running bleve-wiki-indexer from source directory ...

    $ docker run -i -p 8099:8099 -t lgsd/docker-bleve-wiki-indexer bash
    root@1c1532dec11f:/# cd $GOPATH/src/github.com/blevesearch/bleve-wiki-indexer
    root@1c1532dec11f:/gopath/src/github.com/blevesearch/bleve-wiki-indexer# bleve-wiki-indexer -dir /data/bleve.wiki
    2016/01/24 17:41:42 Creating new index...
    2016/01/24 17:41:42 watching '/data/bleve.wiki' for changes...
    2016/01/24 17:41:42 updated: /data/bleve.wiki/ANSI Result Match Highlighter.md
    2016/01/24 17:41:42 checking commit 155f99bcfa0e1ee7ea395a2df1eeec0dad21efee
    2016/01/24 17:41:42 checking commit 1a1083b7093e79890dc480d2b9dad0112a43ffbd
    ...
    2016/01/24 17:41:48 gravatar hash is: 16cdfb0c4af5297e261cb36e30fa5c20
    2016/01/24 17:41:48 Listening on :8099

First time you `build` without having any previous intermediate image locally (like google/golang for example), it could take more then 5 minutes to pull & build everithing, so take it easy and relax. In my case, having `google/golang` already present, I spent 3m14.457s.

## Copyright

Copyright (c) 2014 Luca G. Soave
