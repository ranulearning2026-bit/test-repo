# Security Report

Batch: 07c07df6 — sources: `.aee/security-log.jsonl`, `.aee/security-work/verdict.json`

## 1. Executive Summary

| Metric | Value |
|--------|-------|
| Files analysed | 198 |
| Files with findings | 13 |
| Findings — critical | 1 |
| Findings — high | 16 |
| Findings — medium | 4 |
| Findings — low | 1 |
| Findings — total | 22, shown inline |
| Findings — confirmed | 9 |
| Findings — probable | 3 |
| Findings — needs\_cross\_file | 10 |
| Review result | approve |
| Review round | 1 |
| Open issues at approval | none |

Thirteen of 22 findings fall under OWASP A03 Injection; a secondary cluster of 6 findings covers A02 Cryptographic Failures.

## 2. Scope and Method

| Item | Detail |
|------|--------|
| Analysis kind | Static only |
| gitleaks (8.30.1) | 198 files |
| semgrep | missing — not installed |
| bandit | missing — not installed |
| spotbugs | skipped — no compiled classes (Java files covered by manual pass only) |
| Manual review | 13 files (all files with at least one finding) |
| Coverage | 198 of 223 files in intake |
| Scanner failures / skipped | semgrep not installed; bandit not installed; spotbugs skipped (no compiled classes) |
| Review scope — candidates reviewed | 1 |
| Review scope — findings reviewed | 22 |
| Review scope — drops reviewed | 0 |
| Review scope — gaps reviewed | 26 |
| Triage — candidates kept | 1 |
| Triage — candidates dropped | 0 |
| Triage — gaps decided manual | 23 |
| Triage — gaps decided benign | 3 |

## 3. Findings

22 findings, shown inline.

