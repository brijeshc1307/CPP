**CCD (Can Compress Data) Tool Maintenance & Enhancement**

हमारे पास एक थर्ड पार्टी टूल है जिसका नाम **CCD (Can Compress Data)** है, जो 2010 में जर्मनी में डेवलप किया गया था। मेरा काम इस टूल का **maintenance** और **feature enhancement** करना है।

इस टूल का मुख्य कार्य यह है कि यह विभिन्न प्रकार के signals जैसे कि **Pressure, Temperature, Speed** आदि को compress करता है। **उदाहरण के तौर पर**, मान लीजिए हमारे पास **1000 signals** हैं, और हमें इन signals को **compress** करना है। ऐसे में **CCD tool** पहले इन signals को **type के आधार पर group** करता है — जैसे कि:
* Pressure signals एक group में
* Temperature signals एक अलग group में
* Speed signals एक और group में

**Grouping** करने के बाद, CCD इन grouped signals को **CAN messages में compress** करता है और फिर उन्हें एक **`.ccd` एक्सटेंशन वाली फाइल** में **store** कर देता है।

इस प्रोसेस से न सिर्फ data को efficiently store किया जाता है, बल्कि बाद में उसे आसानी से identify और retrieve भी किया जा सकता है।

मैंने इस टूल का पूरा **Documentation** तैयार किया जिसमें शामिल हैं:

* **Developer Guide**
* **Test Plan**
* **Test Results**

शुरुआत में यह टूल केवल **32-bit signals** के लिए डिज़ाइन किया गया था। लेकिन नए requirements के अनुसार हमें इसे **64-bit signals** के लिए भी compatible बनाना था। इसके लिए हमने:

* 32-bit के existing functions को **function overloading** के ज़रिए extend किया।
* Compression logic को modify करके उसे 64-bit signal support के लिए enhance किया।

इस enhancement के बाद CCD टूल अब 64-bit signals को भी compress करके `.ccd` फाइल में सुरक्षित रूप से store कर सकता है।

---

**Developer Guide:**
इसमें हर एक function की **definition** दी गई है, जैसे कि उस function का क्या उपयोग है, वो किस purpose के लिए लिखा गया है, और उसे कैसे call करना है। अब चूंकि हम इस टूल का **maintenance** और **improvement** का कार्य कर रहे हैं, इसलिए Developer Guide को लगातार update किया जाता है ताकि future developers को समझने में आसानी हो।

---

**Test Plan:**
Test Plan एक **structured document** होता है जिसमें हम ये लिखते हैं कि हमें क्या-क्या test करना है और किन steps के द्वारा करना है। यह आमतौर पर **table format** में होता है, और हर प्रोजेक्ट या टीम का format थोड़ा अलग हो सकता है।

Table के ऊपर यह mention होता है कि:

* हम क्या functionality test करने जा रहे हैं
* उसे test करने के लिए कौन-कौन से steps follow किए जाएंगे

उदाहरण के लिए:

| **Step**        | **Expected Result** |
| --------------- | ------------------- |
| Press Space Key | Screen will open    |

इसके बाद जब testing की जाती है, तो जो भी actual result आता है, उसे tester **Test Result** फाइल में mention करता है। इससे हमें यह पता चलता है कि कोई feature pass हुआ या fail, और debugging में भी मदद मिलती है।

---

**Challenge 1 – 32-bit से 64-bit पर Migration:**
पहला चैलेंज यह था कि existing function जो केवल **32-bit** data पर काम कर रहा था, उसे **64-bit** data के लिए compatible बनाना। कुछ critical जगहों पर हम **`void*` (void pointer)** का इस्तेमाल कर रहे थे, जो underlying system architecture पर depend करता है — यानी कि 32-bit system में यह 4 bytes और 64-bit system में 8 bytes handle करता है।

पहले case में हमें सिर्फ **4 byte data** capture करना होता था, इसलिए void pointer expected behavior दे रहा था। लेकिन अब हमें **8 byte data** (64-bit signal) handle करना था, जिसके लिए void pointer के usage को update करना जरूरी था। इसके लिए हमने:

