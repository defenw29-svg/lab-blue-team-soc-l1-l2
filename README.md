# Equipo Azul - Laboratorio SOC L1/L2
> Uso ético y con permiso. Solo entorno autorizado.
> <img width="1920" height="1280" alt="818945419_1402019722987547_6346139476575699635_n" src="https://github.com/user-attachments/assets/bd3f4b73-47d8-4724-a3ce-18455f389473" />

## FASE 1: BUSQUEDA
```bash
sudo ss -tuln
sudo nmap -sV 127.0.0.1
apt list --upgradable
Get-HotFix | Sort-Object InstalledOn -Descending | Select -First 10
```

## FASE 2: ANALISIS
```bash
systemctl list-unit-files --type=service --state=enabled | grep -E "vsftpd|telnet|ftp"
Test-SmbServerConfiguration | Select EnableSMB1Protocol
sudo tshark -i eth0 -c 100
```

## FASE 3: DEFENSA Y REPARACION
```bash
sudo systemctl disable vsftpd --now
sudo ufw deny 21/tcp
sudo apt install --only-upgrade openssh-server
Set-SmbServerConfiguration -EnableSMB1Protocol $false -Force
```

## Resumen del laboratorio
Laboratorio de parcheo y endurecimiento para SOC L1/L2. Validacion de ciclo de vida de parches en Ubuntu y Windows, deshabilitado de SMBv1 y cierre de puertos (vsftpd/21) con UFW. Autor: Iván Ajenjo Morales | defensa29-svg | L1/L2 ITIL SecOps | Licencia MIT
