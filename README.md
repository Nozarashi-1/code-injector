## 🚩 Code Injector 

This Python tool intercepts HTTP traffic and **injects custom JavaScript code** into HTML pages in transit.  
It works by modifying HTTP responses on the fly and inserting your payload before they reach the victim’s browser.

---

## ⚠ Disclaimer

    This tool is intended **only for authorized penetration testing and educational purposes**.  

    Injecting code into web traffic **without permission is illegal** and punishable by law.  

    The author is not responsible for any misuse or damage caused.

---

## 📌 Features
    - Intercepts and modifies HTTP traffic
    - Removes `Accept-Encoding` to prevent compression
    - Injects custom JavaScript payloads into HTML pages
    - Adjusts `Content-Length` header automatically to prevent page breakage
    - Works on Python 2

---

## 🛠 Installation

1. Clone the repository:
```bash
git clone https://github.com/Nozarashi-1/code-injector.git
cd code-injector
```
---

## 🚀 Usage
1. Edit the payload
In the script, find:

       injection_code = 'YOUR MALICIOUS JS SCRIPT>'

Replace it with your JavaScript payload, for example:   

    injection_code = '<script>alert("Hacked!")</script>'

2. Enable IP forwarding

        echo 1 > /proc/sys/net/ipv4/ip_forward

3. Set up iptables to redirect HTTP traffic
For traffic forwarding (man-in-the-middle):

       sudo iptables -I FORWARD -j NFQUEUE --queue-num 0

4. Run the script

        sudo python code_injector.py

5. Flush rules after finishing

        sudo iptables --flush   
   
   
    
