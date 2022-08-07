# AZURE - IOT - RASPBERRY
**En esta practica aprenderas a conectar un recurso de IOT de Azure con un Raspberry simulador (Calculador de Temperatura) Desde LOCAL y en AZURE**

## Requisitos
- Tener una suscripcion en Azure
- Tener una conexion a internet
- Tener un navegador instalado (Brave,Google,Firefox, etc)
- Tener un raspberry o en su caso un simulador, te dejo este por [aqui](https://azure-samples.github.io/raspberry-pi-web-simulator/#getstarted)
- Ocuparas este link para poder hacer la conexion por [aqui](https://github.com/Azure-Samples/web-apps-node-iot-hub-data-visualization)

-------------------------

## TUTORIAL

### **DESDE LOCAL**

**1.-Primero nos vamos al Portal de Azure y buscamos en market o en el buscador IOT HUB**

![imagen 1](imagenes/1.png)

**2.-Le damos lo minimo para crear un recurso en azure**

![imagen 2](imagenes/2.png)

**3.-Nos adentramos adentro del recurso y nos vamos a devices**

![imagen 3](imagenes/3.png)

**4-.Le damos esta configuracion, le damos un id y le damos a save**

![imagen 4](imagenes/4.png)

**5.-Nos vamos a nuestro device ID**

![imagen 5](imagenes/5.png)

**6.-Y aqui tendríamos las credenciales que utilizaremos mas adelante (copiamos Primary Connection String)**

![imagen 6](imagenes/6.png)

**7.-Nos vamos a nuestro Raspberry y la pegamos (en este caso como es un simulador la pegamos donde dice cost ConnectionString = "aqui pegamos" y le damos en run**

![imagen 7](imagenes/7.png)

**8.-Una ves corrido el programa(para prender el rasperry) nos mostrara el sig mensaje: (si te muestra lo mismo o similar vas en buen camino)**

![imagen 8](imagenes/8.png)


**9.-Ahora nos vamos a este respositorio de [github](https://github.com/Azure-Samples/web-apps-node-iot-hub-data-visualization) descargamos el repositorio y abrimos Visual studio code desde la carpeta del repositorio que descargamos**

![imagen 9](imagenes/9.png)
![imagen 9-1](imagenes/10.png)


**10.-Nos vamos a un una terminal (Por ejemplo desde visual studio code agregamos una terminal) y nos logeamos con el sig comando "az login" y le damos nuestras credenciales (recordando que estamos dentro de la carpeta que descargamos anteriormente)**

![imagen 11](imagenes/11.png)

**11.- Conectamos nuestro iot hub con el sig comando "az iot connection-string show --hub name "NOMBRE DEL RECURSO IOT" --policy-name service (y nos preguntara si lo queremos hacer y le tecleamos Y)**

![imagen 12](imagenes/12.png)

**12.-Esperamos a que se instale todo**

![imagen 13](imagenes/13.png)

**13.-Una vez instalado nos aparecera algo similar a esto (es importante que el HostName y el consumer group lo copies en algun lado ya que lo utilizaremos mas adelante)**

![imagen 14](imagenes/14.png)
![imagen 15](imagenes/15.png)

**14.-Ahora tecleamos npm install desde nuestra terminal (en este caso se abrio una terminal en cmd ya que no lo permitia si usted se lo permite desde visual studio code adelante si no abrá un cmd desde la carpeta donde estabamos y tecle lo anteriormente dicho "npm install") y esperamos a que se instale node**

![imagen 16](imagenes/16.png)

**15.- Una vez que se termine de instalar le aparecera los sig:**

![imagen 17](imagenes/17.png)

**16.-¿Te acuerdas del paso num 13 donde copiamos el HostName y el consumergroup? Ahora lo necesitaremos,primero: nos vamos al archivo server.js y copiamos esto "IotHubConnectionString" (Del repositorio descargardo, recuerda que todo lo estamos haciendo desde ahi dentro)**

![imagen 18](imagenes/18.png)

**17.-Ahora nos vamos a nuestra terminal de cmd dentro del repositorio escribimos: "set" espacio "IotHubConnectionString" "=" "HostName" y quedaria de la sig. manera: (Recuerda que el HostName lo sacamos en el paso 13)**

![imagen 19](imagenes/19.png)

**18.-Nos regreamos al archivo server.js y copiamos ahora "EventHubConsumerGroup"**

![imagen 20](imagenes/20.png)

**19.-Nos regresamos a la terminal de cmd y tecleamos: "set" espacio "EventHubConsumerGroup" "=" "consumergroup"(Quedaria como en la imagen). Ahora lo siguiente: tecleamos "npm start" y aparecería como en la imagen (si te aparece Listening 3000 significa que funciono!)**

![imagen 21](imagenes/21.png)

**20.-Aqui puedes ver la imagen completa donde aparecen los datos del Raspberry**

![imagen 22](imagenes/22.png)

**21.- Y finalmente si nos vamos a un navegador y tecleamos localhost:3000 aparecerá nuestro raspberry calculando la temperatura!**

![imagen 23](imagenes/23.png)

### **DESDE AZURE**

**22.-Creamos un recurso de App Service desde el portal de Azure (Le damos lo minimo para crear un recurso) Puedes usar esta configuracion si la deseas, puede cambiar para los requerimientos que ocupes. Le das en revisar y en crear.**

![imagen 24](imagenes/24.png)

**23.-Nos vamos al recurso**

![imagen 25](imagenes/25.png)

**24.-Nos dirigimos en la parte izquierda y seleccionamos TSL/SSL settings y le damos en on donde viene "HTTPS ONLY"**

![imagen 26](imagenes/26.png)

**25.-Nos vamos a configuration y activamos lo sig:**

![imagen 27](imagenes/27.png)

**26.-Ahora nos dirigimos a Deployment Center en FTPS credentials y le damos un username, password y confiramos el password, despues lo guardamos**

![imagen 28](imagenes/28.png)

**27.-Ahora nos Settings y conectamos nuestro git**

![imagen 29](imagenes/29.png)

**28.-Abrimos una terminal y tecleamos "git remote add webapp link"(El link esta en los requerimientos) le damos enter y despues "git remote -v" le damos enter**

![imagen 30](imagenes/30.png)

**29.-Ahora tecleamos "git branch * master" y le damos enter**

![imagen 31](imagenes/31.png)

**30.-Ahora tecleamos: "git push webapp master:master"**

![imagen 32](imagenes/32.png)

**31.-Nos dirigmos al recurso y nos vamos a configuration, damos en Application settings, New application settings**

![imagen 33](imagenes/33.png)

**32.-Le damos un nombre como "IotHubConnectionString" el Value como lo siguiente (recuerda que esto lo sacas haciendo el paso num 13)**

![imagen 34](imagenes/34.png)

**33.-Le damos lo mismo con el consumergroup**

![imagen 35](imagenes/35.png)

**34.-Ahora nos vamos al recurso, en overview y entramos al url**

![imagen 36](imagenes/36.png)

**35.-y como podrás ver si entramos a la url ya esta en funcionamiento!**

![imagen 37](imagenes/37.png)