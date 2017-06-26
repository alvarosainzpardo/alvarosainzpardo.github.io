# Guia del comando _robocopy_

---

## Enlaces, documentación

---

## Comando para hacer backup de los contenidos de un directorio

´´´cmd
C:\>robocopy <origen> <destino> /mir /sl /xjd /xa:sh /xd "AppData" /xf *.inf /copy:dat /dcopy:t /r:0 /w:1 /mt /ndl /tee /log+:\robocopy.log
´´´

### Explicación de las opciones

* **/mir**: realiza
* **/sl**:  
