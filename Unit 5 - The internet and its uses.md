# Unit 5 — The Internet and Its Uses 互联网及其应用

> **考纲**：Cambridge IGCSE Computer Science 0478 / 0984 (2026–2028) — Unit 5 The internet and its uses
> **试卷**：Paper 1 Computer Systems — **75 分 / 1 小时 45 分钟 / 不允许使用计算器**
> **本单元特点**：**每套卷必考，通常占 8–24 分**。题型高度固定——**填词题（gap-fill）、配对表、带标注的图**。这是**最容易靠背标准答案拿满分**的单元，但也是**方向性错误最多**的单元（证书谁发给谁、请求谁发给谁）。

---

## 📋 考纲对照清单

| # | 考纲条目 | 掌握 |
|---|---------|------|
| 5.1.1 | Differences between the internet and the World Wide Web | ☐ |
| 5.1.2 | Meaning of uniform resource locator (URL) | ☐ |
| 5.1.3 | Purpose and operation of http and https | ☐ |
| 5.1.4 | Purpose and function of a web browser | ☐ |
| 5.1.5 | How web pages are located, retrieved and displayed | ☐ |
| 5.1.6 | Types of cookie | ☐ |
| 5.2.1 | How digital currencies are used | ☐ |
| 5.2.2 | The process of blockchaining and how it is used to track digital currency transactions | ☐ |
| 5.3.1 | Cyber security threats: brute force attacks, data interception, DDoS, hacking, malware, phishing, pharming, social engineering | ☐ |
| 5.3.2 | Ways of preventing or mitigating the risks of cyber security threats | ☐ |

---

# 第一部分：互联网与万维网 (5.1)

## 5.1.1 互联网 vs 万维网（每次考试必考的概念区分）

**English（背这句）**
> **The internet is the infrastructure** — a worldwide collection of interconnected networks and devices.
> **The world wide web is a collection of web pages** (multimedia web pages and other information on websites).

**对比表（背下来，直接应付 8 分连线题）**：

| **Internet** | **World Wide Web (WWW)** |
|--------------|--------------------------|
| Users can **send and receive emails** | A **collection of multimedia web pages** and other information on websites |
| Allows **online chatting** (via text, audio and video) | **Web pages are written using hypertext mark-up language (HTML)**; HTTP/HTTPS are the **protocols** used to transfer them |
| Makes use of **transmission protocols (TCP)** and **internet protocols (IPs)** | **Uniform resource locators (URLs)** are used to specify the location of web pages |
| A worldwide collection of **interconnected networks and devices**（物理基础设施） | Web resources are **accessed by web browsers**; WWW uses the internet to access information from web servers |

⚠️⚠️ **最重要的失分点**（Examiner Report 反复点名）：
> ❌ "The world wide web is **the infrastructure** that provides access to websites."
> ❌ 同时说"它既是基础设施又是网页"——**自相矛盾，不得分**。
> ✅ **Internet = 基础设施 (infrastructure)；WWW = 网页的集合 (collection of web pages)**

---

## 5.1.2 URL 统一资源定位符

**English（背这句）**
> A **URL (uniform resource locator)** is a **text-based address for a website/web page**.
> Format: `protocol://website address/path/filename`

```
https://www.hoddereducation.co.uk/cambridge-igcse-computerscience
└─┬──┘ └─┬─┘└────────┬────────┘└─┬─┘ └────────────┬────────────┘
protocol  |      domain name      |          web page/file name
       domain host          domain type
        (www)           (.com/.org/.gov)  +  country code (.uk/.de/.cy)
```

🔧 **答题模板：Identify the parts of a URL** [2-3]

**⚠️ 只有三个"部分"**（Memorise：**Protocol + Domain name + File name**）：

| 部分 | 例子 | 说明 |
|------|------|------|
| **Protocol** 协议 | `https` | http 或 https |
| **Domain name** 域名 | `www.frage-eins-beispiel.org.de` | 含 domain host (www)、domain name、domain type (.org)、country code (.de) |
| **File name** 文件名 | `example-page` | 也叫 **web page name** 或 **path** |

⚠️ **致命失分点**：**file name、web page name、path 是同一个部分**——不能当成两个不同的部分来凑分！Examiner Report 原话：
> "Some candidates gave **multiple names for the same part, for example the file name and the path as two separate parts**."

🔧 **精确定位模板**（题目给一个 URL，问各个部分）：
> 例：`https://www.frage-eins-beispiel.org.de/example-page`
> - (a) domain name → `www.frage-eins-beispiel.org.de`
> - (b) domain type → `.org`
> - (c) file name → `example-page`
> - (d) protocol → `https`

---

## 5.1.3 http 与 https

**English（背这句）**
> **Hypertext transfer protocol (http)** is a **set of rules that must be obeyed when transferring files across the internet**. If some form of security is employed, it becomes **https (s = secure)** and you may also see a **green padlock** in the browser address window.

🔧 **答题模板：Explain how HTTPS makes the transmission of data secure** [4]
> - **Uses SSL/TLS**
> - **Encrypts data** … which **stops the data being understood if intercepted**
> - … using **asymmetric encryption**
> - … data is encrypted using the **web server's public key**
> - … data can only be **decrypted by the web server's private key**
> - **Uses digital certificates**

### SSL/TLS 建立安全连接的全过程（最高频 4-6 分题）

**English（背这句）**

