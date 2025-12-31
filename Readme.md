# 🔁 IP ROTATION

**IP ROTATION** is an advanced IP rotation tool designed for ethical hackers, privacy enthusiasts, and cybersecurity learners.  
It works by launching multiple Tor nodes in parallel and routing traffic through a centralized Privoxy proxy server — enabling users to automatically change their public IP address at customizable intervals.

Whether you're conducting anonymous security research or learning how anonymization networks like Tor work, IPHopper provides a lightweight and powerful CLI-based solution — especially built for **Termux** and **Linux-based systems**.

---

## 🎯 Purpose of IP ROTATION

When working in the cybersecurity field or doing web reconnaissance, constantly changing your IP address can help avoid detection, rate-limiting, and geo-restrictions.  
Most users rely on VPNs, but VPNs are centralized services and not always transparent. Tor, on the other hand, offers a decentralized and free solution for anonymity.

**IPHopper** combines:
- Multiple Tor instances (multi-node parallelization)
- A central Privoxy proxy server
- IP rotation automation via control ports

All packaged in a simple tool with beginner-friendly configuration and advanced functionality under the hood.

---

## 🚀 Features

- 🔁 **Auto IP Rotation** using the Tor Network
- 🧠 **Multiple Tor Nodes**: Five nodes running simultaneously
- 🔒 **Privacy-focused**: All traffic routed through a secure proxy
- 🧱 **No Root Required**: Fully works on non-rooted Termux devices
- 📟 **Custom Rotation Timer**: Set your own rotation interval in seconds
- 🧰 **Self-contained Configuration**: Cleans and reinitializes on every run
- 💻 **Termux + Linux Compatible**
- 👨‍💻 **Developed by Ethical Hackers** for Educational Use

---

## ⚙️ How IP ROTATION Works

1. **Five separate Tor nodes** are launched with their own config files and data directories.
2. A **Privoxy proxy** is set up and configured to forward all traffic across the 5 Tor nodes.
3. A control loop sends **SIGNAL NEWNYM** to all control ports every X seconds (your interval).
4. Your current **public IP** is fetched and displayed from `https://api64.ipify.org`.
5. Your **IP changes automatically**, as if you're hopping across networks — hence the name *IPROTATION*.

---

## 💡 Use Cases

- 🔍 Safe and anonymous reconnaissance
- 🌐 Bypassing soft IP rate-limits during testing
- 🛡️ Practicing anonymity techniques
- 📚 Cybersecurity learning labs
- 🔬 Testing how websites respond to changing IPs

---

## 📄 Disclaimer

> ⚠️ **This tool is created strictly for educational and ethical purposes.**
>
> - You **must not** use this tool for illegal activity, unauthorized scanning, or attacking any network you do not own or have permission to test.
> - This tool does **not guarantee full anonymity**, as DNS leaks, misconfigurations, or user mistakes can expose identity.
> - Always test in **safe and legal environments** (e.g., virtual labs, local servers).
> - The developer, **Alok Thakur**, is **not responsible** for any misuse, damage, or legal consequences arising from the use of this tool.
>
> You are solely responsible for your actions.

### Kali/Termux Packege Install Comments

```
sudo apt update
```
### For Termux
```
pkg install git tor privoxy netcat-openbsd curl -y
```
### For Kali
```
sudo apt install git tor privoxy netcat-openbsd curl -y
```
### Clone Linux/termux
```
git clone https://github.com/BidyutRoy2/ip-rotate.git && cd ip-rotate
```
```
sudo chmod +x setup.sh && sudo bash setup.sh
```
### Remove the # the following lines , (SOCKS5) , Change listens Address

- Kali:
```
sudo nano /etc/privoxy/config
```
- Termux
```
nano $PREFIX/etc/privoxy/config
```
<img width="727" height="340" alt="image" src="https://github.com/user-attachments/assets/e36f161a-928b-4c1d-8338-64f9269d3d09" />
<img width="1005" height="499" alt="image" src="https://github.com/user-attachments/assets/897031f4-85bd-4f85-b397-5e260b4f3f30" />
<img width="1045" height="491" alt="image" src="https://github.com/user-attachments/assets/09cae6e1-a826-47d4-8fb5-e8f9beb29903" />
<img width="1049" height="480" alt="image" src="https://github.com/user-attachments/assets/da6c6e61-21d6-4eca-99a9-379aa2b88653" />

## To Save File (CTRL+X+Y)

### Open Kali's Firewall
```
sudo iptables -I INPUT -p tcp --dport 8118 -j ACCEPT
```

### Restart the service
- Kali: `sudo systemctl restart privoxy`
- Termux: `pkill privoxy && privoxy $PREFIX/etc/privoxy/config`

### Start tool command
```
sudo chmod +x iprotate.sh && sudo bash iprotate.sh
```

### Test the Configuration
```
curl --proxy http://127.0.0.1:8118 https://check.torproject.org/api/ip
```
```
sudo systemctl status tor
```

## If the command above gives you a "Could not get lock" error, it means the system still thinks another process is using the database. You can manually remove those lock files

### Kali Linux
```
sudo rm /var/lib/dpkg/lock-frontend
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a
```
```
sudo apt update --fix-missing
sudo apt install -f
```

### Termux
```
rm $PREFIX/var/lib/dpkg/lock-frontend
rm $PREFIX/var/lib/dpkg/lock
dpkg --configure -a
```
```
pkg update
pkg install -f
```