* Code को carefully analyze किया
* Pointer arithmetic और memory alignment को modify किया
* Functions को **64-bit safe** बनाया ताकि void pointer सही से 8 byte data capture कर सके

---

**Challenge 2 – Precision Loss in Compression Function:**
दूसरे चैलेंज में, compression से related तीन functions में से एक function ऐसा था जिसमें **float values** को automatically **round off** कर दिया जाता था। लेकिन हमें requirement ये थी कि values को **without rounding** maintain किया जाए।

हमने इस issue को trace किया और पाया कि function internally float का use कर रहा है, जिसकी वजह से precision loss हो रहा है। हमने इसे **double** में convert किया ताकि ज़्यादा precision retain किया जा सके। हालांकि यह implementation अभी भी **rounding off** करता है (due to legacy logic), लेकिन हमने client से confirmation लिया और client को यह acceptable है।

---


---

### **CCD (Can Compress Data) Tool – Maintenance & Enhancement**

We have a third-party tool called **CCD (Can Compress Data)**, which was developed in Germany in 2010. My role involves the **maintenance** of this tool and implementing **feature enhancements**.

The primary function of this tool is to **compress various types of signals** such as **Pressure, Temperature, and Speed**.

For example, suppose we have **1000 signals**, and we want to compress them. In this case, the **CCD tool first groups the signals based on their type**, such as:

* Pressure signals in one group
* Temperature signals in another group
* Speed signals in a separate group

After grouping, CCD **compresses these signals into CAN messages** and stores them in a file with the **`.ccd` extension**.

This process not only allows data to be **stored efficiently**, but also makes it **easier to identify and retrieve** later when needed.

I have also prepared the complete **documentation** for this tool, which includes:

* **Developer Guide**
* **Test Plan**
* **Test Results**

Originally, this tool was designed to support only **32-bit signals**. However, based on new requirements, we had to make it compatible with **64-bit signals**. To achieve this, we:

* Extended the existing 32-bit functions using **function overloading**.
* Enhanced the compression logic to support 64-bit signal data.

With these enhancements, the CCD tool is now capable of compressing and storing **64-bit signals** effectively in `.ccd` files.

---

**Developer Guide:**
This document contains the **definition of each function**, explaining what the function does, its purpose, and how it should be called or used. Since we are currently working on the **maintenance** and **improvement** of the tool, the Developer Guide is continuously updated to make it easier for future developers to understand the code and functionality.

---

**Test Plan:**
The Test Plan is a **structured document** where we define what needs to be tested and the steps to perform the testing. It is usually presented in a **table format**, though the format may vary across different teams or projects.

At the top of the table, it is mentioned:

* What functionality we are going to test
* The steps we will follow to test it

For example:

| **Step**        | **Expected Result** |
| --------------- | ------------------- |
| Press Space Key | Screen will open    |

After executing the tests, the tester records the actual outcomes in the **Test Result** file. This helps determine whether a feature has passed or failed and also assists in debugging if needed.

---

**Challenge 1 – Migrating from 32-bit to 64-bit Support:**
The first challenge was to make the existing functions, which were working only with **32-bit data**, compatible with **64-bit data**. There were certain critical sections in the code where we were using a **`void*` (void pointer)** to capture data. A void pointer's behavior depends on the system architecture — on a 32-bit system, it handles 4 bytes, while on a 64-bit system, it handles 8 bytes.

Previously, since we only needed to capture **4 bytes**, the void pointer was functioning correctly. However, with the requirement to handle **8-byte (64-bit)** signals, we had to update the logic accordingly. To resolve this:

* We thoroughly analyzed the existing code
* Updated pointer arithmetic and memory alignment logic
* Modified the functions to make them **64-bit safe**, ensuring that the void pointer correctly captured 8-byte data

---

**Challenge 2 – Precision Loss in Compression Function:**
The second challenge was related to one of the three compression functions, where **float values** were getting **automatically rounded off**. However, the requirement was to retain the original values **without rounding**.

On investigation, we found that the function was internally using `float`, which led to **precision loss**. We modified it to use **`double`** instead, to preserve higher precision. Although the function still performs some rounding (due to legacy logic), we reviewed this behavior with the client, and they confirmed that it is acceptable for their use case.

---

>Note

