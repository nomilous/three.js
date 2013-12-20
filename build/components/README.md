* This components directory houses a set of git sub repos, each a [component](https://github.com/component/component)
* The subrepos can be cloned using [git-seed](https://github.com/nomilous/git-seed) (i think) `git seed clone` or 'git seed pull'
* The Makefile in this directory updates each component repo, `git seed status` will inform changes across all sub repos
* **run git seed from the root if this repo** where the .git-seed file is. 


instanceof all over the renderer makes it a bit tricky to break out into components, a whole bunch of stuff needs to be defined even if rendering with only one of them

```
 grep -oe 'instanceof THREE.[A-Za-z]*' ../../src/renderers/WebGLRenderer.js | sort | uniq -c

   1 instanceof THREE.AmbientLight
   5 instanceof THREE.BufferGeometry
   1 instanceof THREE.Camera
   2 instanceof THREE.CompressedTexture
   1 instanceof THREE.CubeRefractionMapping
   1 instanceof THREE.DataTexture
   4 instanceof THREE.DirectionalLight
   1 instanceof THREE.Fog
   2 instanceof THREE.FogExp
   1 instanceof THREE.Geometry
   2 instanceof THREE.HemisphereLight
   2 instanceof THREE.ImmediateRenderObject
   2 instanceof THREE.LensFlare
   6 instanceof THREE.Line
   2 instanceof THREE.LineBasicMaterial
   2 instanceof THREE.LineDashedMaterial
   7 instanceof THREE.Mesh
   3 instanceof THREE.MeshBasicMaterial
   3 instanceof THREE.MeshDepthMaterial
   3 instanceof THREE.MeshFaceMaterial
   5 instanceof THREE.MeshLambertMaterial
   2 instanceof THREE.MeshNormalMaterial
   6 instanceof THREE.MeshPhongMaterial
   7 instanceof THREE.ParticleSystem
   2 instanceof THREE.ParticleSystemMaterial
   2 instanceof THREE.PointLight
   3 instanceof THREE.ShaderMaterial
   1 instanceof THREE.SkinnedMesh
   4 instanceof THREE.SpotLight
   2 instanceof THREE.Sprite
   5 instanceof THREE.WebGLRenderTargetCube

```

see `instanceof-U-later` in Makefile
