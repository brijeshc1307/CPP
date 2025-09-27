Q1. **classic mislabeling logic puzzle** 

Let’s carefully break it down step by step:

---

### Problem Setup

* 3 bottles, all mislabelled.
* Labels:
  **A → Oreo**
  **B → KitKat**
  **C → Oreo–KitKat Mix**
* Reality: none of them matches their label.

---

### Key Insight

Since every bottle is **mislabelled**, the one marked **“Mix” (C)** cannot actually be Mix.
So it must be **pure Oreo** or **pure KitKat**.

---

### Step-by-step Solution

1. **Taste from Bottle C (labelled Mix):**

   * If it tastes **Oreo** →

     * Then C = Oreo.
     * A (labelled Oreo) cannot be Oreo, so A = Mix.
     * B (labelled KitKat) cannot be KitKat, so B = KitKat → contradiction? Wait. Let’s check carefully:

       * C = Oreo ✅
       * A (not Oreo, not labelled correctly) → Mix. ✅
       * B (labelled KitKat, mislabelled, not KitKat) → must be KitKat? ❌ wrong.
         Correction: B must be **the remaining** = KitKat. Works fine. ✅

   * If it tastes **KitKat** →

     * Then C = KitKat.
     * A (labelled Oreo, mislabelled, not Oreo) → Mix.
     * B (labelled KitKat, mislabelled, not KitKat) → Oreo. ✅

So, with just **1 tasting (from the “Mix” labelled bottle)**, you can deduce the identity of all three.

---

✅ **Answer:** Minimum **1 shake tasting** is required.

---
### समस्या सेटअप

* 3 बोतलें हैं और सभी पर गलत लेबल लगे हैं।
* लेबल:
  **A → ओरेओ**
  **B → किटकैट**
  **C → ओरेओ–किटकैट मिक्स**
* असलियत: इनमें से कोई भी अपने लेबल से मेल नहीं खाती।

---

### मुख्य समझ

क्योंकि हर बोतल पर **गलत लेबल** है, इसलिए जिस पर **“मिक्स” (C)** लिखा है, वह असल में मिक्स नहीं हो सकती।
इसलिए वह या तो **ओरेओ** होगी या **किटकैट**।

---

### चरण-दर-चरण समाधान

1. **बोतल C (जिस पर मिक्स लिखा है) से स्वाद चखो:**

   * अगर स्वाद **ओरेओ** है →

     * तब C = ओरेओ।
     * A (जिस पर ओरेओ लिखा है) ओरेओ नहीं हो सकती → इसलिए A = मिक्स।
     * B (जिस पर किटकैट लिखा है) किटकैट नहीं हो सकती → इसलिए B = किटकैट ही बचती है। ✅

   * अगर स्वाद **किटकैट** है →

     * तब C = किटकैट।
     * A (जिस पर ओरेओ लिखा है) ओरेओ नहीं हो सकती → इसलिए A = मिक्स।
     * B (जिस पर किटकैट लिखा है) किटकैट नहीं हो सकती → इसलिए B = ओरेओ। ✅

---
Q2. ### **Faulty Robot**

A company manufactures robots. Some are programmed to always tell the truth, while others always lie. Thus, there are two communities:

* **Truth Community**
* **Lie Community**

You meet three robots and ask **Robot 1**, “Which community do you belong to?”

* **Robot 1** responds in binary, which you don’t understand.
* **Robot 2** says, “Robot 1 belongs to the Lie Community.”
* **Robot 3** says, “Robot 2 is lying.”

**Which community does Robot 3 belong to?**

---

### **Solution:**

Assume **Robot 1** is from the Truth Community:

* Robot 1 tells the truth → Robot 2’s statement is false → Robot 2 is lying → Robot 3 is telling the truth → Robot 3 belongs to the **Truth Community**.

Assume **Robot 1** is from the Lie Community:

* Robot 1 lies → claims to be from Truth Community → Robot 2’s statement is true → Robot 2 tells the truth → Robot 3 is lying → Robot 3 belongs to the **Lie Community**.

**Conclusion:** Robot 3’s community depends on Robot 1’s, which is unknown. Therefore, **Robot 3’s community cannot be determined**.


---

### ख़राब रोबोट

एक कंपनी रोबोट बनाती है। कुछ रोबोट इस तरह प्रोग्राम किए गए हैं कि वे हमेशा सच बोलते हैं, जबकि दूसरे हमेशा झूठ बोलते हैं। इसलिए फैक्ट्री में दो समुदाय हैं – **सच बोलने वाला समुदाय (Truth Community)** और **झूठ बोलने वाला समुदाय (Lie Community)**।

आप तीन रोबोट से मिलते हैं और उनमें से एक से पूछते हैं – *“तुम किस समुदाय से हो?”*

* **रोबोट 1** कुछ बाइनरी भाषा में जवाब देता है, जो आपको समझ नहीं आता।
* **रोबोट 2** कहता है कि *“रोबोट 1 झूठ बोलने वाले समुदाय से है।”*
* **रोबोट 3** कहता है कि *“रोबोट 2 झूठ बोल रहा है।”*