| # | Severity | Confidence | Component | File | Lines | OWASP | CWE | Tool | Title |
|---|----------|------------|-----------|------|-------|-------|-----|------|-------|
| 1 | critical | confirmed | aurora-portal | src/aurora/aurora-portal/aurora\_portal/telemetry\_consumer.py | 17 | A08 | CWE-502 | manual | yaml.load() without SafeLoader on external bus message body in handle() |
| 2 | high | confirmed | aurora-compute | src/aurora/aurora-compute/api/server.go | 17 | A02 | CWE-295 | manual | TLS certificate verification disabled in newClient() |
| 3 | high | confirmed | aurora-identity | src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/TokenService.java | 18 | A07 | CWE-798 | gitleaks | Hardcoded signing key in SIGNING\_KEY constant |
| 4 | high | confirmed | aurora-portal | src/aurora/aurora-portal/aurora\_portal/session.py | 11 | A07 | CWE-330 | manual | Cryptographically insecure random.choice() used to generate session IDs |
| 5 | high | confirmed | aurora-portal | src/aurora/aurora-portal/aurora\_portal/session.py | 15 | A02 | CWE-327 | manual | SHA-1 used for password hashing in password\_hash() |
| 6 | high | probable | aurora-identity | src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/UserRepository.java | 27 | A03 | CWE-89 | manual | SQL injection via string concatenation in findByName() |
| 7 | high | probable | aurora-identity | src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/UserRepository.java | 34 | A03 | CWE-89 | manual | SQL injection via string concatenation in countByProject() |
| 8 | high | probable | aurora-network | src/aurora/aurora-network/src/packet\_parse.c | 20 | A03 | CWE-120 | manual | Unbounded strcpy from network packet field into fixed-size stack buffer |
| 9 | high | needs\_cross\_file | aurora-cli | src/aurora/aurora-cli/src/index.js | 15 | A03 | CWE-95 | manual | eval() with caller-supplied expression in applyFilter() |
| 10 | high | needs\_cross\_file | aurora-compute | src/aurora/aurora-compute/api/server.go | 24 | A03 | CWE-78 | manual | Shell injection via exec.Command("sh","-c",...) in Console() |
| 11 | high | needs\_cross\_file | aurora-network | src/aurora/aurora-network/src/tunnel.c | 19–20 | A03 | CWE-78 | manual | Command injection via sprintf + system() with unsanitised parameters in tunnel\_up() |
| 12 | high | needs\_cross\_file | aurora-network | src/aurora/aurora-network/src/tunnel.c | 26–27 | A03 | CWE-78 | manual | Command injection via snprintf + system() with unsanitised parameter in tunnel\_down() |
| 13 | high | needs\_cross\_file | aurora-network | src/aurora/aurora-network/src/tunnel.c | 36–37 | A03 | CWE-78 | manual | Command injection via snprintf + system() with unsanitised parameter in tunnel\_mtu() |
| 14 | high | needs\_cross\_file | aurora-portal | src/aurora/aurora-portal/aurora\_portal/api.py | 17 | A08 | CWE-502 | manual | yaml.load() without SafeLoader on file contents in load\_quota\_profile() |
| 15 | high | needs\_cross\_file | aurora-portal | src/aurora/aurora-portal/aurora\_portal/api.py | 31 | A03 | CWE-78 | manual | OS command injection via os.system() with caller-supplied command in export\_report() |
| 16 | high | needs\_cross\_file | aurora-storage | src/aurora/aurora-storage/src/chunk.cpp | 27 | A03 | CWE-120 | manual | memcpy with caller-supplied length may overflow fixed-size destination buffer |
| 17 | high | needs\_cross\_file | aurora-storage | src/aurora/aurora-storage/src/object\_store.cpp | 50 | A03 | CWE-22 | manual | Path traversal via string concatenation in path\_for() |
| 18 | medium | confirmed | aurora-identity | src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/CryptoUtil.java | 19–25 | A02 | CWE-327 | manual | AES/ECB mode used in seal() and open(); no authenticated encryption |
| 19 | medium | confirmed | aurora-identity | src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/TokenService.java | 22 | A02 | CWE-328 | manual | MD5 used as token signing hash in issue() |
| 20 | medium | confirmed | aurora-portal | src/aurora/aurora-portal/aurora\_portal/api.py | 24 | A02 | CWE-295 | manual | TLS verification disabled (verify=False) in fetch\_project() |
| 21 | medium | needs\_cross\_file | aurora-network | src/aurora/aurora-network/src/profile\_label.c | 29 | A03 | CWE-120 | manual | Unbounded strcpy from caller parameter into fixed-size struct field |
| 22 | low | confirmed | aurora-storage | src/aurora/aurora-storage/src/chunk.cpp | 36 | A02 | CWE-338 | manual | std::rand() used for placement group selection in placement\_group() |

---

### Finding 1

**Title:** yaml.load() without SafeLoader on external bus message body in handle()
**Location:** src/aurora/aurora-portal/aurora\_portal/telemetry\_consumer.py L17
**Component:** aurora-portal
**Severity:** critical | **Confidence:** confirmed
**OWASP:** A08 Software and Data Integrity Failures | **CWE:** CWE-502
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-portal/aurora_portal/telemetry_consumer.py:L17 calls yaml.load(message.body) without a Loader; message.body arrives from an external message bus and is attacker-controlled; PyYAML's default Loader allows arbitrary Python object construction, enabling remote code execution.

---

### Finding 2

**Title:** TLS certificate verification disabled in newClient()
**Location:** src/aurora/aurora-compute/api/server.go L17
**Component:** aurora-compute
**Severity:** high | **Confidence:** confirmed
**OWASP:** A02 Cryptographic Failures | **CWE:** CWE-295
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-compute/api/server.go:L17 sets InsecureSkipVerify: true in the tls.Config of the HTTP transport returned by newClient(), disabling TLS certificate validation for all outbound requests and allowing man-in-the-middle attacks.

---

### Finding 3

**Title:** Hardcoded signing key in SIGNING\_KEY constant
**Location:** src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/TokenService.java L18
**Component:** aurora-identity
**Severity:** high | **Confidence:** confirmed
**OWASP:** A07 Identification and Authentication Failures | **CWE:** CWE-798
**Tool:** gitleaks | **Rule ID:** generic-api-key

src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/TokenService.java:L18 declares SIGNING_KEY as a static final String literal; any party with read access to the source code can forge tokens by reproducing the MD5-based signature computed in issue(). (Secret value omitted.)

