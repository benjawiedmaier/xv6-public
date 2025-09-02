1. Hice un fork de https://github.com/mit-pdos/xv6-public.git a mi repositorio propio
2. cree una rama llamado grupoG-t0 para la tarea 0
3. clone el repositorio en mi computador
4. partí a instalar las dependencias para ejecutar xv6
- wsl --install
- inicio wsl, wsl -d Ubuntu
- actualizo paquetes:
-- sudo apt update
-- sudo apt upgrade -y
- Instala las herramientas necesarias para xv6
-- sudo apt install -y build-essential gcc-multilib gdb qemu-system-x86 git
5. abro el repositorio, cd xv6-public
6. trato de compilar y lanzar xv6, make qemu-nox
7. me arroja error: infinite recursion detected
8. agrege una cflag a el makefile (para que no afecte ese error): -Wno-error=infinite-recursion
9. me arrojo error de que sign.pl no estaba, le di permisos de ejecución. sudo chmod +x sign.pl
10. me arrojo el error: array subscript, agrege la siguiente cflag en el makefile, -Wno-error=array-bounds
11. me arrojo un error el sign.pl, pero encontre el origen de ese error:
- benja@bwiedmaier-HP:/mnt/c/Users/Benja/desktop/SO/xv6-public$ head -n1 -v sign.pl | cat -A 
- ==> sign.pl <==$ 
- #!/usr/bin/perl^M$
12. lo arregle usando, sed -i 's/\r$//' sign.pl
13. reconstrui 
- make clean
- make    
14. compile con make qemu-nox y funciono.