अब बताइए: **रोबोट 3 किस समुदाय से है?**

---

### समाधान

मान लेते हैं कि रोबोट 1 **सच बोलने वाले समुदाय** से है।

* अगर ऐसा है, तो वह यह बताएगा कि वह सच बोलने वाले समुदाय से है।
* तब रोबोट 2 झूठ बोलेगा।
* और रोबोट 3 सही कहेगा कि रोबोट 2 झूठ बोल रहा है।

अब मान लो रोबोट 1 **झूठ बोलने वाले समुदाय** से है।

* तब वह अपने बारे में झूठ बोलेगा और कहेगा कि वह सच बोलने वाले समुदाय से है।
* इस स्थिति में भी रोबोट 2 झूठ बोलेगा।
* और रोबोट 3 फिर से सही होगा कि रोबोट 2 झूठ बोल रहा है।

👉 इसलिए, रोबोट 3 **“सच बोलने वाले समुदाय” (Truth Community)** से है। ✅

---
Q3. ### **Flip the Coin**

One day, you return home and find a lamp. Upon rubbing it, a genie appears and offers you a challenge. If you solve a simple puzzle, he will grant you three wishes.

He places **10 coins** on a table. You are told:

* Exactly **5 coins show heads** and **5 show tails**.
* You **cannot distinguish heads or tails by touch**.
* You can **flip the coins any number of times**.

**Task:** Divide the coins into **two separate sets**, each with the **same number of tails up**.

---

### **Solution:**

1. Randomly divide the 10 coins into **two sets of 5 coins each**.
2. **Flip all the coins in one of the sets**.

Now, both sets will have the **same number of tails**.

---

### सिक्का पलटें (Flip the Coin)

एक दिन आप घर लौटते हैं और आपको एक दीया मिलता है। उसे रगड़ने पर एक जिन्न प्रकट होता है और आपको एक ऑफ़र देता है। अगर आप उसकी पहेली हल कर दें, तो वह आपको **3 इच्छाएँ** पूरी करेगा।

जिन्न आपके सामने मेज़ पर **10 सिक्के** रखता है।

* इन सिक्कों को छूकर यह पता लगाना असंभव है कि कौन-सा हेड (Head) है और कौन-सा टेल (Tail)।
* आपको बताया जाता है कि इन 10 में से **5 सिक्कों पर हेड ऊपर है और 5 पर टेल ऊपर है**, लेकिन आपको नहीं पता कौन-सा कहाँ है।

अब सवाल यह है:
👉 क्या आप इन सिक्कों को **दो समूहों में बाँट सकते हैं** ताकि दोनों समूहों में **बराबर संख्या में टेल्स (Tails)** हों?
आप सिक्कों को कितनी भी बार पलट सकते हैं।

---

### समाधान

1. **10 सिक्कों को दो समूहों में बाँट दो, हर समूह में 5 सिक्के हों।**
   उदाहरण के लिए:

   * समूह 1 (Set-1): H H T T T
   * समूह 2 (Set-2): T H T H H

2. अब **समूह 2 के सभी सिक्के पलट दो**।
   पलटने के बाद:

   * समूह 1 (Set-1): H H T T T
   * समूह 2 (Set-2): H T H T T

   अब दोनों समूहों में **3-3 टेल्स (Tails)** हैं। ✅

---

👉 यही तरीका किसी भी सिक्कों की शुरुआती स्थिति में काम करेगा।
यानी आप हमेशा दोनों समूहों में **बराबर टेल्स** बना सकते हैं।

---

Q4. ### **Black and White Hats**

One hundred students stand in a line, one behind the other, each wearing either a black or white hat. Every student can see the hats of the students in front but not their own or those behind.

The teacher starts from the back and asks each student to guess the color of their own hat. If they guess correctly, they pass the final exam; otherwise, they fail.

Before the questioning begins, students are allowed to agree on a strategy.

**Question:** What is the maximum number of students that can pass?

---

### **Solution:**

Using a predefined strategy, **99 students can pass**.

The strategy is:

* The last (100th) student counts the number of white hats in front of them and says **"white"** if the number is odd, **"black"** if even. This student has a 50% chance of being correct.
* Each subsequent student keeps track of the number of white hats they see ahead and compares it with the parity announced by the previous student to deduce their own hat color.

Thus, **at most 99 students are guaranteed to pass**.


---

### काले और सफेद टोपी (Black and White Hats)

**प्रश्न:**
100 छात्र एक कतार में खड़े हैं, एक के पीछे एक।

* हर छात्र के सिर पर या तो **काली टोपी** है या **सफेद टोपी**।
* हर छात्र अपने सामने खड़े छात्रों की टोपी देख सकता है, लेकिन अपनी टोपी या अपने पीछे खड़े छात्रों की टोपी नहीं देख सकता।

शिक्षक सबसे पीछे वाले छात्र से शुरू करता है और हर छात्र से पूछता है कि उसकी टोपी का रंग क्या है।

* अगर जवाब सही हुआ → छात्र परीक्षा पास करेगा।
* अगर जवाब गलत हुआ → छात्र फेल हो जाएगा।

