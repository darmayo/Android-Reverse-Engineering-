<div align="center">

# 🤖 Android Reverse Engineering Toolkit

**Koleksi materi, workflow, dan tools untuk Android Reverse Engineering, APK Analysis, Static Analysis, Dynamic Analysis, Runtime Instrumentation, Network Traffic Analysis, Debugging, Malware Analysis, dan Mobile Security Research.**

![Focus](https://img.shields.io/badge/focus-android%20reverse%20engineering-7F77DD?style=flat-square)
![Usage](https://img.shields.io/badge/usage-ethical%20only-D85A30?style=flat-square)
![Category](https://img.shields.io/badge/category-apk%20analysis%20%7C%20frida%20%7C%20reverse%20engineering-1D9E75?style=flat-square)

</div>

---

## 📑 Daftar Isi

- [🤖 Android Reverse Engineering](#-android-reverse-engineering)
- [📦 Android APK Structure](#-android-apk-structure)
- [🔍 Reverse Engineering Techniques](#-reverse-engineering-techniques)
- [📱 Static Analysis](#-static-analysis)
- [🧪 Dynamic Analysis](#-dynamic-analysis)
- [🌐 Network Traffic Analysis](#-network-traffic-analysis)
- [🧰 Common Android Reverse Engineering Tools](#-common-android-reverse-engineering-tools)
- [🧭 Basic Android Reverse Engineering Workflow](#-basic-android-reverse-engineering-workflow)
- [⚠️ Challenges in Android Reverse Engineering](#️-challenges-in-android-reverse-engineering)
- [✅ Quick Tool List](#-quick-tool-list)
- [📚 Learning Resources](#-learning-resources)
- [⚖️ Disclaimer](#️-disclaimer)

---

## 🤖 Android Reverse Engineering

**Android Reverse Engineering** adalah proses menganalisis aplikasi Android untuk memahami cara kerja internal aplikasi.

Reverse engineering dilakukan dengan memeriksa APK package, Dalvik bytecode, resource, konfigurasi, native library, runtime behavior, network traffic, dan data lokal aplikasi.

Android reverse engineering umum digunakan untuk:

- Security research
- Malware analysis
- Vulnerability discovery
- Application debugging
- Penetration testing legal
- Mobile application security assessment
- Understanding app logic
- Analyzing API communication
- Finding hardcoded secrets
- Reviewing obfuscation and anti-tamper logic

> Gunakan hanya pada aplikasi milik sendiri, lab, CTF, malware sample yang aman, atau aplikasi yang masuk scope pengujian legal.

---

## 📦 Android APK Structure

Android applications didistribusikan sebagai APK (**Android Package**) files.

APK file adalah ZIP archive yang berisi komponen aplikasi.

```bash
APK
├── AndroidManifest.xml
├── classes.dex
├── resources.arsc
├── lib/
├── res/
└── assets/
```

### Key Files

| File / Folder | Description |
|---|---|
| `AndroidManifest.xml` | Permission, package name, activity, service, receiver, provider, exported component, deep link, dan konfigurasi aplikasi. |
| `classes.dex` | Dalvik bytecode hasil kompilasi Java/Kotlin. |
| `resources.arsc` | Compiled Android resources. |
| `res/` | App resources seperti layout, drawable, string, XML, dan UI resource. |
| `assets/` | File tambahan seperti config, bundled data, model, certificate, atau file statis lain. |
| `lib/` | Native libraries seperti `.so` untuk ARM/x86. |
| `META-INF/` | APK signing metadata dan certificate information. |

---

## 🔍 Reverse Engineering Techniques

Android applications bisa dianalisis dengan dua pendekatan utama:

1. **Static Analysis**
2. **Dynamic Analysis**

Static analysis dilakukan tanpa menjalankan aplikasi. Dynamic analysis dilakukan dengan menjalankan aplikasi dan mengamati behavior saat runtime.

---

## 📱 Static Analysis

Static analysis memeriksa APK tanpa menjalankannya.

Typical tasks:

- Extracting application resources
- Reviewing permissions
- Reviewing exported components
- Reviewing deep links and intent filters
- Analyzing code structure
- Identifying embedded secrets
- Finding API endpoints
- Checking WebView configuration
- Checking Firebase/cloud config
- Reviewing native libraries
- Reviewing obfuscation
- Checking debug/backup flags

### Common Static Analysis Tools

| Tool | Link | Fungsi |
|---|---|---|
| [apktool](https://github.com/iBotPeaches/Apktool) | GitHub | Decode dan rebuild APK resources, manifest, dan smali. |
| [jadx](https://github.com/skylot/jadx) | GitHub | Dex to Java decompiler untuk membaca source hasil decompile dari APK/DEX. |
| [dex2jar](https://github.com/pxb1988/dex2jar) | GitHub | Convert `.dex` menjadi `.jar` agar bisa dianalisis dengan Java decompiler. |
| [JD-GUI](https://github.com/java-decompiler/jd-gui) | GitHub | GUI Java decompiler untuk membaca file `.class` atau `.jar`. |
| [strings](https://github.com/bminor/binutils-gdb) | GitHub mirror | Utility untuk mengekstrak string dari binary, APK, DEX, atau native library. |
| [MobSF](https://github.com/MobSF/Mobile-Security-Framework-MobSF) | GitHub | Framework all-in-one untuk static dan dynamic analysis Android/iOS. |
| [Androguard](https://github.com/androguard/androguard) | GitHub | Python framework untuk analisis APK, DEX, dan AndroidManifest. |
| [APKLab](https://github.com/APKLab/APKLab) | GitHub | VS Code extension untuk reverse engineering APK, decompile, rebuild, dan patching. |
| [APKiD](https://github.com/rednaga/APKiD) | GitHub | Identifikasi packer, obfuscator, compiler, dan protector pada APK. |
| [Bytecode Viewer](https://github.com/Konloch/bytecode-viewer) | GitHub | Java/Android bytecode viewer dan decompiler GUI. |

### Example: Decompile APK with apktool

```bash
apktool d app.apk
```

### Example: Decompile APK with jadx

```bash
jadx-gui app.apk
```

### Example: Convert DEX to JAR

```bash
d2j-dex2jar classes.dex
```

### Example: Extract Strings

```bash
strings classes.dex
strings lib/arm64-v8a/libnative.so
```

---

## 🧪 Dynamic Analysis

Dynamic analysis menjalankan aplikasi dan mengamati behavior saat runtime.

Analysts monitor:

- API calls
- Network traffic
- Runtime behavior
- Memory activity
- Local storage
- Logs
- Authentication flow
- SSL pinning behavior
- Root detection behavior
- Anti-debugging behavior
- File system interaction
- Database access

### Common Dynamic Analysis Tools

| Tool | Link | Fungsi |
|---|---|---|
| [Frida](https://github.com/frida/frida) | GitHub | Dynamic instrumentation toolkit untuk hook function, inspect runtime behavior, dan modify behavior saat aplikasi berjalan. |
| [frida-tools](https://github.com/frida/frida-tools) | GitHub | CLI tools untuk Frida. |
| [Objection](https://github.com/sensepost/objection) | GitHub | Runtime mobile exploration toolkit berbasis Frida. |
| [RMS - Runtime Mobile Security](https://github.com/m0bilesecurity/RMS-Runtime-Mobile-Security) | GitHub | Runtime mobile security framework berbasis Frida. |
| [XposedBridge](https://github.com/rovo89/XposedBridge) | GitHub | Java part dari Xposed Framework untuk runtime hooking Android. |
| [LSPosed](https://github.com/LSPosed/LSPosed) | GitHub | Modern Xposed framework untuk Android versi baru. |
| [ADB](https://developer.android.com/tools/adb) | Official Docs | Android Debug Bridge untuk shell, install APK, pull files, logcat, dan device control. |
| [logcat](https://developer.android.com/tools/logcat) | Official Docs | Android logging system untuk melihat log aplikasi dan sistem. |
| [strace](https://github.com/strace/strace) | GitHub | Trace system calls dan signals saat aplikasi/process berjalan. |
| [pidcat](https://github.com/JakeWharton/pidcat) | GitHub | Colored logcat per package untuk monitoring log aplikasi. |
| [fridump3](https://github.com/rootbsd/fridump3) | GitHub | Dump memory process menggunakan Frida untuk analisis runtime. |

### Example: ADB & Logcat

```bash
adb devices
adb shell
adb logcat
adb logcat | grep com.example.app
```

---

## 🌐 Network Traffic Analysis

Banyak aplikasi Android berkomunikasi dengan remote servers.

Network traffic analysis membantu menemukan:

- API endpoints
- Authentication tokens
- Sensitive data leaks
- Weak TLS configuration
- Missing authorization checks
- IDOR/BOLA issues
- Insecure WebView/backend communication
- Debug endpoints
- Staging endpoints
- Hardcoded base URLs

### Common Network Analysis Tools

| Tool | Link | Fungsi |
|---|---|---|
| [Burp Suite](https://portswigger.net/burp) | Official Website | Proxy utama untuk intercept, inspect, modify, replay request, dan mobile API testing. |
| [Wireshark](https://gitlab.com/wireshark/wireshark) | GitLab | Network protocol analyzer untuk packet capture dan traffic inspection. |
| [mitmproxy](https://github.com/mitmproxy/mitmproxy) | GitHub | Interactive SSL/TLS-capable intercepting proxy untuk HTTP/HTTPS traffic. |
| [OWASP ZAP](https://github.com/zaproxy/zaproxy) | GitHub | Open-source web/API proxy dan scanner. |
| [PCAPdroid](https://github.com/emanuele-f/PCAPdroid) | GitHub | Capture dan analisis traffic langsung dari Android device. |
| [HTTP Toolkit](https://github.com/httptoolkit/httptoolkit) | GitHub | HTTP debugging, interception, and testing toolkit. |

### Example: Proxy Android Traffic

```bash
adb shell settings put global http_proxy 192.168.1.10:8080
```

### Example: Clear Android Proxy

```bash
adb shell settings put global http_proxy :0
```

---

## 🧰 Common Android Reverse Engineering Tools

### APK Decompilers

| Tool | Link | Fungsi |
|---|---|---|
| [apktool](https://github.com/iBotPeaches/Apktool) | GitHub | Decode/rebuild APK resources dan smali. |
| [jadx](https://github.com/skylot/jadx) | GitHub | Decompile DEX/APK langsung ke Java-like source. |
| [dex2jar](https://github.com/pxb1988/dex2jar) | GitHub | Convert DEX ke JAR. |
| [JD-GUI](https://github.com/java-decompiler/jd-gui) | GitHub | Java decompiler GUI untuk membaca JAR/class. |
| [Bytecode Viewer](https://github.com/Konloch/bytecode-viewer) | GitHub | Java/Android bytecode viewer dan decompiler GUI. |

### Dynamic Instrumentation

| Tool | Link | Fungsi |
|---|---|---|
| [Frida](https://github.com/frida/frida) | GitHub | Runtime instrumentation dan function hooking. |
| [Objection](https://github.com/sensepost/objection) | GitHub | Runtime mobile exploration berbasis Frida. |
| [XposedBridge](https://github.com/rovo89/XposedBridge) | GitHub | Xposed Framework Java bridge untuk Android hooking. |
| [LSPosed](https://github.com/LSPosed/LSPosed) | GitHub | Modern Xposed framework untuk Android versi baru. |
| [RMS](https://github.com/m0bilesecurity/RMS-Runtime-Mobile-Security) | GitHub | Runtime Mobile Security framework berbasis Frida. |
| [Frida-Script-Runner](https://github.com/z3n70/Frida-Script-Runner) | GitHub | Runner untuk menjalankan dan mengelola script Frida. |
| [Auto-Frida](https://github.com/ommirkute/Auto-Frida) | GitHub | Tool otomasi Frida untuk mempercepat dynamic testing. |

### Android Debugging Tools

| Tool | Link | Fungsi |
|---|---|---|
| [ADB](https://developer.android.com/tools/adb) | Official Docs | Device control, shell, install, pull/push file, dan debugging. |
| [logcat](https://developer.android.com/tools/logcat) | Official Docs | Melihat log aplikasi dan sistem. |
| [strace](https://github.com/strace/strace) | GitHub | Trace syscall dan process behavior. |
| [pidcat](https://github.com/JakeWharton/pidcat) | GitHub | Colored logcat per package. |
| [scrcpy](https://github.com/Genymobile/scrcpy) | GitHub | Mirror dan control Android device dari desktop. |

### Network & Proxy Tools

| Tool | Link | Fungsi |
|---|---|---|
| [Burp Suite](https://portswigger.net/burp) | Official Website | Intercepting proxy dan web/mobile API testing. |
| [Wireshark](https://gitlab.com/wireshark/wireshark) | GitLab | Packet capture dan protocol analysis. |
| [mitmproxy](https://github.com/mitmproxy/mitmproxy) | GitHub | HTTP/HTTPS intercepting proxy. |
| [OWASP ZAP](https://github.com/zaproxy/zaproxy) | GitHub | Open-source proxy dan scanner. |
| [PCAPdroid](https://github.com/emanuele-f/PCAPdroid) | GitHub | Android packet capture dan traffic inspection. |

### Native Library Analysis

| Tool | Link | Fungsi |
|---|---|---|
| [Ghidra](https://github.com/NationalSecurityAgency/ghidra) | GitHub | Reverse engineering suite untuk analisis native library `.so`. |
| [radare2](https://github.com/radareorg/radare2) | GitHub | Reverse engineering framework untuk binary dan native library analysis. |
| [Cutter](https://github.com/rizinorg/cutter) | GitHub | GUI reverse engineering berbasis Rizin/radare2 ecosystem. |
| [soSaver](https://github.com/TheQmaks/soSaver) | GitHub | Tool terkait native `.so` Android untuk analisis library native. |
| [blutter](https://github.com/worawit/blutter) | GitHub | Tool untuk membantu reverse engineering Flutter apps. |

### Local Storage & Database Analysis

| Tool | Link | Fungsi |
|---|---|---|
| [SQLiteStudio](https://github.com/pawelsalawa/sqlitestudio) | GitHub | GUI SQLite database viewer/editor untuk analisis database lokal aplikasi Android. |
| [DB Browser for SQLite](https://github.com/sqlitebrowser/sqlitebrowser) | GitHub | GUI SQLite viewer/editor alternatif. |
| [Android Backup Extractor](https://github.com/nelenkov/android-backup-extractor) | GitHub | Ekstrak dan analisis backup Android. |

---

## 🧭 Basic Android Reverse Engineering Workflow

```bash
Obtain APK
    ↓
Extract APK contents
    ↓
Static analysis: code + resources
    ↓
Review manifest, permissions, components
    ↓
Find endpoints, secrets, config, and strings
    ↓
Install APK on test device
    ↓
Dynamic analysis
    ↓
Runtime instrumentation
    ↓
Network traffic analysis
    ↓
Identify vulnerabilities or behavior
    ↓
Document evidence and remediation
```

This workflow helps analysts systematically understand Android applications.

---

## ⚠️ Challenges in Android Reverse Engineering

Modern Android applications often use protection mechanisms such as:

- Code obfuscation with ProGuard / R8
- Root detection
- SSL pinning
- Anti-debugging techniques
- Anti-tamper protection
- Native code packing
- Runtime integrity checks
- Emulator detection
- Certificate pinning
- Integrity verification
- Dynamic code loading

These techniques are designed to prevent reverse engineering, tampering, and unauthorized analysis.

---

## ✅ Quick Tool List

```bash
# Static analysis
apktool
jadx
dex2jar
JD-GUI
strings
MobSF
Androguard
APKLab
APKiD

# Dynamic analysis
Frida
frida-tools
Objection
Xposed
LSPosed
RMS
ADB
logcat
strace
pidcat
fridump3

# Network analysis
Burp Suite
Wireshark
mitmproxy
OWASP ZAP
PCAPdroid
HTTP Toolkit

# Native analysis
Ghidra
radare2
Cutter
soSaver
blutter

# Storage analysis
SQLiteStudio
DB Browser for SQLite
Android Backup Extractor
```

---

## 📚 Learning Resources

| Resource | Link | Deskripsi |
|---|---|---|
| [OWASP MASTG](https://mas.owasp.org/MASTG/) | Official | Mobile Application Security Testing Guide. |
| [OWASP MASVS](https://mas.owasp.org/MASVS/) | Official | Mobile Application Security Verification Standard. |
| [Android Security Awesome](https://github.com/ashishb/android-security-awesome) | GitHub | Awesome list Android security. |
| [Damn Vulnerable Android App](https://github.com/payatu/diva-android) | GitHub | Vulnerable Android app untuk latihan reverse engineering dan mobile security. |
| [InsecureBankv2](https://github.com/dineshshetty/Android-InsecureBankv2) | GitHub | Vulnerable Android banking app untuk latihan mobile security testing. |
| [OWASP GoatDroid](https://github.com/jackMannino/OWASP-GoatDroid-Project) | GitHub | Vulnerable Android app untuk latihan security testing. |

---

## ⚖️ Disclaimer

Gunakan tools dan teknik ini hanya untuk:

- Aplikasi milik sendiri
- Lab pribadi
- CTF
- Malware analysis defensif
- Bug bounty yang jelas scope-nya
- Penetration testing berizin
- Security research legal

Jangan melakukan reverse engineering, bypass, interception, credential capture, traffic manipulation, exploit, atau analisis terhadap aplikasi, akun, device, jaringan, atau sistem pihak lain tanpa izin eksplisit.
