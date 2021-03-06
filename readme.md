[sr]: http://signalr.net/
[aq]: https://github.com/androidquery/androidquery

#SignalA#

##Description##
SignalA is a [SignalR][sr]-client for Android. It's implemented as a Android-library. At this moment is long polling the only implemented transport. Long polling is a separate library.
Http-requests in the Long polling library is using [Android-query][aq].

##How to use?##

To use SignalA you have to get a copy of the two libraries, SignalA and SignalA.LongPolling. Add a reference to SignalA.LongPolling under Properties > Android > Library.
Then add the following code to your activity.

      String url = "http://<address to your SignalR-server>";
      con = new com.zsoft.SignalA.Connection(url, this, new LongPollingTransport()) {

			@Override
			public void OnError(Exception exception) {
	            Toast.makeText(DemoActivity.this, "On error: " + exception.getMessage(), Toast.LENGTH_LONG).show();
			}

			@Override
			public void OnMessage(String message) {
	            Toast.makeText(DemoActivity.this, "Message: " + message, Toast.LENGTH_LONG).show();
			}

			@Override
			public void OnStateChanged(StateBase oldState, StateBase newState) {
			}
		};

To start and stop the SignalA connection use code similar to the following.

	public void startSignalA()
	{
		if(con!=null)
			con.Start();
	}
	
	public void stopSignalA()
	{
		if(con!=null)
			con.Stop();
	}

That's it!

For a complete sample see the Demo-project.

##Limitations##
Currently is Groups and Hubs not implemented, only PersistentConnection. 

##Contributions##
I'll be more than happy to get contributions!!!

##License##

    Copyright 2013 Erik Zetterqvist
    
    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at
    
    http://www.apache.org/licenses/LICENSE-2.0
    
    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

Disclaimer: I'm a .NET-coder and this is my first attemt to write a Java-library so bare with me.
