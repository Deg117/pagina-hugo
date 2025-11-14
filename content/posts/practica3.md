---
title: "Práctica 3"
date: 2025-01-01
draft: false
---

# UNIVERSIDAD AUTONOMA DE BAJA CALIFORNIA  
## FACULTAD DE INGENIERIA, ARQUITECTURA Y DISEÑO  

---

### **Materia:** Paradigmas de Programacion  

### **Alumno:** Brian De Jesus Gastelum Fierro  
  
### **Fecha:** 07/11/2025  

---

# Instalacion del entorno de desarrollo de Haskell
## 1. Introduccion

Los pasos que segui para instalar el entorno de desarrollo de Haskell en Windows utilizando GHCup.  

---

## 2. Instalacion del entorno de Haskell 

### Acceso a la pagina de descargas

1. Entre a la pagina oficial de Haskell.  
2. Ahi se indica que la forma recomendada de instalar todo el entorno es mediante GHCup, el instalador universal de Haskell.  
3. En esa pagina viene un enlace directo a **GHCup**, que abre la página oficial del instalador.  

### Uso de GHCup en Windows PowerShell 

1. Desde la página seleccione la instalación para Windows.  
2. Copie el comando para PowerShell que viene preparado para descargar y ejecutar el instalador.  
3. Abri PowerShell 
4. Pegue el comando y lo ejecute.  
5. Segui las instrucciones del instalador, aceptando las opciones por defecto.

Con esto se descargan e instalan todas las herramientas necesarias del entorno Haskell.

---

## 3. Verificacion de la instalacion

Despues de instalar GHCup, segui la guia Get Started de Haskell para comprobar que todo funcionaba.

### Verificar GHC
```bash
ghc --version
```

### Probar el interprete interactivo
```bash
ghc
```
Dentro del interprete probe desde vscode:
```haskell
2 + 3
```

###  Verificar Stack
```bash
stack --version
```

### Ejecutar un programa sencillo
Archivo `hello.hs`:
```haskell
main = do
  putStrLn "Hello, everybody!"
  putStrLn ("Please look at my favorite odd numbers: " ++ show (filter odd [10..20]))
```

Ejecutado con:
```bash
ghc hello.hs
```

---

## 7. Conclusiones

- GHCup simplifica la instalación del entorno de Haskell desde un solo comando.  
- La guía  Get Startedpermite verificar la instalación de manera rápida.  

---
[Portafolio](https://github.com/Deg117/Portafolio/tree/main/paradigmas_de_la_programacion)