```
① Web browser 向 web server 请求 → 要求它证明身份
   (asks the web server to identify itself)
              ↓
② Web server 发回它的 digital certificate
   (sends back its digital certificate)
              ↓
③ Web browser 验证这个证书是否可信
   (authenticates/validates the digital certificate)
              ↓
④ 如果证书有效 → 开始加密传输；如果无效 → 连接不安全/取消
              ↓
⑤ 数据用【公钥】加密（web browser 用 web server 的 public key 加密）
              ↓
⑥ Web server 用【私钥】解密（private key 只有服务器有）
```

🔧 **满分填空答案（背这一段）**：
> The **web browser** asks the **web server** to identify itself. The **web server** sends back its **digital certificate**. The **web browser** authenticates the digital certificate. If it is authentic, **encrypted** data transmission begins.

⚠️⚠️ **方向性铁律（考试最常见的错误）**：
| 动作 | 谁 → 谁 |
|------|---------|
| **发证书** | **Web server → Web browser** ✅ |
| ❌ 错 | ~~Web browser 把证书发给 web server~~ |
| **用公钥加密** | **Web browser** 用服务器的公钥加密 |
| **用私钥解密** | **Web server** 用自己的私钥解密 |

❌ **不给分的答案**："Checking the certificate/web server is safe" —— 太笼统。
❌ 只说 "two different keys are used" —— 不够，必须说 **public key 加密 / private key 解密**。

---

## 5.1.4 网页浏览器 Web Browser

**English（背这句）**
> Web browsers (often simply referred to as "browsers") are **software that allow users to access and display web pages or play multimedia from websites**. The browser **interprets hypertext mark-up language (HTML)** sent from the websites.

**浏览器的功能（背这张表，题目会先给你 1-2 个，让你再给 3 个）**：

| 功能 | English |
|------|---------|
| Address bar | Provides an address bar for a user to enter a URL |
| **Bookmarks** | Storing **bookmarks/favourites** |
| **History** | Recording **user history** |
| **Multiple tabs** | Allowing use of **multiple tabs** |
| **Cookies** | Storing cookies |
| **Navigation tools** | Providing navigation tools (forwards/backwards, hyperlinks) |
| **Home page** | Can set a **home page** |
| **Rendering** | Displays a web page by **rendering/interpreting HTML** |
| Cache | Data stored as a **cache** |
| JavaScript | Make use of **JavaScript** |
| Hyperlinks | Using **hyperlinks** to navigate between websites |

🔧 **答题模板：Give three other functions of a web browser** [3]
> 直接从上表挑题目**没给过**的 3 个。⚠️ 题目已经给你的（如 address bar、cookies）**不能再写**。

🔧 **答题模板：Describe the main purpose of a web browser** [2]
> **Software/application that allows users to view/access web pages by rendering HTML.**

---

## 5.1.5 网页的定位、检索与显示（年年必考，5-6 分）

**English（背这句）**
> To retrieve pages from a website, a browser needs to know the **IP address**. A **domain name server (DNS)** is used to find the IP address from the domain name in the URL.

**完整流程（必须按顺序写，这是 5-6 分大题的骨架）**：

```
① 用户在地址栏输入 URL
       ↓
② Web browser 把 URL 中的 domain name 发给 DNS
   (sends the domain name from the URL to the DNS)
       ↓
③ DNS 在数据库中查找匹配的 IP address
   —— 如果找不到，就把请求转发给下一台 DNS（直到找到）
       ↓
④ DNS 把 IP address 返回给 web browser
       ↓
⑤ Web browser 向 web server 发送 request，请求那个网页
       ↓
⑥ Web server 把网页数据（HTML files）发回 web browser
       ↓
⑦ Web browser 渲染 HTML，显示网页
```

🔧 **满分填空答案（背这一段）**：
> The user types the URL into the address bar. The web browser sends the **domain name** from the URL to the **domain name server (DNS)**. This searches for the matching **IP address** and sends this back to the **web browser**. The web browser sends a **request** to the web server for the web page. The web server then sends the data for the web page back to the web browser. The web browser renders the **hypertext markup language (HTML)** to display the web page.

🔧 **答题模板：Describe the role of the DNS** [2]
> - **Storing a database of URLs and matching IP addresses**
> - **Searching its database for the matching IP address**
> - **Sending the URL to another DNS if the URL cannot be found**
> - **Returning the IP address to the web browser**

⚠️⚠️ **方向性铁律（Examiner Report 两次点名）**：
> ❌ **"The request for the web page is sent from the DNS to the web server."** —— **错！**
> ✅ **请求是由 web browser 发给 web server 的**。DNS 只负责"域名 → IP 地址"的翻译，它不参与请求网页。

**相关术语速查**：

| 术语 | English |
|------|---------|
| **IP address** | A **numerical address used to locate the web server** |
| **DNS** | A system that **stores URLs/domain names and their matching IP addresses**, and provides the matching IP address for a webpage to the web browser |
| **HTML** | The language that is often used to **write/author web pages** |
| **Web browser** | A piece of software that is used to **display web pages** |
| **SSL/TLS/HTTPS** | A **secure protocol** that can be used to transmit data sent to and from a web server |
| **Router** | The device that **automatically assigns an IP address** to a computer each time it connects to the network (via DHCP) |

---

## 5.1.6 Cookie（高频，考过 7 分填词）

**English（背这句）**
> Cookies are **small text files** that are stored by a **web browser**. They are sent by a **web server to the browser** on a user's computer. A cookie behaves like a **small look-up table** which allows the cookie to **track data about the user's internet activity**. Every time the user re-visits a website, it checks if it has set cookies on the browser before.

