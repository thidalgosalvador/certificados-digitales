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

# Certificados digitales

## Entidades Emisoras (CA’s)
El prestador de Servicios de Confianza (PSC) Camerfirma, del grupo italiano Inforcert, con 16 sedes electrónicas (39%) ocupa un destacado primer puesto en certificados emitidos para Diputaciones Provinciales. Destaca el PSC vasco, Izenpe S.A., un proyecto de Autoridad Certificadora impulsado por el Gobierno Vasco y las Diputaciones Forales, que emite certificados para las tres diputaciones de la comunidad autónoma del País Vasco.
