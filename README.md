# Actualizar ayuda de PowerShell
```powershell
update-help
```

# Obtener ayuda de un cmdlet
```powershell
Get-Help Get-Process
```

# CMDLET ejemplos
```powershell
get
set
remove
new
```
```powershell
get-localuser
get-date
clear-host
get-location
get-childitem
get-localgroup
get-netadapter
get-command # todos los cmdlets disponibles
get-command -verb get # todos los cmdlets que empiezan con get
get-command *localgroup* # todos los cmdlets que contienen localgroup
```

# modulos
```powershell
get-module
get-module -listavailable
Get-Command -Module  Microsoft.PowerShell.LocalAccounts # cmdlets de un modulo
import-module bitlocker -verbose # importar un modulo
get-module -name bitlocker
remove-module bitlocker # remover un modulo
```

# Ayudas

```powershell
get-help new-localuser  -examples
```
# Atajos

 - alias : get-alias
 - historial : get-history (h)
    - invoke-history numero de comando
    - r numero de comando
    - ctrl + r buscar comando dentro del historial
    - clear-history (clhy) limpiar historial
 - tabulador

# Gestión de archivos y carpetas

```powershell
Get-Location (pwd) # ubicación actual
Set-Location (cd) # cambiar de ubicación
Get-ChildItem (ls) # listar archivos y carpetas
Get-ChildItem -Path C:\ -Recurse # listar archivos y carpetas de forma recursiva

Get-ChildItem c:\ -Recurse -attributes hidden # listar archivos y carpetas ocultos
```

# Crear y eliminar archivos y carpetas

```powershell
new-item prueba1 -itemtype directory # crear carpeta
new-item prueba2 -itemtype file # crear archivo
rm prueba1 -recurse # eliminar carpeta
rm prueba2 # eliminar archivo
```

# Mover y copiar archivos y carpetas

```powershell
mv prueba1 prueba3 # mover carpeta
cp prueba2 prueba4 # copiar archivo
get-content prueba4 # ver contenido de archivo
rename-item prueba4 prueba5 # renombrar archivo
```

# Tuberias y redirecciones

```powershell
get-command  | measure-object # contar cmdlets
get-childitem - recurse | where-object {$.length -gt 100} # filtrar archivos por tamaño
get-childitem - recurse | where-object {$.length -gt 100} | sort-object -descending -property length # ordenar archivos por tamaño
get-nettcpconnection | where-object {$.state -eq "Established"} # filtrar conexiones establecidas
get-nettcpconnection | where-object {$.state -eq "Established"} | select-object -property localaddress, remoteaddress > prueba.txt # seleccionar propiedades
```

# Scripts

```powershell
Get-ExecutionPolicy # ver politica de ejecución
Set-ExecutionPolicy -ExecutionPolicy Unrestricted # cambiar politica de ejecución
```
ISE (Integrated Scripting Environment)

# Scripts 2

```powershell
# Esto es un comentario
<#
Esto es un comentario
de varias lineas
#>
```

# Variables y constantes

```powershell
$variable = "valor"
$variable.GetType() # tipo de variable
New-Variable -Name C -Value 300000 -Option Constant # constante
#Ejemplo de tipo de datos
Clear-Host
$nombre=Read-Host "Tu nombre"
[int]$edad=Read-Host "edad"
Write-Host "tu nombre es $nombre y tu edad es $edad"

# Ejemplo Concatenacion
Clear-Host
$nombre="Adrian"
$apellido="CE"
$nombrecompleto=$nombre + " " + $apellido
Write-Host tu nombre completo es : $nombrecompleto
```

# Estrucuturas condicionales,repetitivas y de control

```powershell
# ctrl j y buscar snippets
if ($x -gt $y)
{
    
}
elseif ($x -eq $y)
{
    
}
else
{
    
}
```
```powershell
#conexion a un servidor
clear-host
write-host "Conectando a un servidor"
$ip=Read-Host "Ingresa la ip del servidor"
#Test-Connection $ip -count 1 -quiet 
if (Test-Connection $ip -count 1 -quiet)
{
    write-host "Conexion exitosa"
}
else
{
    write-host "Conexion fallida"
}
```
```powershell
#ctrl j y buscar snippets while, do while,for,foreach
Clear-host
Write-host "Probando conexiones..."
$datos=Get-content C:\Users\Usuario\Downloads\servidores.txt
foreach ($i in $datos) {
$respuesta=Test-Connection $i -count 1 -Quiet
if ($respuesta -eq "true"){
Write-Host "$i--Conexion ok"
}else {
Write-Host "error en $i"
}
}
```

# Funciones

```powershell
#definición funciones
function conectividad ($datos){
foreach ($i in $datos) {
$respuesta=Test-Connection $i -count 1 -Quiet
if ($respuesta -eq "true"){
Write-Host "$i--Conexion ok"
}else {
Write-Host "error en $i"
}
}
}
 #inicio
Clear-host
Write-host "Probando conexiones..."
$datos=Get-content C:\Users\Usuario\Downloads\servidores.txt
conectividad $datos
```




