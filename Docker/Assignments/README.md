DNS Round Robin test
---------------------------
* Create a new virtual network
* Create two containers from `elasticsearch:2` image
* Research and use `--network-alias` search when creating them to give an additional DNS name to respond to
* Run *alpine nslookup search* with `--net` to see the two containers list for the same DNS name.
* Run `centos curl -s search:9200` with `--net` multiple times until you see both "name" fields show 
