# Creating an integration between Twitter and Kafka

## Setting up the Twitter connection

1. Go to https://developer.twitter.com and get yourself a Twitter developer
account.
2. Create an App on that website, that *includes a website and a call back URL
   for OAuth*. Details are here: https://access.redhat.com/documentation/en-us/red_hat_fuse/7.4/html/fuse_online_sample_integration_tutorials/twitter-to-salesforce_tutorials#register-with-twitter_t2sf
3. Go to Fuse Online, Settings, Twitter and enter your Consumer API and API
   Secret keys
4. Go to Fuse Online, Connections, Create Connection. Select Twitter. Walk
   through the fields. Log into Twitter if you need to.

## Setting up the Kafka connection

1. Go to Fuse Online, Connections, Create Connection. Enter the IP of the
   bootstrap service with port 9092. (Question: for me, the broker service did
   not have an IP associated with it, which was odd, since I expected to use
   that service and not the bootstrap one. Misunderstanding or bug?)
2. Fill in the following fields, if any.

## Creating the integration itself

1. Go to Fuse Online, Integrations, Create integration. Select the Twitter
   connection as the first Connection. Pick Search, enter a search term.
2. Select Kafka Message Broker as the second Connection. Select the right
   topic.
3. Type specification is not required. Leave it empty for now.
4. Publish.

## Testing
Connect to the terminal of one of the pods running Kafka and run:

bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic twitter-stuff --from-beginning
