<script>
	import ArrowClosCss from '../components/ArrowClosCSS.svelte';
	import Background from '../components/Background.svelte';
	import HeroButton from '../components/HeroButton.svelte';
	import Menu from '../components/Menu.svelte';
	import TextLandingPange from '../components/TextLandingPange.svelte';
	import Portfolio from '../components/Portfolio.svelte';
</script>

<div class="background"><Background /></div>
<div class="WebHead">
	<ArrowClosCss />
	<Menu />
</div>

<div class="seeMyWork">
	<div class="textLandingPage"><TextLandingPange /></div>
	<div class="heroButton"><HeroButton /></div>
</div>

<div><Portfolio /></div>

<style>
	.WebHead {
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		margin-top: 20px;
	}

	.background {
		position: absolute;
		right: 35px;
		top: 40px;
		scale: 120%;
	}

	.heroButton {
		scale: 80%;
		margin-top: 40px;
	}

	.textLandingPage {
		color: rgb(9, 39, 56);
		font-family: Heebo, HElvetica, Arial;
		padding-left: 10%;
		padding-top: 6%;
	}
	.seeMyWork {
		padding-top: 7%;
		padding-left: 3%;
	}
</style>
