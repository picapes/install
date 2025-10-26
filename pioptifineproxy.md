## PiCape's OptiFine Proxy (All Versions & Clients)
**PiCape's OptiFine Proxy** reroutes requests from OptiFine’s servers to ours, letting capes and cosmetics display in nearly any Minecraft version or client that supports OptiFine capes (e.g., OptiFine itself or the [Capes Mod](https://modrinth.com/mod/capes)).

> [!NOTE]  
> Animated capes are **not supported** in PiOptiFine Proxy. Normal capes will still work.

# Installation for:
* [Windows](#windows--install)
* [MacOS](#macos--install)
* [Linux](#linux--install)
* [Android/iOS (NextDNS)](/notes/mobile-via-dns.md)

---

### Windows — Install
1. Right-click the **Windows button** → select **Windows PowerShell (Administrator)**.  
2. Run this command [Removes any existing OptiFine proxies (Cloaks+, Mantle, Arcmetica, etc.)]:  
   ```powershell
   Get-DnsClientNrptRule | Where-Object { $_.Namespace -eq 's.optifine.net' } | Remove-DnsClientNrptRule -Force; (Get-Content $env:SystemRoot\System32\drivers\etc\hosts | Where-Object { $_ -notmatch 's\.optifine\.net' }) | Set-Content -Path $env:SystemRoot\System32\drivers\etc\hosts -Force
   ```
2. Run this command [Addd the PiOF Proxy DNS rule]:

   ```powershell
   Add-DnsClientNrptRule -Namespace "s.optifine.net" -NameServers "38.224.226.95"
   ```
3. Run Flush DNS command:

   ```powershell
   ipconfig /flushdns
   ```
5. Restart Minecraft.

---

### Windows — Uninstall

1. Open **Windows PowerShell (Administrator)**.
2. Run:

   ```powershell
   Get-DnsClientNrptRule | Where-Object { $_.Namespace -eq 's.optifine.net' } | Remove-DnsClientNrptRule -Force; (Get-Content $env:SystemRoot\System32\drivers\etc\hosts) | Where-Object {$_ -notmatch 's\.optifine\.net'} | Set-Content $env:SystemRoot\System32\drivers\etc\hosts
   ```
3. Restart Minecraft.

---

### macOS — Install

1. Open **Terminal** (⌘+Space → type "Terminal").
2. Run:

   ```bash
   sudo nano /etc/hosts
   ```

   *(Enter your Mac password; nothing will show while typing.)*
3. Scroll to the bottom of the file.
4. Add this line (delete any existing `s.optifine.net` entries first):

   ```
   38.224.226.95 s.optifine.net
   ```
5. Save and exit (**Ctrl+O**, **Enter**, then **Ctrl+X**).
6. Restart Minecraft.

---

### macOS — Uninstall

1. Open **Terminal**.
2. Run:

   ```bash
   sudo nano /etc/hosts
   ```
3. Remove the line(s) containing `s.optifine.net`.
4. Save and exit (**Ctrl+O**, **Enter**, then **Ctrl+X**).
5. Restart Minecraft.

---

### Linux — Install

1. Press **Ctrl+Alt+T** to open a terminal.
2. Run:

   ```bash
   sudo nano /etc/hosts
   ```

   *(Enter your sudo password; nothing will show while typing.)*
3. Scroll to the bottom of the file.
4. Add this line (delete any existing `s.optifine.net` entries first):

   ```
   38.224.226.95 s.optifine.net
   ```
5. Save and exit (**Ctrl+X**, then press **Y**, then **Enter**).
6. Restart Minecraft.

---

### Linux — Uninstall

1. Open a terminal (**Ctrl+Alt+T**).
2. Run:

   ```bash
   sudo nano /etc/hosts
   ```
3. Remove the line(s) containing `s.optifine.net`.
4. Save and exit (**Ctrl+X**, then press **Y**, then **Enter**).
5. Restart Minecraft.

---

### No Admin / Sudo Access?

If you don’t have administrator privileges, you can still use the [Cape Provider X](https://modrinth.com/mod/cape-provider-x) mod on modern Fabric versions to display PiCapes without modifying system settings.
