<script>
	import { getContext } from "svelte";
	import Projects from "$components/Projects.svelte";
	import Awards from "$components/Awards.svelte";
	import Clients from "$data/clients.csv"
	import AwardsData from "$data/awards.csv"

	// import Footer from "$components/Footer.svelte";

	// const copy = getContext("copy");
	// const data = getContext("data");
	
</script>
<div class="wrapper">
	<h1>Matt is visual journalist based in Detroit, reporting on stories that struggle to be told with prose alone.</h1>
	<h1 class="transition">To advance the craft of visual storytelling, he founded two organizations...</h1>
	<div class="orgs">
		<div class="org">
			<h3><a target="_blank" href="https://polygraph.cool">Polygraph</a></h3>
			<p>Data Visualization Studio <span>(Est. 2015)</span></p>
			<p class="subhead">Clients</p>
			<div class="clients">
				{#each Clients as client}
					<p>{client["client"]}</p>
				{/each}
			</div>


		</div>
		<div class="org">
			<h3><a target="_blank" href="https://pudding.cool">The Pudding</a></h3>
			<p>Digital Journal for Visual Essays <span>(Est. 2017)</span></p>
			<p class="subhead">Awards</p>
			<div class="pudding-awards">
				{#each AwardsData.filter(d => d.type == "editorial").sort((a,b) => +b.year - +a.year) as award}
					<p>{award.text}, {award.year}</p>
				{/each}
			</div>
		</div>
	</div>

	<h3>Individual Awards</h3>
	<Awards data={AwardsData.filter(d => d.type == "individual").sort((a,b) => +b.year - +a.year)}/>
	<h3>Projects</h3>
	<Projects />	
</div>


<style>
	.clients, .pudding-awards {
		margin-top: 10px;
	}
	.clients {
		display: grid;
		grid-template-columns: 1fr 1fr;
		grid-auto-flow: row;
		column-gap: 10px;
	}
	.clients p, .pudding-awards p {
		font-size: 14px;
		font-weight: 900;
		margin: 0;
		margin-bottom: 5px;
		opacity: .7;
	}
	.org p span {
		opacity: .8;
		font-size: 14px;
		font-style: italic;
	}
	
	li {
		font-size: 16px;
		font-weight: 700;
	}
	.org .subhead {
		margin-top: 30px;
	}
	.orgs {
		margin-bottom: 50px;
		display: grid;
		margin-top: 50px;
		column-gap: 20px;
		grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
	}
	a {
		border: none;
		text-decoration: underline;
		text-decoration-color: rgba(0,0,0,1);
		text-decoration-thickness: from-font;
	}
	.transition {
		/* font-size: 22px; */
		/* max-width: 500px; */
		opacity: .7;
	}
	.wrapper {
		width: calc(100% - 50px);
		margin: 0 auto;
		max-width: 1200px;
		margin-top: 100px;
	}
	h1 {
		font-size: 48px;
		letter-spacing: -1px;
		line-height: 1.1;
		font-weight: 700;
	}
	h3 {
		font-weight: 700;
	}
</style>
<!-- <Footer /> -->