---

### Finding 4

**Title:** Cryptographically insecure random.choice() used to generate session IDs
**Location:** src/aurora/aurora-portal/aurora\_portal/session.py L11
**Component:** aurora-portal
**Severity:** high | **Confidence:** confirmed
**OWASP:** A07 Identification and Authentication Failures | **CWE:** CWE-330
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-portal/aurora_portal/session.py:L11 builds session identifiers using random.choice(); Python's random module is not cryptographically secure and its output is predictable, making session IDs guessable by an attacker who can observe prior values.

---

### Finding 5

**Title:** SHA-1 used for password hashing in password\_hash()
**Location:** src/aurora/aurora-portal/aurora\_portal/session.py L15
**Component:** aurora-portal
**Severity:** high | **Confidence:** confirmed
**OWASP:** A02 Cryptographic Failures | **CWE:** CWE-327
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-portal/aurora_portal/session.py:L15 returns hashlib.sha1 as the password digest; SHA-1 is a fast, cryptographically weak hash not designed for password storage and is vulnerable to brute-force and rainbow-table attacks.

---

### Finding 6

**Title:** SQL injection via string concatenation in findByName()
**Location:** src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/UserRepository.java L27
**Component:** aurora-identity
**Severity:** high | **Confidence:** probable
**OWASP:** A03 Injection | **CWE:** CWE-89
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/UserRepository.java:L27 builds the query as "SELECT id, name, project FROM users WHERE name = '" + name + "'" and executes it via java.sql.Statement.executeQuery; the 'name' parameter is concatenated without escaping, allowing SQL injection.

---

### Finding 7

**Title:** SQL injection via string concatenation in countByProject()
**Location:** src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/UserRepository.java L34
**Component:** aurora-identity
**Severity:** high | **Confidence:** probable
**OWASP:** A03 Injection | **CWE:** CWE-89
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/UserRepository.java:L34 builds the query as "SELECT COUNT(*) FROM users WHERE project = '" + project + "'" via java.sql.Statement; the 'project' parameter is concatenated without escaping, allowing SQL injection.

---

### Finding 8

**Title:** Unbounded strcpy from network packet field into fixed-size stack buffer
**Location:** src/aurora/aurora-network/src/packet\_parse.c L20
**Component:** aurora-network
**Severity:** high | **Confidence:** probable
**OWASP:** A03 Injection | **CWE:** CWE-120
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-network/src/packet_parse.c:L20 calls strcpy(tag, header) inside parse_tenant_tag(); 'header' is a char* from network packet data and 'tag' is a fixed-size stack buffer declared at L19; no length check is present, allowing a crafted packet to overflow the stack buffer.

---

### Finding 9

**Title:** eval() with caller-supplied expression in applyFilter()
**Location:** src/aurora/aurora-cli/src/index.js L15
**Component:** aurora-cli
**Severity:** high | **Confidence:** needs\_cross\_file
**OWASP:** A03 Injection | **CWE:** CWE-95
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-cli/src/index.js:L15 passes the caller-supplied parameter 'expression' directly to eval() inside applyFilter(); no sanitisation or allow-list is visible in this file, so an attacker who controls 'expression' can execute arbitrary JavaScript in the Node.js process.

---

### Finding 10

**Title:** Shell injection via exec.Command("sh","-c",...) in Console()
**Location:** src/aurora/aurora-compute/api/server.go L24
**Component:** aurora-compute
**Severity:** high | **Confidence:** needs\_cross\_file
**OWASP:** A03 Injection | **CWE:** CWE-78
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-compute/api/server.go:L24 constructs a shell command with exec.Command("sh", "-c", fmt.Sprintf("virsh console %s", instance)); the 'instance' parameter is not validated or escaped, so shell metacharacters in the caller's input could inject arbitrary commands.

---

### Finding 11

**Title:** Command injection via sprintf + system() with unsanitised parameters in tunnel\_up()
**Location:** src/aurora/aurora-network/src/tunnel.c L19–20
**Component:** aurora-network
**Severity:** high | **Confidence:** needs\_cross\_file
**OWASP:** A03 Injection | **CWE:** CWE-78
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-network/src/tunnel.c:L19 constructs a shell command with sprintf using the caller-supplied 'name' and 'remote' parameters, then L20 executes it via system(); no validation or escaping is performed, allowing shell metacharacters in either parameter to inject arbitrary commands.