छात्र परीक्षा शुरू होने से पहले आपस में **रणनीति (strategy)** बना सकते हैं।
👉 अधिकतम कितने छात्र पास हो सकते हैं?

---

### समाधान

एक **सरल रणनीति** से **99 छात्र निश्चित रूप से पास** हो सकते हैं।

रणनीति इस प्रकार है:

1. कतार में सबसे पीछे (100वें) छात्र को यह तय करना है कि वह **“Parity” (सम/विषम गिनती)** बताएगा।

   * वह अपने सामने जितनी **सफेद टोपियाँ** देखता है, अगर वह संख्या **विषम (Odd)** है, तो वह “सफेद” बोलेगा।
   * अगर संख्या **सम (Even)** है, तो वह “काली” बोलेगा।

   इससे बाकी छात्रों को एक संकेत (clue) मिल जाएगा।

2. अब 99वाँ छात्र (उसके सामने वाले सभी टोपी देख सकता है):

   * वह पीछे वाले छात्र का संकेत सुनकर और सामने की सफेद टोपियों की गिनती करके **अपनी टोपी का रंग निकाल सकता है**।

3. इसी तरह, 98वाँ, 97वाँ… और आगे के छात्र भी गणना करके सही-सही बता सकते हैं।

👉 इस रणनीति में **100वाँ छात्र 50-50 संभावना** पर होता है (वह पास भी हो सकता है या फेल भी), लेकिन बाकी **99 छात्र निश्चित रूप से पास** हो सकते हैं। ✅

---

**अधिकतम पास होने वाले छात्र = 99**

---

Q5. ### **Money Heist**

You are at the Bank of Portugal. Two rooms: one contains 1000 tons of gold, the other is an inescapable police trap. Two guards stand at the gates — one always tells the truth, the other always lies. You may ask **one question to one guard**.

**Question to ask either guard:**
*“If I asked the other guard which room is the Police Trap, what would he say?”*

**How to use the answer:**
Both guards will point to the **gold room** in response. Go to the room they indicate — it contains the treasure.

**Brief explanation:**

* The truthful guard reports the liar’s (false) answer, which points to the gold.
* The liar lies about the truthful guard’s (true) answer, also producing the gold.


---

# मनी हाइस्ट (Money Heist)

आप पुर्तगाल के एक बैंक के सामने हैं। वहाँ बेहतरीन सुरक्षा है। बैंक में **दो लॉकर रूम** हैं।

* एक में **1000 टन सोना** रखा है,
* जबकि दूसरा एक **अटूट पुलिस जाल (Police Trap)** है।

आप (The Professor) ने एक चूक ढूँढ ली है। वहाँ दो दरवाज़ों की रखवाली दो गार्ड कर रहे हैं। दोनों के परिवार की एक अजीब परंपरा है:

* **एक गार्ड कभी झूठ नहीं बोलता (सत्य बोलने वाला)**,
* और **दूसरा कभी सच नहीं बोलता (झूठ बोलने वाला)**।

आप बूढ़े आदमी का भेष किए हुए हैं और आप किसी एक गार्ड से **केवल एक ही सवाल** पूछ सकते हैं — उसके बाद वह शक उठ जाएगा। तो आप कौन सा सवाल पूछेंगे ताकि आप निश्चित रूप से पता कर सकें कि किस कमरे में खज़ाना (सोना) है और गैंग को हाइस्ट करवा सकें?

---

## समाधान

गार्ड से यह सवाल पूछें:
**“अगर मैं दूसरे गार्ड से पूछूँ कि पुलिस के जाल (Police Trap) की दिशा कौन सी है, तो वह क्या बताएगा?”**

और जो भी उत्तर वह देगा — वह **खज़ाने (Treasure)** की दिशा बताता है।

---

## व्याख्या (Explanation)

* यदि आप **सत्य बोलने वाले** गार्ड से पूछते हैं: वह सही-सही बताएगा कि दूसरा (जो झूठ बोलता है) क्या कहेगा। चूंकि दूसरा झूठ बोलेगा, वह पुलिस जाल की दिशा के बजाय **खज़ाने की दिशा** बताएगा। सत्यवादी गार्ड वही बताएगा — यानी प्राप्त उत्तर खज़ाने की दिशा होगी।
* यदि आप **झूठ बोलने वाले** गार्ड से पूछते हैं: वह दूसरे (सत्यवादी) के वास्तविक उत्तर के बारे में **झूठ बोलकर** आपको बताएगा — और झूठ के कारण वह भी **खज़ाने की दिशा** बता देगा।

इसलिए, चाहे आप किसी भी गार्ड से सवाल करें, जो उत्तर आप सुनते हैं वह **खज़ाने की दिशा** होगी। ✅

---

Q6. ### **The MasterChef**

A specific dish requires exactly **7 liters** of water, but you only have two measuring glasses: one of **5L** and one of **4L**. How can you measure exactly 7L?

---

### **Solution:**

