## 🔍 Escaneo Ping Simple (`-sn`)

### Comando ejecutado:

```bash
nmap -sn 1.1.1.1
```

### 📖 Descripción:

La opción `-sn` (anteriormente conocida como `-sP`) en **Nmap** realiza un escaneo **ping sweep**, es decir, un **escaneo sin puertos**. Su propósito es simplemente **determinar si el host está activo** (encendido y accesible en la red), **sin escanear puertos** ni servicios.

Este comando es útil cuando quieres saber si una dirección IP específica o un rango de IPs están en línea (por ejemplo, para descubrir dispositivos activos en una red local).

---

### 🧾 Resultado del escaneo:

```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-07-10 10:15 CST
Nmap scan report for 1.1.1.1
Host is up (0.00082s latency).
Nmap done: 1 IP address (1 host up) scanned in 0.00 seconds
```

---

### 📌 Análisis del resultado:

![Resultado de nmap -sn](/Imagenes/nmap_sn_result.png)


* **`Starting Nmap 7.94SVN (...)`**
  Indica la versión de Nmap utilizada y la fecha/hora local de inicio del escaneo.

* **`Nmap scan report for 1.1.1.1`**
  Especifica la dirección IP objetivo que se escaneó.

* **`Host is up (0.00082s latency).`**
  El host está **activo y responde a solicitudes ICMP (ping)**.
  La **latencia** (tiempo de respuesta) es muy baja: 0.00082 segundos, lo que sugiere que el host está en una red cercana (probablemente una red local).

* **`Nmap done: 1 IP address (1 host up) scanned in 0.00 seconds`**
  Confirma que se escaneó una dirección IP, y que 1 host está activo. El escaneo fue muy rápido (menos de un segundo).

---

### 🧠 Nota técnica:

Este tipo de escaneo **no requiere privilegios de administrador**, pero en algunos sistemas operativos (como Linux), **puede necesitar permisos elevados para enviar paquetes ICMP**. En ese caso, se recomienda ejecutarlo como superusuario (por ejemplo, usando `sudo`).

---

### 🛡️ Uso común:

* Descubrir hosts activos en una red.
* Verificar si un servidor o dispositivo está encendido.
* Realizar inventarios de red de forma no intrusiva.

---

Perfecto. Aquí tienes una sección **Markdown completa y explicada** para incluir en tu manual de GitHub sobre el uso de `nmap -p` para escanear puertos específicos:

---

## 🔍 Escaneo de Puertos Específicos (`-p`)

### 📦 Comando ejecutado:

```bash
nmap -p22,80,8080,443,666 1.1.1.1
```

### 🎯 Descripción:

La opción `-p` permite a Nmap escanear **puertos específicos**, en lugar de hacer un escaneo completo de los 1000 puertos más comunes. En este ejemplo se escanean los siguientes puertos TCP:

* `22` → SSH
* `80` → HTTP
* `443` → HTTPS
* `8080` → HTTP alternativo o proxy
* `666` → Doom (un servicio poco común, a veces asociado con malware o software personalizado, en mi caso suele ser un balanceador de red)

---

### 🧾 Resultado del escaneo:

```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-07-10 10:41 CST
Nmap scan report for 1.1.1.1.
Host is up (0.00068s latency).

PORT     STATE  SERVICE
22/tcp   open   ssh
80/tcp   open   http
443/tcp  open   https
666/tcp  closed doom
8080/tcp closed http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.03 seconds
```

---

### 🖼️ Captura del resultado:

![Resultado de nmap -p](/Imagenes/escaneo_puerto.png)

(Asegúrate de que la imagen esté subida con ese nombre en la carpeta `Imagenes/`)

---

### 📌 Análisis del resultado:

* **`Host is up`**
  El host está encendido y responde.

* **`PORT     STATE  SERVICE`**
  Lista los puertos analizados, su estado y el servicio asociado según la base de datos de Nmap.

#### ✅ Puertos abiertos:

* **22/tcp → `open` → ssh**: El sistema permite conexiones remotas por SSH.
* **80/tcp → `open` → http**: Hay un servidor web escuchando en HTTP.
* **443/tcp → `open` → https**: El servidor web tiene HTTPS activo.

#### ❌ Puertos cerrados:

* **666/tcp → `closed` → doom**: No hay servicio escuchando en este puerto. Aunque se llama "doom", normalmente es usado por programas personalizados o pruebas.
* **8080/tcp → `closed` → http-proxy**: Podría indicar que el puerto estuvo activo anteriormente o está filtrado/cerrado actualmente.

---

### 🧠 Nota:

Escanear puertos de forma dirigida es útil para auditorías rápidas, para verificar servicios conocidos o sospechosos sin escanear toda la máquina.

---

