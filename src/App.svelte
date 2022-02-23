<script>
	// let name = "Jack Ma"
	// let skill = {
	// 	namaSkill : "web dev",
	// 	reting : 20
	// }
	// deklarasi data object = skill.namaSkill

	import Navigationbar from "./components/NavigationBar.svelte";
	import Card from "./components/Card.svelte";
	import { Col, Container, Row, ListGroup } from 'sveltestrap';
	import { Button } from 'sveltestrap';
	import ListItem from './components/listItem.svelte';
	import Welcome from './components/Welcome.svelte';
	import Table from './components/Table.svelte';

	const colors = [
		'primary',
	];


	// REACTIVITY, menggunakan $:
	let keranjang = 0;
	let harga = 1000000

	const diskon = {
		beli3 : 0.1,
		beli10 : 0.3
	}

	$: hargaTotal = keranjang  * harga

	$: if (keranjang >= 10) {
		hargaTotal = keranjang * harga - keranjang * harga * diskon.beli10
	} else if (keranjang >= 3) {
		hargaTotal = keranjang * harga - keranjang * harga * diskon.beli3
	}

	function belanja(){
		keranjang += 1
	}
	

	// PROPS atau Property menggunakan export
	// data dibuat dalam bentuk array
	// selebihnya ada di Component/listitem.svelte
	const handPhone = {
		namaProduk: "Iphone 12",
		Keterangan: "handphone terbaru"
	}  


	// Conditional View (berdasarkan role masing2)
	// selebihnya ada di Component/welcome.svelte
	let user = {
		user: "rama",
		role: 2
	}

	// looping
	// ada pada komponen table.svelte

</script>

<main>

	<div id="Navbar">
		<Navigationbar/>
	</div>
	<Welcome {...user}/>
	<div id="content">
		<Card/>
		<Card/>
		<Card/>
		<Card/>
	</div>


	<!--Reactivity-->
	<Container>
		<h2>Reactivity</h2>
		<Row>
			{#each colors as color}
				<Col><Button on:click={belanja} outline {colors} >add to chart</Button></Col>
			{/each}
			<Col>
				jumlah belanja  : {keranjang} <br>
				Total Harga 	: {hargaTotal} 
			</Col>
		  </Row>
	</Container>


	<!--Props-->
	<Container>
		<h2>Props</h2>
		<Row>
			<Col>
				<ListGroup>
					<ListItem namaProduk ={'Samsung A51'}/>
					<ListItem namaProduk ={'Samsung A52'}/>
					<ListItem {...handPhone}/>
					<ListItem namaProduk = {handPhone.namaProduk} Keterangan = {handPhone.Keterangan}/>
					<ListItem/>
				</ListGroup>
			</Col>
		</Row>
	</Container>


	<!-- looping -->
	<Container>
		<h2>looping</h2>
		<Table/>
	</Container>

</main>

<style>
	#content {
		margin: 20px;
		display: flex;
		gap: 12px;
	}
	h2{
		margin-top: 30px;
		margin-bottom: 30px;
	}
</style>