#
# total novice here... so, um, 
#


SRC=../../src
LIC=../../LICENSE

components: base color math-common render-common webgl-renderer object camera

BASE=\
	${SRC}/Three.js

base: ${BASE}

	#
	# base
	#

	cp ${LIC} three/
	cat ${BASE} > three/index.js
	echo "\nmodule.exports = THREE;\n" >> three/index.js



COLOR=\
	${SRC}/math/Color.js

color:

	#
	# color
	#

	cp ${LIC} three-color/
	echo "module.exports = THREE = require('three');\n\n" > three-color/index.js
	cat ${COLOR} >> three-color/index.js



MATH-COMMON=\
	${SRC}/math/Math.js \
	${SRC}/math/Quaternion.js \
	${SRC}/math/Euler.js \
	${SRC}/math/Vector2.js \
	${SRC}/math/Vector3.js \
	${SRC}/math/Vector4.js \
	${SRC}/math/Matrix3.js \
	${SRC}/math/Matrix4.js \
	${SRC}/math/Box3.js \
	${SRC}/math/Sphere.js \
	${SRC}/math/Plane.js \
	${SRC}/math/Ray.js \
	${SRC}/math/Frustum.js 

math-common: ${MATH-COMMON}

	#
	# math common
	#

	cp ${LIC} three-math-common/
	echo "module.exports = THREE = require('three');\n\n" > three-math-common/index.js
	cat ${MATH-COMMON} >> three-math-common/index.js


RENDER-COMMON=\
	${SRC}/core/Raycaster.js \
	${SRC}/core/Projector.js \
	${SRC}/core/EventDispatcher.js \
	${SRC}/textures/Texture.js \
	${SRC}/materials/Material.js \
	${SRC}/materials/ShaderMaterial.js \
	${SRC}/renderers/shaders/UniformsLib.js \
	${SRC}/renderers/shaders/UniformsUtils.js \
	${SRC}/renderers/shaders/ShaderChunk.js \
	${SRC}/renderers/shaders/ShaderLib.js

render-common: ${RENDER-COMMON}

	#
	# render common
	#

	cp ${LIC} three-render-common/
	echo "module.exports = THREE = require('three');\nrequire('three-color');\nrequire('three-math-common');\n\n" > three-render-common/index.js
	cat ${RENDER-COMMON} >> three-render-common/index.js


WEBGL-RENDERER=\
	${SRC}/extras/shaders/ShaderFlares.js \
	${SRC}/extras/renderers/plugins/ShadowMapPlugin.js \
	${SRC}/extras/renderers/plugins/SpritePlugin.js \
	${SRC}/extras/renderers/plugins/LensFlarePlugin.js \
	${SRC}/renderers/WebGLRenderer.js

webgl-renderer: ${WEBGL-RENDERER}

	#
	# webgl renderer
	#

	cp ${LIC} three-webgl-renderer/
	echo "module.exports = THREE = require('three');\nrequire('three-render-common');\n" > three-webgl-renderer/index.js
	cat ${WEBGL-RENDERER} >> three-webgl-renderer/index.js



OBJECT=\
	${SRC}/core/Object3D.js

object: ${OBJECT}

	#
	# object
	#

	cp ${LIC} three-object/
	echo "module.exports = THREE = require('three');\nrequire('three-math-common');\n" > three-object/index.js
	cat ${OBJECT} >> three-object/index.js



CAMERA=\
	${SRC}/cameras/Camera.js \
	${SRC}/cameras/OrthographicCamera.js \
	${SRC}/cameras/PerspectiveCamera.js

camera: ${CAMERA}

	#
	# camera
	# 

	cp ${LIC} three-camera/
	echo "module.exports = THREE = require('three');\nrequire('three-object');\nrequire('three-math-common');\n" > three-camera/index.js
	cat ${CAMERA} >> three-camera/index.js

