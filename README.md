# Mini projet - Windows Listening Ports Audit

Suite à l'achat d'un nouveau PC j'ai refais un auto diagnostique de mes ports.

J'ai fait ce mini projet qui reprend la procédure que j'ai utilisé pour faire l'audit de mes ports, et identifier
quoi sécuriser.
Les ports sont fictifs.

EN

Identify listening TCP ports on a Windows workstation and provide security recommendations.

Ports are not real ones.

## Environment

- Windows 11
- PowerShell
- Git

## Structure

scripts/
results/
docs/

## Execution

powershell
.\scripts\audit_ports.ps1
Résultat / Output
docs/recommandations.md

Le script génère un fichier CSV contenant les ports d’écoute TCP.

EN

The script generates a CSV file containing listening TCP ports.

# instructions

# Commandes

## 1. Créer le projet

Ouvre PowerShell :

mkdir windows-listening-ports-audit  

cd windows-listening-ports-audit  


mkdir scripts  

mkdir results  

mkdir docs

New-Item README.md
New-Item scripts\audit_ports.ps1
New-Item docs\recommendations.md

##2. Créer le script d'audit
Ouvre : notepad scripts\audit_ports.ps1

Colle :

Get-NetTCPConnection -State Listen |
Select-Object LocalAddress, LocalPort |
Sort-Object LocalPort |
Export-Csv ".\results\ports.csv" -NoTypeInformation
Enregistre.

3. Exécuter le script
Si l'exécution est bloquée :

Set-ExecutionPolicy -Scope Process Bypass

Puis :

.\scripts\audit_ports.ps1

Le fichier :

results\ports.csv

sera généré.

## 4. Vérifier les résultats
Afficher le contenu :

Import-Csv .\results\ports.csv

Ou :
notepad .\results\ports.csv

## 5. Identifier les services associés aux ports
Lister les ports :

Get-NetTCPConnection -State Listen |
Sort-Object LocalPort |
Format-Table LocalAddress,LocalPort
Exemple :

135  -> RPC
445  -> SMB
3389 -> RDP
80   -> HTTP
443  -> HTTPS

enfin, applique les recommandations conseillées

# Compétences / Skills

Administration de Windows
PowerShell
Sécurité de l’infrastructure
Audit de sécurité
Git/GitHub

EN
Windows Administration
PowerShell
Infrastructure Security
Security Auditing
Git/GitHub



