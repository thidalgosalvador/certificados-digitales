Estudio SSL/TLS en Diputaciones Provinciales
=========================================

### Introducción
La entrada en vigor de las Leyes 39/2015 y 40/2015 recogen aspectos significativos de la relación electrónica entre las Administraciones y los ciudadanos como el derecho y obligación de relacionarse electrónicamente con las AA.PP, las notificaciones electrónicas o el registros electrónicos de apoderamientos, entre otros. Así mismo, el artículo 36 LRBRL indica que son competencias propias de las Diputaciones Provinciales la prestación de los servicios de administración electrónica y la contratación centralizada en los municipios con población inferior a 20.000 habitantes. Es por ello, que los sistemas informáticos que ofrecen los servicios de sede electrónica ofrezcan la seguridad adecuada.

Este estudio presenta un estado básico de la seguridad de las sedes electrónicas de las diferentes Diputaciones Provinciales de España centrado en configuración de protocolos de comunicaciones, cifrados utilizados y otros parámetros. Se plantea desde un punto de vista general, meramente estadístico, sin entrar en el detalle de configuraciones particulares. 

Se muestran los datos de diputaciones provinciales en las provincias de las comunidades autónomas de Galicia, Aragón, Cataluña, Comunidad Valenciana, Castilla y León, Castilla-La Mancha, Extremadura y Andalucía. Así mismo, se han incluido los datos de las diputaciones forales del País Vasco. Para un estudio futuro se considerarán los cabildos (Comunidad autónoma de Canarias) y los Consejos Insulares (Comunidad Islas Baleares).

| COMUNIDAD AUTÓNOMA   | Nº Diputaciones |
|---------------------:|:---------------:|
| ANDALUCIA            | 8               |
| ARAGON               | 3               |
| CASTILLA Y LEON      | 9               |
| CASTILLA\-LA MANCHA  | 5               |
| CATALUÑA             | 4               |
| COMUNIDAD VALENCIANA | 3               |
| EXTREMADURA          | 2               |
| GALICIA              | 4               |
| PAIS VASCO           | 3               |

Otras comunidades autónomas uniprovinciales como, el Principado de Asturias, Cantabria, Comunidad de Madrid, Región de Murcia, Navarra o La Rioja, no están representadas en el estudio dado que no poseen Diputación Provincial. Del mismo modo, las ciudades autónomas de Ceuta y Melilla, donde las competencias propias de las Diputaciones son asumidas por el propio gobierno y asamblea autonómica tampoco aparecen en el estudio.

### Sedes electrónicas bajo HTTPS
Como era de esperar, en un entorno sensible como las sedes electrónicas de las Diputaciones Provinciales, la totalidad de las mismas ofrecen sus servicios bajo el protocolo HTTPS.

| Uso de HTTPS   | Sedes | %      |
|---------------:|:-----:|-------:|
| Configurado    | 41    | 100,0% |
| No configurado | 0     | 0,0%   |

Sin embargo, destaca que dos sedes (4,9%) no redirección automáticamente de HTTP a HTTPS.

| Redirección | Nº de Sedes | %     |
|-----------:|:-----------:|------:|
| Código 200  | 2           | 4,9%  |
| Código 30x  | 39          | 95,1% |

Así mismo, llama la atención la baja implantación de HSTS. HTTP Strict Transport Security (HSTS) es una política de seguridad web que permite a un servidor web imponer/forzar el uso de TLS para los User-Agent compatibles, como -por ejemplo- un navegador web. El HSTS permite una implementación más efectiva del TLS asegurando que toda la comunicación se lleve a cabo sobre una capa de transporte segura en el lado del cliente. En particular, el HSTS mitiga las variantes de los ataques de "hombre en el medio" (MiTM) en los que el TLS puede ser eliminado de las comunicaciones con un servidor, dejando al usuario vulnerable a mayores riesgos.

| HSTS           | Sedes | %     |
|---------------:|:-----:|------:|
| Configurado    | 3     | 7,3%  |
| No configurado | 38    | 92,7% |

Si bien, la configuración de este mecanismo de seguridad en la parte del servidor web no es complejo, tan solo tres sedes electrónicas lo tienen implementado a la hora de realizar el estudio.

