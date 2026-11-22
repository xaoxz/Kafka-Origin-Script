# Kafka Origin Script (`S2.0.0`)

> เอกสารฉบับนี้มีทั้งภาษาไทยและภาษาอังกฤษ / This document is written in Thai first, followed by English.

---

## ภาษาไทย (Thai)

### Script คืออะไร?

**Script** คือลันเชอร์สำหรับ **Kafka Origin** บน Windows และ Linux ทำหน้าที่ดูแลการเปิด-ปิดเซิร์ฟเวอร์ เข้าตัวเกม (รันตรงบน Windows หรือผ่าน Wine บน Linux) แก้ไขข้อมูลไอดีและเซฟเกม (เอเจนต์, จัดทีม, W-Engine, ดิสก์, แบงบู, ด่าน Endgame และโปรไฟล์) จัดการม็อด ZZMI ตั้งค่าข้อความบนหน้าจอ (`custom.uid`) จัดการและย้ายโฟลเดอร์อย่างปลอดภัยในหน้า **Settings > Paths** รวมถึงอัปเดตและย้อนเวอร์ชันของทุกส่วนผ่านหน้า **Updates**

สิ่งที่เปลี่ยนใน **Script `S2.0.0`**:

- **ดีไซน์สไตล์ในเกมครบทั้งลันเชอร์:** ออกแบบหน้าตาใหม่ทั้งหมดในสไตล์ในเกม ได้แก่ **Home, Updates, Settings (พร้อม Paths), Agents, Squads, W-Engine, Discs, Bangboo, Endgames, Profile, Mods, HUD, Console, Help และ About** โดยยังคงมีสไตล์คลาสสิกให้เลือกใช้ได้ (สลับได้จากหน้าตั้งค่า หรือกด `Ctrl+Shift+U`)
- **รูปเอเจนต์และหน้าแก้ไขเอเจนต์สไตล์ในเกม:**
  - รูปเอเจนต์ถูกจัดกรอบให้ตรงใบหน้าของเอเจนต์แต่ละคนในทุกจุด (หน้ารายชื่อเอเจนต์, การ์ดทีมในหน้า **Home** และหน้า **Squads**)
  - หน้าแก้ไขเอเจนต์ออกแบบใหม่ในสไตล์ในเกม (ปรับเลเวล, Mindscape, สกิล, W-Engine และดิสก์ พร้อมบันทึกด้วยคีย์ `Ctrl+S`)
  - หน้า **W-Engine** และหน้าดิสก์ (**Discs**) แสดงให้เห็นว่าเอเจนต์คนใดกำลังสวมใส่ไอเทมแต่ละชิ้นอยู่
  - **Kafka**, **Robin** และ **Sunbringer** แสดงค่าสเตตัสพื้นฐาน (Base stats) แล้ว
- **ปรับปรุงหน้า Home, Settings, Updates, Endgames และ Profile:**
  - หน้า **Home** เปิดมาพร้อมเคอร์เซอร์วางอยู่ที่ปุ่ม **Start** (กด `Enter` เพื่อเริ่มเกมได้เลย) รายการอัปเดตที่รออยู่จะแสดงเป็นแถวบนหน้า **Home** และจุดสีแดงบนไอคอน **Updates** แทนป๊อปอัปบังปุ่ม Start
  - หน้า **Home** และ **Settings** มีพื้นที่แสดงผลกว้างขึ้น, รายละเอียดในหน้า **Updates** แสดงเป็นตารางที่กระชับ, แต่ละแถวในหน้า **Endgames** แสดงรูปศัตรู และหน้า **Profile** ออกแบบให้เหมือนบัตร Proxy License
