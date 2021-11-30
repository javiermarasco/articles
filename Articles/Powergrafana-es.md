---
toc: true
layout: post
description: 'PowerGrafana, una herramienta para el manejo dinamico de paneles en Grafana'
categories: 
  - Grafana
  - PowerShell
  - Spanish
title: PowerGrafana
comments: true
published: false
---

## PowerGrafana, ¿qué es y para qué se utiliza?

### Comencemos con un poco de contexto y cómo comenzó todo

A veces sucede que tenemos que monitorear alguna aplicación, servicio o componente (entre otras cosas) y la herramienta que usamos o usa nuestra empresa es [Grafana](https://grafana.com), mientras que tenemos pocas cosas que monitorear no es un gran problema pero a medida que agregamos más elementos al Estos paneles se vuelven más complejos de mantener y / o configurar.

Imagine que tiene que implementar 20 aplicaciones, cada una ejecutándose en un [app service](https://azure.microsoft.com/en-us/services/app-service), por lo que seguramente querríamos monitorear el uso de CPU y memoria (para empezar) y seguramente algunas cosas más.
En este escenario simplista tenemos que configurar algunos paneles en un tablero y en cada panel poner las métricas que queremos mostrar (CPU y Memoria) en nuestro caso.

Esto suena simple pero en poco tiempo seguramente necesitaremos agregar otra métrica o desplegar una nueva versión de nuestra aplicación, peor aún, podríamos desplegar una nueva versión de algunos componentes y no de otros mientras tenemos que mantener todas las versiones (el el inicial más el nuevo) de cada componente, como puedes ver esto se vuelve cada vez más complejo de mostrar en Grafana, es mucho tiempo pinchando en la interfaz o (la alternativa) editando archivos json para pegarlos en el Grafana interfaz web y generar los cuadros de mando o paneles (créanme que es muy fácil cometer errores al editar esos archivos).
### La alternativa

PowerGrafana fue creado para resolver este problema (o intentar que sea más fácil de manejar) extrayendo toda la complejidad de lidiar con la interfaz web, los archivos json o incluso ingresando los nombres de los recursos a monitorear a mano.
Usando un módulo simple de PowerShell podemos iterar rápidamente a través de nuestros recursos y para cada uno de ellos crear un panel que muestre el uso de CPU y memoria.

Cada comando posee su ayuda, la cual pueden consultar ejecutando:  
```powershell
PS> Get-Help New-GrafanaDashboard 

NAME
    New-GrafanaDashboard
    
SYNOPSIS
    Creates a dashboard in Grafana
    
    
SYNTAX
    New-GrafanaDashboard [-DashboardName] <Object> [[-Tags] <String[]>] [<CommonParameters>]
    
    
DESCRIPTION
    This cmdlet will create an empty dashboard in Grafana that can be used as starting point to create your grafana monitoring.
    
EXAMPLE
    New-GrafanaDashboard -DashboardName "My new dashboard" -Tags @('Web','Azure','Production')

RELATED LINKS

REMARKS
    To see the examples, type: "Get-Help New-GrafanaDashboard -Examples"
    For more information, type: "Get-Help New-GrafanaDashboard -Detailed"
    For technical information, type: "Get-Help New-GrafanaDashboard -Full"
    For online help, type: "Get-Help New-GrafanaDashboard -Online"
```


## Referencias

- [Link a PowerGrafana en GitHub](https://github.com/javiermarasco/PowerGrafana)  
- [Link a PowerGrafana en la galería de PowerShell](https://www.powershellgallery.com/packages/PowerGrafana/0.1.0)