### **CCD (Can Compress Data) Tool – Maintenance & Enhancement**

I’ve been working on a third-party tool called **CCD**, which stands for **Can Compress Data**. It was originally developed in Germany back in 2010. My current role involves handling its **maintenance** and implementing **new feature enhancements** as per the client’s evolving requirements.

The main purpose of the CCD tool is to **compress various types of sensor signals** — such as **pressure, temperature, speed**, etc.

Let’s say we receive around **1000 signals**, and we don’t need to process them immediately. In that case, CCD helps by **grouping the signals based on their type** — for example, pressure signals go into one group, temperature into another, and speed into a separate one. After grouping, the tool **compresses them into CAN messages** and saves the result into a `.ccd` file.

This process not only helps **optimize storage** but also makes the data **easier to retrieve and manage** later on.

---

### **Documentation Work**

As part of the project, I also created complete documentation for the tool, which includes:

* **Developer Guide** – This explains each function’s purpose, how it works, and how to use it. It's very useful for current and future developers during maintenance or enhancement.
* **Test Plan** – A step-by-step guide that outlines what functionality we’re testing and how we’re testing it. It’s usually structured in a table format.
* **Test Results** – After executing tests, we log the actual outcomes to verify whether each feature passed or failed.

Here’s a quick example from the test plan:

* **Step:** Press Space Key
* **Expected Result:** Screen should open

---

### **Key Challenges & Solutions**

#### **Challenge 1 – Migrating from 32-bit to 64-bit Support**

Originally, CCD was designed to work with **32-bit signal data** only. But over time, we had a requirement to **support 64-bit data** as well.

This was a bit tricky — some parts of the code used **`void*` pointers** to handle raw signal data. Now, void pointers behave differently on different systems:

* On 32-bit systems, they handle 4 bytes
* On 64-bit systems, they handle 8 bytes

When we were capturing only 4 bytes earlier, everything worked fine. But once we moved to 64-bit, we had to update the logic to make sure the pointers could safely capture 8 bytes of data. To do that:

* We analyzed the existing logic thoroughly
* Updated the pointer arithmetic and memory handling
* Modified the functions using **function overloading** to support both 32-bit and 64-bit operations

Now, the tool works seamlessly with both signal types.

---

#### **Challenge 2 – Precision Loss in Compression**

The second challenge was around one of the **compression functions**. It was originally using **float values**, which caused some **rounding off** — and we were losing precision, which wasn’t acceptable in some use cases.

After investigating, we realized the function internally used `float`, which was the reason for the data loss. We updated it to use `double` instead, so we could retain more precision.

Although the function still performs slight rounding due to some legacy logic, we aligned with the client on this behavior — and they confirmed that it’s acceptable for their needs.

---
OR
---

### **CCD (Can Compress Data) Tool**

We have a third-party tool called **CCD (Can Compress Data)**, which was developed in Germany in 2010. My primary responsibility is maintaining this tool and implementing feature enhancements.

#### **Purpose of the Tool**

The main function of this tool is to **compress various types of signals** such as pressure, temperature, and speed.
For example, suppose we have 1000 signals that need to be compressed. CCD first groups these signals based on their type:

* Pressure signals in one group
* Temperature signals in another
* Speed signals in a separate group

After grouping, the CCD tool compresses these signals into CAN messages and stores them in a file with the `.ccd` extension.

This process not only helps in efficient data storage but also makes it easier to identify and retrieve the data later.

---

### **My Contributions**

I prepared the complete documentation for this tool, including:

* **Developer Guide**
* **Test Plan**
* **Test Results**

---

### **Enhancement – 64-bit Signal Support**

Initially, the tool was designed to handle only **32-bit signals**. However, based on new requirements, we needed to make it compatible with **64-bit signals**. To achieve this, we:

* Extended existing 32-bit functions using **function overloading**
* Modified the compression logic to support 64-bit signals

After this enhancement, the CCD tool is now capable of compressing and storing 64-bit signals in `.ccd` files.

---

### **Documentation Details**

#### **Developer Guide**

This guide includes definitions for each function — explaining its purpose, usage, and how to call it. As we continue to maintain and improve the tool, the Developer Guide is regularly updated to make it easier for future developers to understand the codebase.

