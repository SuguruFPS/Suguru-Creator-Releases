# Suguru Creator - telechargements

Ce depot ne contient **que les versions installables** (pas le code source).

## Installation (PowerShell)

```powershell
[Net.ServicePointManager]::SecurityProtocol = 'Tls12'
iwr https://github.com/SuguruFPS/suguru-creator-releases/releases/latest/download/install.ps1 -OutFile $env:TEMP\suguru-install.ps1
powershell -NoProfile -ExecutionPolicy Bypass -File "$env:TEMP\suguru-install.ps1" -Dir "D:\Suguru Creator"
```

Le script verifie l'empreinte SHA-256 de l'archive, installe dans le dossier choisi (donnees dans `<dossier>\data`),
installe WebView2 s'il manque et cree `Lancer Suguru Creator.bat`.

Installation manuelle : telecharge `suguru-creator-windows-x64.zip`, verifie son SHA-256 avec `SHA256SUMS.txt`, extrais-le.
Versions non signees : SmartScreen peut avertir.

## Variante dans cmd.exe (curl.exe est livre avec Windows)

```bat
curl.exe -L --fail -o "%TEMP%\suguru-install.ps1" https://github.com/SuguruFPS/Suguru-Creator-Releases/releases/latest/download/install.ps1 && powershell -NoProfile -ExecutionPolicy Bypass -File "%TEMP%\suguru-install.ps1" -Dir "D:\Suguru Creator" -Repo SuguruFPS/Suguru-Creator-Releases
```

## Si le telechargement echoue (reseau, antivirus, release non publiee)

Telecharge a la main (navigateur) `suguru-creator-windows-x64.zip`, `SHA256SUMS.txt` et `install.ps1` dans un meme dossier
(ex. `D:\Suguru Creator\telechargements`), puis :

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File "D:\Suguru Creator\telechargements\install.ps1" -Dir "D:\Suguru Creator" -LocalDir "D:\Suguru Creator\telechargements"
```
