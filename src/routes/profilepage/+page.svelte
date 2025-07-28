<script lang="ts">
	import { SignedIn, UserButton } from 'svelte-clerk/client';
    let sidebarOpen = false;
	import { goto } from '$app/navigation';
</script>
<SignedIn>
	<div class="border">
        <div class="sidebar" class:open={sidebarOpen}>
            <div class="button-container">
				<button on:click={() => goto('/dashboard')}>Home</button>
				<button on:click={() => goto('/profilepage')}>Profile</button>
                <button>Settings</button>
                <button>Log Out</button>
            </div>
        </div>
		<button class="setting-btn" on:click={() => sidebarOpen = !sidebarOpen}>
			<span class="bar bar1"></span>
			<span class="bar bar2"></span>
			<span class="bar bar1"></span>
		</button>
		<div class="dashboard">
			<header>
				<h1>Welcome to your profile page!</h1>
				<UserButton />
			</header>
			<main>
				<p>Here you can view your profile information and edit it.</p>
			</main>
		</div>
	</div>
</SignedIn>
<style>
	.dashboard {
		padding: 15rem;
		background-color: black;
		color: rgb(255, 255, 255);
		box-sizing:border-box;
		font-family: 'Lilita One', cursive;
		text-align: center;
		align-items: center;
		display: flex;
		flex-direction: column;
	}
	.border {
		border: 2px solid #f08c00; 
		border-radius: 15px;
		height: 100vh;
		box-sizing: border-box;
        position:absolute;
		top: 0;
		left: 0;
		right: 0;
		width: 100%;
        overflow: hidden;
	}
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		border-bottom: 1px solid #ffffff;
		padding-bottom: 1rem;
		margin-bottom: 1rem;
	}
	.setting-btn {
		position: absolute;
		top: 10px;
		left: 10px;
		width: 45px;
		height: 45px;
		display: flex;
		z-index: 1000;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 6px;
		background-color: rgb(129, 110, 216);
		border-radius: 10px;
		cursor: pointer;
		border: none;
		box-shadow: 0px 0px 0px 2px rgb(212, 209, 255);
	}
	.bar {
		width: 50%;
		height: 2px;
		background-color: rgb(229, 229, 229);
		display: flex;
		align-items: center;
		justify-content: center;
		position: relative;
		border-radius: 2px;
	}
	.bar::before {
		content: "";
		width: 2px;
		height: 2px;
		background-color: rgb(126, 117, 255);
		position: absolute;
		border-radius: 50%;
		border: 2px solid white;
		transition: all 0.3s;
		box-shadow: 0px 0px 5px white;
	}
	.bar1::before {
		transform: translateX(-4px);
	}
	.bar2::before {
		transform: translateX(4px);
	}
	.setting-btn:hover .bar1::before {
		transform: translateX(4px);
	}
	.setting-btn:hover .bar2::before {
		transform: translateX(-4px);
	}
    .sidebar {
        position: absolute;
        top: 0;
        left: -300px;
        width: 300px;
        height: 100%;
        background-color: rgb(42, 42, 42);
        transition: left 0.3s ease-in-out;
        border: 2px solid #f08c00;
        border-radius: 15px;
        box-sizing: border-box;
    }
    .sidebar.open {
        left: 0;
    }
    .button-container {
        padding-top: 60px;
    }
    .sidebar button {
        width: calc(100% - 30px);
        margin: 15px;
        background-color: rgb(42, 42, 42);
        border: 2px solid #f08c00;
        color: white;
        font-family: 'Lilita One', cursive;
        text-align: center;
        padding: 10px 0;
        border-radius: 10px;
        cursor: pointer;
    }
</style>