#### **Test Plan**

The Test Plan is a structured document outlining:

* What functionalities are to be tested
* The step-by-step process to test them

Typically, it’s in a table format. For example:

| Step            | Expected Result    |
| --------------- | ------------------ |
| Press Space Key | Screen should open |

#### **Test Results**

After executing the test plan, testers record actual results in the Test Results document. This helps identify pass/fail status and supports debugging.

---

### **Key Challenges Faced**

#### **Challenge 1: Migration from 32-bit to 64-bit**

The first challenge was to make existing functions (which worked only with 32-bit data) compatible with 64-bit data. In some critical places, we used `void*` (void pointers), which behave differently depending on system architecture — 4 bytes on 32-bit systems and 8 bytes on 64-bit systems.

In the original design, only 4-byte data was needed, so the `void*` behaved as expected. But for 64-bit signals (8 bytes), we had to:

* Carefully analyze the code
* Modify pointer arithmetic and memory alignment
* Update functions to be **64-bit safe** so they could correctly handle 8-byte data using void pointers

---

#### **Challenge 2: Precision Loss in Compression Function**

The second challenge was related to one of the three compression functions that was **rounding off float values**, which wasn't acceptable for the new requirements.

Upon investigation, we found the function was internally using `float`, which caused **precision loss**. We resolved this by converting the logic to use `double`, ensuring higher precision.

Although due to some legacy logic it still performs rounding in specific cases, we discussed it with the client and received confirmation that the current behavior is acceptable.

---
In short
---

We use a third-party tool called **CCD (Can Compress Data)**, which was originally developed in Germany in 2010. My main responsibility is to maintain this tool and implement new feature enhancements as needed.

CCD's core function is to compress different types of signal data—such as **pressure**, **temperature**, and **speed**. For example, when dealing with a large dataset, say **1,000 signals**, the tool first groups the signals by type:

* All pressure signals are grouped together
* All temperature signals in another group
* And speed signals in their own group

Once grouped, CCD compresses the signals into **CAN messages** and stores the output in a file with the **.ccd** extension.

This approach not only improves **data storage efficiency** but also makes it easier to **identify and retrieve specific data** later.

As part of my work, I created **comprehensive documentation** for CCD, including:

* A **Developer Guide**
* A detailed **Test Plan**
* Complete **Test Results**

Originally, CCD supported only **32-bit signals**. However, due to new requirements, we needed to extend its functionality to handle **64-bit signals**. To accomplish this, we:

* Used **function overloading** to extend the existing 32-bit logic
* Updated the **compression algorithm** to support 64-bit data

With these enhancements, CCD is now fully capable of compressing and storing both **32-bit and 64-bit signals** in `.ccd` files.

---

### Example: Function Overloading for Compressing Signals

Let’s say we’re writing a `compressSignal` function in CCD that works with both 32-bit and 64-bit signals.

```cpp
#include <iostream>

// Compress function for 32-bit signals
void compressSignal(uint32_t signal) {
    std::cout << "Compressing 32-bit signal: " << signal << std::endl;
    // Compression logic for 32-bit signal
}

// Overloaded compress function for 64-bit signals
void compressSignal(uint64_t signal) {
    std::cout << "Compressing 64-bit signal: " << signal << std::endl;
    // Compression logic for 64-bit signal
}

int main() {
    uint32_t signal32 = 123456;
    uint64_t signal64 = 9876543210123;

    compressSignal(signal32);  // Calls the 32-bit version
    compressSignal(signal64);  // Calls the 64-bit version

    return 0;
}
```

### 💡 What's happening here?

* Both functions are named `compressSignal`.
* The compiler determines which one to use **based on the argument type**:

  * If you pass a `uint32_t`, it calls the 32-bit version.
  * If you pass a `uint64_t`, it calls the 64-bit version.

---


### **General Project Understanding**

**Q1: What is the CCD tool, and what does it do?**

**A:** CCD stands for *Can Compress Data*. It's a third-party tool developed in Germany in 2010. Its main function is to compress sensor signals like pressure, temperature, and speed into CAN messages and store them in a `.ccd` file. This helps in efficient storage and later retrieval.

---