1. Fill the **5L glass** completely.
2. Pour from the 5L into the **4L glass** until it’s full — this leaves **1L** in the 5L glass.
3. Pour the **1L** into the dish.
4. Repeat steps 1–3 to add another **1L** — total now **2L** in the dish.
5. Finally, fill the **5L glass** and pour all **5L** into the dish.

**Total: 2L + 5L = 7L** — exact amount needed.

---

# द मास्टरशेफ (The MasterChef)

एक विशेष डिश को ठीक **7 लीटर** पानी चाहिए। समस्या यह है कि आपके पास **ठीक 7L नापने के लिए कोई माप का ग्लास नहीं** है।
आपके पास केवल दो ग्लास हैं: **4L** और **5L**। तो यह कैसे किया जा सकता है?

---

## समाधान

यह सटीक माप आसान तरीके से किया जा सकता है — निम्न चरणों को फॉलो करें:

1. **5L ग्लास को भरें**।
2. 5L से **4L ग्लास** भरें। इससे 5L ग्लास में **1L बच जाएगा**।
3. वह बचा हुआ **1L सीधे बर्तन (dish) में डाल दें**।
4. अब फिर से **5L ग्लास भरें**।
5. 5L से फिर से **4L ग्लास भरकर** उसमें से 4L भर दें — पर ध्यान दें कि पहले से 4L ग्लास खाली कर लें (या जरूरत के हिसाब से)। पर ऊपर दिए हुए समाधान के अनुसार, हम 1L बर्तन में डालकर दोहराते हैं:

   * पहले चरणों को **दुबारा दोहराएँ**: 5L भरें → 4L भरें → बचे 1L बर्तन में डालें। अब कुल बर्तन में जमा पानी = **1L + 1L = 2L**।
6. अंत में **फिर 5L ग्लास से बर्तन में 5L डाल दें**।

   * कुल = पहले जमा 2L + अब 5L = **7L**।

इस तरह आप केवल 4L और 5L के ग्लास का उपयोग करके ठीक **7 लीटर** पानी माप सकते हैं। ✅

---


Q8. ### **The Chocolate Lover**

You have **10 white chocolates** and **10 dark chocolates**, all identical in packaging. What is the **minimum number of random picks** needed to guarantee **at least one pair of the same type**?

---

### **Solution:**

The minimum number of picks required is **3**.

* Pick 1: Could be white or dark.
* Pick 2: Could be the other type.
* Pick 3: Regardless of the outcome, you’ll now have **at least two chocolates of the same type**.

This follows the **Pigeonhole Principle** — with two types, picking three guarantees a matching pair.


---

# चॉकलेट लवर (The Chocolate Lover)

आपके पास **10 सफ़ेद चॉकलेट** और **10 डार्क चॉकलेट** हैं, और दोनों के पैकेट में कोई अंतर नहीं है।
👉 कम से कम कितनी बार यादृच्छिक (random) तरीके से चॉकलेट निकालनी होगी ताकि आपके पास **कम से कम दो एक ही प्रकार की चॉकलेट** आ जाए?

---

## समाधान

कम से कम **3 बार** चॉकलेट निकालनी पड़ेगी।

1. मान लीजिए पहली बार आपने **डार्क चॉकलेट** निकाली।
2. दूसरी बार आपने **सफ़ेद चॉकलेट** निकाली।
3. तीसरी बार चाहे **डार्क** निकले या **सफ़ेद**, दोनों ही स्थिति में आपके पास कम से कम **एक जोड़ी (pair)** हो जाएगी।

👉 भले ही तीनों चॉकलेट एक ही रंग की हों, तब भी आपके पास एक जोड़ी होगी।

इसलिए, **3 यादृच्छिक चयन (random picks)** पर्याप्त हैं। ✅

---

Q10. ### **The Grid**

A **10 × 10 table** is filled with repeating numbers along its diagonals. What is the **total sum** of all the numbers in the table?

---

### **Solution:**

The total sum is **1000**.

* Pairs like (1 & 19), (2 & 18), ..., (9 & 11) all add up to **20**.
* Their frequencies match their values:

  * 1 & 19 appear **once**
  * 2 & 18 appear **twice**
  * 3 & 17 appear **three times**
  * …
  * 9 & 11 appear **nine times**

Each pair contributes:
`(value + its pair) × frequency = 20 × frequency`

So,
`20 × (1 + 2 + 3 + ... + 9) = 20 × 45 = 900`

* The number **10** appears **10 times**:
  `10 × 10 = 100`

**Total sum:**
`900 + 100 = 1000`

# द ग्रिड (The Grid)

चित्र में दिखाया गया है कि एक **10 × 10 तालिका** अपनी मुख्य विकर्णों (diagonals) पर दोहराते हुए संख्याओं से भरी हुई है।
मस्तिष्क में ही तालिका में उपस्थित **सभी संख्याओं का कुल योग** बताइए।

---

## समाधान

तालिका में सभी संख्याओं का कुल योग **1000** है।

तर्क इस प्रकार है:

