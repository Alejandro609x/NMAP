## 🔍 Escaneo Ping Simple con Nmap (`-sn`)

### Comando ejecutado:

```bash
nmap -sn 10.1.195.79
```

### 📖 Descripción:

La opción `-sn` (anteriormente conocida como `-sP`) en **Nmap** realiza un escaneo **ping sweep**, es decir, un **escaneo sin puertos**. Su propósito es simplemente **determinar si el host está activo** (encendido y accesible en la red), **sin escanear puertos** ni servicios.

Este comando es útil cuando quieres saber si una dirección IP específica o un rango de IPs están en línea (por ejemplo, para descubrir dispositivos activos en una red local).

---

### 🧾 Resultado del escaneo:

```
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-07-10 10:15 CST
Nmap scan report for 10.1.195.79
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
