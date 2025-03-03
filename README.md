# react_sub_mqtt (cond)
React subscribe MQTT example (cond)

<p align="center" width="100%">
    <img width="30%" src="https://github.com/jkaewprateep/MQTT_in_react/blob/main/python-logo.jpg">
    <img width="20%" src="https://github.com/jkaewprateep/MQTT_in_react/blob/main/mqtt.jpg">
    <img width="8.3%" src="https://github.com/jkaewprateep/MQTT_in_react/blob/main/image21.jpg">
    <img width="18.9%" src="https://github.com/jkaewprateep/MQTT_in_react/blob/main/kid_17.jpg"> </br>
    <b> Implement MQTT in react application </b> </br>
    <b> ( Picture from Internet ) </b> </br>
</p>

🧸💬 By resolving the subscribe and unsubscribe issue, we can use a dropdown input to switch subscribing topics for similar information display and improve user experience. Similar to other APIs we are using nowadays, unsubscribing before subscription is recommended, where the component API claims to destroy the object, with the connectivity still requiring unsubscribing for calculation reasons. </br>
🐑💬 ➰ Repeating unsubscribe items does not make an error, but forgetting does, given statistics and report or communication, because some API provide dedicated bandwidth for connection or they count as a group member or reliability traveling part for ring communication or node communication. </br>

🦭💬 Ring communication is a secure and self-organizing network, formal or non-formal connectivity is defined from the active status of a peer or node you are connecting as a network. Non-formal communication is seen as useful by many applications where the guaranteed network is representing of both the end and sometimes the traveling path for guaranteeing the success of communication.  </br>
👧💬 🎈 Do you mean witness communication⁉️ communication securely by the party that does not in conversation but guarantees communication by appearance.</br>

🐯💬 Culture-INFO, public organizes accept formal communication because they have had IT security and community standards for communication, none-formal can create secured communication as formal communication, but they are not present both ends of the communication or path of communication. </br>
🦁💬 Path of communication including network, endpoints, equipment, bandwidth, OS, matching and algorithms they are conform into communication way represents both end virtually see as same conversation in organization place. Communication traceback is to know what, where, and when the conversation has been in place because face-to-face communication does not require tracing back.</br>

## Codings example

🐐💬 Without secured policy security and login, anybody can connect to MQTT service; they can intercept messages by using internet browser or a network sniffer. This MQTT is public for study and work anyway, they also create a timeout policy to prevent third-party interception. We can use multiple sources for our study. </br> 
```
useEffect(() => {
        console.log("🟢 Source Selected:", sourceselect.data);
    
        let selectedTopics = [];
    
        if (sourceselect.data === "Alpaca") {
            selectedTopics = [
                "tg/alpaca/QCOM", "tg/alpaca/SMCI", "tg/alpaca/TSLA",
                "tg/alpaca/AMZN", "tg/alpaca/GOOGL", "tg/alpaca/META",
                "tg/alpaca/TQQQ", "tg/alpaca/AAPL", "tg/alpaca/AMD",
                "tg/alpaca/COIN", "tg/alpaca/CRWD", "tg/alpaca/SQQQ",
                "tg/alpaca/MSFT", "tg/alpaca/MSTR", "tg/alpaca/NFLX",
                "tg/alpaca/NVDA"
            ];
        } else if (sourceselect.data === "Polygon") {
            selectedTopics = [
                "tg/polygon/QCOM", "tg/polygon/SMCI", "tg/polygon/TSLA",
                "tg/polygon/AMZN", "tg/polygon/GOOGL", "tg/polygon/META",
                "tg/polygon/TQQQ", "tg/polygon/AAPL", "tg/polygon/AMD",
                "tg/polygon/COIN", "tg/polygon/CRWD", "tg/polygon/SQQQ",
                "tg/polygon/MSFT", "tg/polygon/MSTR", "tg/polygon/NFLX",
                "tg/polygon/NVDA"
            ];
        } else {
            selectedTopics = [
                "tg/techglobelab/QCOM", "tg/techglobelab/SMCI", "tg/techglobelab/TSLA",
                "tg/techglobelab/AMZN", "tg/techglobelab/GOOGL", "tg/techglobelab/META",
                "tg/techglobelab/TQQQ", "tg/techglobelab/AAPL", "tg/techglobelab/AMD",
                "tg/techglobelab/COIN", "tg/techglobelab/CRWD", "tg/techglobelab/SQQQ",
                "tg/techglobelab/MSFT", "tg/techglobelab/MSTR", "tg/techglobelab/NFLX",
                "tg/techglobelab/NVDA"
            ];
        }
    
        console.log("🔄 Updating Topics:", selectedTopics);
    
        const client = mqtt.connect(MQTT_WEBSOCKET_URL, {
            clean: true,
            connectTimeout: 4000,
            reconnectPeriod: 1000,
        });
    
        client.on("connect", () => {
            console.log("✅ Connected to MQTT Broker");
    
            client.unsubscribe("#", (err) => {
                if (err) {
                    console.error("❌ Unsubscribe error:", err);
                } else {
                    console.log("🔄 Unsubscribed from all topics");
    
                    client.subscribe(selectedTopics, (err) => {
                        if (err) {
                            console.error("❌ Subscribe error:", err);
                        } else {
                            console.log("✅ Subscribed to topics:", selectedTopics);
                        }
                    });
                }
            });
        });
    
        client.on("message", (topic, message) => {
            const payload = JSON.parse(message.toString());
            console.log(`📩 Received from ${topic}:`, payload);
    
            setMessages((prevMessages) => {
                const existingIndex = prevMessages.findIndex(
                    (stock) => stock.symbol === payload.symbol
                );
    
                if (existingIndex !== -1) {
                    return prevMessages.map((stock, index) =>
                        index === existingIndex ? { ...stock, ...payload } : stock
                    );
                } else {
                    return [...prevMessages, payload];
                }
            });
        });
    
        client.on("error", (err) => {
            console.error("❌ MQTT Error:", err);
        });
    
        return () => {
            console.log("❌ Disconnecting from MQTT...");
            client.end();
        };
    }, [sourceselect.data]);
```

---

<p align="center" width="100%">
    <img width="30%" src="https://github.com/jkaewprateep/advanced_mysql_topics_notes/blob/main/custom_dataset.png">
    <img width="30%" src="https://github.com/jkaewprateep/advanced_mysql_topics_notes/blob/main/custom_dataset_2.png"> </br>
    <b> 🥺💬 รับจ้างเขียน functions </b> </br>
</p>
