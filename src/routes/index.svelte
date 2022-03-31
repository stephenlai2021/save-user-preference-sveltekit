<script lang="ts" context="module">
	import type { Load } from '@sveltejs/kit';
	import type { Colors } from '$lib/types';

	import { colors } from '$lib/utils/stores';

	export const load: Load = ({ session }) => {
		const locals = session as Partial<{ colors: Colors }>;
		const color_preference = locals.colors;
		if (color_preference) {
			colors.set(color_preference);
		}
		return {};
	};
</script>

<script lang="ts">
	import Customize from '$lib/components/Customize.svelte';
</script>

<div class="absolute top-0 w-full flex p-4 sm:px-8 place-content-between place-items-center z-50">
	<p class="text-lg font-medium" style:color={$colors.logo}>Logo</p>
</div>
<div class="min-h-screen flex place-items-center place-content-center px-4 md:px-8">
	<Customize />
</div>
