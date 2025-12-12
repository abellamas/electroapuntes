# LaTex en VsCode

Para Windows lo mejor es trabajar con la distribución MiKTeX. Se puede descargar desde [aquí](https://miktex.org/download).
También es necesario instalar una fuente de LaTeX para VSCode, la más popular es LaTeX Workshop, que se puede encontrar en el marketplace de VSCode.
Y por otro lado, se recomienda instalar Perl para evitar problemas con la compilación de bibliografías. Se puede descargar desde [aquí](https://www.perl.org/get.html). Luego de la instalación reiniciar VsCode y MikTeX Console.

Luego puede ser necesario abrir MikTex Console y actualizar los paquetes instalados. También es recomendable activar la opción de instalación automática de paquetes en MikTeX Console, para que cuando compilemos un proyecto y falte algún paquete, este se instale automáticamente.

# Directorio de trabajo

Para el proyecto es útil organizar subcarpetas para el directorio de trabajo. Una posible organización es la siguiente, con sections, figures, fonts, bib, out etc.

```
Proyecto/
│├── sections/
││   ├── 01-intro.tex
││   ├── 02-chapter_name2.tex
││   └── 03-chapter_name3.tex
│├── figures/
││   ├── image1.png
││   └── diagram1.pdf
│├── tables/
││   ├── table1.tex
││   └── table2.tex
│├── bib/
││   └── references.bib
│├── fonts/
││   ├── customfont1.ttf
││   └── customfont2.otf
│├── out/
││   ├── project.pdf
││   └── project.log
│├── main.tex
│└── preamble.tex
```

# Compilación de proyecto

Luego de guardar los cambios, se puede compilar el proyecto con la combinación de teclas `Ctrl + Alt + B` o desde el menú de comandos con `Ctrl + Shift + P` y luego escribir `LaTeX Workshop: Build with recipe`.
Todo está automatizado desde el settings.json del proyecto, por lo que no es necesario ejecutar comandos manuales en la terminal.

```
{
  "latex-workshop.latex.outDir": "./out",
  "latex-workshop.latex.autoBuild.run": "onSave",

  "latex-workshop.latex.tools": [
    {
      "name": "lualatex",
      "command": "lualatex",
      "args": [
        "-interaction=nonstopmode",
        "-file-line-error",
        "-output-directory=out",
        "%DOC%"
      ]
    }
  ],
  "latex-workshop.latex.recipes": [
    {
      "name": "LuaLaTeX",
      "tools": ["lualatex"]
    }
  ]
}
```