### 两种 Cookie 对比（必考）

| | **Session cookie** 会话 cookie | **Persistent cookie** 持久 cookie |
|---|---|---|
| **存储位置** | Stored **temporarily on the user's computer**（存在 **RAM**） | Stored on the user's **HDD/SSD**（**secondary storage**） |
| **生命周期** | **Deleted when the web browser is closed** / website session ends | **Permanent** — until **expiry date** reached or **user deletes** them |
| **是否收集用户信息** | **Don't collect any information** about the user and **don't identify who they are** | **Remember user's log in details**, track browsing habits |
| **典型用途** | Making online purchases; **virtual shopping baskets**; single website session | **Remember passwords and email addresses**; recognise users each visit; **target advertising** |

🔧 **满分填空答案（背这一段，考过 7 分）**：
> Cookies are small text files that are stored by a **web browser**. **Session** cookies are **temporary** text files that are deleted when the **web browser** is closed. **Persistent** cookies are **permanent** text files that are stored on a user's secondary storage device until they are manually deleted or they **expire**.

🔧 **答题模板：State one similarity between session and persistent cookies** [1]
> - They are both **small text files**
> - They both **store data about the user**
> - They are both **stored/managed by the web browser**
> - They are both **downloaded on to a user's computer**

🔧 **答题模板：Explain one difference between session and persistent cookies** [2]
> **结构 = 1 分说 session + 1 分说匹配的 persistent**（必须**两边都写**）
> - Session cookies are **deleted when the web browser is closed** … whereas persistent cookies are **deleted by the user / expire after a certain time**
> - Session cookies are **only stored in RAM** … whereas persistent cookies are **stored in the secondary storage**

🔧 **答题模板：Give three uses of cookies** [3]
> - User preferences (e.g. language)
> - Login details
> - Payment details
> - User's personal details (e.g. address)
> - Contents of a shopping cart
> - Targeted advertising

⚠️⚠️ **失分点（教材原文警告）**：
> ❌ "Session cookies are **temporary** whereas persistent cookies are **permanent**" —— **不算描述差异！**
> ✅ 必须**解释** temporary 和 permanent 是什么意思（deleted at the end of a website session / stored until deleted or expiry date reached）。

---

# 第二部分：数字货币与区块链 (5.2)

## 5.2.1 数字货币 Digital Currency

**English（背这句）**
> Digital currency **exists purely in a digital format** and has **no physical form**, unlike fiat currency (for example, £, $, €, ¥). It relies on a **central banking system (centralisation)**; however, this makes it **difficult to maintain confidentiality and security**.

**Cryptocurrency（加密货币）** 是数字货币的一种，它解决了安全和保密问题：
> Unlike other types of digital currency, cryptocurrency has **no state control** and transactions are **publicly available and can be fully tracked**. Cryptocurrency uses **cryptography** to track transactions.

🔧 **答题模板：Identify features of digital currency** [2]
> - Only exists **electronically**
> - Can be a **decentralised** system
> - Can be a **centralised** system
> - Usually **encrypted**

🔧 **答题模板：Describe the difference between digital currency and cryptocurrency** [3]
> **格式：相似点 + 差异 + 为什么有差异**（缺一不可）
> - **Similarity**: Both types of currency are in a **digital format** and have **no physical form**, unlike traditional money
> - **Difference**: Digital currency **relies on a central banking system** to make a transaction, whereas cryptocurrency has **no state control** and **no need for a central banking system**
> - **Why it matters**: Due to centralisation, digital currencies have **security and confidentiality issues**; cryptocurrency transactions are **all publicly available to all members on the network** — all transactions can therefore be **tracked using blockchaining**, making all transactions transparent and removing risks such as hacking

⚠️ **教材警告**：❌ 说 "digital currency is centralised whereas cryptocurrency is not" —— **只给对立面，不给解释，0 分**。

---

## 5.2.2 区块链 Blockchaining（重点，也是历年最弱题）

**English（背这句）**
> **Blockchain** is a **decentralised database**; when a new transaction takes place, **all networked computers in the system get a copy of the transaction**, removing security risks such as hacking.

**区块结构（必背）**：
> When a new transaction takes place, a **new block is created**. The new block contains **data**, a **new hash value** (a unique value generated by an algorithm) and a **previous hash value** pointing to the preceding block. The hash value is unique to each block and includes a **timestamp**, which identifies when the creation of the block took place. In a blockchain the **first block is called the genesis block**.

```
┌──────────┐   ┌──────────┐   ┌──────────┐   ┌──────────┐
│ Block 1  │   │ Block 2  │   │ Block 3  │   │ Block 4  │
│ hash:A4BF│◄──│ hash:6AB1│◄──│ hash:34EE│◄──│ hash:FF12│
│ prev:0000│   │ prev:A4BF│   │ prev:6AB1│   │ prev:34EE│
└──────────┘   └──────────┘   └──────────┘   └──────────┘
   genesis        ← 每个块的 prev hash 指向前一个块的 hash →
```

**防篡改机制（考点）**：
> If a block has been accessed illegally (for example, by a hacker), the **hash value will change** — this means the **link to all the following blocks is now broken**. A **proof-of-work** is used to prevent high-speed number crunching from altering all of the block hash values by a cybercriminal; the proof-of-work **takes ten minutes to complete**, thus preventing cyberattacks. Cryptocurrency is "policed" by **miners** — special network users who get a **commission for each new block created**.

