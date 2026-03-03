# 🇧🇷 Português Brasileiro

# Monitor Virtual no Windows 10/11 --- Tutorial Completo (Inicialização Automática)

## Visão Geral

Este guia ensina como instalar e ativar automaticamente um **monitor
virtual** no Windows 10/11 usando o driver IDD da Amyuni.

Ideal para acesso remoto (AnyDesk) e notebooks com tampa fechada.

------------------------------------------------------------------------

## Por que usar monitor virtual?

Sem monitor conectado o Windows pode:

-   Desativar aceleração GPU
-   Reduzir resolução
-   Mostrar tela preta no acesso remoto

O monitor virtual mantém o pipeline gráfico ativo.

------------------------------------------------------------------------

## Requisitos

-   Windows 10 ou superior
-   Permissões administrativas
-   Driver virtual Amyuni

------------------------------------------------------------------------

## Passo 1 --- Baixar Driver

https://github.com/dbyte-suporte/Monitor-Virtual-no-Windows-10-11/raw/refs/heads/main/usbmmidd_v2.zip

Extraia para:

    C:\temp\usbmmidd_v2

------------------------------------------------------------------------

## Passo 2 --- Abrir Prompt como Administrador

Menu Iniciar → Prompt de Comando → Executar como administrador.

------------------------------------------------------------------------

## Passo 3 --- Instalar Driver

    cd C:\temp\usbmmidd_v2
    deviceinstaller64 install usbmmidd.inf usbmmidd

(Use `deviceinstaller` em sistemas 32‑bits.)

------------------------------------------------------------------------

## Passo 4 --- Ativar Monitor Virtual

    deviceinstaller64 enableidd 1

Execute até quatro vezes para múltiplas telas.

------------------------------------------------------------------------

## Passo 5 --- Configurar Tela

Configurações → Sistema → Vídeo.

Resolução padrão: **1920×1080**.

------------------------------------------------------------------------

# Ativação Automática Após Reiniciar (IMPORTANTE)

O monitor virtual não permanece ativo após reboot.\
Precisamos automatizar.

------------------------------------------------------------------------

## Método 1 --- Agendador de Tarefas (RECOMENDADO)

### Abrir

    Win + R
    taskschd.msc

### Criar Tarefa

Clique **Criar Tarefa**.

### Aba Geral

-   Nome: `Enable Virtual Monitor`
-   ✔ Executar estando usuário conectado ou não
-   ✔ Executar com privilégios mais altos

### Aba Disparadores

Novo → **Ao iniciar o sistema**

### Aba Ações

Programa:

    C:\temp\usbmmidd_v2\deviceinstaller64.exe

Argumentos:

    enableidd 1

Iniciar em:

    C:\temp\usbmmidd_v2

### Aba Condições

Desmarque:

-   Iniciar somente se conectado à energia

### Aba Configurações

Ative:

-   Executar assim que possível após iniciar

Salvar e inserir senha.

✅ Monitor virtual será ativado automaticamente.

------------------------------------------------------------------------

## Método 2 --- Script na Inicialização

Crie:

`enable_virtual_monitor.bat`

    @echo off
    cd C:\temp\usbmmidd_v2
    deviceinstaller64 enableidd 1

Execute:

    Win + R → shell:startup

Coloque o arquivo nessa pasta.

⚠ Funciona apenas após login.

------------------------------------------------------------------------

## Configuração da Tampa do Notebook

Painel de Controle → Opções de Energia → Escolher função ao fechar a
tampa.

Configure:
```
  Ação         Configuração
  ------------ ----------------
  Na bateria   Não fazer nada
  Conectado    Não fazer nada
```
------------------------------------------------------------------------

## Desativar Monitor Virtual

    deviceinstaller64 enableidd 0

------------------------------------------------------------------------

## Remover Driver

    deviceinstaller64 stop usbmmidd
    deviceinstaller64 remove usbmmidd

------------------------------------------------------------------------

## Solução de Problemas

### Tela preta no AnyDesk

Reinicie após instalação inicial.

### Programa abriu em tela invisível

Use:

    Win + Shift + Setas

### Tarefa não executa

Verifique: - privilégios elevados - caminho correto - disparador "Ao
iniciar"

------------------------------------------------------------------------

## Segurança

-   Driver assinado digitalmente.
-   Baixe apenas do site oficial.

------------------------------------------------------------------------

