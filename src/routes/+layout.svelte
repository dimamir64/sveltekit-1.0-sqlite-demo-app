<script lang="ts">
	import type { LayoutServerData } from './$types';

	export let data: LayoutServerData;
</script>

<header>
	<nav class="navbar is-primary px-4" aria-label="main navigation">
		<div class="navbar-brand pr-4">
			<span class="is-size-3 has-text-weight-semibold">SvelteKit + SQLite</span>
		</div>
		<div class="navbar-menu">
			<div class="navbar-start">
				<a href="/" class="navbar-item">Home</a>
				{#if data?.username}
					<div class="navbar-item has-dropdown is-hoverable">
						<span class="navbar-link"> Admin </span>

						<div class="navbar-dropdown">
							<a href="/admin/invoices" class="navbar-item">Invoices</a>
							<a href="/admin/playlistTracks" class="navbar-item">Playlists</a>
							<a href="/admin/charts_css" class="navbar-item">Charts.css</a>
						</div>
					</div>
				{/if}

				<a href="/about" class="navbar-item">About</a>
			</div>
		</div>

		<div class="navbar-end">
			<div class="navbar-item">
				<div class="buttons">
					{#if data?.username}
						<a
							href="/logout"
							class="button is-primary"
							data-sveltekit-preload-data="off"
							data-sveltekit-reload>Hello {data.username}, Log out</a
						>
					{:else}
						<a href="/login" class="button is-primary">Log in</a>
					{/if}
				</div>
			</div>
		</div>
	</nav>
</header>
<slot />
