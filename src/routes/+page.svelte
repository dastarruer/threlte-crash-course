<script lang="ts">
	import { Canvas } from '@threlte/core';
	import Scene from '$lib/components/Scene.svelte';
</script>

<!-- div tag is necessary; otherwise nothing will show up -->
<div>
	<Canvas>
		<Scene />
	</Canvas>
</div>

<style>
	:root {
		background-color: black;
	}

	div {
		height: 100%;
	}
</style>
