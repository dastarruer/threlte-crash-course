<script lang="ts">
	import { T } from '@threlte/core';
</script>

<T.PerspectiveCamera
	makeDefault
	position={[14, 10, 0]}
	// No matter where the camera moves, always keep the mesh centered
	oncreate={(ref) => ref.lookAt(0, 0, 0)}
/>

<T.DirectionalLight position={[10, 20, 10]} intensity={2} castShadow />
<T.AmbientLight color="#d6efff" />

<T.Mesh position.y={2} castShadow>
	<T.SphereGeometry args={[2, 32, 32]} />
	<T.MeshStandardMaterial color="#ff6467" />
</T.Mesh>

<!-- This plane cannot be seen without the PerspectiveCamera -->
<T.Mesh rotation.x={-Math.PI / 2} receiveShadow>
	<T.PlaneGeometry args={[10, 10]} />
	<T.MeshStandardMaterial />
</T.Mesh>
