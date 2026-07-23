# Repurposed Laptop → Ubuntu Server with CasaOS

## Goal
I have an old Alienware laptop with a damaged display instead of tossing it, I converted it into a functioning home server to learn Linux server administration and self-hosting hands-on.

## What I did
- Wiped the existing Windows installation
- Installed **Ubuntu Server** as the base operating system
- Configured initial setup: user accounts, SSH access, basic networking
- Installed **CasaOS** as a management layer for self-hosted services and Docker containers
- Will be configuring **Pi-Hole**

## Why Ubuntu Server + CasaOS
Ubuntu Server gave me hands-on command-line Linux experience without a GUI to fall back on, while CasaOS provided an accessible way to manage Docker containers and services on top of that foundation. This lets me focus on learning both the underlying OS and practical self-hosting at the same time.

## Challenges encountered
- I needed to Keep the server running even with the lid closed. I went into the logind.conf and made edits to handle lid switch, handle lid switch external power, handle lid switch docked and lid switch ignore inhibited. Afterwards the laptop would not go to sleep even with the Lid closed, allowing me to use it through ssh on my main PC       

## Skills demonstrated
- Linux installation and initial server configuration
- Command-line administration (Ubuntu Server has no GUI)
- SSH setup and remote access
- Docker/container concepts via CasaOS
- Repurposing legacy hardware for practical use

## What's next
Planning to expand this server's role by adding a Windows Server VM for Active Directory labbing (see Project 3).
