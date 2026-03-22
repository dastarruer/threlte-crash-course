<script lang="ts">
	import { T, useTask } from '@threlte/core';
	import { interactivity } from '@threlte/extras';
	import { Spring } from 'svelte/motion';

	let rotation: number = $state(0);

	// After every frame, multiply the time between the current and last frame (delta) by 0.5, and add that to rotation
	useTask((delta) => {
		rotation += delta * 0.5;
	});

	interactivity();
	const scale = new Spring(1);
</script>

<T.PerspectiveCamera
	makeDefault
	position={[14, 10, 0]}
	// No matter where the camera moves, always keep the mesh centered
	oncreate={(ref) => ref.lookAt(0, 0, 0)}
/>

<T.DirectionalLight position={[10, 20, 10]} intensity={2} castShadow />
<T.AmbientLight color="#d6efff" />

<T.Mesh
	scale={scale.current}
	rotation.y={rotation}
	onpointerenter={() => (scale.target = 0.5)}
	onpointerleave={() => (scale.target = 1)}
	position.y={2}
	castShadow
>
	<T.SphereGeometry args={[2, 32, 32]} />
	<T.MeshStandardMaterial color="#ff6467" wireframe />
</T.Mesh>

<!-- This plane cannot be seen without the PerspectiveCamera -->
<T.Mesh rotation.x={-Math.PI / 2} receiveShadow>
	<T.PlaneGeometry args={[10, 10]} />
	<T.MeshStandardMaterial />
</T.Mesh>