🔧 **答题模板：Describe what happens if block 3 was hacked** [2]
> The **hash value of block 3 would change**. This means the **previous hash value stored in block 4 would no longer match**, so the **link between block 3 and all following blocks is broken** — the tampering is **immediately detectable by all networked computers**.

🔧 **答题模板：Draw and annotate a diagram to show how a payment is made using digital currency and blockchain** [4]

⚠️⚠️ **这是 2024 Nov 最惨的一道题**（Examiner Report: "Very few candidates were able to draw a representation"）。**得分点（任选 4 个）**：
> - **Digital ledger is used**
> - **Device encrypting data**
> - **Device sending data to digital ledger**
> - **Payment being recorded on digital ledger**
> - … including details such as **digital signature / time / date stamp**
> - **Transaction is stored in a block** … **in multiples**
> - **Each block has a block hash / unique identifier**
> - When the block is executed or full … **it is applied to every device that has the blockchain** / block is added to blockchain on each device

💡 **画图建议**：画一个"设备 → 加密 → 区块（含 hash + timestamp）→ 复制到网络上所有设备"的流程图，标注上面这些词，就能拿满。

**区块链的其他用途（考点）**：smart contracts（智能合约）；in research (development of new drugs)；in politics；in many areas of education。

---

# 第三部分：网络安全 Cyber Security (5.3)

## 5.3.1 网络威胁（八大威胁，必背）

**English（背这句）**
> **Cyber security** refers to **systems put in place to defend computers (or electronic devices), web servers, mobile phones and networks (and their associated data) from an attack by a cybercriminal**.

### 1. Brute force attack 暴力破解

**English**
> A brute force attack is a method where **all combinations of letters, numbers and other symbols are tried to generate passwords**. The method relies on the **high speed of computer processing**; therefore **longer, more complex passwords make the task much harder**.
> Criminals also: check if the password is in a **list of commonly used passwords**; if not, check a **word list** (a text file containing a collection of words used in passwords by certain groups).

🔧 **答题模板：Describe how the hacker would perform a brute-force attack** [2]
> - **Try to find out/guess a password**
> - … **by repeatedly entering different combinations/passwords**
> - … could use **software to do it automatically**

### 2. Data interception 数据拦截

**English**
> Data interception is the **stealing of data by tapping into a network**. This can be done by **packet sniffers**, which **examine all data packets on a network and read the data being moved across the network**.
> **War driving** (also known as access point mapping) is a method that **intercepts Wi-Fi signals**; it requires a laptop/smartphone/tablet, an **antenna**, a **GPS device**, and software to gather the data.

### 3. DDoS 分布式拒绝服务攻击

**English**
> A **distributed denial-of-service (DDoS) attack** is an attempt to **prevent anyone accessing part of a network**, for example a specific web server. The system uses a **network of computers** to carry out an attack. It is slightly different from a **denial-of-service (DoS)** attack, which only uses a **single computer**; DoS is therefore **much easier to identify and remove the risk**.
> DDoS can also attack an individual's computer by preventing them accessing their emails, certain websites or online services (e.g. by sending masses of **spam emails** which overload a server).

🔧 **答题模板：Draw and annotate a diagram to show the process of a DDoS attack** [5]
> - A **perpetrator/third party sending malware** / user downloads malware
> - **Each computer is turned into a bot** …
> - … to create a **botnet**
> - **Third party initiates the attack**
> - **All the bots send a request at once to a web server**
> - … **crashing the webserver**

### 4. Hacking 黑客入侵

**English**
> **Hacking is gaining illegal access to a computer system without the user's permission.** It can lead to **identity theft**, gaining personal information, or the **loss/corruption of key data**.
> ⚠️ **Hacking is NOT prevented by using measures such as encryption**, but can be mitigated by using a **firewall, usernames and frequency-changed strong passwords**; anti-hacking software also exists. Some hacking is referred to as **ethical hacking**, where companies employ staff to try to hack into their own systems to check how strong their security measures are.

⚠️ **MS 判分警告**：`stealing/changing data without permission` **不给分**，必须提到 **gaining access to the device/account**。

### 5. Malware 恶意软件（六个类型必背）

**English（背这张表）**

| 类型 | English 定义 |
|------|-------------|
| **Virus** | Programs (or program code) that can **replicate or copy themselves** with the intention of **deleting or corrupting files**, or causing the computer to malfunction. They **need an active host program** on the target computer or an OS that has already been infected. Often part of an **email attachment** and require the user to **take some action** |
| **Worm** | Types of **stand-alone viruses** that can replicate themselves with the intention of **spreading to other computers**. They often use **networks** to search out computers with weak security. Worms can spread throughout a network **without any action by an end user** — potentially **more dangerous than viruses** |
| **Trojan horse** | **Malicious programs often disguised as legitimate software**. They **replace all or part of the legitimate software** with the intent of carrying out harm. A Trojan horse **needs to be executed by an end user**; often arrive as an email attachment or downloaded from an infected website |
| **Spyware** | Software that **gathers information by monitoring all the activity on a user's computer** and **captures personal data**. The gathered information is sent back to the person who sent the software. Sometimes monitors key presses — then referred to as **key logging software** |
| **Adware** | Software that **floods a user's computer with unwanted advertising**, usually in the form of **pop-ups**. Can **redirect the browser to a fake website**. Not necessarily harmful, but can highlight weaknesses in network security and be **difficult to remove since anti-malware doesn't see them as harmful** |
| **Ransomware** | Programs that **encrypt the data on a user's computer**, so a **decryption key** is needed. The key is sent to the user **once they pay a sum of money (a ransom)**. Often sent via a **Trojan horse** or by **social engineering** |