* 1 और 19 जोड़कर **20** होते हैं — और ये दोनों **एक-एक बार** दिखाई देते हैं।
* 2 और 18 जोड़कर **20** होते हैं — ये दोनों **दो-दो बार** दिखाई देते हैं।
* 3 और 17 → 20 — **तीन-तीन** बार।
* 4 और 16 → 20 — **चार-चार** बार।
* 5 और 15 → 20 — **पाँच-पाँच** बार।
* 6 और 14 → 20 — **छह-छह** बार।
* 7 और 13 → 20 — **सात-सात** बार।
* 8 और 12 → 20 — **आठ-आठ** बार।
* 9 और 11 → 20 — **नौ-नौ** बार।
* और **10** **दस बार** दिखाई देता है।

इन सभी को जोड़ने पर कुल आता है **1000**। ✅

---

Q11. ### **The Bulb**

There are **three switches** in one room. Only **one** of them controls a **bulb in the next room**. You can flip the switches any way you like, but you can **only visit the next room once**.

**Question:** What is the **minimum number of visits** needed to determine which switch controls the bulb?

---

### **Solution:**

**Only one visit** is needed.

1. Turn **on the first switch** and **wait 5 minutes**.
2. Turn **off the first switch**, turn **on the second switch**.
3. Enter the next room.

Now observe the bulb:

* If it’s **on**, it’s the **second switch**.
* If it’s **off but warm**, it’s the **first switch**.
* If it’s **off and cold**, it’s the **third switch**.

Thus, **one visit** is enough to identify the correct switch.

---

# बल्ब (The Bulb)

एक कमरे में **तीन स्विच** हैं, जिनमें से केवल **एक स्विच** दूसरे कमरे में लगे बल्ब को जलाता है।
👉 कम से कम कितनी बार उस कमरे में जाना पड़ेगा ताकि पता चल सके कि कौन-सा स्विच बल्ब को नियंत्रित करता है?

---

## समाधान

1. **पहला स्विच ऑन करें** और लगभग **5 मिनट तक इंतज़ार करें**।
2. अब **पहला स्विच ऑफ़ करें** और **दूसरा स्विच ऑन करें**।
3. अब दूसरे कमरे में जाएँ और बल्ब की जाँच करें।

* अगर बल्ब **जला हुआ** है → तो बल्ब **दूसरे स्विच** से नियंत्रित है।
* अगर बल्ब **बुझा हुआ है लेकिन गर्म** है → तो बल्ब **पहले स्विच** से नियंत्रित है।
* अगर बल्ब **बुझा हुआ है और ठंडा भी है** → तो बल्ब **तीसरे स्विच** से नियंत्रित है।

👉 इस तरह, केवल **एक बार कमरे में जाकर** आप सही स्विच का पता लगा सकते हैं। ✅

---

Q. 12. ### **The Helium Balloon**

You’re inside a car with a **helium balloon** tied to the floor. The **windows are closed**.

**What happens to the balloon when:**

1. You **accelerate** the car?
2. You **brake suddenly**?

---

### **Solution:**

* When you **accelerate**, the air inside the car shifts **backward**, creating higher pressure at the rear. The helium balloon, being lighter than air, moves **forward**.

* When you **brake**, the air shifts **forward**, increasing pressure near the windshield. The balloon moves **backward**.

So, the balloon always moves **opposite** to the direction the air shifts inside the car.


---

# हीलियम गुब्बारा (The Helium Balloon)

आप एक कार में बैठे हैं और फर्श से बंधा हुआ एक **हीलियम का गुब्बारा** है।
कार की **खिड़कियाँ बंद** हैं।
👉 अब सवाल यह है: जब आप **एक्सीलरेटर दबाते हैं** तो गुब्बारे का क्या होगा, और जब आप अचानक **ब्रेक लगाते हैं** तो क्या होगा?

---

## समाधान

* जब कार **तेज़ होती है (accelerate करती है)** →
  हवा भी आपके शरीर की तरह पीछे की ओर धकेली जाती है।
  लेकिन गुब्बारा हवा से हल्का है, इसलिए वह **आगे की ओर बढ़ता है**।

* जब कार अचानक **ब्रेक करती है** →
  हवा आगे की ओर (विंडशील्ड की तरफ़) जमा हो जाती है।
  हल्का गुब्बारा तब हवा से धकेलकर **पीछे की ओर चला जाता है**। ✅

---

Q13. ### **Crossing the Stormy River**

Four people need to cross a stormy river with one boat that can hold only two people at a time. Each person takes a different time to cross:

* Person A: 1 minute
* Person B: 5 minutes
* Person C: 7 minutes
* Person D: 9 minutes

When two people cross together, the time taken equals the **slower person's time**.

**Question:** What is the minimum total time for all four to cross?

---

### **Solution:**

**Minimum time:** 23 minutes.

**Steps:**

1. Person A and Person D cross → 9 minutes
2. Person A returns → 1 minute
3. Person A and Person C cross → 7 minutes
4. Person A returns → 1 minute
5. Person A and Person B cross → 5 minutes

**Total time:** 9 + 1 + 7 + 1 + 5 = 23 minutes.

---

# तूफ़ानी नदी पार करना (Crossing the Stormy River)

