# Best Practices for the Southern California Mesh
Last updated: 2/19/25

Background: As the SoCalMesh network running on Meshtastic gets bigger and more knowledgeable, its members have discovered a few best practices for settings. The following are not mandatory settings, just recommendations to de-congest the network and hopefully get your messages through.

Reference:  https://meshtastic.org/docs/introduction/

[Quick Start](https://discord.com/channels/1197390116201697290/1197390117128646769/1220500317850964202)⁠

[Meshtastic Routing Issues & Deployment Scenarios](https://youtu.be/htjwtnjQkkE)

## Radio Configuration:
### Channel: 
SoCalMesh uses the default primary channel settings. There is no separate PSK or channel selection required to connect to the public network. You are welcome to set your own private keys for your own devices.
When in doubt, conduct a FACTORY RESET to return your settings to default

### Device Role: 
#### CLIENT
Best all around setting. If you are unsure, use this. Best role for "hop-out" nodes that are a bit higher than your location.

#### CLIENT_MUTE
Best for mobile nodes. Device will not participate in forwarding mesh packets, but will still allow sending and receiving messages and transmitting NODEINFO and POSITION updates.

#### ROUTER
Best for remote nodes on top of the highest peaks in your geographic area. Very few nodes have this setting.

#### REPEATER
DO NOT USE. There are very few valid use cases for this role and typically causes problems.

### Hop Count:
3-5. You can try up to 7 occasionally, but not recommended to leave it at this high of a setting.

### Broadcast Interval (Position, Telemetry, Node Info):
Infrastructure Nodes:
Position: 86400 seconds
Telemetry: 3600-7200 seconds
Node Info: 86400 seconds

### Mobile Nodes:
Position: 900 seconds
Telemetry: 900 seconds
Node Info: 86400 seconds

### LoRa:
Ignore MQTT

## Some words of wisdom from @Coopersmith:

In Meshtastic it's generally easier to receive than send on portable units with stock antennas.  What getting those nodes in your list means though is you've established your basic settings are correct and your receiver is working.

Antennas and height are the name of the game here.  Better antennas help get the maximum signal transmitted out of your node and height tends to mean you have better line of sight.  Signals at these frequencies are very dependant on line of sight.  Anything other than glass or plastic in the way tends to be a signal loss and Meshtastic runs at very low power.

With good antennas and good line of sight to the receiver, the range is actually quite amazing.

Due to the way Meshtastic works, it's entirely possible (though less probable) the intended recipient actually did get the message, but conditions were such a confirmation couldn't get back to you even at the "max transmissions" status level.

The more "hops" though other nodes, the less the probability is of you being able to actually establish two-way communication.  But that's all just part of the game here.

## Changing the name of the Primary Channel

For the Default "LongFast" channel to function, it either needs to keep its default name with no other changes made, or it needs to be called "LongFast" (with no other changes made).

The LongFast channel canbe used as a Secondary channel, if again called "LongFast" with a Key of "AQ==".

Also, if the Primary channel is changed in any way (name, key, etc.), the Frequency Slot setting under LoRa Config must be set back to "20".
