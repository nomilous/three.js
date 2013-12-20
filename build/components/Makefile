# 
# cd ../../ && git pull https://github.com/mrdoob/three.js.git master  # refresh from upstream
# cd - && make                                                         # rebuilds the entire set
# git seed status                                                      # informs changes across entire set
# 
#             # update / rejig / commit accordingly
# 
# make tag                                                             # retag version across entire set
# 

#
# total Makefile novice here... so, um, here follows hopefully coherent and platform compatable
# 

VER=0.0.1
SRC=../../src
LIC=../../LICENSE

COMPONENTS=\
	base \
	system \
	color \
	math-common \
	render-common \
	webgl-renderer \
	object \
	camera \
	scene \
	line \
	particle


components: ${COMPONENTS}

tag:

	#
	# tag
	# 
	# * a possible future rejig of the dependancy tree is highly likely
	# * so ANY change should increment version for the entire set
	#

	for COMPONENT in ${COMPONENTS}; do \
		if [ -d three-$${COMPONENT} ]; then \
			cd three-$${COMPONENT} && \
			git tag ${VER} && \
			git push origin ${VER} && \
			cd - ;\
		fi \
	done

	#
	# TODO: also change version inside each relevant component.json and dependancies automatically
	#


BASE=\
	${SRC}/Three.js

base: ${BASE}

	#
	# base
	#

	cp ${LIC} three/
	cat ${BASE} > three/index.js
	echo "\nmodule.exports = THREE;\n" >> three/index.js



SYSTEM=\
	${SRC}/core/EventDispatcher.js

system: ${SYSTEM}

	#
	# system
	#

	cp ${LIC} three-system/
	echo "module.exports = THREE = require('three');\n\n" > three-system/index.js
	cat ${SYSTEM} >> three-system/index.js



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
	${SRC}/textures/Texture.js \
	${SRC}/materials/ShaderMaterial.js \
	${SRC}/renderers/shaders/UniformsLib.js \
	${SRC}/renderers/WebGLRenderTarget.js \
	${SRC}/renderers/WebGLRenderTargetCube.js \
	${SRC}/renderers/shaders/UniformsUtils.js \
	${SRC}/renderers/shaders/ShaderChunk.js \
	${SRC}/renderers/shaders/ShaderLib.js

render-common: ${RENDER-COMMON}

	#
	# render common
	# * perhaps ShaderMaterial can be moved to the instanceof-U-later
	# * gets material and math via object
	#

	cp ${LIC} three-render-common/
	echo "module.exports = THREE = require('three');\n\nrequire('three-system');\nrequire('three-color');\nrequire('three-object');\n\n" > three-render-common/index.js
	cat ${RENDER-COMMON} >> three-render-common/index.js



OBJECT=\
	${SRC}/core/Object3D.js \
	${SRC}/core/Geometry.js \
	${SRC}/core/BufferGeometry.js \
	${SRC}/materials/Material.js 

object: ${OBJECT}

	#
	# object
	#

	cp ${LIC} three-object/
	echo "module.exports = THREE = require('three');\nrequire('three-system');\nrequire('three-math-common');\nrequire('three-color');\n" > three-object/index.js
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



SCENE=\
	${SRC}/scenes/Fog.js \
	${SRC}/scenes/FogExp2.js \
	${SRC}/scenes/Scene.js

scene: ${SCENE}

	#
	# scene
	# 

	cp ${LIC} three-scene/
	echo "module.exports = THREE = require('three');\nrequire('three-camera');\nrequire('three-object');\nrequire('three-color');\n" > three-scene/index.js
	cat ${SCENE} >> three-scene/index.js



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
	echo "\
	module.exports = THREE = require('three'); \n\
	require('three-render-common'); \n\
	\n\
	/* instanceof-U-later */ \n\
	\n\
	if ('undefined' == typeof THREE.Light                 ) THREE.Light                  = function() {}; \n\
	if ('undefined' == typeof THREE.Bone                  ) THREE.Bone                   = function() {}; \n\
	\n\
	if ('undefined' == typeof THREE.BufferGeometry        ) THREE.BufferGeometry         = function() {}; \n\
	if ('undefined' == typeof THREE.Mesh                  ) THREE.Mesh                   = function() {}; \n\
	if ('undefined' == typeof THREE.Line                  ) THREE.Line                   = function() {}; \n\
	if ('undefined' == typeof THREE.ParticleSystem        ) THREE.ParticleSystem         = function() {}; \n\
	if ('undefined' == typeof THREE.ImmediateRenderObject ) THREE.ImmediateRenderObject  = function() {}; \n\
	if ('undefined' == typeof THREE.Sprite                ) THREE.Sprite                 = function() {}; \n\
	if ('undefined' == typeof THREE.LensFlare             ) THREE.LensFlare              = function() {}; \n\
	\n\
	if ('undefined' == typeof THREE.MeshFaceMaterial      ) THREE.MeshFaceMaterial       = function() {}; \n\
	if ('undefined' == typeof THREE.MeshDepthMaterial     ) THREE.MeshDepthMaterial      = function() {}; \n\
	if ('undefined' == typeof THREE.MeshNormalMaterial    ) THREE.MeshNormalMaterial     = function() {}; \n\
	if ('undefined' == typeof THREE.MeshBasicMaterial     ) THREE.MeshBasicMaterial      = function() {}; \n\
	if ('undefined' == typeof THREE.MeshLambertMaterial   ) THREE.MeshLambertMaterial    = function() {}; \n\
	if ('undefined' == typeof THREE.MeshPhongMaterial     ) THREE.MeshPhongMaterial      = function() {}; \n\
	if ('undefined' == typeof THREE.LineBasicMaterial     ) THREE.LineBasicMaterial      = function() {}; \n\
	if ('undefined' == typeof THREE.LineDashedMaterial    ) THREE.LineDashedMaterial     = function() {}; \n\
	if ('undefined' == typeof THREE.ParticleSystemMaterial) THREE.ParticleSystemMaterial = function() {}; \n\
	\n\
	if ('undefined' == typeof THREE.DirectionalLight      ) THREE.DirectionalLight       = function() {}; \n\
	if ('undefined' == typeof THREE.PointLight            ) THREE.PointLight             = function() {}; \n\
	if ('undefined' == typeof THREE.SpotLight             ) THREE.SpotLight              = function() {}; \n\
	if ('undefined' == typeof THREE.HemisphereLight       ) THREE.HemisphereLight        = function() {}; \n\
	\n\
	if ('undefined' == typeof THREE.SkinnedMesh           ) THREE.SkinnedMesh            = function() {}; \n\
	\n\
	" > three-webgl-renderer/index.js
	cat ${WEBGL-RENDERER} >> three-webgl-renderer/index.js



LINE=\
	${SRC}/materials/LineBasicMaterial.js \
	${SRC}/materials/LineDashedMaterial.js \
	${SRC}/objects/Line.js

line: ${LINE}

	#
	# line
	#

	cp ${LIC} three-line/
	echo "module.exports = THREE = require('three');\nrequire('three-object');\n" > three-line/index.js
	cat ${LINE} >> three-line/index.js



PARTICLE=\
	${SRC}/materials/ParticleSystemMaterial.js \
	${SRC}/objects/ParticleSystem.js

particle: ${PARTICLE}

	#
	# particle
	#

	cp ${LIC} three-particle/
	echo "module.exports = THREE = require('three');\nrequire('three-object');\n" > three-particle/index.js
	cat ${PARTICLE} >> three-particle/index.js