⚠️ **判分警告**：**hacking 不是 malware**！Examiner Report: "Some candidates gave inaccurate examples that **may involve the use of malware, but were not examples of malware, for example hacking**."

### 6. Phishing 网络钓鱼

**English**
> **Phishing is the sending out of legitimate-looking emails to users**; they may contain links to or attachments to **fake websites**. They **require the user to take some action** to initiate the attack, for example by **clicking on the link**. Once a link is established, the user's browser is taken to a **fake website where personal information can be stolen**.
> Another type is **spear phishing** — a cybercriminal **targets specific individuals/companies** to get access to financial data or for **industrial espionage**. Normal phishing isn't usually specific in who it targets.

🔧 **答题模板：Describe the process of phishing** [4]
> - A **legitimate looking email is sent to the user**
> - **The user clicks a link in the email / replies to the email**
> - **The user is directed to a fake website**
> - **The user enters their personal data** …
> - … **that is stolen/used by a third party** (for malicious purposes)

🔧 **答题模板：Give two ways an employee could identify phishing** [2]
> - **Check the email address** that the email has been sent from
> - **Check the tone/spelling** of the email
> - **Check the URL** that is attached to the link

**防范措施**：awareness training；不点不明链接；用浏览器自带 anti-phishing 工具；保持浏览器和防火墙更新；点信息图标查看真实发件地址。

### 7. Pharming 域名欺骗（与 phishing 的关键区别）

**English**
> **Pharming is malicious code installed on a user's computer or web server without their knowledge.** The user **doesn't need to take any action** to initiate the pharming attack; it is **initiated automatically by the stored code**. The creator of the malicious code can gain information by **sending the user's browser to a fake website without their knowledge**.
> Pharming redirects the user's browser to a fake/malicious website often by using **DNS cache poisoning** (cache poisoning **changes the genuine IP address stored in a DNS server's/resolver's cache for a domain name to a fake IP address** that takes the browser to the fake website).

⚠️⚠️ **Phishing vs Pharming 的核心区别（必考）**：
| | **Phishing** | **Pharming** |
|---|---|---|
| **需要用户动作吗** | ✅ **需要**（点击链接/附件） | ❌ **不需要**，自动触发 |
| **手段** | 假冒邮件 | 用户电脑/服务器上的恶意代码 |
| **机制** | 骗用户自己点 | **DNS cache poisoning** |

❌ **Examiner Report 点名**："Some candidates gave a **confused description that referred to aspects from both phishing and pharming**. For example, they referred to **malware being downloaded on the user's computer**." —— 描述 phishing 时**不要**扯 malware 下载。

### 8. Social engineering 社会工程（5 种类型 + 3 种情绪）

**English**
> **Social engineering** occurs when a cybercriminal **creates a social situation that can lead to a potential victim "dropping their guard"**. It involves the **manipulation of people into breaking their normal security procedures**. **No hacking is required**, since the user **willingly gives** the cybercriminal the necessary access or information.

**五种类型**：

| 类型 | English |
|------|---------|
| **Instant messaging** | Malicious links embedded into instant messages (e.g. an important software upgrade) — relies on **curiosity** |
| **Scareware** | A **pop-up message** claiming the user's computer is infected; user is told to **download the fake antivirus immediately** — relies on **fear** |
| **Emails / phishing scams** | The user is tricked by the **apparent genuineness of an email** and opens a link → redirected to a fake website — relies on **trust** |
| **Baiting** | The cybercriminal **leaves a malware-infected memory stick** somewhere it can be found; the finder plugs it in — relies on **curiosity** |
| **Phone calls** | A so-called **IT professional calls** claiming the device has been compromised; user is advised to **download special software** allowing takeover — relies on **fear** |

**被利用的三种情绪**：**Fear**（恐惧）、**Curiosity**（好奇）、**Empathy and trust**（同理心与信任）。

🔧 **答题模板：Describe what is meant by social engineering. Include an example.** [3]
> **2 分**：Involves **manipulating/deceiving people** … **with the aim of obtaining confidential/personal/valuable data**
> **1 分**：一个例子 —— **Phishing** / **Baiting** / **Shoulder surfing**（任选一个并说明）

---

## 5.3.2 防护措施（保持数据安全）

### 1. 访问级别 Access Levels（考过 5 分）

