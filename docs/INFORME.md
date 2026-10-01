Roles: ¿qué puede hacer un Maintain que no pueda un Write? ¿Quién podría haber quitado la protección de main?
Con el rol de Maintain tenemos más capacidades para la gestión del repositorio de alguien con el rol de Write. Como Maintain podemos hacer configuraciones como:
Configurar varios aspectos del repositorio.
Gestionar operaciones operativas que con el rol de Write no podríamos.
En cambio lo relacionado con la gestión de reglas de protección de ramas corresponde a usuarios con permisos de Admin o alguien con un rol personalizado con el permiso de modificar reglas del repositorio. 
Si mañana un miembro sube un force push a main, ¿qué se pierde y qué lo impide en vuestro repositorio?
Si un miembro sube un force push puede reescribir el historial de una rama, esto puede hacer que commits que estaban en main dejen de ser alcanzables desde esa rama. Github nos advierte de que esto puede provocar pérdida aparente de commits, conflictos y Pull Request dañadas o incoherentes.
En nuestro repositorio nos lo impide la protección aplicada al main, que por defecto, las ramas protegidas bloquean los force push, al menos que el administrador active explícitamente la opción Allow force pushes.
En la Fase 1 compartíais un portátil y en la Fase 2 cada uno tenía el suyo. ¿Qué diferencia práctica tiene eso para la identidad del autor de cada commit y para cómo aparecen los conflictos?
Una de las principales diferencias es que en la Fase 1 los commits quedan  registrados por el mismo id configurado localmente, aunque físicamente hubiéramos realizado cambios diferentes personas. Porque Git registra como autor el id configurado localmente en ese entorno. 
En cambio en la Fase 2, cada uno trabajamos desde nuestros portátiles, con nuestra propia copia local del repositorio y nuestra propia configuración de nombre y correo. Esto nos permite ver quién creó esos commits. Además de esta manera cada miembro del grupo podemos trabajar de manera paralela e independiente. Como un miembro puede tener cambios que otro todavía no ha descargado, puede provocar rechazos del push y la necesidad de hacer un pull y conflictos al integrar las modificaciones.
