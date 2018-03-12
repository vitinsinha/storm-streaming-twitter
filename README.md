# Storm Streaming Twitter

This is a demo application for learning Apache Storm. It uses:
 - Apache Storm 1.2.1
 - Twitter 4j 4.0.6
 
This application uses Twitter 4j library for consuming live Twitter streaming API feed and processes it and prints the count of each hashtag.
 
This application can be run locally on Intellij IDEA or can be submitted to an existing Storm cluster.

### Storm installation
```
I followed this article to setup Apache Storm on a single server:

https://vincenzogulisano.com/2015/07/30/5-minutes-storm-installation-guide-single-node-setup/
```

### Submitting the topology to an existing storm cluster
```
/opt/apache-storm-1.2.1/bin/storm jar storm-streaming-twitter-1.0.0-SNAPSHOT-jar-with-dependencies.jar TwitterHashtagStormTopology your-twitter-consumer-key your-twitter-consumer-secret your-twitter-access-token your-twitter-access-token-secret food

Here I am passing a filter argument 'food', so I will get all the tweets which have this word 'food' in it.
```

### Running locally on Intellij IDEA
```
Step 1: In pom.xml, remove 'provided' scope from the 'storm-core' dependency

Step 2: In TwitterHashtagStormTopology class, use LocalCluster class to submit the topology; instead of StormSubmitter class.

Step 3: The main class takes 4 mandatory arguments (your Twitter ConsumerKey, ConsumerSecret, AccessToken & AccessTokenSecret) and any number of filter arguments for filtering the tweets.

Also, additionally, you can shutdown the cluster after some sleep time; so you don't have to kill it manually.
```


### Checking the logs

```
When I submitted my topology to the storm cluster, I found the log file at this location:

/opt/apache-storm-1.2.1/logs/workers-artifacts/TwitterHashtagStormTopology-1-1520807840/6700/worker.log

```

