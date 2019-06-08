#Set的使用

## 用Set实现数组的并集

    const ninjas = ["Kuma", "Hattori", "Yagyu"];
    const samurai = ["Hattori", "Oda", "Tomoe"]; 
    const warriors = new Set([...ninjas, ...samurai]);

## 用Set实现数组的交集

    const ninjas = new Set(["Kuma", "Hattori", "Yagyu"]);
    const samurai = new Set(["Hattori", "Oda", "Tomoe"]);
    const ninjaSamurais = new Set(
    	[...ninjas].filter(ninja => samurai.has(ninja))
    );
## 用Set实现数组的差集

    const ninjas = new Set(["Kuma", "Hattori", "Yagyu"]);
    const samurai = new Set(["Hattori", "Oda", "Tomoe"]);
    const ninjaSamurais = new Set(
    	[...ninjas].filter(ninja => !samurai.has(ninja))
    );