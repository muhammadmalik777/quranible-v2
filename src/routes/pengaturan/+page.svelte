<script>
	import Heading from '../../components/Heading.svelte';
	import Seo from '../../components/SEO.svelte';
	import { themeChoice, transliterationChoice, autoScrollChoice } from '../../stores/SettingStore';

	let themeValue = $themeChoice;
	let transliterationValue = $transliterationChoice;
	let autoScrollValue = $autoScrollChoice;

	const themes = [
		{
			name: 'Terang',
			value: 'light',
			bgColor: 'bg-slate-100',
			borderColor: 'border-white'
		},
		{
			name: 'Gelap',
			value: 'dark',
			bgColor: 'bg-slate-800',
			borderColor: 'border-slate-500'
		}
	];
</script>

<Seo title="Pengaturan | Al-Quran Digital" />

<section class="min-h-screen dark:text-slate-300">
	<Heading title="Pengaturan" />
	<h5 class="mb-4 text-xl font-medium mt-8">Pilihan Tema</h5>
	<div id="themes" class="flex flex-wrap items-center mb-8">
		{#each themes as theme}
			<label
				for="{theme.value}-theme"
				on:click={() => themeChoice.set(theme.value)}
				class="flex items-center mb-4 md:mb-0 mr-3 {theme.value == themeValue
					? 'bg-slate-300 dark:bg-slate-800'
					: ''} px-4 py-2 rounded-3xl"
			>
				<div class="h-5 w-5 rounded-full {theme.bgColor} border-2 {theme.borderColor} mr-2" />
				{theme.name}
				<input
					type="radio"
					class="hidden"
					name="theme"
					id="{theme.value}-theme"
					value={theme.value}
					bind:group={themeValue}
				/>
			</label>
		{/each}
	</div>
	<h5 class="mb-4 text-xl font-medium">Tampilkan Ayat Latin</h5>
	<div id="latin-radios">
		<label for="yes-transliteration" class="mr-3">
			<input
				type="radio"
				name="transliteration"
				id="yes-transliteration"
				class="mr-1"
				bind:group={transliterationValue}
				value={1}
				on:click={() => transliterationChoice.set(1)}
			/>
			Ya
		</label>
		<label for="no-transliteration">
			<input
				type="radio"
				name="transliteration"
				id="no-transliteration"
				class="mr-1"
				bind:group={transliterationValue}
				value={0}
				on:click={() => transliterationChoice.set(0)}
			/>
			Tidak
		</label>
	</div>
	<h5 class="mb-4 text-xl font-medium mt-8">Otomatis Scroll Audio</h5>
	<div id="auto-scroll-radios">
		<label for="yes-auto-scroll" class="mr-3">
			<input type="radio" name="auto_scroll" id="yes-auto-scroll" class="mr-1" bind:group={autoScrollValue} value={1} on:click={() => autoScrollChoice.set(1)} />
			Ya
		</label>
		<label for="no-auto-scroll">
			<input type="radio" name="auto_scroll" id="no-auto-scroll" class="mr-1" bind:group={autoScrollValue} value={0} on:click={() => autoScrollChoice.set(0)} />
			Tidak
		</label>
	</div>
</section>

<style>
	label {
		cursor: pointer;
	}
</style>