- **หน้า Updates และการย้อนเวอร์ชัน:** หน้า **Updates** รวมเป็นรายการเดียวโดยแสดงรายการที่รออัปเดตไว้บนสุด พร้อมปุ่ม **"Update N items"** ปุ่มเดียว และระบบย้อนเวอร์ชันจะเก็บเวอร์ชันก่อนหน้าไว้ 2 เวอร์ชัน
- **คีย์ลัดและการป้องกันการกดค้าง:** คีย์ลัด `Ctrl+K` (ค้นหา) และ `Ctrl+S` (บันทึก) ใช้งานได้แม้ขณะสลับเป็นแป้นพิมพ์ภาษาไทย และการกด `Enter` หรือ `Ctrl+S` ค้างไว้จะไม่สั่งงานซ้ำรัวๆ อีกต่อไป
- **ความเสถียร ความปลอดภัย และการจัดการโฟลเดอร์:**
  - การสั่งปิดเครื่อง (Shutdown) หรือออกจากระบบ (Logout) จะไม่ทำให้ลันเชอร์แจ้งเตือนว่าแครชในการเปิดครั้งถัดไปอีก
  - ข้อความจากภายนอก (ข้อมูลเกม ชื่อรีลีส ชื่อบัญชี) ไม่สามารถแทรกสิ่งแปลกปลอมเข้ามาในหน้าของลันเชอร์ได้
  - เปิดเกมครั้งที่สองในเซสชันลันเชอร์เดิมได้ตามปกติ และบน Windows รันสคริปต์ช่วยเหลือผ่าน PowerShell ทำให้ใช้ชื่อโฟลเดอร์ที่มีอักขระพิเศษอย่าง `&` ได้
  - ตัวติดตั้งตรวจสอบพื้นที่ว่างสำหรับการติดตั้งและการนำเข้าข้อมูลรวมกัน และปุ่ม **"Remove old copy"** ในหน้า **Settings > Paths** จะปฏิเสธการลบตราบใดที่ยังมีสิ่งใดใช้งานสำเนาเก่าอยู่ (รวมถึงผ่านลิงก์) หรือในขณะที่กำลังมีการอัปเดตหรือติดตั้งทำงานอยู่ ไม่ทำให้เซฟที่เข้าถึงผ่านลิงก์สูญหาย และไม่ลบสิ่งใดนอกโฟลเดอร์นั้น

ซอร์สโค้ดเป็นแบบส่วนตัวและไม่มีการเผยแพร่ คลังสาธารณะนี้เก็บเฉพาะหน้า README และไฟล์รีลีสที่ลงลายเซ็นแล้วเท่านั้น

### เวอร์ชัน

- **Script:** `S2.0.0` (อยู่ในชุด **Kafka Origin `K2.0.0`** ร่วมกับ Whisper `W1.0.3` และ Hunter `H2.0.0`)
- **ตัวเกมที่รองรับ:** `CNBetaWin3.4.5` (`S2.0.0 · เกม 3.4.5`)
- **ระบบที่รองรับ:** Windows (`x86_64`) และ Linux (`x86_64`)

### ไฟล์รีลีสอยู่ที่ไหน?

