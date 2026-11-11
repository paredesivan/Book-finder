# Book Search — metabuscador legal

Metabuscador personal de libros pensado para que **ChatGPT sea la fachada**. El objetivo no es depender de una sola tienda o biblioteca: consulta fuentes estructuradas grandes y, cuando no alcanzan, genera un plan de búsqueda web legal para cubrir la cola larga de editoriales, librerías, bibliotecas y repositorios.

## Cobertura estructurada (sin claves)

1. Google Books — catálogo, muestras, ebook y disponibilidad.
2. Open Library / Internet Archive — catálogo, préstamo y acceso público.
3. Internet Archive directo — textos y objetos digitales; no presume que todo sea libre.
4. Project Gutenberg vía Gutendex — dominio público y formatos descargables.
5. Wikisource — textos de dominio público/licencia libre.
6. LibriVox — audiolibros de dominio público.
7. DOAB — libros académicos de acceso abierto.
8. OAPEN Library — libros académicos de acceso abierto.
9. Library of Congress — registros y objetos digitalizados.

## Segunda capa: búsqueda web legal

Ningún catálogo contiene “todo lo legal que existe”. Por eso el resultado incluye `web_search_plan`: consultas preparadas para que la capa conversacional/web busque además en:

- editoriales y autores;
- librerías y tiendas de ebooks;
- bibliotecas nacionales, universitarias y municipales;
- repositorios institucionales;
- servicios de préstamo digital;
- libros usados y segunda mano;
- sitios regionales que no tengan API.

Esto evita mantener a mano una lista cerrada de miles de sitios que cambia constantemente.

## Qué significa «encontrado»

El motor distingue:

- texto completo gratis/legal;
- dominio público;
- acceso abierto;
- préstamo digital;
- muestra/vista parcial;
- compra ebook;
- audiolibro;
- objeto digital con derechos a verificar;
- ficha bibliográfica solamente.

Nunca confunde una ficha de catálogo con un ebook disponible.

## Prioridad para este proyecto

Por defecto: **español primero**. Luego se prioriza mejor coincidencia y mejor tipo de acceso. EPUB/PDF/AUDIO se indican cuando la fuente los informa.

## Uso local

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python -m booksearch.search "El hombre y sus símbolos" --author Jung --lang es
```

JSON:

```bash
python -m booksearch.search "Incógnito" --author "David Eagleman" --json
```

## Desde GitHub Issues

La Action incluida responde a issues cuyo título empiece con:

```text
BUSCAR: El hombre y sus símbolos
```

Cuerpo opcional:

```text
autor: Jung
idioma: es
```

ChatGPT puede crear la issue, leer el resultado y completar con búsqueda web legal cuando haga falta.

## Límites honestos

No existe una API universal de “todos los libros legales del planeta”. Algunos catálogos requieren credenciales, otros no ofrecen API y otros cambian por país. Por eso este proyecto usa una arquitectura híbrida:

**catálogos estructurados + búsqueda web actual**.

No busca ni enlaza repositorios piratas.
