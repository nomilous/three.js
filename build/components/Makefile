#
# total novice here... so, um, 
#


SRC=../../src
LIC=../../LICENSE


CORE=\
	${SRC}/math/Color.js \
	${SRC}/math/Vector3.js \
	${SRC}/math/Euler.js \
	${SRC}/math/Box3.js \
	${SRC}/math/Sphere.js \
	${SRC}/math/Frustum.js \
	${SRC}/renderers/WebGLRenderer.js


core: ${CORE}
	cp ${LIC} three-core/
	cp ${SRC}/Three.js three-core/index.js
	echo "\nmodule.exports = THREE;\n" >> three-core/index.js
	cat ${CORE} >> three-core/index.js

MOO=1