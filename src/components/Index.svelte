<script>
	import { getContext } from "svelte";
	import Projects from "$components/Projects.svelte";
	// import Footer from "$components/Footer.svelte";

	// const copy = getContext("copy");
	// const data = getContext("data");
</script>
<div class="wrapper">
	<h1>Matt is a visual journalist reporting on stories that struggle to be told with prose alone.</h1>
	<h3>PROJECTS</h3>
	<Projects />	
</div>


<style>
	.wrapper {
		width: calc(100% - 50px);
		margin: 0 auto;
		max-width: 1200px;
	}
	h1 {
		font-size: 48px;
		letter-spacing: -1.6px;
		margin-bottom: 100px;
		line-height: 1.1;
		font-weight: 700;
	}
	h3 {
		font-weight: 700;
		text-decoration: underline;
		text-decoration-thickness: from-font;
    	text-decoration-style: double;
	}
</style>
<!-- <Footer /> -->