## Licença

Siga os termos da Amyuni Technologies.

------------------------------------------------------------------------
# 🇺🇸 English

# Virtual Display on Windows 10/11 --- Complete Tutorial (Persistent Setup)

## Overview

This guide explains how to install and automatically enable a **virtual
monitor** on Windows 10/11 using the Amyuni USB Mobile Monitor Indirect
Display Driver (IDD).

It is ideal for **remote access (AnyDesk, Parsec, Remote Desktop)** and
headless laptops where the lid remains closed.

------------------------------------------------------------------------

## Why Use a Virtual Display?

Without a connected monitor, Windows may:

-   Disable GPU acceleration
-   Lower resolution
-   Cause black screens in remote software

A virtual display keeps the graphics pipeline active.

------------------------------------------------------------------------

## Requirements

-   Windows 10 or newer
-   Administrator privileges
-   Amyuni virtual display driver

------------------------------------------------------------------------

## Step 1 --- Download Driver

Download:

https://github.com/dbyte-suporte/Monitor-Virtual-no-Windows-10-11/raw/refs/heads/main/usbmmidd_v2.zip

Extract to:

    C:\temp\usbmmidd_v2

------------------------------------------------------------------------

## Step 2 --- Open Administrator Command Prompt

1.  Start Menu
2.  Search **Command Prompt**
3.  Right-click → **Run as Administrator**

------------------------------------------------------------------------

## Step 3 --- Install Driver

    cd C:\temp\usbmmidd_v2
    deviceinstaller64 install usbmmidd.inf usbmmidd

(32‑bit systems use `deviceinstaller`.)

------------------------------------------------------------------------

## Step 4 --- Enable Virtual Monitor

    deviceinstaller64 enableidd 1

Run up to four times for multiple displays.

------------------------------------------------------------------------

## Step 5 --- Configure Display

Open:

Settings → System → Display

You may extend desktop, change resolution, or reposition monitors.

Default resolution: **1920×1080**.

------------------------------------------------------------------------

# Automatic Activation After Reboot (IMPORTANT)

The virtual monitor does NOT persist after restart.\
We must automate activation.

------------------------------------------------------------------------

## Method 1 --- Task Scheduler (Recommended)

### Open Task Scheduler

Press:

    Win + R
    taskschd.msc

### Create Task

Click **Create Task** (not Basic Task).

### General Tab

-   Name: `Enable Virtual Monitor`
-   ✔ Run whether user is logged on or not
-   ✔ Run with highest privileges
-   Configure for Windows 10/11

### Triggers Tab

New → Begin task: **At startup**

### Actions Tab

Program/script:

    C:\temp\usbmmidd_v2\deviceinstaller64.exe

Arguments:

    enableidd 1

Start in:

    C:\temp\usbmmidd_v2

### Conditions Tab

Uncheck:

-   Start only if on AC power

### Settings Tab

Enable:

-   Run task as soon as possible after startup

Save and enter your Windows password.

✅ Virtual monitor now starts automatically.

------------------------------------------------------------------------

## Method 2 --- Startup Script (Simpler)

Create:

`enable_virtual_monitor.bat`

    @echo off
    cd C:\temp\usbmmidd_v2
    deviceinstaller64 enableidd 1

Open:

    Win + R → shell:startup

Place the file there.

⚠ Runs only after login.

------------------------------------------------------------------------

## Laptop Lid Configuration (Required)

Control Panel → Power Options → Choose what closing the lid does

Set:
```
  Action       Setting
  ------------ ------------
  On battery   Do nothing
  Plugged in   Do nothing
```
------------------------------------------------------------------------

## Disable Virtual Monitor

    deviceinstaller64 enableidd 0

------------------------------------------------------------------------

## Remove Driver

    deviceinstaller64 stop usbmmidd
    deviceinstaller64 remove usbmmidd

Or uninstall via Device Manager.

------------------------------------------------------------------------

## Troubleshooting

### Black screen in AnyDesk

Restart after first installation.

### Apps open on invisible display

Use:

    Win + Shift + Arrow Keys

### Task not running

Ensure: - Highest privileges enabled - Correct folder path - Task
trigger = At startup

------------------------------------------------------------------------

## Security Notes

-   Driver is digitally signed.
-   Download only from official website.
-   Requires administrator privileges.

------------------------------------------------------------------------

## License

Follow Amyuni Technologies license terms.
