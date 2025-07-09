# SSH Key Setup and PuTTY Configuration Guide

## 🔐 Using `ssh-keygen` to Generate SSH Keys

### 1. Open Command Prompt or PowerShell
Search for **"cmd"** or **"powershell"** in the Windows search bar and launch the application.

### 2. Generate the Key Pair
Run the following command:

```bash
ssh-keygen -t rsa -b 4096
```

- `-t rsa`: Specifies the RSA algorithm.
- `-b 4096`: Sets the key length to 4096 bits (recommended).

### 3. Choose a Location and File Name
You’ll be prompted:

```
Enter file in which to save the key (/c/Users/YourUsername/.ssh/id_rsa):
```

- Press **Enter** to accept the default (`C:\Users\Dev\.ssh\id_rsa`) or specify a custom path.

### 4. Set a Passphrase (Optional but Recommended)
You’ll be asked to enter a passphrase to protect your private key:

```
Enter passphrase (empty for no passphrase):
```

- You can leave it blank and press Enter twice if you don't want a passphrase.

### 5. Confirm the Passphrase
Re-enter the same passphrase if you chose one.

### 6. Key Pair Generated
You should see this confirmation:

```
Your identification has been saved in C:\Users\Dev/.ssh/id_rsa
Your public key has been saved in C:\Users\Dev/.ssh/id_rsa.pub
```

---

## 🔄 Converting Private Key for PuTTY

PuTTY does **not** support the OpenSSH format directly. You must convert your private key to `.ppk` format using PuTTYgen.

### 📥 Download PuTTY and PuTTYgen

Download from the official PuTTY site:

**[PuTTY Download Page](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)**  
Direct installer (64-bit):  
[putty-64bit-0.83-installer.msi](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

### 🛠 Convert Private Key with PuTTYgen

1. Open **PuTTYgen**.
2. Click **"Load"**.
   - Set file type to `All Files (*.*)`
   - Select `C:\Users\Dev\.ssh\id_rsa`
3. Click **"Save private key"**.
   - Save as something like `my-key.ppk`.

---

## 🖥 Connecting with PuTTY

1. Open **PuTTY**.
2. Under **"Host Name (or IP address)"**, enter:

   ```
   167.172.2.62
   ```

3. Ensure **Port** is set to `22` (default for SSH).

### Additional Configuration in PuTTY:

- In the left sidebar:
  - Go to `Connection > Data`:
    - **Auto-login username**: `root`
  - Go to `Connection > SSH > Auth`:
    - **Private key file for authentication**: Browse and select the `.ppk` file you saved using PuTTYgen.

4. Go back to **Session** and click **Open** to connect.

---

✅ You're now ready to use SSH with PuTTY on Windows!