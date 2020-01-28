# Agent unable to trace path to destination?

In a strange series of circumstances, you can end up with a Enterprise Agent showing 0% loss, without the path visualization showing connectivity to the destination.

## Problem

There is a disconnect between the loss statistics of the Enterprise Agent \(showing 0% loss\), and the gateway for the Enterprise Agent \(showing 100% loss\).

## Cause

This occurs specifically when a Enterprise Agent is connected to the internet behind an Apple Airport gateway, running an up to date firmware revision.  This happens due to the fact that Apple Airport routers rewrite the IP header on outbound packets to ensure their routability back to the host which generated them.  This disrupts the flow of packets from ThousandEyes, which uses the Identifier field to identify packet sequence. 

The example below shows the path visualization of a test which is 100% successful.  Note the agent is green, and shows 0% loss, and the endpoint \(showing 100% loss\) is an Apple Airport device \(which is the default gateway for the agent\), with 100% loss. 

IMAGE MISSING

## Resolution

We are working on a workaround for these specific circumstances, but for now, any Enterprise Agent which shows as green, and indicates 0% loss, with a route which terminates on the edge \(or gateway\) which is an Apple Airport device can be ignored as a troubleshooting point.  The fact that we are showing 100% loss at the edge is an indicator of this behavior, rather than an indicator of loss.

