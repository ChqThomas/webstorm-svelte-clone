<script lang="ts">
	import { openedFile } from '../../stores/states';
	import FileIcon from '../ui/FileIcon.svelte';
	import ChevronRight from '$lib/images/icons/chevronRight_dark.svg?component';

	$: path = [import.meta.env.VITE_GITHUB_REPO, ...$openedFile.split('/')];
</script>

<div id="breadcrumb" class="flex items-center h-[32px] px-2">
	<span class="blue-square" />
	{#each path as item, i}
		<span class="flex items-center gap-1 hover:text-white hover:bg-g-h px-1">
			{#if i === path.length - 1}
				{#key $openedFile}
					<FileIcon filename={$openedFile} />
				{/key}
			{/if}
			{item}
		</span>
		{#if i < path.length - 1}
			<span class="px-1">
				<ChevronRight />
			</span>
		{/if}
	{/each}
</div>

<style>
	#breadcrumb {
		color: #aeaeae;
	}

	.blue-square {
		width: 8px;
		height: 8px;
		border: 1px solid #4f80e3;
		margin-right: 5px;
		border-radius: 2px;
	}
</style>
