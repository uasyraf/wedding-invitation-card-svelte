<script>
	// Props
	/** Exposes parent props to this component. */
	// export let any;

	// Stores
	import { getModalStore } from '@skeletonlabs/skeleton';
	const modalStore = getModalStore();

	let choice = "Yes";

	let choices = ["Yes", "No"];

	// We've created a custom submit function to pass the response and close the modal.
	function onFormSubmit() {
		if ($modalStore[0].response) $modalStore[0].response(formData);
		modalStore.close();
	}

	function onFormClose() {
		modalStore.close();
	}

	function section(c) {
		choice = c;
	}

	// Base Classes
	const cBase = 'card p-4 w-modal shadow-xl space-y-4';
	const cHeader = 'text-2xl font-bold';
	const cForm = 'border border-surface-500 p-4 space-y-4 rounded-container-token';
</script>

<!-- @component This example creates a simple form modal. -->


{#if $modalStore[0]}
	<div class="modal-example-form {cBase}">
		<div class="flex justify-between">
			<header class={cHeader}>{$modalStore[0].title ?? 'RSVP'}</header>
			<div class="flex items-end ">
				<button id="close" type="button" class="items-end top-3 right-2.5 text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 ml-auto inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white" data-modal-hide="authentication-modal"
					on:click={onFormClose}
				>
					<svg class="w-3 h-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 14">
						<path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"/>
					</svg>
				</button>
			</div>
		</div>
		
		<article>{$modalStore[0].body ?? '(body missing)'}</article>
		<!-- Enable for debugging: -->
		<form class="modal-form {cForm}">
			<label class="label">
				<span>{$modalStore[0].inputTitle1 ?? 'Not found'}</span>
				<input class="input pl-4 pt-2 pb-2" type="text" placeholder={$modalStore[0].placeholder1 ?? 'Not found'} />
			</label>
			<label class="label">
				<span>{$modalStore[0].inputTitle2 ?? 'Not found'}</span>
				<input class="input pl-4 pt-2 pb-2" type="text" placeholder={$modalStore[0].placeholder2 ?? 'Not found'} />
			</label>
			<label class="label">
				<span>{$modalStore[0].inputTitle3 ?? 'Not found'}</span>
				<input class="input pl-4 pt-2 pb-2" type="tel" placeholder={$modalStore[0].placeholder3 ?? 'Not found'} />
			</label>
			{#each choices as c}
			<span
				class="chip {choice === c ? 'variant-filled' : 'variant-soft'}"
				on:click={() => { section(c); }}
				on:keypress
				aria-hidden="true">
				{#if choice === c}
				<span>
					<svg class="w-3 h-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 14 14">
						<path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"/>
					</svg>
				</span>
				{/if}
				<span>{c}</span>
			</span>
			{/each}
		</form>
		
		<!-- prettier-ignore -->
		<footer class="modal-footer {parent.regionFooter}">
        <button class="btn {parent.buttonPositive}" on:click={onFormSubmit}>Submit Form</button>
    </footer>
	</div>
{/if}

<style lang="postcss">
	.modal-example-form {
	}
</style>