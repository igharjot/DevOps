# Day 14 – Networking Fundamentals & Hands-on Checks

## OSI Model vs TCP/IP Model

### 🌐 Overview Comparison

    ------------------------------------------------------------------------
    Feature         **OSI Model**            **TCP/IP Model**
    --------------- ------------------------ -------------------------------
    **Full Form**   Open Systems             Transmission Control Protocol /
                  Interconnection          Internet Protocol

    **Developed     ISO (International       DARPA / DoD
    By**            Organization for         
                  Standardization)         

    **Type**        Conceptual reference     Practical protocol suite
                  model                    

    **Layers**      **7 Layers**             **4 Layers**

    **Approach**    Theoretical              Implementation-oriented

    **Usage**       Teaching / design        Real-world networking
                  standard                 
    ------------------------------------------------------------------------


## 🧱 Layer Comparison

    **OSI (7 Layers)**   **TCP/IP (4 Layers)**
    -------------------- -----------------------
    7️⃣ Application       Application
    6️⃣ Presentation      Application
    5️⃣ Session           Application
    4️⃣ Transport         Transport
    3️⃣ Network           Internet
    2️⃣ Data Link         Network Access
    1️⃣ Physical          Network Access

-----------------------------------------------------------------------

### ✅ 2️⃣ Nature

**OSI Model** - Purely conceptual - Protocol-independent

**TCP/IP** - Based on actual protocols - Defines real communication
rules

------------------------------------------------------------------------

### ✅ 3️⃣ Layer Strictness

**OSI** ✔ Clear separation\
✔ Strict boundaries

**TCP/IP** ✔ Flexible\
✔ Less rigid

------------------------------------------------------------------------

### ✅ 4️⃣ Protocol Dependency

**OSI** ❌ Does NOT mandate specific protocols

**TCP/IP** ✔ Built around real protocols: - TCP - IP - UDP - HTTP - DNS
etc.

------------------------------------------------------------------------

### ✅ 5️⃣ Adoption

**OSI** Mostly educational/reference

**TCP/IP** ✔ Internet standard\
✔ Used globally

------------------------------------------------------------------------

## 🚀 Practical Insight

-   **OSI → Explains how networking *should* work**
-   **TCP/IP → Explains how networking *actually* works**

------------------------------------------------------------------------

# 📡 Where Common Protocols Sit in TCP/IP Stack

## **Application Layer**

Handles user-facing network services.

Protocols: - **HTTP / HTTPS** - **DNS** - **FTP** - **SMTP** - **SSH**

------------------------------------------------------------------------

## **Transport Layer**

Responsible for end-to-end communication & ports.

Protocols: - **TCP** → Reliable, connection-oriented - **UDP** → Fast,
connectionless

------------------------------------------------------------------------

## **Internet Layer**

Logical addressing & routing.

Protocols: - **IP (Internet Protocol)** → Packet delivery - **ICMP** →
Errors & diagnostics - **ARP** → IP-to-MAC mapping

------------------------------------------------------------------------

## **Network Access Layer**

Physical transmission of data.

Examples: - Ethernet - Wi‑Fi - MAC addressing - Frames

------------------------------------------------------------------------

---

## Running Networking Commands

<img width="947" height="811" alt="image" src="https://github.com/user-attachments/assets/fbeeab48-adb1-4894-933b-25c50ea5294f" />
 
 ---

<img width="955" height="716" alt="image" src="https://github.com/user-attachments/assets/327bf1d0-b8cc-4914-a579-b97812464de8" />

---

<img width="870" height="678" alt="image" src="https://github.com/user-attachments/assets/2ce17c3f-f7b1-4d1e-8957-a551f6fbe6d9" />

---