---

### Finding 12

**Title:** Command injection via snprintf + system() with unsanitised parameter in tunnel\_down()
**Location:** src/aurora/aurora-network/src/tunnel.c L26–27
**Component:** aurora-network
**Severity:** high | **Confidence:** needs\_cross\_file
**OWASP:** A03 Injection | **CWE:** CWE-78
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-network/src/tunnel.c:L26 uses snprintf to build a command incorporating the caller-supplied 'name' parameter, and L27 passes the result to system(); the 'name' string is not sanitised, allowing shell metacharacters to inject arbitrary commands.

---

### Finding 13

**Title:** Command injection via snprintf + system() with unsanitised parameter in tunnel\_mtu()
**Location:** src/aurora/aurora-network/src/tunnel.c L36–37
**Component:** aurora-network
**Severity:** high | **Confidence:** needs\_cross\_file
**OWASP:** A03 Injection | **CWE:** CWE-78
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-network/src/tunnel.c:L36 builds a shell command with snprintf including the caller-supplied 'name' parameter, and L37 executes it via system(); 'name' is not sanitised, so shell metacharacters in the caller's input can inject arbitrary commands.

---

### Finding 14

**Title:** yaml.load() without SafeLoader on file contents in load\_quota\_profile()
**Location:** src/aurora/aurora-portal/aurora\_portal/api.py L17
**Component:** aurora-portal
**Severity:** high | **Confidence:** needs\_cross\_file
**OWASP:** A08 Software and Data Integrity Failures | **CWE:** CWE-502
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-portal/aurora_portal/api.py:L17 calls yaml.load(handle.read()) without a Loader argument; the default Loader in PyYAML allows arbitrary Python object construction, enabling remote code execution if an attacker can control the YAML file contents.

---

### Finding 15

**Title:** OS command injection via os.system() with caller-supplied command in export\_report()
**Location:** src/aurora/aurora-portal/aurora\_portal/api.py L31
**Component:** aurora-portal
**Severity:** high | **Confidence:** needs\_cross\_file
**OWASP:** A03 Injection | **CWE:** CWE-78
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-portal/aurora_portal/api.py:L31 passes the 'command' parameter directly to os.system(); if 'command' is derived from user-controlled input, shell metacharacters can inject arbitrary OS commands.

---

### Finding 16

**Title:** memcpy with caller-supplied length may overflow fixed-size destination buffer
**Location:** src/aurora/aurora-storage/src/chunk.cpp L27
**Component:** aurora-storage
**Severity:** high | **Confidence:** needs\_cross\_file
**OWASP:** A03 Injection | **CWE:** CWE-120
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-storage/src/chunk.cpp:L27 calls std::memcpy(c.id, id.c_str(), id.size()) where id.size() is the caller-supplied string length and c.id is a fixed-size array; no bounds check is performed before the copy, so a string longer than the array overflows the destination.

---

### Finding 17

**Title:** Path traversal via string concatenation in path\_for()
**Location:** src/aurora/aurora-storage/src/object\_store.cpp L50
**Component:** aurora-storage
**Severity:** high | **Confidence:** needs\_cross\_file
**OWASP:** A03 Injection | **CWE:** CWE-22
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-storage/src/object_store.cpp:L50 builds the file path as root_ + "/" + key where 'key' is derived from the caller's input; without normalisation, a key containing "../" sequences can escape the intended root directory and access arbitrary files.

---

### Finding 18

**Title:** AES/ECB mode used in seal() and open(); no authenticated encryption
**Location:** src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/CryptoUtil.java L19–25
**Component:** aurora-identity
**Severity:** medium | **Confidence:** confirmed
**OWASP:** A02 Cryptographic Failures | **CWE:** CWE-327
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/CryptoUtil.java:L19 (seal) and L25 (open) both call Cipher.getInstance("AES/ECB/PKCS5Padding"); ECB mode produces identical ciphertext for identical plaintext blocks, enabling block-pattern analysis and replay; no integrity protection is provided.