### Server Signature
La firma del servidor (en inglés, Server Signature) es la identidad pública del servidor web. Contiene información sensible que -en general- como buena práctica de seguridad se suele desactivar para evitar la divulgación de las versiones de software utilizadas. Nueve de las sedes estudiadas no han devuelto ningún dato mientras que el resto mostraba la versión y software utilizado para servir los contenidos. Destaca el uso de servidores web Apache, en su rama 2.2 (6 sedes) y 2.4 (7 sedes), y del servidor web nginx (6 sedes). Así mismo, tres sedes todavía utilizan servidores web bajo Microsoft-IIS/7.5, ofrecidos en servidores con sistema operativo Windows Server 2008 R2, fuera de soporte desde enero de 2020.

| Aplicación          | FQDN |
|--------------------:|:----:|
| No Especificado     | 9    |
| Apache/2\.4         | 7    |
| nginx               | 6    |
| Apache/2\.2         | 6    |
| Apache\-Coyote/1\.1 | 5    |
| Microsoft\-IIS/7\.5 | 3    |
| Microsoft\-IIS/8\.5 | 3    |
| BigIP               | 2    |

### Certificados digitales

#### Entidades Emisoras (CA’s)

El prestador de Servicios de Confianza (PSC) Camerfirma, del grupo italiano Inforcert, con 16 sedes electrónicas (39%) ocupa un destacado primer puesto en certificados emitidos para Diputaciones Provinciales. Destaca el PSC vasco, Izenpe S.A., un proyecto de Autoridad Certificadora impulsado por el Gobierno Vasco y las Diputaciones Forales, que emite certificados para las tres diputaciones de la comunidad autónoma del País Vasco.

| Entidad Emisora     | Sedes | %     |
|--------------------:|:-----:|------:|
| AC Camerfirma S\.A  | 16    | 39,0% |
| DigiCert Inc        | 7     | 17,1% |
| FNMT\-RCM           | 5     | 12,2% |
| ACCV                | 4     | 9,8%  |
| IZENPE S\.A\.       | 3     | 7,3%  |
| Let's Encrypt       | 2     | 4,9%  |
| CATCert             | 2     | 4,9%  |
| Firmaprofesional    | 1     | 2,4%  |
| GoDaddy\.com, Inc\. | 1     | 2,4%  |

Si a nivel mundial, el auge de popularidad de la entidad Lets Encrypts, que emite certificados gratuitos, en los últimos meses ha sido destacada, en el ámbito de las Diputaciones, según los datos del estudio, tan solo está implantada en dos sedes electrónicas.

#### Tamaño de Clave

Respecto al tipo de clave usado en los certificados digitales, el 100% de las sedes electrónicas usan el algoritmo RSA. La mayoría de ellas, un 85,4%, utiliza un tamaño de clave de 2048bits, mientras que tan solo seis sedes optaron por un tamaño mayor de 4096bits. Destaca -por su ausencia- el uso de claves con algoritmos de Curva Eliptica (ECDSA), que con menor número de bits ofrecen una seguridad y robustez de cifrado que el algoritmo RSA; y su compatibilidad con los actuales navegadores y sistemas operativos es amplia tanto en equipos PC como en dispositivos móviles.

| Key Size      | Sedes | %     |
|--------------:|:-----:|------:|
| RSA 2048 bits | 35    | 85,4% |
| RSA 4096 bits | 6     | 14,6% |

#### Registro CAA

En lo que respecta al control de emisión de certificados, ninguna de las sedes del estudio implementa el mecanismo CAA. CAA (Certificate Authority Authorization) es un registro DNS que especifica aquella(s) CA(s) que pueden emitir un certificado digital para el nombre de dominio correspondiente. Los registros de CAA son verificados por las CA antes de emitir el certificado digital.

| CAA            | Sedes | %      |
|---------------:|:-----:|-------:|
| Configurado    | 0     | 0,0%   |
| No configurado | 41    | 100,0% |

#### Cadena de confianza

