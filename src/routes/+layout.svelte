<script>
	import Footer from '$lib/Footer.svelte';
	import Navbar from '$lib/Navbar.svelte';
	import '../app.css';
</script>

<Navbar />
<div class="bg-gray-200">
	<div class="mx-4">
		<div class="translate-y-16 pb-24">
			<div class="flex justify-center">
				<div class="w-screen max-w-screen md:max-w-2xl lg:max-w-4xl xl:max-w-5xl min-h-screen">
					<slot />
				</div>
			</div>
		</div>
	</div>
</div>
<Footer />