---

### Finding 19

**Title:** MD5 used as token signing hash in issue()
**Location:** src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/TokenService.java L22
**Component:** aurora-identity
**Severity:** medium | **Confidence:** confirmed
**OWASP:** A02 Cryptographic Failures | **CWE:** CWE-328
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-identity/src/main/java/cloud/aurora/identity/TokenService.java:L22 calls MessageDigest.getInstance("MD5") to produce the token signature digest; MD5 is cryptographically broken and allows collision and pre-image attacks, undermining token integrity.

---

### Finding 20

**Title:** TLS verification disabled (verify=False) in fetch\_project()
**Location:** src/aurora/aurora-portal/aurora\_portal/api.py L24
**Component:** aurora-portal
**Severity:** medium | **Confidence:** confirmed
**OWASP:** A02 Cryptographic Failures | **CWE:** CWE-295
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-portal/aurora_portal/api.py:L24 calls requests.get with verify=False, disabling TLS certificate validation for the outbound HTTP request; this allows a man-in-the-middle attacker to intercept or modify the response.

---

### Finding 21

**Title:** Unbounded strcpy from caller parameter into fixed-size struct field
**Location:** src/aurora/aurora-network/src/profile\_label.c L29
**Component:** aurora-network
**Severity:** medium | **Confidence:** needs\_cross\_file
**OWASP:** A03 Injection | **CWE:** CWE-120
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-network/src/profile_label.c:L29 calls strcpy(slot->label, label) inside aurora_profile_label(); 'label' is an unchecked char* parameter and slot->label is a fixed-size field of struct profile_slot defined at L17-20; a string longer than the field overwrites adjacent struct memory.

---

### Finding 22

**Title:** std::rand() used for placement group selection in placement\_group()
**Location:** src/aurora/aurora-storage/src/chunk.cpp L36
**Component:** aurora-storage
**Severity:** low | **Confidence:** confirmed
**OWASP:** A02 Cryptographic Failures | **CWE:** CWE-338
**Tool:** manual | **Rule ID:** —

src/aurora/aurora-storage/src/chunk.cpp:L36 uses std::rand()%groups to select a placement group; std::rand() is not cryptographically secure and its output is predictable, which may allow an attacker to influence placement outcomes if the seed is recoverable.

---

## 4. Component View

1 component has no findings (third\_party).

| Component | Files | Code lines | Files with findings | Critical | High | Medium | Low | Total |
|-----------|-------|-----------|---------------------|----------|------|--------|-----|-------|
| aurora-cli | 4 | 63 | 1 | 0 | 1 | 0 | 0 | 1 |
| aurora-compute | 19 | 753 | 1 | 0 | 2 | 0 | 0 | 2 |
| aurora-identity | 53 | 1301 | 3 | 0 | 3 | 2 | 0 | 5 |
| aurora-network | 57 | 2590 | 3 | 0 | 4 | 1 | 0 | 5 |
| aurora-portal | 19 | 326 | 3 | 1 | 4 | 1 | 0 | 6 |
| aurora-storage | 51 | 1745 | 2 | 0 | 2 | 0 | 1 | 3 |
| third\_party | 6 | 29 | 0 | — | — | — | — | 0 |

## 5. Supply Chain and Infrastructure

**Dependency Advisories:** not part of the current outputs.

**Dependency Inventory:** not part of the current outputs.

**License Inventory:** not part of the current outputs.

**Infrastructure Findings:** not part of the current outputs.

## 6. Review Status and Limitations

### Review Status

Verdict: **approve** — round 1.

Reviewed: 1 candidate, 22 findings, 0 drops, 26 gaps.

No issue was open at approval.

### Limitations

The analysis is static only and per file. Cross-file taint flows are not covered by this report.

**Scanner failures / skipped files:**

- semgrep: not installed — files must not be described as scanned clean by semgrep.
- bandit: not installed — Python files must not be described as scanned clean by bandit.
- spotbugs: skipped — no compiled classes; Java files were not scanned by spotbugs.
