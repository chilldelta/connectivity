## Network Connectivity Monitor ##
### Get notification the moment network connection is lost, and restored -- <em>a must have for your client-server based Android app</em> ###
Android network connectivity monitor periodically checks network connectivity and notifies listeners of network status change. Call backs are done on main thread, allowing listeners to make UI changes without any worry.

| <img src='http://connectivity.googlecode.com/files/com.arifsoft.arifzefen.network_banner.png' width='300px' />| <img src='http://connectivity.googlecode.com/files/com.arifsoft.arifzefen.no_network_banner.png' width='300px' />|
|:--------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------|
|[ArifZefen App](https://market.android.com/details?id=com.arifsoft.arifzefen) using the [connectivity](#.md) library|[ArifZefen App](https://market.android.com/details?id=com.arifsoft.arifzefen) using the [connectivity](#.md) library to <br />show the unavailability of network|

The sample app included in this project simply shows a connected or disconnected text message based on network status.

## How to Install ##
Get a copy of the source [here](https://code.google.com/p/connectivity/source/checkout). Copy-paste the /src/com folder to your project's source folder.
In your main `Activity` (or any `Activity`), import the classes and configure the `NetworkConnectivity` singleton instance prior to use as follows:
```
import com.tekle.oss.android.connectivity.NetworkConnectivity;
import com.tekle.oss.android.connectivity.NetworkMonitorListener;
...
NetworkConnectivity.sharedNetworkConnectivity().configure(this);
```
Once it's configured, you may add as many network monitor listeners as you like by doing:
```
NetworkConnectivity.sharedNetworkConnectivity().addNetworkMonitorListener(new NetworkMonitorListener() {
        @Override
        public void connectionCheckInProgress() {
               //Okay to make UI updates (check-in-progress is rare)
        }

        @Override
        public void connectionEstablished() {
               //Okay to make UI updates -- do something now that connection is avaialble           
        }

        @Override
        public void connectionLost() {
               //Okay to make UI updates -- bummer, no connection
        }
});
```
Don't forget to start the monitor:
```
NetworkConnectivity.sharedNetworkConnectivity().startNetworkMonitor();
```

You can also get the network state synchronously as follows:
```
boolean isConnected = NetworkConnectivity.sharedNetworkConnectivity().isConnected();
```
It's that simple!

## Disclaimer ##
You may use, modify, etc. this code. However, give credit per the license agreement.