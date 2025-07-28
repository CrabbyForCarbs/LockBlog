<script lang="ts">
	import { SignInButton, SignedIn, SignedOut } from 'svelte-clerk/client';
	import { goto } from '$app/navigation';
	import { useClerkContext } from 'svelte-clerk/client';
	const { clerk } = useClerkContext();
	const ctx = useClerkContext();
	const userId = $derived(ctx.auth.userId);
</script>

<SignedOut>
	<div class="page">
		<div class="container">
			<SignInButton signUpForceRedirectUrl="/dashboard">
				<button class="signin-btn">
					Sign in to LockBlog
				</button>
			</SignInButton>
		</div>
	</div>
</SignedOut>

<SignedIn>
	{#if typeof window !== 'undefined'}
		{goto('/dashboard')}
	{/if}
</SignedIn>
<style>
	.container {
		background-color: #ffd005;
		color: #ffd005;
		display: flex;
		justify-content: center;
		align-items: center;
		min-height: 100vh;
		width: 100%;
	}
	.signin-btn {
		background-color: white;
		color: black;
		border: 2px solid black;
		padding: 15px 30px;
		font-size: 18px;
		font-weight: bold;
		border-radius: 8px;
		cursor: pointer;
		transition: all 0.2s ease;
	}
	.signin-btn:hover {
		background-color: #f0f0f0;
		transform: translateY(-2px);
		box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
	}
</style>