Relacionado con los certificados digitales, la configuración en la parte servidor de la cadena de confianza, según las buenas prácticas, debe ofrece el certificado final junto con la jerarquía de certificados de la CA emisora (sin agregar la CA raíz, o rootCA). Un 43,9% de las sedes (18 de ellas) muestran errores a la hora de enviar la cadena de confianza. Si bien esto no supone un error con impacto en los usuarios finales que acceden a las sedes, su correcta configuración haría más optimo el acceso a las mismas.

| Jerarquía   | Sedes | %     |
|------------:|:-----:|------:|
| Correcta    | 23    | 56,1% |
| Con errores | 18    | 43,9% |

##### Validación de certificados

En el inicio de la comunicación segura entre un cliente (navegador web) y el servidor web de la sede electrónica se realiza el proceso de validación del certificado digital facilitado por el servidor. Esta validación se puede realizar mediante protocolo OCSP o a través de listas CRL.

La opción más óptima para conocer el estado de revocación de un certificado digital consiste es configurar OCSP Stapling. En este caso, es el servidor quien realiza el proceso de validación del certificado, y el resultado se lo envía al cliente en la negociación inicial TLS, eliminando la necesidad de que los clientes se pongan en contacto con el CA.

| OCSP           | Sedes | %     |
|---------------:|:-----:|------:|
| Configurado    | 2     | 4,9%  |
| No configurado | 39    | 95,1% |

Tan solo dos sedes electrónicas tienen activado la opción de OCSP Stapling, funcionalidad que mejora la seguridad, el rendimiento y la privacidad.

#### Renovación de certificados

Respecto a la renovación de certificados digitales, se observó en el momento de realizar el estudio que, en dos sedes electrónicas, las fechas de expiración estaban a 4 y 17 días vista. Este dato indica una gestión incorrecta del ciclo de vida del certificado, donde las buenas prácticas indican una renovación del certificado 30 días antes de su caducidad, y en el caso de periodos cortos -como los emitidos por Lets Encrypts- pasados 2/3 del tiempo de vida.

### Protocolos y cifrados
#### Protocolos SSL/TLS

Por defecto, el protocolo criptográfico más utilizado en las sedes electrónicas es la versión 1.2 de TLS. Se ofrece en 36 sedes. En la parte positiva en el uso de protocolos por defecto, destacar que una de las sedes ya utiliza TLS v1.3. Mientras que, en el aspecto negativo, aún cuatro sedes no ofrecen más allá de TLS v1.0, un protocolo que apareció en 1999, y que posee múltiples vulnerabilidades de seguridad que se desaconseja su uso hoy en día.

| Protocolo por defecto | Sedes | %     |
|----------------------:|:-----:|------:|
| TLS1\.0               | 4     | 9,8%  |
| TLS1\.2               | 36    | 87,8% |
| TLS1\.3               | 1     | 2,4%  |

Si bien TLS v1.2 es el protocolo por defecto negocia en un 87,8% de los casos, el uso de protocolos depreciados y/o obsoletos en las configuraciones es aún amplio. Tan solo seis sedes ofrecen nada más que TLS v1.2, mientras que la mayoría (25 sedes) ofrecen las tres versiones de TLS (v1, v1.1 y v1.2)

| Protocolos                       | Sedes | %     |
|---------------------------------:|:-----:|------:|
| TLSv1                            | 4     | 9,8%  |
| TLSv1\.2                         | 6     | 14,6% |
| TLSv1\.1 \+ TLSv1\.2             | 5     | 12,2% |
| TLSv1 \+ TLSv1\.1 \+ TLSv1\.2    | 25    | 61,0% |
| TLSv1\.1 \+ TLSv1\.2 \+ TLSv1\.3 | 1     | 2,4%  |

Las mejores prácticas de seguridad recomiendan eliminar las versiones TLS v1 y TLS v1.1, y por supuesto, descartar por completo el uso de versión obsoletas como SSL v2 y SSLv3. Llama la atención que estos últimos protocolos con serías vulnerabilidades de seguridad sigan ofreciéndose en alguna de las sedes estudiadas.

| Se ofrece | SSLv2 | SSLv3 |
|-----------|-------|-------|
| NO        | 40    | 35    |
| SI        | 1     | 6     |

#### Conjunto de Cifrados (Ciphersuite)