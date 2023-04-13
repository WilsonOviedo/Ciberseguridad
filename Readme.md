# escaneo de IPs
```
arp-scan -I ens33 --localnet
```

# Listar dispositivos con su MAC
```
macchanger -l
```
# Listar dispositivos con su MAC y filtrar
```
macchanger -l | grep -i vmware
```

# Verificar si llega conectividad directa
```
ping -c 1 192.168.111.8
```
# Escanear puertos sin resolucion DNS y exportar los datos en fromato Grep
```
nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn 192.168.111.45 -oG allPorts 
```
# Visualizar archivo
```
cat allPorts
```

# script bash extraccion de puertos
```

# Extract nmap information
function extractPorts(){
    ports="$(cat $1 | grep -oP '\d{1,5}/open' | awk '{print $1}' FS='/' | xargs | tr ' ' ',')"
    ip_address="$(cat $1 | grep -oP 'Host: .* \(\)' | head -n 1 | awk '{pint $2}')"
    echo -e "\n[*] Extracting information...\n" > extractPorts.tmp
    echo -e "\t[*] IP Address: $ip_address"  >> extractPorts.tmp
    echo -e "\t[*] Open ports: $ports\n"  >> extractPorts.tmp
    echo $ports | tr -d '\n' | xclip -sel clip
    echo -e "[*] Ports copied to clipboard\n"  >> extractPorts.tmp
    cat extractPorts.tmp 
    rm extractPorts.tmp
}

```

# Lanzar scripts de reconocimiento y deteccion de version y servicios para los puertos especificados y exportar en texto al archivo targeted
```
nmap -sC -sV -p22,80 192.168.111.45 -oN targeted
```
# Mostrar tecnologias de una web
```
whatweb http://192.168.111.45
```
# Inyeccion sql de prueba para login
```
admin' or 1=1-- -
admin' and sleep(5)-- -

```