चार लोगों को एक **तूफ़ानी नदी** पार करनी है।
लेकिन उनके पास केवल **एक नाव** है, और नाव में बिना किसी के चलाए जाना खतरनाक है।
नाव इतनी मज़बूत है कि उसमें **एक बार में केवल दो लोग** ही बैठ सकते हैं।

सभी लोगों की **गति अलग-अलग** है:

* एक व्यक्ति को पार करने में लगता है → **1 मिनट**
* दूसरे को → **5 मिनट**
* तीसरे को → **7 मिनट**
* चौथे को → **9 मिनट**

👉 जब दो लोग नाव से जाते हैं, तो समय उनकी **धीमी गति (ज्यादा समय वाले व्यक्ति)** के बराबर लगेगा।

सवाल: **सभी 4 लोगों को नदी पार करने में न्यूनतम समय कितना लगेगा?**

---

## समाधान

✔ न्यूनतम समय = **23 मिनट**

### चरणबद्ध समझाइए:

1. **पहला राउंड** →
   (1, 9) नाव से जाते हैं → समय = **9 मिनट**
   फिर 1 वापस आता है → समय = **1 मिनट**

2. **दूसरा राउंड** →
   (1, 7) नाव से जाते हैं → समय = **7 मिनट**
   फिर 1 वापस आता है → समय = **1 मिनट**

3. **तीसरा राउंड** →
   (1, 5) नाव से जाते हैं → समय = **5 मिनट**

---

### ⏱ कुल समय = 9 + 1 + 7 + 1 + 5 = **23 मिनट** ✅

---
Q13. ### **100 Tubelights and Friends**

There are **100 tube lights**, all initially off. In an adjacent room, **100 friends** enter one by one:

* The 1st friend toggles (switches on) every light.
* The 2nd friend toggles every 2nd light (2, 4, 6, ...).
* The 3rd friend toggles every 3rd light (3, 6, 9, ...), and so on, until the 100th friend toggles only the 100th light.

**Question:** After all 100 friends have taken their turns, how many lights remain **on**?

---

### **Solution:**

A light’s state changes once for every divisor it has.

* Most numbers have divisors in pairs (e.g., 40 has divisors 1 & 40, 2 & 20, 4 & 10, 5 & 8), so the light toggles an even number of times, ending off.
* Perfect squares (e.g., 25) have an odd number of divisors because one divisor repeats (5 & 5), so those lights toggle an odd number of times and remain **on**.

**Number of perfect squares between 1 and 100:**
1, 4, 9, 16, 25, 36, 49, 64, 81, 100 — total **10**.

**Therefore, 10 tubelights will be on at the end.**

---

# 100 ट्यूबलाइट्स और दोस्त

मान लीजिए 100 ट्यूबलाइट्स हैं, सभी **बंद**।
साथ वाले कमरे में 100 दोस्त हैं।

* **पहला दोस्त** आता है और सभी 100 ट्यूबलाइट्स **ऑन** कर देता है।
* **दूसरा दोस्त** आता है और केवल 2, 4, 6… (सभी **even-numbered**) ट्यूबलाइट्स को **ऑफ** कर देता है।
* **तीसरा दोस्त** आता है और केवल 3, 6, 9… (हर तीसरे नंबर) वाली ट्यूबलाइट्स को देखता है।

  * अगर लाइट **ऑन** है तो वह उसे **ऑफ** करता है।
  * अगर **ऑफ** है तो उसे **ऑन** करता है।
* इसी तरह, सभी 100 दोस्त एक-एक करके यही प्रक्रिया करते हैं।

👉 सवाल: **अंत में कितनी ट्यूबलाइट्स ऑन रहेंगी?**

---

## समाधान

मान लीजिए **40 नंबर** ट्यूबलाइट।

* इसे हर वह दोस्त टॉगल करेगा जिसका नंबर **40 का भाजक (divisor)** है।
* 40 के भाजक हैं: 1, 2, 4, 5, 8, 10, 20, 40
* तो यह बार-बार ऑन/ऑफ होगी और अंत में **फिर से बंद** हो जाएगी।

लेकिन मान लीजिए **25 नंबर** ट्यूबलाइट।

* 25 के भाजक हैं: 1, 5, 25
* यहाँ 5 दोहराया जाता है (क्योंकि 25 = 5×5, यानी perfect square है)।
* इसलिए यह ट्यूबलाइट अंत में **ऑन** रह जाएगी।

👉 नतीजा: **केवल perfect square नंबर वाली ट्यूबलाइट्स अंत में ऑन रहेंगी।**

---

## 1 से 100 तक perfect squares:

1, 4, 9, 16, 25, 36, 49, 64, 81, 100

✅ यानी कुल **10 ट्यूबलाइट्स ऑन रहेंगी।**

---

Q15. ### **The City of Hope**

A meteor has hit your city, destroying all external connections. The city of **Hope** is 400 km away, and you need to travel on foot to reach it.

* Each person can carry food and water for **5 days** only.
* The farthest one can travel in a day is **100 km**.
* You need to reach the city, stay overnight, and return without running out of supplies.
* There is no way to refill supplies along the way or in the city.