ไฟล์รีลีสที่ลงลายเซ็นแล้ว (`kafka-origin-script-S2.0.0-windows-x86_64.zip`, `kafka-origin-script-S2.0.0-linux-x86_64.zip`, `SHA256SUMS` และ `SHA256SUMS.sig`) เผยแพร่อยู่ที่หน้า [Releases ของ xaoxz/Kafka-Origin-Script](https://github.com/xaoxz/Kafka-Origin-Script/releases)

### วิธีติดตั้ง

**ติดตั้งผ่านตัวติดตั้ง Kafka Origin** จากคลังหลัก [xaoxz/Kafka-Origin](https://github.com/xaoxz/Kafka-Origin/releases/latest):

- **Windows:** ดาวน์โหลด `KafkaOrigin-Setup.exe` (ออนไลน์) หรือ `KafkaOrigin-Setup-Offline.exe` (ออฟไลน์)
- **Linux:** รันคำสั่ง:
  ```bash
  curl -fsSL https://github.com/xaoxz/Kafka-Origin/releases/latest/download/install.sh | bash
  ```

เมื่อติดตั้งแล้ว คุณสามารถอัปเดตหรือย้อนเวอร์ชันของ Script ได้โดยตรงจากหน้า **Updates** ในลันเชอร์

---

## English

### What is Script?

**Script** is the desktop launcher for **Kafka Origin** on Linux and Windows. It starts and supervises the local server, launches the game (directly on Windows or through Wine on Linux), edits player saves and live accounts (agents, squads, W-Engines, Drive Discs, Bangboo, endgames, and profile), manages ZZMI mods and on-screen HUD text (`custom.uid`), checks and moves folders safely under **Settings > Paths**, and updates or rolls back every part through **Updates**.

What's new in **Script `S2.0.0`**:

- **Full In-Game Style Redesign:** The whole launcher is redesigned in the in-game style: **Home, Updates, Settings (with Paths), Agents, Squads, W-Engine, Discs, Bangboo, Endgames, Profile, Mods, HUD, Console, Help, and About**. The classic style is still there (via a setting, or `Ctrl+Shift+U`).
- **In-Game Style Agent Editor, Portraits & Equipment:**
  - Agent pictures are framed on each agent's face everywhere (agent list, **Home** team cards, **Squads**).
  - The agent editor is redesigned in the in-game style (level, Mindscape, skills, W-Engine, and discs; Save with `Ctrl+S`).
  - The **W-Engine** and **Disc** pages show which agent has each item equipped.
  - **Kafka**, **Robin**, and **Sunbringer** now show their base stats.
- **Refined Home, Settings, Updates, Endgames & Profile:**
  - **Home** opens with the cursor on **Start** (`Enter` starts the game); waiting updates show as rows on **Home** and a red dot on the **Updates** icon instead of a popup over Start.
  - **Home** and **Settings** have more room; **Updates** details are a compact table; **Endgames** rows show the enemy picture; **Profile** looks like a Proxy License.
- **Unified Updates & Rollback:** **Updates** is one list with waiting items first and one **"Update N items"** button; **Roll back** keeps two earlier versions.
- **Keyboard Shortcuts & Key-Hold Protection:** `Ctrl+K` (search) and `Ctrl+S` (save) work with a Thai keyboard layout too, and holding `Enter` or `Ctrl+S` no longer repeats an action.
- **Stability, Page Safety & Safe Folders:**
  - A shutdown or logout no longer makes the launcher report a crash on the next start.
  - Text from outside sources (game data, release names, account names) can no longer inject anything into the launcher pages.
  - Starting the game a second time in one launcher session works again; on Windows, helper scripts run through PowerShell so folder names with symbols such as `&` work.
  - Setup checks the free space for the install and the import together, and **"Remove old copy"** under **Settings > Paths** refuses while anything still uses the old copy (including through a link) or while an update or install runs, never loses saves reached through links, and never removes anything outside it.

Source code is private and never published; this public repository holds only this README and signed release files.

### Version

- **Script:** `S2.0.0` (part of **Kafka Origin `K2.0.0`** with Whisper `W1.0.3` and Hunter `H2.0.0`)
- **Game version:** `CNBetaWin3.4.5` (`S2.0.0 · game 3.4.5`)
- **Platforms:** Windows (`x86_64`) and Linux (`x86_64`)

### Where Releases Are

Signed release archives (`kafka-origin-script-S2.0.0-windows-x86_64.zip`, `kafka-origin-script-S2.0.0-linux-x86_64.zip`, `SHA256SUMS`, and `SHA256SUMS.sig`) are published on [xaoxz/Kafka-Origin-Script Releases](https://github.com/xaoxz/Kafka-Origin-Script/releases).

### How to Install

**Install through Kafka Origin Setup** from [xaoxz/Kafka-Origin](https://github.com/xaoxz/Kafka-Origin/releases/latest):

- **Windows:** Download and run `KafkaOrigin-Setup.exe` (online) or `KafkaOrigin-Setup-Offline.exe` (offline).
- **Linux:** Run:
  ```bash
  curl -fsSL https://github.com/xaoxz/Kafka-Origin/releases/latest/download/install.sh | bash
  ```

Once installed, updates and rollbacks are handled through the launcher's **Updates** page.