🔧 **答题模板：Explain how access levels are used to help prevent a cyber security attack being successful** [5]
> - They **limit/restrict a user's access to data** …
> - … by giving users **different permissions** — users can be given **read only / read-write / no access / execute / administrator** permission
> - … so an attacker will **only have access to the data that the user has access to**
> - … to **stop a malicious person/attacker deleting/editing/corrupting data**
> - **Prevents a user/attacker from installing malware** (as they don't have administrator permissions)
> - **Prevents user/attacker from viewing more confidential/important data**

⚠️⚠️ **判分警告（MS 明确列出）**：
> ❌ "different access levels" → **太笼统 (TV)**
> ❌ "low-level or high-level access" → **太笼统 (TV)**
> ✅ **必须说出具体的权限名**：read-only / read-write / no access / execute / administrator

### 2. 反恶意软件 Anti-malware

**English**
> The most common types of anti-malware are **antivirus** and **anti-spyware**. Anti-spyware software detects and removes spyware using two methods:
> 1. **Rules** — looks for certain features associated with spyware
> 2. **File structures** — looks for file structures common to spyware software
>
> Features: **Detects and removes spyware** from user's HDD/SSD; **prevents the downloading of spyware**; **encrypts files**; **encrypts keyboard strokes**; **blocks access to webcam and microphone** if suspicious activity detected; **scans for signs that personal information is being stolen** and warns the user.

🔧 **答题模板：Give three examples of malware that anti-malware software can detect** [3]
> Virus / Worm / Trojan horse / Spyware (keylogger) / Ransomware / Adware

### 3. 防火墙 Firewall（考过 5 分）

🔧 **答题模板：Explain how the firewall operates to help protect the network** [5]
> - **Criteria can be set** (for traffic) …
> - … such as a **blacklist/whitelist** (of IP addresses)
> - It will **examine traffic coming into the network**
> - It will **check that the traffic meets the set criteria** …
> - … and will **reject it if it does not meet criteria**
> - **Certain ports used by hackers can be blocked/closed**

⚠️⚠️ **Examiner Report 原文**："Many candidates **repeated and expanded on parts of the question**, simply stating that the firewall blocked hackers and various examples of malware. Candidates need to have a greater understanding of the **operation** of a firewall."
> ✅ 必须写**机制**（审查流量、应用规则、接受/拒绝、封锁端口），不能写"它挡住黑客"。

### 4. 代理服务器 Proxy Server（考过 3 分 DDoS 防护）

🔧 **答题模板：Describe how the proxy server can stop a DDoS attack reaching a web server** [3]
> - It **examines each request/incoming transmission**
> - It can **slow down the rate at which / limit the number of requests** sent to the server
> - It can use **caching** …
> - … **to respond to the request itself** (rather than forwarding it to the server)
> - It can **stop any requests from a certain IP**
> - It can **hide the public IP address**

**代理服务器的其他功能**：Can act as a firewall；examine incoming data；have set rules/criteria；have a blacklist/whitelist；block traffic that doesn't meet criteria；close certain ports。可以防：**DDoS/DoS、hacking、malware、brute-force attack**。

⚠️ **判分警告**：❌ **phishing 是代理服务器防不住的**（它是针对用户的社会工程攻击）——Examiner Report: "The most common incorrect response given was phishing."

### 5. 加密 Encryption

**English**
> **Symmetric encryption** — the **encryption key is shared with any device receiving the encrypted data**.
> **Asymmetric encryption** — uses a **public key and a private key**.

### 6. 身份验证 Authentication 与生物识别 Biometrics

**English**
> **Authentication** refers to the **ability of a user to prove who they are**. There are **three factors**:
> - **Something you know** (e.g. a password or PIN)
> - **Something you have** (e.g. a mobile phone or tablet)
> - **Something unique to the user** (e.g. biometrics)

**密码要求**：be **changed regularly**；**not be easy to guess**（生日是很弱的密码）；be **strong** — **at least eight characters including numbers, lower case letters, upper case letters and other keyboard symbols**（例：`T7%%asR3£Sc` 很强但 `pas5word` 很弱）。

**四种生物识别对比**：

| 方式 | Benefits | Drawbacks |
|------|----------|-----------|
| **Fingerprint scans** 指纹 | One of the **most developed** biometric techniques; **very easy to use**; **relatively small storage requirements** | **Very intrusive** for some (related to criminal identification); **can make mistakes if the skin is dirty or damaged** (e.g. cuts) |
| **Retina scans** 视网膜 | **Very high accuracy**; **no known way to replicate a person's retina** | **Very intrusive**; can be **relatively slow** to verify using stored scans; **very expensive to install and set up** |
| **Face recognition** 人脸 | **Non-intrusive**; **relatively inexpensive** | Can be affected by **changes in lighting, the person's hair, change in age, and if the person is wearing glasses** |
| **Voice recognition** 声纹 | **Non-intrusive**; verification takes **less than five seconds**; **relatively inexpensive** | A person's **voice can be recorded** and used for unauthorised access; **low accuracy**; **illness (such as a cold) can change a person's voice** |

🔧 **答题模板：Give three cyber security solutions to prevent a brute-force attack** [3]
> - **Strong passwords** — long, with a combination of letters, numbers and symbols
> - **Two-step verification / two-factor authentication**
> - **Biometric password** (e.g. fingerprint)
> - **Limiting the number of login attempts**

🔧 **答题模板：Identify a solution + explain how it prevents hackers** [6]

| 方案 | 怎么防止 |
|------|---------|
| **Strong/complex password** | Requires a mixture of letters, numbers and symbols → **makes it very difficult for the hacker to guess** |
| **Limiting number of attempts** | Cannot keep repeatedly guessing → **stops a brute-force attack being successful** |
| **Biometric device** | Requires the hacker to have biometric data → **very difficult to fake biometric data** |
| **Two-step verification** | Requires the hacker to have additional data → **the data is sent to the user's registered device that the hacker would also need** |
| **Firewall** | **Examines incoming data/traffic** → **can block any data that does not meet set criteria** |
| **Anti-spyware** | **Detects/removes any spyware** → hacker cannot use spyware to get data to discover passwords |

---

# 📝 考试怎么考（Exam Focus）

## 📊 真题实证（考频与分数权重）

> ⭐ **最重要的结论**：**Unit 4 + Unit 5 合起来每套卷必考，占 Paper 1 的 12–30 分（约 16–29%）。**
> Unit 5 单独看分值中等，但**题型是全卷最固定的**（填词 + 配对 + 带标注的图），
> 是**"背标准答案就能拿满分"**的单元 —— 前提是**方向不能搞反**。

### 考频总表

| 考点 | 考频 | 典型分值 | 形式 |
|------|------|---------|------|
| **Internet vs WWW** | **每套必考** | 2–8 | 配对表 / 连线题 |
| **网页检索流程（DNS → IP）** | **每套必考** | 5–6 | **填词**（必背文本） |
| **SSL / HTTPS 安全连接** | 高频 | 4–6 | **填词 + 带标注的图** |
| **Cookie（session vs persistent）** | 高频 | 4–7 | **填词 + 差异说明** |
| **URL 组成部分** | 常考 | 2–3 | Identify / 定位 |
| **Web browser 功能** | 常考 | 2–3 | "Give three **other** functions" |
| **数字货币 vs 加密货币** | 常考 | 2–3 | Describe the difference |
| **区块链 blockchaining** | 常考 | 4 | **Draw and annotate a diagram** |
| **网络威胁（八大）** | **每套必考** | 2–6 | 定义 / 识别 / 配对 |
| **防护措施** | **每套必考** | 3–6 | "Explain how X prevents…" |
| **Phishing vs Pharming 区别** | 常考 | 2–3 | Describe / Compare |
| **Social engineering** | 常考 | 2–3 | Describe + example |
| **Biometrics 优缺点** | 常考 | 3–4 | Benefits / drawbacks |

### 🔑 关键判分规则（MS 原文）

| 规则 | 说明 |
|------|------|
| **Internet vs WWW 配对题** | 每条描述要么属于 Internet 要么属于 WWW。⚠️ **自相矛盾（既说是基础设施又说是网页）→ 不得分** |
| **填词题（gap-fill）** | **按空给分**，拼写必须能辨认。背熟三段标准文本即可拿满 |
| **方向性答案** | 证书：**server → browser**；网页请求：**browser → web server**。**反了就 0 分** |
| **"Explain how X prevents..." 题** | **必须写机制**，不能写"它阻止了黑客"。写法：`它做什么` → `所以攻击者无法做什么` |
| **配对/Compare 题** | 必须**两边都写**（A 怎样 + whereas + B 怎样），单写一边最多一半分 |
| **"Give three OTHER functions"** | 题目已经给你的**不能再写**，写了不算 |
| **Identify 题** | 只要**术语名**，不要描述。要求 identify sensor 时写 "it measures light" = **0 分** |

### 三类必背的"标准填词文本"

> **① 网页检索流程**
> "The user types the URL into the address bar. The web browser sends the **domain name** from the URL to the **domain name server (DNS)**. This searches for the matching **IP address** and sends this back to the **web browser**. The web browser sends a **request** to the web server for the web page. The web server then sends the data for the web page back to the web browser. The web browser **renders** the **hypertext markup language (HTML)** to display the web page."

> **② SSL / HTTPS**
> "The **web browser** asks the **web server** to identify itself. The **web server** sends back its **digital certificate**. The **web browser** authenticates the digital certificate. If it is authentic, **encrypted** data transmission begins."

> **③ Cookie**
> "Cookies are **small text files** that are stored by a **web browser**. **Session** cookies are **temporary** text files that are deleted when the **web browser** is closed. **Persistent** cookies are **permanent** text files that are stored on a user's **secondary storage device** until they are manually deleted or they **expire**."

---

## 各题型答题模板

### 模板 1：填词题（gap-fill）—— 每套卷 2-3 道
> 背熟三段标准文本：
> - **网页检索流程**（DNS → IP → browser → request → HTML）
> - **SSL 流程**（browser 请求 → server 发证书 → browser 验证 → 加密）
> - **Cookie 段落**（web browser → session → temporary → persistent → permanent → expire）

### 模板 2：带标注的图（draw and annotate）—— 每套卷 1-2 道
> 四种图必须会画：**网页检索图**、**SSL 握手图**、**DDoS 攻击图**、**区块链支付图**。
> 💡 画图时**每一段都写英文标签**，标签就是得分点。

### 模板 3：配对表 / "哪个是 Internet 哪个是 WWW"
> 背 §5.1.1 那张对比表。

### 模板 4：Describe the role of [X]（DNS / proxy / firewall / browser）[2-5]
> **必须写机制，不能写"它保护网络安全"这种空话。**

### 模板 5：Explain the difference between [A] and [B] [2-4]
> **匹配式写法**：一句说 A 怎样 + 一个 "whereas" + 一句说 B 怎样。**两边都要写**。

### 模板 6：Give three other functions of [browser / IDE / OS] [3]
> 从上表挑题目**没给过的**三个。

### 模板 7：Tick / 单选 / 圈出正确项
> 常考：哪个是 utility software、哪种加密方式、translator 名称、biometrics 的三个描述词（authentication / biometric / input device）。

---

## ⚠️ 高频失分点汇总

| 失分点 | 正确写法 |
|--------|---------|
| WWW 说成 "the infrastructure" | ✅ **Internet = infrastructure；WWW = collection of web pages** |
| **证书由 browser 发给 server** | ✅ **Server → Browser**（反了就是 0 分） |
| **请求网页由 DNS 发给 web server** | ✅ **Web browser → web server**。DNS 只做域名→IP 的翻译 |
| 把 file name 和 path 当成两个 URL 部分 | ✅ **file name = web page name = path，是同一个部分** |
| **说 encryption 能阻止黑客入侵** | ✅ **Encryption 不能阻止入侵**——数据还是被偷了，只是看不懂 |
| Firewall 答案写 "它挡住黑客" | ✅ 必须写**机制**：examine traffic / set criteria / blacklist / reject / block ports |
| Interrupt/malware 举例举成 "keyboard"、"hacking" | ✅ 要举**具体事件**或**真正的 malware 类型** |
| 说 phishing 会下载 malware | ✅ Phishing = 假邮件 → 假网站 → 用户自己填数据。**不要扯 malware 下载** |
| 描述 cookie 差异只说 "temporary vs permanent" | ✅ 必须**解释**这两词的含义（何时删除/存到哪里） |
| 生物识别说 "it's safe" | ✅ 必须给**具体优缺点**（intrusive / expensive / lighting / voice recorded 等） |
| 说 proxy 能防 phishing | ✅ Proxy 防 **DDoS、hacking、malware、brute-force**，**不防 phishing** |

---

## 🧠 一页纸速记

```
【Internet vs WWW】
Internet = infrastructure (TCP/IP, email, chatting, 互联的物理网络)
WWW = collection of web pages (http/https, HTML, URL, web browser)

【URL】protocol://domain name/file name
  三个部分只有: protocol / domain name / file name
  ⚠ file name = web page name = path (同一个)

【http vs https】http 是传输文件的规则; https = secure, 绿锁

【网页检索流程】★ 必背 5-6 分
  输入 URL → browser 把 domain name 发给 DNS
  → DNS 查匹配 IP (找不到就转下一台 DNS)
  → IP 返回 browser → browser 向 web server 发 request
  → server 发回 HTML → browser 渲染显示
  ⚠ 请求是 browser→server, 不是 DNS→server

【SSL/HTTPS 安全连接】★ 必背
  browser 请求 server 证明身份 → server 发 digital certificate
  → browser 验证 → 有效则开始加密
  → 用【public key】加密 (browser 用 server 的公钥)
  → 用【private key】解密 (server 自己)
  ⚠ 证书方向: server → browser

【Web browser 功能】
address bar / bookmarks / history / multiple tabs / cookies /
navigation tools / home page / rendering HTML / cache / JavaScript

【Cookie】
Session: 存 RAM, 关浏览器就删, 不收集用户信息, 购物车/单次会话
Persistent: 存 HDD/SSD, 到过期或手动删除, 记住密码/追踪习惯/定向广告

【数字货币】
纯电子形式, 无实体, 依赖中央银行(centralisation) → 安全保密问题
Cryptocurrency: 无国家控制, 交易公开可追踪, 用 cryptography

【区块链】decentralised database, 每个联网电脑都有副本
  新区块 = data + new hash + previous hash + timestamp
  第一个块 = genesis block
  被篡改 → hash 变 → 后续链接断裂 → 立即被发现
  proof-of-work 需 10 分钟, 防高速暴力篡改
  miners 维护, 每建一个块拿佣金
  其他用途: smart contracts / 研究 / 政治 / 教育

【八大网络威胁】
Brute force — 试遍所有组合; 靠computer高速; 用常见密码表+word list
Data interception — packet sniffer 偷数据; war driving 截Wi-Fi
DDoS — 多台电脑(botnet)同时发请求 → 服务器崩溃 (DoS=单台)
Hacking — 未经许可非法访问; ⚠加密防不住
Malware: virus(需宿主,复制) / worm(独立,走网络) / trojan(伪装合法软件)
         spyware(监控,keylogger) / adware(弹窗广告) / ransomware(加密勒索)
Phishing — 假邮件→假网站→用户自己填数据 (需用户动作)
Pharming — 恶意代码偷偷装, 用户无需动作; 用 DNS cache poisoning
Social engineering — 操纵人; 5种: instant msg / scareware / phishing email
                    / baiting / phone call; 3情绪: fear/curiosity/trust

【防护措施】
Access levels — read-only/read-write/no access/execute/administrator
                ⚠ "different access levels" 太笼统不给分
Anti-malware — antivirus + anti-spyware (rules + file structures)
Firewall — 设criteria(黑/白名单), 审查流量, 不符则拒绝, 封锁端口
Proxy server — 审查请求, 限速, caching, 挡特定IP, 隐藏public IP
               (能防 DDoS/hacking/malware/brute-force, 不防 phishing)
Encryption — symmetric(共享密钥) / asymmetric(public + private)
Authentication — something you know / have / are unique to you
Biometrics — fingerprint / retina / face / voice
             各自的优缺点要能对比
```

---

## 🔗 延伸资源

- 课件：[Unit 5 The internet and its uses 课件目录](../csresource/new/Slides/1%20Computer%20Systems/5%20The%20internet%20and%20its%20uses/)
- 真题：`csresource/.../Past Exam Papers/Questions by Year/` 中各年份 Paper 1
- 在线练习（按考纲章节分类，与本单元一一对应）：
  - [Save My Exams — 5. The internet and its uses](https://www.savemyexams.com/igcse/computer-science/cie/23/topic-questions/)
  - [PapersDaddy — 0478 Topical Paper 1](https://www.papersdaddy.com/cambridge/igcse/computer-science-0478/resources/topical-past-papers/paper-1)（免费下载）
  - [Physics and Maths Tutor — IGCSE Computer Science](https://www.physicsandmathstutor.com/computer-science-revision/igcse-cie/)

---

**上一单元** ← [Unit 4 - Software](Unit%204%20-%20Software.md)
**下一单元** → [Unit 6 - Automated and emerging technologies](Unit%206%20-%20Automated%20and%20emerging%20technologies.md)
