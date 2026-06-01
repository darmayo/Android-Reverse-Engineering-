<div align="center">

# 🤖 Android Reverse Engineering Toolkit — Complete Edition

**Koleksi tools, workflow, dan resource untuk Android Reverse Engineering, APK Analysis, Static Analysis, Dynamic Analysis, Frida Instrumentation, SSL Pinning Research, Mobile API Testing, WebView Analysis, Native Library Analysis, Malware Analysis, Mobile Forensics, dan Security Research.**

![Focus](https://img.shields.io/badge/focus-android%20reverse%20engineering-7F77DD?style=flat-square)
![Usage](https://img.shields.io/badge/usage-ethical%20only-D85A30?style=flat-square)
![Category](https://img.shields.io/badge/category-apk%20analysis%20%7C%20frida%20%7C%20mobile%20security-1D9E75?style=flat-square)
![Resources](https://img.shields.io/badge/resources-190-58a6ff?style=flat-square)

</div>


## 📑 Daftar Isi

- [📚 Standards, Methodology & Checklists](#standards-methodology--checklists)
- [📦 APK Collection, Lab Setup & Device Control](#apk-collection-lab-setup--device-control)
- [📱 Static APK Analysis & Decompilation](#static-apk-analysis--decompilation)
- [🧩 Manifest, Permission, Components, Intent & Deep Link Analysis](#manifest-permission-components-intent--deep-link-analysis)
- [🔐 Secrets, Firebase, Tokens & Cloud Exposure](#secrets-firebase-tokens--cloud-exposure)
- [🧪 Dynamic Analysis, Frida, Hooking & Runtime Instrumentation](#dynamic-analysis-frida-hooking--runtime-instrumentation)
- [🌐 SSL Pinning, Proxy & Network Traffic Analysis](#ssl-pinning-proxy--network-traffic-analysis)
- [🔌 Mobile API, JWT, IDOR/BOLA & Backend Testing](#mobile-api-jwt-idorbola--backend-testing)
- [🧬 WebView, Hybrid App & JavaScript Endpoint Analysis](#webview-hybrid-app--javascript-endpoint-analysis)
- [🔬 Native Library, Flutter, Binary & Reverse Engineering](#native-library-flutter-binary--reverse-engineering)
- [🗄️ Local Storage, Database, Backup & Log Analysis](#local-storage-database-backup--log-analysis)
- [🛡️ Android Malware Analysis, Mobile Forensics & Defensive RE](#android-malware-analysis-mobile-forensics--defensive-re)
- [🤖 AI-Assisted Android RE & Security Automation](#ai-assisted-android-re--security-automation)
- [📚 Labs, Awesome Lists, Learning & Mobile References](#labs-awesome-lists-learning--mobile-references)
- [🚫 Restricted / Research Only](#restricted--research-only)

- [🧭 Android Reverse Engineering Workflow](#-android-reverse-engineering-workflow)
- [✅ Quick Tool List](#-quick-tool-list)
- [⚖️ Disclaimer](#️-disclaimer)

---

## 🧭 Android Reverse Engineering Workflow

1. **Scope & Legal Boundary**
   - Pastikan aplikasi, package name, versi APK, device/emulator, akun uji, backend/API, dan batasan pengujian jelas.

2. **APK Collection & Environment Setup**
   - Ambil APK dari sumber resmi atau device sendiri, siapkan emulator/rooted device, ADB, proxy, certificate testing, dan tools static/dynamic analysis.

3. **Static APK Analysis**
   - Review `AndroidManifest.xml`, permissions, exported components, deep links, intent filters, resources, strings, assets, config, secrets, Firebase, dan native libraries.

4. **Decompilation & Code Review**
   - Gunakan jadx, apktool, dex2jar, JD-GUI, APKLab, MobSF, Androguard, APKiD, dan grep/ripgrep untuk memahami logic aplikasi.

5. **Dynamic Analysis**
   - Jalankan aplikasi, monitor logcat, runtime behavior, filesystem, database, shared preferences, memory, anti-debugging, root detection, dan integrity checks.

6. **Frida / Hooking / Instrumentation**
   - Gunakan Frida, Objection, RMS, Xposed/LSPosed, Auto-Frida, fridump3, dan helper scripts untuk analisis runtime pada lab atau scope legal.

7. **Network & Mobile API Testing**
   - Intercept traffic dengan Burp/ZAP/mitmproxy/HTTP Toolkit, uji JWT, IDOR/BOLA, authorization, rate limit, business logic, dan data exposure.

8. **Native & Flutter Analysis**
   - Analisis `.so`, JNI, Flutter binary, symbol, strings, obfuscation, dan native anti-tamper menggunakan Ghidra, radare2, Cutter, blutter, dan AndroidNativeScanner.

9. **Forensics / Malware / Defensive RE**
   - Analisis sample hanya di lab aman, gunakan MVT, PCAPdroid, Wireshark, forensic tools, dan malware-analysis references.

10. **Reporting**
   - Dokumentasikan APK hash/version, device/emulator, request/response, screenshot, PoC legal, impact, affected component, dan remediation.

---

## 📚 Standards, Methodology & Checklists

| Resource | Link | Fungsi |
|---|---|---|
| OWASP MASTG | https://mas.owasp.org/MASTG/ | Mobile Application Security Testing Guide; referensi utama testing dan analisis aplikasi mobile. |
| OWASP MASVS | https://mas.owasp.org/MASVS/ | Mobile Application Security Verification Standard untuk baseline security mobile. |
| OWASP Mobile Top 10 | https://owasp.org/www-project-mobile-top-10/ | Daftar risiko utama mobile application security. |
| OWASP Mobile Top 10 Article | https://infosecwriteups.com/owasp-mobile-top-10-52987725a12c | Artikel pembelajaran OWASP Mobile Top 10. |
| Android Intent Vulnerabilities Cheat Sheet | https://0xn3va.gitbook.io/cheat-sheets/android-application/intent-vulnerabilities | Cheat sheet Android intent, exported component, dan intent-based vulnerabilities. |
| MobileApp-Pentest-Cheatsheet | https://github.com/tanprathan/MobileApp-Pentest-Cheatsheet | Cheatsheet mobile app pentesting Android/iOS. |
| Android-Pentesting-Checklist | https://github.com/Hrishikesh7665/Android-Pentesting-Checklist | Checklist Android pentesting untuk assessment mobile app. |
| Android-iOS-Cheat-Sheet | https://github.com/justmobilesec/Android-iOS-Cheat-Sheet/ | Cheat sheet Android/iOS security testing. |
| My-iOS-Pentesting-Cheatsheet | https://github.com/Abhinandan-Khurana/My-iOS-Pentesting-Cheatsheet | Cheatsheet iOS pentesting sebagai referensi mobile RE tambahan. |

---

## 📦 APK Collection, Lab Setup & Device Control

| Resource | Link | Fungsi |
|---|---|---|
| ADB | https://developer.android.com/tools/adb | Android Debug Bridge untuk shell, install APK, pull/push file, logcat, dan device control. |
| Android Studio Emulator | https://developer.android.com/studio/run/emulator | Emulator Android resmi untuk lab dynamic analysis. |
| scrcpy | https://github.com/Genymobile/scrcpy | Mirror dan control Android device dari desktop. |
| scrcpy-gui | https://github.com/kil0bit-kb/scrcpy-gui | GUI modern untuk scrcpy; membantu evidence capture dan testing flow. |
| Termux | https://github.com/termux/termux-app | Terminal Android untuk menjalankan command-line tools di device/lab. |
| vphone-aio | https://github.com/34306/vphone-aio | Virtual phone/device workflow helper untuk mobile testing lab. |
| BrutDroid | https://github.com/Brut-Security/BrutDroid/ | Android Studio pentest automator untuk emulator rooting, Frida, dan Burp Suite. |
| APK Extractor | https://github.com/axxapy/apk-extractor | Helper untuk mengambil APK dari device; gunakan pada app yang kamu punya izin. |
| APK Downloader / ipatool equivalent note | https://github.com/majd/ipatool | CLI iOS app downloader; disimpan sebagai referensi mobile app acquisition legal. |

---

## 📱 Static APK Analysis & Decompilation

| Resource | Link | Fungsi |
|---|---|---|
| apktool | https://github.com/iBotPeaches/Apktool | Decode dan rebuild APK resources, manifest, dan smali. |
| jadx | https://github.com/skylot/jadx | Dex to Java decompiler untuk membaca source hasil decompile dari APK/DEX. |
| dex2jar | https://github.com/pxb1988/dex2jar | Convert .dex menjadi .jar agar bisa dianalisis dengan Java decompiler. |
| JD-GUI | https://github.com/java-decompiler/jd-gui | GUI Java decompiler untuk membaca file .class atau .jar. |
| MobSF | https://github.com/MobSF/Mobile-Security-Framework-MobSF | Framework all-in-one untuk static, dynamic, malware analysis, dan security assessment Android/iOS. |
| Androguard | https://github.com/androguard/androguard | Python framework untuk analisis APK, DEX, dan AndroidManifest. |
| APKLab | https://github.com/APKLab/APKLab | VS Code extension untuk reverse engineering APK, decompile, rebuild, dan patching. |
| APKiD | https://github.com/rednaga/APKiD | Identifikasi packer, obfuscator, compiler, dan protector pada APK. |
| Bytecode Viewer | https://github.com/Konloch/bytecode-viewer | Java/Android bytecode viewer dan decompiler GUI. |
| APK Editor Studio | https://github.com/kefir500/apk-editor-studio | GUI untuk reverse engineering, edit, dan rebuild APK pada lab/app berizin. |
| APKToolGUI | https://github.com/AndnixSH/APKToolGUI | GUI untuk apktool/decompile/rebuild APK. |
| APKDeepLens | https://github.com/d78ui98/APKDeepLens | Android APK static analysis dan inspection helper. |
| APKdevastate | https://github.com/rafosw/APKdevastate | Android APK analysis/research helper; audit source sebelum digunakan. |
| apk-info | https://github.com/delvinru/apk-info | APK information extractor untuk static analysis Android. |
| APK Studio | https://github.com/vaibhavpandeyvpz/apkstudio | IDE/tool GUI untuk reverse engineering APK Android. |
| justapk | https://github.com/TheQmaks/justapk | APK analysis/helper tool untuk workflow reverse engineering Android. |
| PulseAPK-Core | https://github.com/deemoun/PulseAPK-Core | Android APK analysis/security testing core/helper. |
| Androidmeda | https://github.com/In3tinct/Androidmeda | Android security analysis/research helper; audit source sebelum digunakan. |
| beerus-android | https://github.com/hakaioffsec/beerus-android?tab=readme-ov-file#getting-started | Android security testing helper pada APK/app yang berizin. |
| apkshield-pt | https://github.com/Whitehat987/apkshield-pt | APK security/protection testing helper untuk lab dan aplikasi berizin. |
| strings / binutils | https://github.com/bminor/binutils-gdb | Utility untuk mengekstrak string dari binary, APK, DEX, atau native library. |
| ripgrep | https://github.com/BurntSushi/ripgrep | Pencarian cepat pada source, decompiled APK, strings, config, dan assets. |
| gf | https://github.com/tomnomnom/gf | Pattern matching untuk token, URL, endpoint, secrets, dan parameter menarik. |
| GF-Patterns | https://github.com/thecybertix/GF-Patterns | Koleksi pattern untuk mempercepat pencarian hasil decompile. |

---

## 🧩 Manifest, Permission, Components, Intent & Deep Link Analysis

| Resource | Link | Fungsi |
|---|---|---|
| Android Manifest Official Docs | https://developer.android.com/guide/topics/manifest/manifest-intro | Referensi AndroidManifest.xml, component, permission, intent-filter, dan metadata. |
| Android App Links Docs | https://developer.android.com/training/app-links | Referensi deep link dan app link behavior. |
| Android Intent Docs | https://developer.android.com/reference/android/content/Intent | Referensi Intent, action, data, category, dan extras. |
| drozer-agent | https://github.com/ReversecLabs/drozer-agent | Agent untuk Android security assessment, component enumeration, dan IPC testing. |
| AndroGoat | https://github.com/satishpatnayak/AndroGoat | Vulnerable Android app untuk latihan manifest/component/insecure storage/WebView. |
| InsecureBankv2 | https://github.com/dineshshetty/Android-InsecureBankv2 | Vulnerable Android banking app untuk latihan mobile security testing. |
| Damn Vulnerable Android App | https://github.com/payatu/diva-android | Vulnerable Android app untuk latihan reverse engineering dan mobile security. |
| OWASP GoatDroid | https://github.com/jackMannino/OWASP-GoatDroid-Project | Vulnerable Android app untuk latihan security testing. |

---

## 🔐 Secrets, Firebase, Tokens & Cloud Exposure

| Resource | Link | Fungsi |
|---|---|---|
| Trail of Bits Firebase APK Scanner Skill | https://github.com/trailofbits/skills/tree/main/plugins/firebase-apk-scanner | Skill untuk mendeteksi Firebase exposure dari APK. |
| droid-llm-hunter | https://github.com/roomkangali/droid-llm-hunter | Mencari indikasi LLM/API usage atau secret terkait AI pada APK Android. |
| Gitleaks | https://github.com/gitleaks/gitleaks | SAST secret scanner untuk repository/source hasil decompile. |
| trufflehog | https://github.com/trufflesecurity/trufflehog | Secret scanning pada Git history dan filesystem. |
| secrets-patterns-db | https://github.com/mazen160/secrets-patterns-db | Database regex pattern untuk secrets, token, API key, dan kredensial. |
| Search Leaked Keys Regex | https://github.com/Lu3ky13/Search-for-all-leaked-keys-secrets-using-one-regex-/tree/main | Regex/kumpulan regex untuk mencari leaked keys dan secrets. |
| Key-Checker | https://github.com/daffainfo/Key-Checker | Mengecek validitas API key atau access token. |
| LEAKEY | https://github.com/rohsec/LEAKEY | Validasi leaked credentials/API token yang ditemukan saat audit. |
| Profanatica Secret Scanner | https://github.com/Profanatic/Profanatica-Secret-Scanner | Secret scanner untuk menemukan kredensial dan token sensitif. |
| mantra | https://github.com/brosck/mantra | Mencari API key/secrets pada halaman web/file JavaScript yang dipakai backend/mobile. |
| s3scanner | https://github.com/sa7mon/s3scanner | Audit bucket S3 terbuka yang ditemukan dari app/config/API. |
| s3tk | https://github.com/KingOfBugbounty/s3tk | Toolkit keamanan Amazon S3. |
| cloudfox | https://github.com/BishopFox/cloudfox | Cloud attack path situational awareness untuk cloud asset yang masuk scope. |
| SecurityTrails | https://securitytrails.com/ | Historical DNS/backend discovery. |
| Shodan | https://www.shodan.io/ | Mencari exposed backend/API service. |
| Censys | https://censys.io/ | Mencari host, cert, dan service backend. |
| FullHunt | https://fullhunt.io/ | Attack surface management untuk backend mobile app. |

---

## 🧪 Dynamic Analysis, Frida, Hooking & Runtime Instrumentation

| Resource | Link | Fungsi |
|---|---|---|
| Frida | https://github.com/frida/frida | Dynamic instrumentation toolkit untuk hook function dan inspect runtime behavior. |
| frida-tools | https://github.com/frida/frida-tools | CLI tools untuk Frida. |
| Objection | https://github.com/sensepost/objection | Runtime mobile exploration toolkit berbasis Frida. |
| RMS - Runtime Mobile Security | https://github.com/m0bilesecurity/RMS-Runtime-Mobile-Security | Runtime mobile security framework berbasis Frida. |
| XposedBridge | https://github.com/rovo89/XposedBridge | Java part dari Xposed Framework untuk runtime hooking Android. |
| LSPosed | https://github.com/LSPosed/LSPosed | Modern Xposed framework untuk Android versi baru. |
| Auto-Frida | https://github.com/ommirkute/Auto-Frida | Tool otomasi Frida untuk mempercepat dynamic testing. |
| Frida-Script-Runner | https://github.com/z3n70/Frida-Script-Runner | Runner/helper untuk menjalankan Frida scripts. |
| frida-ui | https://github.com/adityatelange/frida-ui | UI/helper untuk Frida workflow. |
| frida-android-helper2 | https://github.com/secuworm2/frida-android-helper2 | Frida helper untuk Android dynamic analysis dan instrumentation. |
| frida-jdwp-loader | https://github.com/frankheat/frida-jdwp-loader | Frida/JDWP loader helper untuk Android dynamic analysis. |
| phantom-frida | https://github.com/TheQmaks/phantom-frida | Frida helper/research tool untuk Android dynamic analysis. |
| fridump3 | https://github.com/rootbsd/fridump3 | Dump memory process menggunakan Frida untuk runtime analysis. |
| medusa | https://github.com/Ch0pin/medusa | Android security/dynamic instrumentation framework. |
| pidcat | https://github.com/JakeWharton/pidcat | Colored logcat per package. |
| strace | https://github.com/strace/strace | Trace system calls dan signals saat aplikasi/process berjalan. |
| logcat | https://developer.android.com/tools/logcat | Android logging system untuk melihat log aplikasi dan sistem. |

---

## 🌐 SSL Pinning, Proxy & Network Traffic Analysis

| Resource | Link | Fungsi |
|---|---|---|
| Burp Suite | https://portswigger.net/burp | Proxy utama untuk intercept, inspect, modify, replay request, dan mobile API testing. |
| OWASP ZAP | https://github.com/zaproxy/zaproxy | Open-source web/API proxy dan scanner. |
| mitmproxy | https://github.com/mitmproxy/mitmproxy | Interactive SSL/TLS-capable intercepting proxy untuk HTTP/HTTPS traffic. |
| Wireshark | https://gitlab.com/wireshark/wireshark | Network protocol analyzer untuk packet capture dan traffic inspection. |
| PCAPdroid | https://github.com/emanuele-f/PCAPdroid | Capture dan analisis traffic langsung dari Android device. |
| HTTP Toolkit | https://github.com/httptoolkit/httptoolkit | HTTP debugging, interception, dan testing toolkit. |
| apk-mitm | https://github.com/niklashigi/apk-mitm | Patch APK untuk membantu testing traffic interception/certificate pinning pada lab/legal scope. |
| SSLPinDetect | https://github.com/aancw/SSLPinDetect | Tool untuk mendeteksi SSL pinning pada Android apps. |
| SSL-bypass | https://github.com/0xCD4/SSL-bypass | Helper SSL pinning bypass testing pada app milik sendiri atau scope legal. |
| frida-interception-and-unpinning | https://github.com/httptoolkit/frida-interception-and-unpinning | Script Frida untuk interception dan SSL unpinning research pada environment legal. |
| Bypassing SSL Pinning on Play Store AVDs Without Frida | https://www.mfumis.com/posts/bypassing-ssl-pinning-on-play-store-avds-without-frida/ | Artikel pembelajaran bypass SSL pinning pada Android emulator/AVD untuk lab legal. |
| atlantis-android | https://github.com/ProxymanApp/atlantis-android | Android network inspection/debugging helper dari ekosistem Proxyman. |
| intercept | https://github.com/smittix/intercept | Mobile/network interception helper; gunakan pada aplikasi/device berizin. |
| InterceptSuite | https://github.com/InterceptSuite/InterceptSuite | Interception/proxy suite untuk web/API/mobile traffic testing. |
| FoxyProxy | https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/ | Proxy switching untuk Burp/ZAP. |

---

## 🔌 Mobile API, JWT, IDOR/BOLA & Backend Testing

| Resource | Link | Fungsi |
|---|---|---|
| APIStrike | https://github.com/RevoltSecurities/apistrike | API security scanner berbasis OpenAPI spec dan role config. |
| Autoswagger | https://github.com/intruder-io/autoswagger/ | Mencari dan menguji unauthenticated endpoints dari Swagger/OpenAPI docs. |
| IDOR-Forge | https://github.com/errorfiathck/IDOR-Forge | Membantu pengujian IDOR pada endpoint API. |
| jwtauditor | https://github.com/dr34mhacks/jwtauditor | Tool untuk audit JWT vulnerabilities pada mobile API. |
| jwt_tool | https://github.com/ticarpi/jwt_tool | Testing, decoding, dan auditing JWT. |
| Damn Vulnerable RESTaurant API Game | https://github.com/theowni/Damn-Vulnerable-RESTaurant-API-Game | Lab API vulnerable untuk latihan API security. |
| OWASP crAPI | https://github.com/OWASP/crAPI | Lab API vulnerable yang relevan untuk mobile backend/API testing. |
| PAYGoat | https://github.com/stuxctf/PAYGoat/ | Lab business logic untuk alur finansial/payment. |
| Webhook.site | https://webhook.site/ | Testing callback, SSRF, webhook, dan OOB interaction dari mobile backend. |
| Very Lazy Tech JWT Vulnerabilities | https://www.verylazytech.com/jwt-vulnerabilities | Referensi pembelajaran JWT vulnerabilities. |

---

## 🧬 WebView, Hybrid App & JavaScript Endpoint Analysis

| Resource | Link | Fungsi |
|---|---|---|
| JSAnalyzer | https://github.com/jenish-sojitra/JSAnalyzer | Analisis JavaScript untuk endpoint, secret, URL, dan email. |
| JSRecon-Buddy | https://github.com/TheArqsz/JSRecon-Buddy | Browser extension untuk menemukan endpoint, routes, secrets, dan subdomain dari JavaScript. |
| JSMap-Inspector | https://github.com/ynsmroztas/JSMap-Inspector | Inspeksi JavaScript Source Map .js.map. |
| MapperPlus | https://github.com/midoxnet/mapperplus | Ekstraksi source dari exposed .js.map untuk hybrid app/WebView backend. |
| LinkFinder | https://github.com/GerbenJavado/LinkFinder | Menemukan endpoint dari JavaScript. |
| jsluice | https://github.com/BishopFox/jsluice | Ekstraksi URL, endpoint, dan secret dari JS. |
| xnLinkFinder | https://github.com/xnl-h4ck3r/xnLinkFinder | Discovery link mendalam dari JavaScript dan halaman web. |
| sourcemapper | https://github.com/denandz/sourcemapper | Ekstraksi source asli dari source map. |
| XSSNow | https://github.com/dr34mhacks/xssnow | Payload XSS untuk WebView/client-side testing. |
| XSS-Payloads | https://github.com/orwagodfather/XSS-Payloads | Koleksi payload XSS. |
| XSS-Automation | https://github.com/dirtycoder0124/XSS-Automation | Automation scripts untuk XSS testing. |
| xssgenai | https://github.com/merdekasiberlab/xssgenai | AI-assisted XSS payload generation/testing helper. |
| DomLogger++ | https://github.com/kevin-mizu/domloggerpp | Monitor JavaScript sinks untuk client-side/WebView testing. |

---

## 🔬 Native Library, Flutter, Binary & Reverse Engineering

| Resource | Link | Fungsi |
|---|---|---|
| Ghidra | https://github.com/NationalSecurityAgency/ghidra | Reverse engineering suite untuk analisis native library .so. |
| radare2 | https://github.com/radareorg/radare2 | Reverse engineering framework untuk binary dan native library analysis. |
| Cutter | https://github.com/rizinorg/cutter | GUI reverse engineering berbasis Rizin/radare2 ecosystem. |
| angr-management | https://github.com/angr/angr-management | GUI untuk angr binary analysis framework. |
| AndroidNativeScanner | https://github.com/ynsmroztas/AndroidNativeScanner | Tool untuk analisis native Android libraries dan workflow mobile reverse engineering. |
| soSaver | https://github.com/TheQmaks/soSaver | Helper untuk mengambil/menyimpan native library .so dari Android apps. |
| blutter | https://github.com/worawit/blutter | Tool untuk reverse engineering Flutter apps dan analisis binary/app Flutter. |
| DaliVM | https://github.com/fatalSec/DaliVM | Android/Dalvik VM research helper. |
| GhidraMCP | https://github.com/LaurieWired/GhidraMCP | Integrasi MCP untuk workflow reverse engineering dengan Ghidra dan AI-assisted analysis. |
| GhidraGPT | https://github.com/weirdmachine64/GhidraGPT | AI-assisted reverse engineering helper untuk Ghidra. |
| Reverse-Engineering-Cheatsheet | https://github.com/Kennyslaboratory/Reverse-Engineering-Cheatsheet | Cheatsheet reverse engineering untuk learning dan analysis. |
| Awesome-Reversing | https://github.com/ReversingID/Awesome-Reversing | Awesome list reverse engineering. |
| awesome-reverse-engineering | https://github.com/alphaSeclab/awesome-reverse-engineering | Awesome list reverse engineering tools dan resources. |
| linux-re-101 | https://github.com/michalmalik/linux-re-101 | Materi dasar Linux reverse engineering. |
| reversingBits | https://github.com/mohitmishra786/reversingBits | Reverse engineering learning/resource. |
| reverse-engineering | https://github.com/wtsxDev/reverse-engineering | Reverse engineering notes/resources. |
| awesome-python-re | https://github.com/Svenskithesource/awesome-python-re | Python reverse engineering resource/tools. |
| Awesome-Android-Reverse-Engineering | https://github.com/user1342/Awesome-Android-Reverse-Engineering | Resource Android reverse engineering untuk analisis APK dan mobile security. |

---

## 🗄️ Local Storage, Database, Backup & Log Analysis

| Resource | Link | Fungsi |
|---|---|---|
| SQLiteStudio | https://github.com/pawelsalawa/sqlitestudio | GUI SQLite database viewer/editor untuk analisis database lokal aplikasi Android. |
| DB Browser for SQLite | https://github.com/sqlitebrowser/sqlitebrowser | GUI SQLite viewer/editor alternatif. |
| Android Backup Extractor | https://github.com/nelenkov/android-backup-extractor | Ekstrak dan analisis backup Android. |
| adb backup notes | https://developer.android.com/identity/data/autobackup | Referensi Android backup/autobackup behavior. |
| SharedPreferences Docs | https://developer.android.com/training/data-storage/shared-preferences | Referensi penyimpanan lokal SharedPreferences. |
| Android Data Storage Docs | https://developer.android.com/training/data-storage | Referensi data storage Android. |

---

## 🛡️ Android Malware Analysis, Mobile Forensics & Defensive RE

| Resource | Link | Fungsi |
|---|---|---|
| MVT | https://github.com/mvt-project/mvt | Mobile Verification Toolkit untuk forensic analysis Android/iOS secara konsensual. |
| OSINT-FORENSICS-MOBILE | https://github.com/CScorza/OSINT-FORENSICS-MOBILE | Resource OSINT dan mobile forensics untuk investigasi defensif. |
| ForensicsTools | https://github.com/mesquidar/ForensicsTools | Koleksi forensic tools untuk investigasi defensif dan incident response. |
| MalwareAnalysis101 | https://github.com/CYB3RMX/MalwareAnalysis101 | Materi dasar malware analysis untuk defensive research dan lab. |
| rshipp awesome-malware-analysis | https://github.com/rshipp/awesome-malware-analysis | Awesome list malware analysis untuk DFIR dan defensive research. |
| fabacab awesome-malware | https://github.com/fabacab/awesome-malware | Koleksi resource malware research dan analysis. |
| kh4sh3i Malware-Analysis | https://github.com/kh4sh3i/Malware-Analysis | Resource malware analysis untuk learning dan lab defensif. |
| Malfixer | https://github.com/Cleafy/Malfixer | Tool/resource untuk malware analysis atau remediation workflow. |
| RevBot | https://github.com/exfil0/RevBot | AI/reverse-engineering assistant untuk lab dan analisis defensif. |
| ios_forensics_suite | https://github.com/piotrbania/ios_forensics_suite | iOS forensics suite untuk analisis mobile forensic pada device/sampel berizin. |

---

## 🤖 AI-Assisted Android RE & Security Automation

| Resource | Link | Fungsi |
|---|---|---|
| Trail of Bits Skills | https://github.com/trailofbits/skills | Plugin/skills collection untuk security automation dan AI-assisted assessment. |
| Claude-BugHunter | https://github.com/elementalsouls/Claude-BugHunter | Claude-assisted bug hunting workflow/helper. |
| Claude-OSINT | https://github.com/elementalsouls/Claude-OSINT | Claude-assisted OSINT workflow/helper untuk investigasi legal. |
| FuzzyAI | https://github.com/cyberark/FuzzyAI | AI security testing/fuzzing research tool. |
| Guardian CLI | https://github.com/zakirkun/guardian-cli | AI-powered pentest automation CLI. |
| CAI | https://github.com/aliasrobotics/cai | Cybersecurity AI framework untuk agent security testing. |
| RAI | https://github.com/RevoltSecurities/RAI | CLI framework untuk LLM agent/team workflow. |
| secskills | https://github.com/trilwu/secskills | Security skills/workflows untuk AI-assisted security work. |
| pentest-ai-agents | https://github.com/0xSteph/pentest-ai-agents | AI subagents untuk offensive security workflow. |
| Bug-Bounty-Agents | https://github.com/matty69v/Bug-Bounty-Agents | Agent AI untuk bug bounty workflow. |
| AIRecon | https://github.com/pikpikcu/airecon | Autonomous security agent berbasis Ollama/Kali Docker. |
| Reverse Engineering with Claude Code | https://zanestjohn.com/blog/reing-with-claude-code | Artikel pembelajaran reverse engineering dengan bantuan Claude Code. |

---

## 📚 Labs, Awesome Lists, Learning & Mobile References

| Resource | Link | Fungsi |
|---|---|---|
| Android Security Awesome | https://github.com/ashishb/android-security-awesome | Awesome list Android security. |
| awesome-mobile-security | https://github.com/noname1007/awesome-mobile-security | Awesome list mobile security untuk Android/iOS. |
| awesome-android-security / Swordfish | https://github.com/Swordfish-Security/awesome-android-security | Awesome list Android security dari Swordfish Security. |
| awesome-android-security / retr0-13 | https://github.com/retr0-13/awesome-android-security | Awesome list Android security untuk tools dan learning. |
| Android-Pentesting-Skill | https://github.com/DragonJAR/Android-Pentesting-Skill | Resource/skill untuk belajar Android pentesting. |
| android-reverse-engineering-skill | https://github.com/SimoneAvogadro/android-reverse-engineering-skill | Skill/resource untuk belajar Android reverse engineering. |
| just-mobile-security-mobile-docker | https://github.com/justmobilesec/just-mobile-security-mobile-docker | Docker environment untuk mobile security testing, reverse engineering, dan Android/iOS assessment lab. |
| OWApp Benchmarking Suite | https://github.com/Mobile-IoT-Security-Lab/OWApp-Benchmarking-Suite | Benchmarking suite untuk mobile app security testing dan evaluasi OWASP-style checks. |
| iOS Hardening Guide | https://github.com/martinholovsky/Security-Blueprints/blob/main/iOS-Hardening-Guide.md | Panduan hardening iOS untuk pembelajaran mobile security dan defensive configuration. |
| osx-and-ios-security-awesome | https://github.com/ashishb/osx-and-ios-security-awesome | Awesome list iOS/macOS security. |
| awesome-ios-security / Cy-clon3 | https://github.com/Cy-clon3/awesome-ios-security | Awesome list iOS security. |
| awesome-iOS-security-tools | https://github.com/0xdad0/awesome-iOS-security-tools | Koleksi tools iOS security dan mobile assessment. |
| awesome-ios-security / Swordfish | https://github.com/Swordfish-Security/awesome-ios-security | Awesome list iOS security dari Swordfish Security. |
| OpenMF | https://github.com/scorelab/OpenMF | Open-source app yang bisa dijadikan target lab untuk security review dan AppSec learning. |
| Security Blueprints | https://github.com/martinholovsky/Security-Blueprints/tree/main | Security architecture, hardening, dan blueprint resource. |

---

## 🚫 Restricted / Research Only

> Resource di bagian ini bersifat dual-use/high-risk. Simpan hanya untuk lab, aplikasi milik sendiri, bug bounty scope, pentest berizin, malware analysis defensif, atau research legal.

| Resource | Link | Catatan |
|---|---|---|
| PhoneSploit-Pro | https://github.com/AzeemIdrisi/PhoneSploit-Pro | Android security testing tool; gunakan hanya pada device sendiri atau lab berizin. |
| PhantomDroid | https://github.com/psychohackers/PhantomDroid | Android security research tool; audit source dan gunakan hanya di lab/device sendiri. |
| Android-IMEI-Changer | https://github.com/omerjerk/Android-IMEI-Changer | IMEI changer; berisiko legal/abuse, tidak direkomendasikan untuk workflow utama. |
| Tsunami-Bomber-Android | https://github.com/tykawaii98/Tsunami-Bomber-Android | Bomber/spam-style Android tool; tidak cocok untuk toolkit profesional. |
| rootengine | https://github.com/rafosw/rootengine | Android/rooting research helper; gunakan hanya pada device/lab milik sendiri. |
| CORUNA_IOS-MACOS_FULL_DUMP | https://github.com/Rat5ak/CORUNA_IOS-MACOS_FULL_DUMP | Dump/research resource; gunakan hanya untuk lab/device sendiri atau analisis legal. |
| iOS SSL pinning bypass without jailbreak | https://github.com/SahilH4ck4you/iOS-SSL-pinning-bypass-without-jalibreak | iOS SSL pinning bypass research; app testing with permission only. |

---

## ✅ Quick Tool List

```text
Static APK Analysis:
apktool, jadx, dex2jar, JD-GUI, MobSF, Androguard, APKLab, APKiD, Bytecode Viewer, APK Editor Studio

Manifest / Component Review:
AndroidManifest.xml, permissions, exported activities/services/receivers/providers, intent filters, deep links, app links

Secrets / Cloud:
Firebase APK Scanner Skill, droid-llm-hunter, Gitleaks, trufflehog, secrets-patterns-db, Key-Checker, LEAKEY, s3scanner

Dynamic Analysis:
ADB, logcat, pidcat, strace, Frida, frida-tools, Objection, RMS, Xposed, LSPosed, Auto-Frida, fridump3

Network / SSL Pinning:
Burp Suite, OWASP ZAP, mitmproxy, Wireshark, PCAPdroid, HTTP Toolkit, apk-mitm, SSLPinDetect, SSL-bypass

Mobile API:
APIStrike, Autoswagger, IDOR-Forge, jwtauditor, jwt_tool, crAPI, RESTaurant API Game, Webhook.site

WebView / Hybrid:
JSAnalyzer, LinkFinder, jsluice, JSMap-Inspector, MapperPlus, xnLinkFinder, XSS payload resources

Native / Flutter:
Ghidra, radare2, Cutter, angr-management, AndroidNativeScanner, soSaver, blutter, GhidraMCP, GhidraGPT

Storage / Forensics:
SQLiteStudio, DB Browser for SQLite, Android Backup Extractor, MVT, PCAPdroid, ForensicsTools
```

---

## ⚖️ Disclaimer

Gunakan tools dan teknik ini hanya untuk:

- Aplikasi milik sendiri
- Lab pribadi
- CTF
- Malware analysis defensif di lab aman
- Bug bounty yang jelas scope-nya
- Penetration testing berizin
- Security research legal

Jangan melakukan reverse engineering, bypass, interception, credential capture, traffic manipulation, exploit, patching, atau analisis terhadap aplikasi, akun, device, jaringan, atau sistem pihak lain tanpa izin eksplisit.