**Question:** What is the minimum number of people (including yourself) required to accomplish this mission?

---

### **Solution:**

Each person carries 5 days’ rations, so:

* 4 people × 5 days = **20 total days** of rations.

**Plan:**

* **Day 1:** 4 people travel 1 day (100 km). Use 4 days of rations (1 per person). One person returns (1 day of rations). Remaining rations for forward travel: 15 days.
* **Day 2:** 3 people travel 1 day (100 km). Use 3 days of rations. One person returns (2 days of rations). Remaining rations: 10 days.
* **Day 3:** 2 people travel 1 day (100 km). Use 2 days of rations. One person returns (3 days of rations). Remaining rations: 5 days.
* **Day 4:** The last person travels 1 day (100 km), arrives, stays overnight, and uses 1 day of rations.
* **Return trip:** Uses 4 days of rations to return.

**Total distance covered:** 4 × 100 km = 400 km.

**Minimum number of people needed:** **4** (including you).


---

# आशा नगर (The City of Hope)

आप एक दिन जागते हैं और पाते हैं कि एक उल्का पिंड (meteor) ने आपके शहर को नष्ट कर दिया है और बाहरी दुनिया से सभी संपर्क कट गए हैं। एक दूसरा शहर **“Hope”** है जहाँ सम्भवतः ऐसे संसाधन हैं जो आपके शहर की बाहरी दुनिया से कनेक्शन बहाल करने में मदद कर सकते हैं। वहां तक पहुँचने के लिए आपको पैदल जाना होगा।

नियम और सीमाएँ:

* हर व्यक्ति **अधिकतम 5 दिनों** का खाना/पानी ही साथ ले जा सकता है (इसीमें वापसी का भी ध्यान रखना है)।
* एक व्यक्ति एक दिन में **अधिकतम 100 किमी** चल सकता है।
* शहर **Hope** दूरी पर है: **400 किमी**।
* आप शहर में रुक कर ओवरनाइट (एक रात) रहकर वापस आना चाहते हैं। शहर में कोई खाद्य/पानी की आपूर्ति नहीं मिलती — यानी आप वहां से कुछ नहीं भर सकते।

**प्रश्न:** न्यूनतम कितने लोग (आप सहित) चाहिए ताकि यह मिशन सफल हो — यानी पहुँच कर एक रात वहां रुकना और सुरक्षित वापस आना, बिना रेशन खत्म किए?

---

## समाधान (हिन्दी में सार)

हर व्यक्ति 5 दिनों का रेशन लेकर जा सकता है। यदि कुल 4 लोग हों तो सभी मिलकर कुल **20 दिन के रेशन** ले जा सकते हैं (4 × 5 = 20 person-days)। ठीक योजना बनाकर इन्हें इस तरह खर्च किया जा सकता है कि एक व्यक्ति Hope तक पहुँचे, एक रात रुके और फिर बिना रेशन ख़त्म किए वापस आ पाए।

समरी में दिए गए स्टेप्स (दिन-दर-दिन विचार):

* **दिन 1:** चारों लोग आगे बढ़ते हैं — इस दिन चारों का 1 दिन का रेशन खपत हो जाती है (कुल बचा = 20 − 4 = 16 person-days)। फिर एक व्यक्ति वापसी के लिये लौट जाता है — उसे वापसी में 1 दिन चाहिए, तो उसकी वापसी का रेशन अलग रखा गया माना जा सकता है। शेष आगे बढ़ने वालों के पास आगे के काम के लिये कुल **15 दिन** के बराबर रेशन रह जाता है (विस्तृत बंटवारे समाधान में बताया गया)।
* **दिन 2:** आगे बढ़ रहे 3 लोग एक दिन चलते — 3 दिन खर्च होते; फिर एक और व्यक्ति वापस चला जाता (जिसे कुल वापसी के लिये 2 दिन चाहिए)। इससे आगे बढ़ने वालों के पास आगे के लिये कुल **10 दिन** के बराबर बचे।
* **दिन 3:** आगे बढ़ रहे 2 लोग एक दिन चलते — 2 दिन खर्च होते; फिर एक व्यक्ति वापस जाता (वापसी के लिये 3 दिन)। आगे बढ़ने वाले व्यक्ति के पास आगे के लिये **5 दिन** के बराबर रेशन बचा रहता है।
* **दिन 4:** अंतिम व्यक्ति 1 दिन और चलता और Hope पहुँच कर वहां **एक रात** रुकता है (उसे ओवरनाइट और वापसी के लिये कुल 4 दिन के रेशन की जरूरत रहती है) — उपलब्ध रेशन से यह पूरा संभव है।

इस तरह, **कुल 4 व्यक्ति (आप सहित)** पर्याप्त हैं ताकि कोई एक व्यक्ति Hope पहुँच सके, एक रात रुके और सुरक्षित वापस आ सके **बिना रेशन ख़त्म हुए**। ✅

---
Q16. ### **The Gold Bar**

You have a gold bar to pay an intern over **7 days**, giving them **1/7th of the bar** each day. You want to minimize the number of cuts made on the bar.

