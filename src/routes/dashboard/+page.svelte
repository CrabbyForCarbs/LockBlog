<script lang="ts">
	import { SignedIn, UserButton } from 'svelte-clerk/client';
</script>
<SignedIn>
	<div class="dashboard">
		<header>
			<h1>Welcome to LockBlog Dashboard!</h1>
			<UserButton />
		</header>
		<main>
			<p>You are successfully signed in!</p>
			<!-- Add your dashboard content here -->
		</main>
	</div>
</SignedIn>
<style>
	.dashboard {
		padding: 2rem;
	}
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		border-bottom: 1px solid #ccc;
		padding-bottom: 1rem;
		margin-bottom: 2rem;
	}
</style>
