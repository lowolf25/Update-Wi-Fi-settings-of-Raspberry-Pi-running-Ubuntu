---

# 🛜 Updating Wi-Fi Settings (Netplan)

This section explains how to configure Wi-Fi on the TurtleBot3 SBC (Raspberry Pi running Ubuntu).
Netplan controls network settings in Ubuntu Server images, so Wi-Fi edits must be made here.

---

## 📂 1. Open the Netplan Configuration File

Run the following command:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```

---

## ✏️ 2. Update the File with Your Wi-Fi Credentials

Replace the existing content with the format below.
Be sure to insert your actual Wi-Fi **SSID** and **password**:

```yaml
network:
  version: 2
  renderer: networkd
  wifis:
    wlan0:
      dhcp4: true
      access-points:
        "YOUR_WIFI_SSID":
          password: "YOUR_WIFI_PASSWORD"
```

### ⚠️ Important Notes

* **YAML is indentation-sensitive** — use **2 spaces** for each level.
* Do **not** use tabs.
* Put the SSID in **quotes** if your Wi-Fi name has spaces.
* Ensure that the filename ends with `.yaml`.

---

## 🔄 3. Apply the New Wi-Fi Settings

Run:

```bash
sudo netplan apply
```

If Netplan reports an error, the issue is usually indentation.

---

## 🔁 4. Reboot (Recommended)

```bash
sudo reboot
```

After reboot, the Raspberry Pi should automatically connect to your Wi-Fi network.

---
