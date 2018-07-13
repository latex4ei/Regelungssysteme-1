cmake_minimum_required(VERSION 2.8)

project(RS NONE)
include(UseLATEX)

add_custom_target(
	writegitid ALL
	COMMAND ${CMAKE_CURRENT_SOURCE_DIR}/write-gitid.sh
	WORKING_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}
)

configure_file(${CMAKE_CURRENT_SOURCE_DIR}/scientific.sty ${CMAKE_CURRENT_BINARY_DIR}/scientific.sty COPYONLY)
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/latex4ei.sty ${CMAKE_CURRENT_BINARY_DIR}/latex4ei.sty COPYONLY)
configure_file(${CMAKE_CURRENT_SOURCE_DIR}/latex4ei.cls ${CMAKE_CURRENT_BINARY_DIR}/latex4ei.cls COPYONLY)

set(IMAGES
	img/beobachter.jpg
	img/beobachternormalform.jpg
	img/Bode-Diagramme_Regler.pdf
	img/cat.jpg
	img/control_circle.pdf
	img/input.pdf
	img/kanonischenormalform.jpg
	img/Logo.pdf
	img/OK_G0.pdf
	img/OK_GO.pdf
	img/output.svg
	img/petri_constructs.pdf
	img/Regelkreis.pdf
	img/regelnormalform.jpg
	img/reglerstrecke.pdf
	img/trigo.pdf
	img/wok2.jpg
	img/wok_kinds.jpg
	img/wok.pdf
	img/blocks/P_G.pdf
	img/blocks/PN_1h.pdf
	img/blocks/PN_1.pdf
	img/blocks/PN_2h.pdf
	img/blocks/PN_2.pdf
	img/blocks/PN_3h.pdf
	img/blocks/PN_3.pdf
	img/blocks/PN_4h.pdf
	img/blocks/PN_4.pdf
	img/blocks/PN_5h.pdf
	img/blocks/PN_5.pdf
	img/blocks/PN_6h.pdf
	img/blocks/PN_6.pdf
)

add_latex_document(
  Regelungssysteme.tex
  FORCE_PDF
	IMAGES ${IMAGES}
	DEPENDS writegitid
)
