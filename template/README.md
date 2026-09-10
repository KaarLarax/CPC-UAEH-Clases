# Plantilla de clases

Esta carpeta sirve como base para crear el material de cualquier año, periodo,
nivel y tema. No se debe editar directamente: copia su contenido dentro de la
carpeta del periodo correspondiente.

## Estructura

```text
periodo-academico/
└── nivel/
    └── tema/
        ├── tema.md
        └── editoriales/
            ├── editorial.md
            └── problema.md
```

## Cómo usarla

1. Copia `periodo-academico` dentro de la carpeta del año, por ejemplo `2027/`.
2. Cambia `periodo-academico`, `nivel` y `tema` por nombres descriptivos.
3. Renombra `tema.md` con el nombre del tema en minúsculas y con guiones.
4. Completa `tema.md` siguiendo el orden de la plantilla.
5. Agrega una editorial por problema dentro de `editoriales/` usando el formato de `problema.md`.
6. Actualiza el README principal con los enlaces del nuevo material.
7. Consulta las [reglas para contribuir](../.github/CONTRIBUTING.md) para convenciones de commits, ramas y contenido.

## Convenciones

- Usa nombres de carpetas en minúsculas.
- Usa guiones para nombres de archivo: `divide-y-venceras.md`.
- Mantén los niveles disponibles: `basicos`, `intermedios` y `avanzados`.
- Escribe las complejidades como `O(...)` e indica tiempo y memoria.
- Revisa los enlaces antes de publicar el material.
