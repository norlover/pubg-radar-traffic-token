# pubg-radar-traffic-token

![oooooooooooooooooo.png](https://i.loli.net/2019/08/14/vB4CUAk5ldDHZ7t.png)

how get IV and Key 


```python
import re
import mitmproxy.websocket
from mitmproxy import ctx, websocket


class SniffWebsocket:
    def websocket_message(self, flow: mitmproxy.websocket.WebSocketFlow):
        """
            Called when a WebSocket message is received from the client or
            server. The most recent message will be flow.messages[-1]. The
            message is user-modifiable. Currently there are two types of
            messages, corresponding to the BINARY and TEXT frame types.
        """
        for flow_msg in flow.messages:
            packet = flow_msg.content
            if isinstance(packet,str):
                # [0,null,"ClientApi","StartGameConfirmed","no more show ","no more show ",{"Key":"e3CEOhynSuAJaCX7s4XECw==","ServerIV":"k1XLwkirCbZ3IdB3","ClientIV":"yJDvGoYU1nmV2Krp"}]
                matchObj = re.search('{"Key"."ServerIV".}', packet)
                if matchObj:
                    print("packet: %s" % packet)
                    print("match: %s" % matchObj.group())
```
