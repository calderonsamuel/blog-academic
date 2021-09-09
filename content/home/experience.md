---
# An instance of the Experience widget.
# Documentation: https://wowchemy.com/docs/page-builder/
widget: experience

# This file represents a page section.
headless: true

# Order that this section appears on the page.
weight: 40

title: Experiencia
subtitle:

# Date format for experience
#   Refer to https://wowchemy.com/docs/customization/#date-format
date_format: Jan 2006

# Experiences.
#   Add/remove as many `experience` items below as you like.
#   Required fields are `title`, `company`, and `date_start`.
#   Leave `date_end` empty if it's your current employer.
#   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.

# Para convertir png a svg
# library(magick)
# my_image <- image_read("assets/media/icons/brands/inei-png.png")
# my_svg <- image_convert(my_image, format="svg")
# my_svg <- image_resize(my_svg, geometry_size_pixels(width = 100))
# image_write(my_svg, "assets/media/icons/brands/inei-svg.svg")


experience:
  - title: Integrante del Equipo Técnico Normativo de la Dirección de Licenciamiento
    company: Superintendencia Nacional de Educación Universitaria
    company_url: 'https://www.gob.pe/sunedu'
    company_logo: sunedu-svg
    location: Lima
    date_start: '2020-08-21'
    date_end: ''
    description: |2-
        Responsabilidades:
        
        * Recopilación, análisis y sistematización de información sobre la educación superior a nivel nacional e internacional
        * Modelo de Renovación de Licencia Institucional (Modelo 2.0)
        
  - title: Seguimiento al Plan Sectorial de Lucha contra la Corrupción
    company: Ministerio de Vivienda, Construcción y Saneamiento
    company_url: 'https://www.gob.pe/vivienda'
    company_logo: vivienda-svg
    location: Lima
    date_start: '2019-04-25'
    date_end: '2020-08-11'
    description: Seguimiento, sistematización, procesamiento y análisis de información, y elaboración de instructivos para la Oficina de Integridad y Lucha contra la Corrupción.
  - title: Asistente Académico de Capacitación
    company: Escuela Nacional de Administración Pública – ENAP
    company_url: 'https://www.enap.edu.pe/'
    company_logo: 'enap-svg'
    location: Lima
    date_start: '2018-10-20'
    date_end: '2018-12-17'
    description: 'Asistencia académica presencial y virtual para la implementación, ejecución y evaluación de cursos de capacitación.'
  - title: Supervisor de encuestadores
    company: Ministerio de Salud
    company_url: 'https://www.gob.pe/minsa'
    company_logo: 'minsa-svg'
    location: Lima
    date_start: '2018-05-02'
    date_end: '2018-02-27'
    description: 'Supervisión a encuestadores, procesamiento y análisis de consistencia de la información recogida en el Proyecto Termómetro Salud de la DGOS'
  - title: Supervisor de encuestadores
    company: Ministerio de Salud
    company_url: 'https://www.gob.pe/minsa'
    company_logo: 'minsa-svg'
    location: Lima
    date_start: '2018-05-02'
    date_end: '2018-02-27'
    description: 'Supervisión a encuestadores, procesamiento y análisis de consistencia de la información recogida en el Proyecto piloto Semáforo Salud de la DGOS'
  - title: Operador de aplicación de Encuestas
    company: Instituto Nacional de Estadística e Informática
    company_url: 'https://www.inei.gob.pe/'
    company_logo: 'inei-svg'
    location: Lima
    date_start: '2016-06-12'
    date_end: '2017-09-30'
    description: 'Levantamiento de información en hogares, procesamiento y análisis de consistencia de la información recogida en la Encuesta Nacional de Hogares – ENAHO'

design:
  columns: '2'
---
