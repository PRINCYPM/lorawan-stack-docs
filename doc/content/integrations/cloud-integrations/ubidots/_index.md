---
title: "Ubidots"
description: ""
weight: 
aliases: ["/integrations/cloud-integrations/ubidots/ubidots-setup", "/integrations/cloud-integrations/ubidots/tts-setup"]
---

[Ubidots](https://ubidots.com/) provides a secure and easy way to build IoT solutions for students, makers and researchers. It is used for sending data from any Internet-enabled device to the cloud, triggering actions and alerts based on that data, and visualizing it. 

<!--more-->

## Prerequisites

1. A Ubidots user account.

## Setup Ubidots

Log in to your Ubidots account and find the **Devices** tab in the upper part of your dashboard. In its drop-down list, choose **Plugins**.

{{< figure src="plugins.png" alt="Ubidots Plugins" >}}

Click on the **+** or on the **Create Data Plugin** button to create a new plugin.

When you are presented with available plugins, select **The Things Stack** plugin.

{{< figure src="tts-plugin.png" alt="TTS plugin" >}}

You will see details about **Inputs**, **Usage**, etc. Move forward by clicking the **>** button.

Next, you need to provide the name for a **Ubidots device type** after which a new device type will be created and linked to this plugin. This device type will later allow you to make changes for all devices that receive data through this plugin.

You also need to select a **Ubidots token**. You can use the **Default token**, but creating a new token specifically for this plugin is **recommended**.

{{< figure src="device-type.png" alt="Creating a device type and selecting token" >}}

To create a new token, first click on your avatar in the upper right corner and select **API Credentials**. Then select **More** below the **Default token** and add a new token within the **API Credentials page**.

{{< figure src="tokens.png" alt="Creating token" >}}

Select **>** to continue and then hit the checkmark to finish.

{{< figure src="name-description.png" alt="Finish with creating the plugin" >}}

After a few moments, your newly created plugin will show the status **Running**.

{{< figure src="running.png" alt="Status: Running" >}}

To complete the integration with {{% tts %}}, you will need to provide the plugin ID and aforementioned token. 

To find the plugin ID, click on your newly created plugin and navigate to the **Decoder** tab on the left. The plugin ID is available as part of the **HTTPs Endpoint URL** (as highlighted on the image below).

{{< figure src="plugin-id.png" alt="Plugin ID" >}}

## Decoding Payload

In order for payload that is being sent from your end device in uplink messages to be decoded and presented on the Ubidots dashboard, you have two options:

- to create an [uplink payload formatter]({{< ref "/integrations/payload-formatters" >}}) on {{% tts %}} (whose format has to be [Ubidots-friendly](https://ubidots.com/docs/hw/#send-data-to-a-device))
- to edit the pre-loaded sample decoder on Ubidots so that it decodes the Base64-encoded payload received from {{% tts %}} in `uplink_message.frm_payload` field

## Configure {{% tts %}}

When you have prepared the setup on Ubidots, it is the time to create a Webhook integration on {{% tts %}} by using the **Ubidots** [Webhook template]({{< ref "/integrations/webhooks/webhook-templates" >}}).

{{< note >}} Advanced users can also use [UbiFunctions](https://help.ubidots.com/en/articles/2132086-analytics-ubifunctions-user-guide) module to complete this integration. {{</ note >}}

On {{% tts %}}, navigate to **Integrations &#8594; Webhooks** and choose the **Ubidots** Webhook template.

Name your integration by filling in the **Webhook ID**.

Paste the **Plugin ID** and **Ubidots token** values from Ubidots.

{{< figure src="ubidots-integration.png" alt="Ubidots webhook template" >}}


