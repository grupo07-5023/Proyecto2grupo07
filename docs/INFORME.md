# Informe — Preguntas

## Miembro A (Aitor): preguntas 1–3

### 1. ¿Por qué el segundo push del apartado 2.2 fue rechazado? ¿Qué dos operaciones hace `git pull` por debajo?

Porque B ya había subido a `main` un commit que C no tenía en local. Los historiales divergieron y Git solo acepta pushes que sean fast-forward, para no sobrescribir el trabajo de B.

`git pull` hace dos operaciones:

1. `git fetch`: descarga los commits nuevos del remoto.
2. `git merge origin/main`: los integra en la rama actual. Con `pull.rebase false` es un merge.

### 2. En vuestro historial, señalad un merge fast-forward y un merge commit. ¿Qué los diferencia?

**Fast-forward:** el merge de `contacto-a` en `main`. `main` no había cambiado desde que se creó la rama, así que Git solo movió el puntero hasta `84d904d`. El historial sigue lineal y no aparece ningún commit de merge.

**Merge commit:** `9c7c6b1` "He solucionado el conflicto entre contacto-a y contacto-b". Tiene dos padres, `84d904d` y `731e5c0`, y en el grafo se ve como un `|\ ... |/`. Se creó porque `main` ya incluía `contacto-a` cuando se fusionó `contacto-b`, y las dos ramas habían tocado la misma línea. Git creó un commit nuevo que une ambos historiales, y ahí se resolvió el conflicto. Los merges de PR de GitHub en 2.4, como `ea8c04d`, también son de este tipo.

**Diferencia:** el fast-forward solo desplaza el puntero de la rama y no crea ningún commit, porque el historial es lineal. El merge commit se crea cuando los historiales han divergido, y su resultado es un commit con dos padres.

### 3. ¿Por qué rellenar filas distintas de la tabla no dio conflicto y cambiar `Última revisión` sí?

Git fusiona por líneas. Las filas de la tabla del README son líneas distintas, así que Git pudo unir los tres cambios solo. En `Última revisión:`, los tres cambiaron la misma línea con valores diferentes y Git no sabe cuál conservar, así que da conflicto.
