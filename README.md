
# Context

This is a quick (and very dirty) setup that was made to create an [Infranodus](https://infranodus.com) Text Network Analysis server for one of the projects of [Hackathon Covid 19](https://hackcovid19.bemyapp.com): Covisualisation from [@jbingold](https://twitter.com/JBingold).


# Requirements

This setup requires docker (or podman) to be installed.


# Setup

- Start a Neo4J container with APOC
```
bin/run-neo4j 
```

- Check the logs and wait for the server to be `Started`
```
docker logs neo4j -f 
```


- Configure indexes and triggers for Neo4J
```
cat bin/setup_neo4j | docker exec -i  neo4j  bash
```

- Start Infranodus
```
bin/run-server 
```

- Check the logs 
```
docker logs server -f 
```

- Connect to Infranodus with the invitation code on http://localhost:3001/signup?invitation=secretcode 

# Clean up

```
docker rm -f server neo4j
```

# TODO

There's a **lot** of room for improvement, starting with:
1. the infranodus image version (2 yo)
1. setting up authentication
1. injecting `setup_neo4j` per the official Neo4J image procedure
1. move this away from plain docker link (docker-compose, k8s...)