**Q2: What was your role in the project?**

**A:** I was responsible for **maintenance and enhancement** of the CCD tool. I worked on improving its functionality, adding support for 64-bit signals, fixing legacy issues, and also prepared its complete technical documentation including Developer Guide, Test Plan, and Test Results.

---

**Q3: How does the signal compression process work?**

**A:** First, the CCD tool **groups the signals** by their type — for example, pressure signals are grouped together, temperature signals in another group, and so on. Once grouped, these are **compressed into CAN messages** and written to a `.ccd` file.

---

**Q4: How do you decide which signals to compress and store?**

**A:** The selection is based on whether the signals are required for immediate use. If not, we compress and store them. The tool typically works with bulk signal data, so the grouping and compression logic is applied to whichever signals are available and need archiving.

---

### **Technical Challenges**

**Q5: The tool was initially built for 32-bit data. How did you extend support to 64-bit?**

**A:** We used **function overloading** to extend existing 32-bit functions for 64-bit support. We also modified memory handling logic, especially where `void*` pointers were used to capture data. Since a void pointer behaves differently in 32-bit and 64-bit architectures, we carefully updated pointer arithmetic and ensured memory alignment for 8-byte data.

---

**Q6: What challenges did you face while dealing with 64-bit data handling?**

**A:** The key challenge was with `void*` pointers — earlier, they were capturing 4 bytes, but with 64-bit data, we needed to safely capture 8 bytes. This required updating the logic so that the memory operations were compatible with 64-bit data types and did not lead to data corruption or crashes.

---

**Q7: You mentioned compression logic—were there any precision issues?**

**A:** Yes, one of the compression functions was using `float`, which was causing **automatic rounding of values**, resulting in precision loss. Since we needed higher accuracy, we updated that logic to use `double` instead. Although some minor rounding still exists due to legacy behavior, we validated it with the client and they approved it.

---

### **Documentation & Testing**

**Q8: What is included in your Developer Guide?**

**A:** The Developer Guide explains **each function’s purpose**, how it works, its parameters, and return values. It’s designed to help new developers understand the codebase easily and speed up maintenance or enhancements.

---

**Q9: Can you explain your Test Plan structure?**

**A:** The Test Plan is structured as a table where each row describes:

* The action/step to be performed
* The expected result

For example:

* **Step:** Press Space Key
* **Expected Result:** Screen should open

This makes it easy to track whether the feature behaves as expected.

---

**Q10: What’s in the Test Results?**

**A:** Once the tests are executed, the tester logs the **actual result** in the Test Results file. This helps verify whether the feature passed or failed and also helps identify bugs if any step doesn’t produce the expected result.

---

### **Design and Maintenance**

**Q11: How do you ensure backward compatibility while enhancing the tool?**

**A:** We maintained backward compatibility by **overloading functions** rather than replacing them. So, the 32-bit version continues to work as-is, and the new 64-bit logic is handled separately, ensuring older integrations remain unaffected.

---

**Q12: Did you refactor any part of the code?**

**A:** Yes, while extending support for 64-bit and improving the compression logic, we had to refactor portions of the code to improve readability, maintainability, and type safety — especially around pointer operations and data casting.

---

### **Client Communication**

**Q13: How did you validate the final output with the client?**

**A:** After implementing the changes, we conducted thorough testing. We shared the test results and compression accuracy reports with the client. For the float-to-double change, we discussed the slight rounding issue, and they confirmed that the behavior was acceptable for their use case.

---

**Q14: Were there any performance improvements?**

**A:** Yes, by grouping the signals before compression and optimizing the memory alignment logic, we achieved **faster compression speed and reduced file size**, especially with large data sets.

---

### **High-Level & Behavioral**

**Q15: What did you learn from this project?**

**A:** I learned how to work with legacy systems, understand deep pointer-level memory handling, and how to balance enhancement with backward compatibility. It also improved my technical writing skills through documentation and my testing/debugging skills during validation.

---

**Q16: How would you explain this project to a non-technical person?**

**A:** Think of CCD like a ZIP tool for sensor data. Instead of saving every sensor reading one by one, we group and compress them, then store the result in one file. It saves space and helps us pull out the data later when we need it.

---