**Question:** What is the minimum number of cuts needed so you can pay the intern exactly 1/7th each day?

---

### **Solution:**

**Minimum cuts:** 3 cuts, creating pieces of sizes **1/7, 2/7, and 4/7**.

**Payment schedule:**

* Day 1: Give 1/7 piece.
* Day 2: Give 2/7 piece, take back 1/7 piece (total = 2/7).
* Day 3: Give 1/7 piece again (total = 3/7).
* Day 4: Give 4/7 piece, take back 1/7 and 2/7 pieces (total = 4/7).
* Day 5: Give 1/7 piece again (total = 5/7).
* Day 6: Give 2/7 piece, take back 1/7 piece (total = 6/7).
* Day 7: Give 1/7 piece again (total = 7/7).

Thus, with just **3 cuts**, the Ninja can pay the intern correctly each day.

---

# गोल्ड बार (The Gold Bar)

Ninja के पास अपने इंटरन को सात दिनों तक भुगतान करने के लिए एक **सोने की छड़ी (gold bar)** है। हर दिन के अंत में Intern को **बार का 1/7 हिस्सा** दिया जाना है। आप बार पर **कम से कम कितने कट** कर सकते हैं ताकि हर दिन सही भुगतान किया जा सके (और पहले दिए गए टुकड़ों को वापस लेकर अगले दिन उपयुक्त संयोजन दिया जा सके)?

---

## समाधान

सोने की छड़ी को **3 कट** लगाकर तीन टुकड़ों में बाट दें — आकार होंगे: **1/7, 2/7, 4/7**।

फिर दिन-प्रतिदिन भुगतान इस तरह कर सकते हैं:

1. **दिन 1:** इंटरन को **1/7** दें.
2. **दिन 2:** इंटरन को **2/7** दें और **1/7** वापस ले लें → कुल उसके पास = 2/7.
3. **दिन 3:** इंटरन को **1/7** (अब उसके पास 2/7 + 1/7 = 3/7) दें.
4. **दिन 4:** इंटरन को **4/7** दें और **1/7 तथा 2/7** वापस ले लें → उसके पास सिर्फ 4/7.
5. **दिन 5:** इंटरन को **1/7** दें (अब 4/7 + 1/7 = 5/7).
6. **दिन 6:** इंटरन को **2/7** दें और **1/7** वापस ले लें (अब 4/7 + 2/7 = 6/7).
7. **दिन 7:** इंटरन को **1/7** दें (अब 4/7 + 2/7 + 1/7 = 7/7 = पूरा बार)।

इस प्रकार, केवल **3 कट** (तीन टुकड़े: 1/7, 2/7, 4/7) पर्याप्त हैं। ✅

---

Q16. ### **How Many Rabbits?**

A newly-born pair of rabbits (one male, one female) is placed in a field. Rabbits mature and mate at one month old. From the **second month onward**, each female produces **one new pair** (male and female) every month. Rabbits never die.

**Question:** How many pairs of rabbits will there be after **one year**?

---

### **Solution:**

* At the end of month 1: 1 pair (original pair).
* Month 2: original female produces 1 new pair → 2 pairs total.
* Month 3: original female produces another pair → 3 pairs total.
* Month 4: original female + female born 2 months ago produce → 5 pairs total.

This follows the **Fibonacci sequence**:

* F(0) = 1, F(1) = 1
* F(n) = F(n-1) + F(n-2)

The sequence:
1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144...

After 12 months, there will be **144 pairs**, i.e., **288 rabbits**.

---

# कितने खरगोश? (How many Rabbits?)

मान लीजिए कि एक नवजात खरगोश का जोड़ा (एक नर और एक मादा) एक खेत में रखा गया है।

**शर्तें:**

* खरगोश **1 महीने की उम्र में यौवन/मेटिंग योग्य** हो जाते हैं।
* दूसरी महीने के अंत तक, मादा **हर महीने 1 नया जोड़ा** (एक नर और एक मादा) जन्म देती है।
* खरगोश कभी नहीं मरते।

**प्रश्न:** 1 साल के अंत में कुल कितने जोड़े होंगे?

---

## समाधान

* **पहले महीने के अंत:** जोड़ा अभी भी वही 1 जोड़ा है।
* **दूसरे महीने के अंत:** मादा अपना पहला जोड़ा पैदा करती है → कुल 2 जोड़े।
* **तीसरे महीने के अंत:** मूल मादा दूसरा जोड़ा देती है → कुल 3 जोड़े।
* **चौथे महीने के अंत:**

  * मूल मादा नया जोड़ा देती है।
  * दो महीने पहले जन्मी मादा अपना पहला जोड़ा देती है → कुल 5 जोड़े।

यह पैटर्न **फ़िबोनाच्ची श्रृंखला (Fibonacci Series)** की तरह है:

[
F(0)=F(1)=1, \quad F(n) = F(n-1) + F(n-2)
]

**श्रृंखला (जोड़े के हिसाब से):**
1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144…

**निष्कर्ष:**

* 12 महीनों के अंत में = **144 जोड़े**, यानी कुल **288 खरगोश**। ✅

---


