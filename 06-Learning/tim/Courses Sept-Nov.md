
Да. Я собрал **единый список Udemy-курсов**, уже с учётом новой программы IT STEP и того, что у него **Python не beginner-level: он работает с Django, читает документацию, использует Copilot и будет работать с Claude Code**.

В новой программе STEP прямо присутствуют CCNA networking, Linux, Bash, Windows Server 2025, Python для системного администрирования, application security, AWS, GitHub, Docker, Kubernetes, Prometheus/Grafana и cloud security. Поэтому наши Udemy-курсы должны заранее закрыть именно эти основы.

## Основной Udemy roadmap до 29 ноября

| №   | Направление                   | Курс                                                                                                                                                                              | Объём       | Что делаем                                                                           | Приоритет   |
| --- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------- | ------------------------------------------------------------------------------------ | ----------- |
| 1   | **Networking / CCNA**         | [David Bombal — Complete Networking Fundamentals / CCNA](https://www.udemy.com/course/complete-networking-fundamentals-course-ccna-start/?couponCode=MT260902G1B)                 | ~73 ч       | OSI, IPv4/IPv6, subnetting, VLAN, STP, routing, OSPF, ACL, NAT, DHCP + Packet Tracer | 🔴 Critical |
| 2   | **Linux Administration**      | [Jason Cannon — Linux Administration Bootcamp](https://www.udemy.com/course/linux-administration-bootcamp/?couponCode=MT260902G1B)                                                | 9 ч 19 мин  | Linux CLI, users, permissions, SSH, processes, services, networking                  | 🔴 Critical |
| 3   | **Windows Server**            | [Kevin Brown — Windows Server 2025 Administration](https://www.udemy.com/course/windows-server-2025-administration-kevin/?couponCode=MT260902G1B)                                 | 26 ч        | AD DS, GPO, DNS, DHCP, Hyper-V, certificates, file services                          | 🔴 Critical |
| 4   | **PowerShell / AD Coding**    | [Kevin Brown — PowerShell for Active Directory Administrators](https://www.udemy.com/course/powershell-for-active-directory-administrators/)                                      | 2 ч 57 мин  | автоматизация AD, users, groups, computers, bulk operations                          | 🔴 Critical |
| 5   | **Python Network Automation** | [David Bombal — Python Network Programming for Network Engineers](https://www.udemy.com/course/python-network-programming-for-network-engineers-python-3/?couponCode=MT260902G1B) | 12 ч 50 мин | SSH, Netmiko, NAPALM, Cisco automation, GNS3                                         | 🔴 Critical |
| 6   | **Bash Coding**               | [Jason Cannon — Bash Scripting and Shell Programming](https://www.udemy.com/course/bash-scripting/)                                                                               | 2 ч 33 мин  | shell scripting, automation, Linux tasks                                             | 🟠 High     |
| 7   | **Security**                  | [Jason Dion — CompTIA Security+ SY0-701](https://www.udemy.com/course/securityplus/)                                                                                              | большой     | threats, vulnerabilities, architecture, operations, IAM, crypto                      | 🟠 High     |
| 8   | **AWS**                       | [Stéphane Maarek — AWS Cloud Practitioner CLF-C02 2026](https://www.udemy.com/course/aws-certified-cloud-practitioner-new/?couponCode=MT260902G1B)                                | 14 ч 35 мин | IAM, EC2, S3, VPC, CloudWatch, RDS, cloud security                                   | 🟠 High     |
| 9   | **SQL / Database coding**     | [Jose Portilla — The Complete SQL Bootcamp](https://www.udemy.com/course/the-complete-sql-bootcamp/?couponCode=MT260902G1B)                                                       | 8 ч 51 мин  | PostgreSQL, SELECT, JOIN, GROUP BY, CRUD                                             | 🟡 Medium   |
| 10  | **Git / GitHub**              | [The Complete Git & GitHub 2026 Course](https://www.udemy.com/course/github-git/?couponCode=MT260902G1B)                                                                          | 7 ч 39 мин  | branches, merges, PRs, GitHub workflow, collaboration                                | 🟡 Medium   |

Bombal's network-programming course особенно хорошо подходит под его текущий уровень: это не обучение Python с нуля, а работа через GNS3, SSH, Netmiko и NAPALM с реальными network automation scenarios. Linux Bootcamp обновлён в августе 2026 и занимает около 9 часов, а Bash-курс того же автора — всего 2.5 часа, поэтому Bash я бы полностью закрыл ещё до STEP.

---

## Отдельно: Coding Track

Вот это я предлагаю считать **отдельной параллельной программой программирования**, а не просто частью cybersecurity.

### 1. Python Network Programming — основной

**David Bombal — Python Network Programming for Network Engineers**

Открыть курс на Udemy

Именно его я ставлю №1 по coding.

Он будет писать:

```
device = {
    "device_type": "cisco_ios",
    "host": "192.168.1.1",
    "username": "admin"
}
```

и постепенно переходить к:

```
Python
   ↓
SSH
   ↓
Cisco router/switch
   ↓
Netmiko
   ↓
retrieve configuration
   ↓
parse result
   ↓
JSON/YAML
```

Курс содержит 171 lecture и около 12 ч 50 мин практического материала.

### Projects после курса

**Network Inventory**

```
devices.yaml
     ↓
Python
     ↓
SSH
     ↓
hostname
interfaces
IOS version
IP addresses
     ↓
JSON
```

**Configuration Backup**

```
Python → Netmiko
        ↓
Router01
Router02
Switch01
        ↓
running-config
        ↓
Git
```

**Network Health Checker**

```
Python
 ↓
multiple devices
 ↓
ping / SSH
 ↓
interfaces
 ↓
status
 ↓
JSON report
```

---

## 2. PowerShell — второй обязательный coding language

**Kevin Brown — PowerShell for Active Directory Administrators**

Открыть курс

Он короткий, поэтому проходим **100%**.

Курс прямо ориентирован на управление AD users, computers, groups и массовые операции.

После него проект:

```
employees.csv
      ↓
PowerShell
      ↓
Active Directory
      ├── Create OU
      ├── Create User
      ├── Create Groups
      ├── Group Membership
      └── Report
```

Это уже непосредственно полезно для будущего **IAM/PAM/CyberArk**.

---

## 3. Bash scripting

**Jason Cannon — Bash Scripting and Shell Programming**

Открыть курс

Курс очень компактный — примерно **2 ч 33 мин**, обновлён в августе 2026.

Его тоже пройти полностью.

Например:

```
#!/bin/bash

for host in $(cat hosts.txt)
do
    ping -c 1 $host
done
```

Потом усложнить:

```
Bash
 ↓
check services
 ↓
read logs
 ↓
disk usage
 ↓
network status
 ↓
generate report
```

Это напрямую соответствует Bash scripting из программы STEP.

---

## 4. SQL

**Jose Portilla — The Complete SQL Bootcamp**

Открыть курс

Около **8 ч 51 мин**, PostgreSQL.

Но проходить весь до ноября необязательно.

Нам нужны:

```
SELECT
WHERE
ORDER BY
GROUP BY
JOIN

INSERT
UPDATE
DELETE
```

И обязательно связать с Python/Django.

Например:

```
Django
   ↓
PostgreSQL
   ↓
Security Events
   ↓
Python
   ↓
Network data
```

---

## 5. Git/GitHub

Здесь я бы поменял старый вариант на более свежий курс.

### The Complete Git & GitHub 2026 Course

Открыть на Udemy

Курс обновлён в июле 2026 и включает commits, branches, merges, pull requests, forks, webhooks и collaboration workflows.

Но поскольку сын уже coding делает, ему не требуется изучать Git 20–30 часов.

Достаточно:

```
clone
add
commit
push
pull
branch
merge
rebase basics
.gitignore
tags
PR
issues
GitHub Actions basics
```

И дальше **каждый project хранится в GitHub**.

---

# Как будет выглядеть Coding Stack

Я бы фактически строил вот это:

```
                  CODING
                     │
       ┌─────────────┼──────────────┐
       │             │              │
     Python      PowerShell        Bash
       │             │              │
 Network/API      Windows/AD      Linux
       │             │              │
       └─────────────┼──────────────┘
                     │
                    SQL
                     │
                 PostgreSQL
                     │
                   Django
                     │
                 REST API
                     │
                  GitHub
```

Это намного сильнее, чем просто «учить несколько programming languages».

---

# Что я НЕ предлагаю ему изучать сейчас

До 29 ноября я бы **не добавлял**:

- beginner Python;
- Java;
- C++;
- React;
- Node.js;
- ещё один Django course;
- algorithms mega-course;
- machine learning;
- linear regression;
- TensorFlow/PyTorch.

Не потому что они не нужны вообще.

Просто сейчас они размоют цель.

Наша текущая специализация:

> **Infrastructure + Networking + Cybersecurity + Automation.**

А программирование должно её усиливать.

---

# Что купить прямо сейчас

Если покупать всё не хочется, мой **минимальный mandatory package** такой:

### Infrastructure

**1. David Bombal — CCNA / Networking**  
Udemy

**2. Jason Cannon — Linux Administration Bootcamp**  
Udemy

**3. Kevin Brown — Windows Server 2025**  
Udemy

### Coding

**4. David Bombal — Python Network Programming**  
Udemy

**5. Kevin Brown — PowerShell for AD**  
Udemy

**6. Jason Cannon — Bash Scripting**  
Udemy

И только после них:

**7. Security+**  
Udemy

**8. AWS CLF-C02**  
Udemy

**9. SQL Bootcamp**  
Udemy

**10. Git/GitHub 2026**  
Udemy

### Мой порядок прохождения до 29 ноября

**Networking + Linux → Windows Server/AD → PowerShell → Python Network Automation → Bash → Security fundamentals → SQL → AWS fundamentals.**

Причём **Networking, Linux и coding идут параллельно**, а не последовательно.

## Так к началу STEP он уже будет практически знаком со всей базовой инфраструктурой, которую новая программа потом станет систематизировать и углублять. STEP сама включает Cisco CCNA Academy, NDG Linux Essentials, PCAP Python, Windows Server/Azure и AWS Academy, поэтому такой overlap здесь полезен — это будет deliberate second pass, а не пустое дублирование.

If you want, I can:

- Продолжи с подробным планом по Bash и PowerShell, включая примерные проекты для каждого
- Опиши практические проекты для Python Network Programming с разбивкой по этапам
- Расскажи, как оптимально интегрировать изучение SQL и Git/GitHub в общий учебный путь